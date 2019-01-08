---
title: Konfigurieren von mehreren Subnetzen AlwaysOn-Verfügbarkeitsgruppen und Failoverclusterinstanzen unter Linux | Microsoft-Dokumentation
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/1/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 595add5d077136c4093776fae8e3a2f7ab04bb26
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52396173"
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>Konfigurieren von mehreren Subnetzen AlwaysOn-Verfügbarkeitsgruppen und Failoverclusterinstanzen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Wenn eine Always On Availability Group (-Verfügbarkeitsgruppen) oder ein Failover Cluster-Instanz (FCI) mehr als ein Standort, der jeder Standort in der Regel umfasst verfügt über eigene Netzwerke aus. Dies bedeutet häufig, dass jeder Standort eine eigene IP-Adressen hat. Starten z. B. Standort A-Adressen mit 192.168.1 aufweisen. *x* und Standort B Adressen mit 192.168.2 zu beginnen. *X*, wobei *x* ist der Teil der IP-Adresse, die für den Server eindeutig ist. Ohne irgendein auf Netzwerkebene direktes routing werden dieser Server nicht miteinander kommunizieren können. Es gibt zwei Möglichkeiten zum Behandeln dieses Szenarios: Einrichten eines Netzwerks, das die zwei verschiedenen Subnetzen, bekannt als ein VLAN verbindet, oder Konfigurieren des Routings zwischen den Subnetzen.

## <a name="vlan-based-solution"></a>VLAN-basierte Lösung
 
**Erforderliche**: Für eine VLAN-basierte Lösung benötigt jeder Server, die Teil einer Verfügbarkeitsgruppe oder FCI zwei Netzwerkkarten (NICs) für eine ordnungsgemäße Verfügbarkeit (zwei Ports NIC wäre eine einzelne Fehlerquelle auf einem physischen Server), damit dieser IP-Adressen auf einem systemeigenen Subnetz als auch zugewiesen werden kann Klicken Sie auf das VLAN. Dies erfolgt zusätzlich zu anderen netzwerkanforderungen, wie z. B. iSCSI, die auch ein eigenen Netzwerk benötigt.

Die Erstellung der IP-Adresse für die Verfügbarkeitsgruppe oder FCI wird auf das VLAN ausgeführt. Im folgenden Beispiel hat das VLAN ein Subnetz mit 192.168.3. *x*, sodass die IP-Adresse für die Verfügbarkeitsgruppe oder FCI erstellt 192.168.3.104 ist. Keine weiteren Aktionen erforderlich konfiguriert werden, da eine einzelne IP-Adresse, die die Verfügbarkeitsgruppe oder FCI zugewiesen ist.

![](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Mit der Pacemaker

In der Windows-Welt wird ein Windows Server Failover Cluster (WSFC) nativ mehrere Subnetze unterstützt, und mehrere IP-Adressen über einen OR-Abhängigkeit der IP-Adresse behandelt. Unter Linux es gibt keine OR-Abhängigkeit, aber gibt es eine Möglichkeit, eine ordnungsgemäße multisubnetz systemintern mit Pacemaker zu erreichen ist, wie im folgenden Beispiel dargestellt. Sie können nicht dazu einfach mit der normalen Pacemaker-Befehlszeile zum Ändern von Ressourcen. Sie müssen die Clusterinformationen Basis (CIB) zu ändern. Die CIB ist eine XML-Datei mit der Pacemaker-Konfiguration.

![](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>Aktualisieren Sie die CIB

1.  Exportieren Sie die CIB.

    **Red Hat Enterprise Linux (RHEL) und Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    Wo *Filename* ist der Name der CIB aufgerufen werden soll.

2.  Bearbeiten Sie die Datei, die generiert wurde. Suchen Sie nach der `<resources>` Abschnitt. Sie sehen die verschiedenen Ressourcen, die für die Verfügbarkeitsgruppe oder FCI erstellt wurden. Suchen der IP-Adresse zugeordnet. Hinzufügen einer `<instance attributes>` im Abschnitt mit den Informationen für die zweite IP-Adresse oberhalb oder unterhalb der vorhandenen Dateigruppe, jedoch bevor `<operations>`. Es ähnelt der folgenden Syntax:

    ```xml
    <instance attributes id="<NameForAttribute>" score="<Score>">
        <rule id="<RuleName>" score="INFINITY">
            <expression id="<ExpressionName>" attribute="\#uname" operation="eq" value="<NodeNameInSubnet2>" />
        </rule>
        <nvpair id="<NameForSecondIP>" name="ip" value="<IPAddress>"/>
        <nvpair id="<NameForSecondIPNetmask>" name="cidr\_netmask" value="<Netmask>"/>
    </instance attributes>
    ```
    
    in denen *NameForAttribute* ist der eindeutige Name für dieses Attribut, *Bewertung* ist das Attribut, das höher als die primären Subnetzes sein muss, zugewiesene Nummer *RuleName*ist der Name der Regel *ExpressionName* ist der Name des Ausdrucks *NodeNameInSubnet2* ist der Name des Knotens in das andere Subnetz *NameForSecondIP* ist der Name der zweiten IP-Adresse zugeordnet *IP-Adresse* ist die IP-Adresse des zweiten Subnetzes *NameForSecondIPNetmask* ist der Name, der die Netzmaske, zugeordnet und *Netzmaske* die Netzmaske für das zweite Subnetz ist.
    
    Das folgende Beispiel zeigt ein Beispiel aus.
    
    ```xml
    <instance attributes id="Node3-2nd-IP" score="2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node" attribute="\#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet-2" name="ip" value="192.168.2.102"/>
        <nvpair id="Netmask-For-IP2" name="cidr\_netmask" value="24" />
    </instance attributes>
    ```

3.  Importieren Sie die geänderte CIB, und konfigurieren Sie Pacemaker.

    **RHEL/Ubuntu**
    
    ```bash
    sudo pcs cluster cib-push <filename>
    ```

    **SLES**
    
    ```bash
    sudo cibadmin -R -x <filename>
    ```

    wo *Filename* ist der Name der Datei CIB durch die geänderte IP-Adressinformationen.

### <a name="check-and-verify-failover"></a>Überprüfen Sie, und überprüfen Sie failover

1.  Nachdem die CIB mit der aktualisierten Konfiguration wurde erfolgreich angewendet wurde, Pingen Sie den DNS-Namen, die die IP-Adressressource in Pacemaker zugeordnet. Sie sollten die IP-Adresse, die dem Subnetz, das derzeit gehostet wird, die Verfügbarkeitsgruppe oder FCI zugeordnet widerspiegeln.
2.  Fehlschlagen der AG und FCI dem anderen Subnetz an.
3.  Nachdem die Verfügbarkeitsgruppe oder FCI vollständig online ist, Pingen Sie den DNS-Namen der IP-Adresse zugeordnet. Sie sollten die IP-Adresse des zweiten Subnetzes widerspiegeln.
4.  Falls gewünscht, führen Sie die Verfügbarkeitsgruppe oder FCI Failback zu das ursprüngliche Subnetz an.
