---
title: Konfigurieren von Verfügbarkeitsgruppen und Failoverclusterinstanzen für mehrere Subnetze (Linux)
description: In diesem Artikel erfahren Sie, wie Sie Always On-Verfügbarkeitsgruppen und Failoverclusterinstanzen für mehrere Subnetze unter Linux konfigurieren.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 12/01/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: f35f1916107e8ede0e7bf7cc3df483a0c33f3355
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75558609"
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>Konfigurieren von Always On-Verfügbarkeitsgruppen für und Failoverclusterinstanzen für Multisubnetze

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Wenn eine Always On-Verfügbarkeitsgruppe (Availability Group, AG) oder eine Failoverclusterinstanz (FCI) mehrere Standorte umfasst, verfügt jeder Standort in der Regel über ein eigenes Netzwerk. Dies bedeutet häufig, dass jeder Standort über eine eigene IP-Adressierung verfügt. Beispielsweise beginnen die Adressen von Standort A mit 192.168.1*x* und die Adressen von Standort B mit 192.168.2.*x*, wobei *x* der Teil der IP-Adresse ist, der für den Server eindeutig ist. Wenn auf der Netzwerkebene kein Routing vorhanden ist, sind diese Server nicht in der Lage, miteinander zu kommunizieren. Es gibt zwei Möglichkeiten, dieses Szenario zu behandeln: richten Sie ein Netzwerk ein, das als Brücke zwischen den beiden unterschiedlichen Subnetzen dient – auch als VLAN bezeichnet – oder konfigurieren Sie das Routing zwischen den Subnetzen.

## <a name="vlan-based-solution"></a>VLAN-basierte Lösung
 
**Voraussetzung**: Bei einer VLAN-basierten Lösung benötigt jeder Server, der zu einer Verfügbarkeitsgruppe oder FCI gehört, zwei Netzadapter (NICs) für die ordnungsgemäße Verfügbarkeit (ein Dualanschluss-NIC wäre auf einem physischen Server ein Single Point of Failure), sodass Ihm IP-Adressen sowohl in seinem nativen Subnetz als auch dem VLAN zugewiesen werden können. Dies gilt zusätzlich zu allen anderen Netzwerkanforderungen, z.B. iSCSI, die auch ein eigenes Netzwerk benötigen.

Die IP-Adresserstellung für die Verfügbarkeitsgruppe oder FCI erfolgt im VLAN. Im folgenden Beispiel weist das VLAN ein Subnetz von 192.168.3*x*auf, daher lautet die für die Verfügbarkeitsgruppe oder FCI erstellte IP-Adresse 192.168.3.104. Es müssen keine zusätzlichen Elemente konfiguriert werden, da der Verfügbarkeitsgruppe oder FCI eine einzelne IP-Adresse zugewiesen ist.

![](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Konfiguration mit Pacemaker

In der Windows-Welt unterstützt ein Windows Server-Failovercluster (WSFC) nativ mehrere Subnetze und verarbeitet mehrere IP-Adressen über eine OR-Abhängigkeit der IP-Adresse. Unter Linux gibt es keine OR-Abhängigkeit, aber es gibt eine Möglichkeit, ein ordnungsgemäßes Multisubnetz nativ mit Pacemaker zu erreichen, wie im Folgenden gezeigt. Hierfür können Sie nicht einfach die normale Pacemaker-Befehlszeile verwenden, um eine Ressource zu ändern. Sie müssen die Clusterinformationenbasis (CIB) ändern. Die CIB ist eine XML-Datei mit der Pacemaker-Konfiguration.

![](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>Aktualisieren der CIB

1.  Exportieren Sie die CIB.

    **Red Hat Enterprise Linux (RHEL) und Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    Wobei *filename* der Name ist, den Sie als CIB bezeichnen möchten.

2.  Bearbeiten Sie die generierte Datei. Suchen Sie nach dem `<resources>`-Abschnitt. Die verschiedenen Ressourcen, die für die Verfügbarkeitsgruppe oder FCI erstellt wurden, werden angezeigt. Suchen Sie diejenige, die der IP-Adresse zugeordnet ist. Fügen Sie einen `<instance attributes>`-Abschnitt mit den Informationen für die zweite IP-Adresse hinzu, entweder oberhalb oder unterhalb der vorhandenen IP-Adresse, jedoch vor `<operations>`. Dies ähnelt der folgenden Syntax:

    ```xml
    <instance attributes id="<NameForAttribute>" score="<Score>">
        <rule id="<RuleName>" score="INFINITY">
            <expression id="<ExpressionName>" attribute="\#uname" operation="eq" value="<NodeNameInSubnet2>" />
        </rule>
        <nvpair id="<NameForSecondIP>" name="ip" value="<IPAddress>"/>
        <nvpair id="<NameForSecondIPNetmask>" name="cidr\_netmask" value="<Netmask>"/>
    </instance attributes>
    ```
    
    wobei *NameForAttribute* der eindeutige Name für dieses Attribut ist, *Score* ist die Nummer, die dem Attribut zugewiesen ist, die höher sein muss als die des primären Subnetzes, *RuleName* ist der Name der Regel, *ExpressionName* ist der Name des Ausdrucks, *NodeNameInSubnet2* ist der Name des Knotens im anderen Subnetz, *NameForSecondIP* ist der Name, der der zweiten IP-Adresse zugeordnet ist, *IPAddress* ist die IP-Adresse für das zweite Subnetz, *NameForSecondIPNetmask* ist der Name, der der Netzmaske zugeordnet ist, und *Netmask* ist die Netzmaske für das zweite Subnetz.
    
    Die Folgenden wird ein Beispiel gezeigt.
    
    ```xml
    <instance attributes id="Node3-2nd-IP" score="2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node" attribute="\#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet-2" name="ip" value="192.168.2.102"/>
        <nvpair id="Netmask-For-IP2" name="cidr\_netmask" value="24" />
    </instance attributes>
    ```

3.  Importieren Sie die geänderte CIB, und konfigurieren Sie Pacemaker neu.

    **RHEL/Ubuntu**
    
    ```bash
    sudo pcs cluster cib-push <filename>
    ```

    **SLES**
    
    ```bash
    sudo cibadmin -R -x <filename>
    ```

    wobei *filename* der Name der CIB-Datei mit den geänderten IP-Adressinformationen ist.

### <a name="check-and-verify-failover"></a>Überprüfen des Failovers

1.  Nachdem die CIB mit der aktualisierten Konfiguration erfolgreich angewendet wurde, pingen Sie den DNS-Namen, der mit der IP-Adressressource in Pacemaker verknüpft ist. Dies sollte die IP-Adresse des Subnetzes widerspiegeln, das zurzeit die Verfügbarkeitsgruppe oder FCI hostet.
2.  Führen Sie ein Failover der Verfügbarkeitsgruppe oder FCI zum anderen Subnetz aus.
3.  Nachdem die Verfügbarkeitsgruppe oder FCI vollständig online ist, pingen Sie den DNS-Namen, der der IP-Adresse zugeordnet ist. Er sollte die IP-Adresse im zweiten Subnetz widerspiegeln.
4.  Falls gewünscht, führen Sie ein Failback der Verfügbarkeitsgruppe oder FCI zum ursprünglichen Subnetz aus.
