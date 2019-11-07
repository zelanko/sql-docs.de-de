---
title: Planen des Nachweises des Host-Überwachungsdiensts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/12/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: rpsqrd
ms.author: ryanpu
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 439dd1e7cafd6d0766668188660aaedaffca8ca3
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73595635"
---
# <a name="plan-for-host-guardian-service-attestation"></a>Planen des Nachweises des Host-Überwachungsdiensts

[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

Wenn Sie [Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md) verwenden, möchten Sie sicherstellen, dass Ihre Clientanwendung innerhalb des [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Prozesses mit einer vertrauenswürdigen Enclave-Instanz kommuniziert. Für eine virtualisierungsbasierte Sicherheits-Enclave (Virtualization-based Security, VBS) beinhaltet dies die Überprüfung, ob der Code innerhalb der Enclave gültig ist und ob der Computer, der [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] hostet, vertrauenswürdig ist. Der Remotenachweis erreicht dieses Ziel durch die Einführung einer dritten Instanz, die die Identität (und optional die Konfiguration) des [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computers überprüfen kann. Bevor [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] eine Enclave für eine Abfrage nutzen kann, müssen dem Nachweisdienst Informationen über deren Betriebsumgebung zur Verfügung gestellt werden, um ein Integritätszertifikat zu erhalten. Dieses Integritätszertifikat wird dann an den Client gesendet, der unabhängig davon dessen Authentizität mit dem Nachweisdienst überprüfen kann. Sobald das Integritätszertifikat vom Client als vertrauenswürdig eingestuft wurde, wird auch die VBS-Enclave als vertrauenswürdig erkannt und eine Abfrage ausgegeben, die diese Enclave verwendet.

Die Rolle „Host-Überwachungsdienst“ (HGS) in Windows Server 2019 bietet für Always Encrypted mit VBS-Enclaves die Möglichkeit, Remotenachweise zu erstellen.
Dieser Artikel führt Sie durch die Entscheidungen und Anforderungen bei der Verwendung von Always Encrypted mit VBS-Enclaves und HGS-Nachweis.

## <a name="architecture-overview"></a>Übersicht über die Architektur

Der Host-Überwachungsdienst ist ein gruppierter Webdienst, der unter Windows Server 2019 ausgeführt wird.
Bei einer typischen Bereitstellung gibt es 1 bis 3 HGS-Server, mindestens einen [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer und einen Computer, auf dem eine Clientanwendung oder Tools ausgeführt werden, z. B. SQL Server Management Studio.
Da der HGS dafür verantwortlich ist, zu bestimmen, welche [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer vertrauenswürdig sind, ist eine physische und logische Isolation von der [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Instanz erforderlich, die er schützt.
Wenn dieselben Administratoren Zugriff auf HGS und einen [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer haben, könnten sie den Nachweisdienst so konfigurieren, dass ein bösartiger Computer [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] ausführen kann, wodurch die VBS-Enclave kompromittiert wird.

### <a name="hgs-domain"></a>HGS-Domäne

Das HGS-Setup erstellt automatisch eine neue Active Directory-Domäne für die HGS-Server, Failoverclusterressourcen und Administratorkonten.

Der Computer mit [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] muss nicht mit einer Domäne verbunden werden, aber wenn er verbunden ist, sollte es eine andere Domäne sein als die, die der HGS-Server verwendet.

### <a name="high-availability"></a>Hohe Verfügbarkeit

Über die HGS-Funktion wird automatisch ein Failovercluster installiert und konfiguriert.
Es wird empfohlen, für Hochverfügbarkeit in einer Produktionsumgebung drei HGS-Server zu verwenden. Weitere Informationen zu der Bestimmung eines Clusterquorums und alternative Konfigurationen, einschließlich zweier Knotencluster mit einem externen Zeugen, finden Sie in der [Dokumentation zu Failoverclustern](https://docs.microsoft.com/windows-server/failover-clustering/manage-cluster-quorum).

Die HGS-Knoten müssen keinen gemeinsamen Speicher nutzen. Eine Kopie der Nachweisdatenbank ist auf jedem HGS-Server gespeichert und wird vom Clusterdienst automatisch über das Netzwerk repliziert.

### <a name="network-connectivity"></a>Netzwerkkonnektivität

Sowohl der SQL-Client als auch [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] müssen in der Lage sein, mit dem HGS über HTTP zu kommunizieren. Wahlweise können Sie den HGS mit einem TLS-Zertifikat konfigurieren, um verschlüsselte HTTPS-Verbindungen zu unterstützen.

In HGS-Servern müssen die einzelnen Knoten im Cluster miteinander verbunden sein, um sicherzustellen, dass die Datenbank des Nachweisdiensts synchron bleibt. Es ist eine bewährte Methode für Failovercluster, die HGS-Knoten in einem Netzwerk für die Clusterkommunikation zu verbinden und ein separates Netzwerk für andere Clients zur Kommunikation mit dem HGS zu verwenden.

### <a name="attestation-modes"></a>Nachweismodi

Wenn ein [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer versucht, einen HGS-Nachweis zu erstellen, wird vom HGS zunächst die Information abgerufen, wie der Nachweis erbracht werden soll.
HGS unterstützt zwei Nachweismodi für die Verwendung mit [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]:

| Nachweismodus | Erklärung |
| ---------------- | ------- |
| TPM | Der TPM-Nachweis (Trusted Platform Module) bietet die stärkste Sicherheit in Bezug auf die Identität und Integrität der Computer, die einen HGS-Nachweis aufweisen. [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] muss auf den Computern ausgeführt werden, damit TPM-Version 2.0 installiert werden kann. Jeder TPM-Chip enthält eine eindeutige und unveränderliche Identität (Endorsement Key), die zum Identifizieren eines bestimmten Computers verwendet werden kann. TPMs messen auch den Startprozess des Computers, wobei Hashes von sicherheitsrelevanten Messungen in Plattformkonfigurationsregistern (PCRs) gespeichert werden, die vom Betriebssystem gelesen, aber nicht geändert werden können. Diese Messungen werden bei der Überprüfung des Nachweises als kryptografischer Beleg verwendet, dass sich ein Computer in der von ihm angegebenen Sicherheitskonfiguration befindet. |
| Hostschlüssel | Ein Hostschlüsselnachweis ist eine einfachere Form des Nachweises, bei der nur die Identität eines Computers mithilfe eines asymmetrischen Schlüsselpaars überprüft wird. Der private Schlüssel wird auf dem Computer gespeichert, auf dem [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] ausgeführt wird, und der öffentliche Schlüssel wird dem HGS bereitgestellt. Die Sicherheitskonfiguration des Computers wird nicht erfasst, und ein TPM 2.0-Chip ist auf dem [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer nicht erforderlich. Es ist wichtig, den privaten Schlüssel zu schützen, der auf dem [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer installiert ist. Anderenfalls kann jeder, der diesen Schlüssel erhält, die Identität eines legitimen [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computers und der VSB-Enclave annehmen, die in [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] ausgeführt wird. |

### <a name="trust-model"></a>Vertrauenswürdiges Modell

Im vertrauenswürdigen Modell der VBS-Enclave werden verschlüsselte Abfragen und Daten in einer softwarebasierten Enclave bewertet, um diese vom Hostbetriebssystem aus zu schützen.
Der Zugriff auf diese Enclave wird durch den Hypervisor auf dieselbe Weise geschützt, wie zwei virtuelle Computer, die auf demselben Computer ausgeführt werden und dabei nicht auf den Arbeitsspeicher des jeweils anderen zugreifen können.
Damit ein Client darauf vertrauen kann, dass er mit einer legitimen Instanz von VBS kommuniziert, müssen Sie einen TPM-basierten Nachweis verwenden, der eine Stammvertrauensstellung mit der Hardware des [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computers herstellt.
Die während des Startvorgangs erfassten TPM-Messungen enthalten den eindeutigen Identitätsschlüssel der VSB-Instanz, um sicherzustellen, dass das Integritätszertifikat nur auf genau diesem Computer gültig ist.
Wenn ein TPM auf einem Computer verfügbar ist, auf dem VSB ausgeführt wird, wird der private Teil des VSB-Identitätsschlüssels außerdem durch das TPM geschützt, sodass niemand die Identität dieser VSB-Instanz annehmen kann.

Ein sicherer Start mit TPM-Nachweis ist erforderlich, damit sichergestellt ist, dass UEFI einen legitimen, von Microsoft signierten Bootloader geladen hat und dass keine Rootkits oder Bootkits den Startvorgang des Hypervisors abgefangen haben.
Außerdem ist ein IOMMU-Gerät standardmäßig erforderlich, um sicherzustellen, dass Enclave-Speicher von Hardwaregeräten mit direktem Speicherzugriff nicht überprüft oder geändert werden können.

Bei allen diesen Schutzmaßnahmen wird davon ausgegangen, dass der [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer ein physischer Computer ist.
Wenn es sich bei dem [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer um eine VM handelt, ist nicht mehr garantiert, dass der VM-Speicher vor einer Überprüfung durch den Hypervisor oder Hypervisoradministrator geschützt ist. Ein Hypervisoradministrator könnte zum Beispiel eine Sicherungskopie vom Arbeitsspeicher des virtuellen Computers erstellen und Zugriff auf die Klartextversion der Abfrage und der Daten in der Enclave erhalten.
Gleichermaßen kann die VM, selbst wenn sie über ein virtuelles TPM verfügt, nur den Zustand und die Integrität des VM-Betriebssystems und der Startumgebung messen.
Der Zustand des Hypervisors, der die VM steuert, kann nicht gemessen werden.

Auch wenn [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] virtualisiert ist, ist die Enclave weiterhin vor Angriffen geschützt, die innerhalb des VM-Betriebssystems ausgeführt werden.
Wenn Sie Ihren Hypervisor oder Cloudanbieter als vertrauenswürdig einstufen und sich in erster Linie über Angriffe auf vertrauliche Daten von Datenbank- und Betriebssystemadministratoren Sorgen machen, kann eine virtualisierte [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Instanz Ihre Anforderungen erfüllen.

Ebenso ist der Hostschlüsselnachweis in Situationen nützlich, in denen kein TPM 2.0-Modul auf dem [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer installiert ist, oder in einem Entwicklungs- bzw. Testszenario, bei dem die Sicherheit nicht ausschlaggebend ist.
Viele der oben genannten Sicherheitsfunktionen, wie ein sicherer Start und ein TPM 1.2-Modul, können Sie weiterhin verwenden, um VBS und das Betriebssystem insgesamt besser zu schützen.
Da es für den HGS jedoch keine Möglichkeit gibt, zu überprüfen, ob der Computer diese Einstellungen tatsächlich mit dem Hostschlüsselnachweis aktiviert hat, ist auf Clientseite nicht sichergestellt, dass der Host tatsächlich alle verfügbaren Schutzfunktionen verwendet.

## <a name="prerequisites"></a>Voraussetzungen

### <a name="hgs-server-prerequisites"></a>Voraussetzungen für HGS-Server

Die Computer, auf denen die Rolle „Host-Überwachungsdienst“ ausgeführt wird, müssen die folgenden Anforderungen erfüllen:

| Komponente | Anforderung |
| --------- | ----------- |
| Betriebssystem | Windows Server 2019 Standard oder Datacenter Edition |
| CPU | 2 Kerne (mindestens), 4 Kerne (empfohlen) |
| RAM | 8 GB (mindestens) |
| NICs | 2 NICs empfohlen (1 für Clusterdatenverkehr, 1 für den HGS-Dienst) |

Der HGS ist aufgrund der Anzahl von Aktionen, die eine Verschlüsselung und Entschlüsselung erfordern, eine CPU-gebundene Rolle.
Durch moderne Prozessoren mit Funktionen für schnellere Kryptografievorgänge, wird die Leistung des HGS erheblich gesteigert.
Für Nachweisdaten müssen nur geringe Speicheranforderungen erfüllt werden, die im Bereich von 10 KB bis 1 MB pro einmaligem Computernachweis liegen.

Stellen Sie keine Verknüpfung des HGS-Computers mit einer Domäne her, bevor Sie beginnen.

### <a name="include-ssnoversion-mdincludesssnoversion-mdmd-computer-prerequisites"></a>Voraussetzungen für [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Computer

Die Computer, auf denen [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] ausgeführt wird, müssen sowohl die [Hardware- und Softwareanforderungen für die Installation von SQL Server](../../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md) als auch die [Hyper-V-Hardwareanforderungen](https://docs.microsoft.com/virtualization/hyper-v-on-windows/reference/hyper-v-requirements#hardware-requirements) erfüllen.

Folgende Anforderungen müssen erfüllt sein:

- [!INCLUDE [sssqlv15-md](../../../includes/sssqlv15-md.md)] oder höher
- Windows 10 Enterprise, Version 1809 oder höher oder Windows Server 2019 Datacenter-Edition. Andere Editionen von Windows 10 und Windows Server unterstützen keinen HGS-Nachweis.
- CPU-Unterstützung für Virtualisierungstechnologien:
  - Intel VT-x mit erweiterten Seitentabellen.
  - AMD-V mit schneller Virtualisierungsindizierung.
  - Wenn Sie [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] auf einem virtuellen Computer ausführen, müssen der Hypervisor und die physische CPU Funktionen für die geschachtelte Virtualisierung bereitstellen. Informationen zu den Vertrauensstellungen beim Ausführen von VSB-Enclaves auf einem virtuellen Computer finden Sie im Abschnitt [Vertrauenswürdiges Modell](#trust-model).
    - Für Hyper-V 2016 oder höher [aktivieren Sie die Erweiterungen für geschachtelte Virtualisierung für den VM-Prozessor](https://docs.microsoft.com/virtualization/hyper-v-on-windows/user-guide/nested-virtualization#configure-nested-virtualization).
    - Wählen Sie in Azure eine VM-Größe aus, die die geschachtelte Virtualisierung unterstützt. Hierzu gehören alle VMs der v3-Serie, z. B. Dv3 und Ev3. Siehe [Erstellen einer schachtelungsfähigen Azure-VM](https://docs.microsoft.com/azure/virtual-machines/windows/nested-virtualization#create-a-nesting-capable-azure-vm).
    - Bei VMware vSphere 6.7 oder höher aktivieren Sie die Unterstützung für virtualisierungsbasierte Sicherheit für den virtuellen Computer, wie in der [VMware-Dokumentation](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-C2E78F3E-9DE2-44DB-9B0A-11440800AADD.html) beschrieben.
    - Andere Hypervisoren und öffentliche Clouds unterstützen möglicherweise Funktionen für eine geschachtelte Virtualisierung, die auch die Nutzung von Always Encrypted mit VSB-Enclaves ermöglichen. Informationen zur Kompatibilität und Konfigurationsanweisungen finden Sie in der Dokumentation zu Ihrer Virtualisierungslösung.
- Wenn Sie einen TPM-Nachweis verwenden möchten, benötigen Sie einen TPM 2.0-Chip (Rev 1.16), der auf dem Server verwendet werden kann. Mit TPM 2.0-Chips (Rev 1.38) funktionieren HGS-Nachweise zurzeit nicht. Außerdem muss das TPM über ein gültiges Endorsement Key-Zertifikat verfügen.

## <a name="devtest-environment-considerations"></a>Überlegungen zu Dev/Test-Umgebungen

Wenn Sie Always Encrypted mit VBS-Enclaves in einer Entwicklungs- oder Testumgebung verwenden und keine Hochverfügbarkeit bzw. keinen sicheren Schutz des Computers benötigen, auf dem [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] ausgeführt wird, können Sie für eine vereinfachte Bereitstellung eines oder mehrere der folgenden Zugeständnisse machen:

- Stellen Sie nur einen HGS-Knoten bereit. Auch wenn über den HGS ein Failovercluster installiert wird, müssen Sie keine zusätzlichen Knoten hinzufügen, solange keine Hochverfügbarkeit erforderlich ist.
- Verwenden Sie den Hostschlüsselmodus anstelle des TPM-Modus, um die Einrichtung zu vereinfachen.
- Virtualisieren Sie den HGS und/oder die [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Instanz, um physische Ressourcen zu sparen.
- Führen Sie SSMS oder andere Tools zum Konfigurieren von Always Encrypted mit Secure Enclaves auf demselben Computer wie [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] aus. Dadurch werden die Spaltenhauptschlüssel auf demselben Computer wie [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] belassen. In einer Produktionsumgebung sollten Sie diesen Schritt daher nicht ausführen.

## <a name="next-steps"></a>Nächste Schritte

- [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)
