---
title: Konfigurieren von Verfügbarkeitsgruppen und Failoverclusterinstanzen für mehrere Subnetze (Linux)
description: In diesem Artikel erfahren Sie, wie Sie Always On-Verfügbarkeitsgruppen und Failoverclusterinstanzen für mehrere Subnetze für SQL Server für Linux konfigurieren.
ms.custom: seo-lt-2019
author: liweiSecurity
ms.author: liweiyin
ms.reviewer: VanMSFT
ms.date: 07/28/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 5abe1d99f753e0f41ca74a0864079293800dc1df
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362971"
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>Konfigurieren von Always On-Verfügbarkeitsgruppen für und Failoverclusterinstanzen für Multisubnetze

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Wenn eine Always On-Verfügbarkeitsgruppe (Availability Group, AG) oder eine Failoverclusterinstanz (FCI) mehrere Standorte umfasst, verfügt jeder Standort in der Regel über ein eigenes Netzwerk. Dies bedeutet häufig, dass jeder Standort über eine eigene IP-Adressierung verfügt. Beispielsweise beginnen die Adressen von Standort A mit 192.168.1*x* und die Adressen von Standort B mit 192.168.2.*x*, wobei *x* der Teil der IP-Adresse ist, der für den Server eindeutig ist. Wenn auf der Netzwerkebene kein Routing vorhanden ist, sind diese Server nicht in der Lage, miteinander zu kommunizieren. Es gibt zwei Möglichkeiten, dieses Szenario zu behandeln: richten Sie ein Netzwerk ein, das als Brücke zwischen den beiden unterschiedlichen Subnetzen dient – auch als VLAN bezeichnet – oder konfigurieren Sie das Routing zwischen den Subnetzen.

## <a name="vlan-based-solution"></a>VLAN-basierte Lösung
 
**Voraussetzung**: Bei einer VLAN-basierten Lösung benötigt jeder Server, der zu einer Verfügbarkeitsgruppe oder FCI gehört, zwei Netzadapter (NICs) für die ordnungsgemäße Verfügbarkeit (ein Dualanschluss-NIC wäre auf einem physischen Server ein Single Point of Failure), sodass Ihm IP-Adressen sowohl in seinem nativen Subnetz als auch dem VLAN zugewiesen werden können. Dies gilt zusätzlich zu allen anderen Netzwerkanforderungen, z.B. iSCSI, die auch ein eigenes Netzwerk benötigen.

Die IP-Adresserstellung für die Verfügbarkeitsgruppe oder FCI erfolgt im VLAN. Im folgenden Beispiel weist das VLAN ein Subnetz von 192.168.3*x*auf, daher lautet die für die Verfügbarkeitsgruppe oder FCI erstellte IP-Adresse 192.168.3.104. Es müssen keine zusätzlichen Elemente konfiguriert werden, da der Verfügbarkeitsgruppe oder FCI eine einzelne IP-Adresse zugewiesen ist.

![Konfigurieren mehrerer Subnetze 01](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Konfiguration mit Pacemaker

In der Windows-Welt unterstützt ein Windows Server-Failovercluster (WSFC) nativ mehrere Subnetze und verarbeitet mehrere IP-Adressen über eine OR-Abhängigkeit der IP-Adresse. Unter Linux gibt es keine OR-Abhängigkeit, aber es gibt eine Möglichkeit, ein ordnungsgemäßes Multisubnetz nativ mit Pacemaker zu erreichen, wie im Folgenden gezeigt. Hierfür können Sie nicht einfach die normale Pacemaker-Befehlszeile verwenden, um eine Ressource zu ändern. Sie müssen die Clusterinformationenbasis (CIB) ändern. Die CIB ist eine XML-Datei mit der Pacemaker-Konfiguration.

![Konfigurieren mehrerer Subnetze 02](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>Aktualisieren der CIB

1. Exportieren Sie die CIB.

    **Red Hat Enterprise Linux (RHEL) und Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    Wobei *filename* der Name ist, den Sie als CIB bezeichnen möchten.

2. Bearbeiten Sie die generierte Datei. Suchen Sie nach dem `<resources>`-Abschnitt. Die verschiedenen Ressourcen, die für die Verfügbarkeitsgruppe oder FCI erstellt wurden, werden angezeigt. Suchen Sie diejenige, die der IP-Adresse zugeordnet ist. Fügen Sie einen `<instance attributes>`-Abschnitt mit den Informationen für die zweite IP-Adresse hinzu, entweder oberhalb oder unterhalb der vorhandenen IP-Adresse, jedoch vor `<operations>`. Dies ähnelt der folgenden Syntax:

    ```xml
    <instance attributes id="<NameForAttribute>">
        <nvpair id="<NameForIP>" name="ip" value="<IPAddress>"/>
    </instance attributes>
    ```
    
    Hier entspricht *NameForAttribute* dem eindeutigen Namen dieses Attributs, *NameForIP* entspricht dem Namen, der der IP-Adresse zugeordnet ist, und *IPAddress* entspricht der IP-Adresse für das zweite Subnetz.
    
    Die Folgenden wird ein Beispiel gezeigt.
    
    ```xml
    <instance attributes id="virtualip-instance_attributes">
        <nvpair id="virtualip-instance_attributes-ip" name="ip" value="192.168.1.102"/>
    </instance attributes>
    ```
    
    Standardmäßig enthält die exportierte CIB XML-Datei nur eine Instanz (<instance/>). Angenommen, es gibt zwei Subnetze, die zwei <instance/>-Einträge enthalten sollen.
    Hier sehen Sie ein Beispiel für die Einträge für zwei Subnetze:
    
    ```xml
    <instance attributes id="virtualip-instance_attributes1">
        <rule id="Subnet1-IP" score="INFINITY" boolean-op="or">
            <expression id="Subnet1-Node1" attribute="#uname" operation="eq" value="Node1" />
            <expression id="Subnet1-Node2" attribute="#uname" operation="eq" value="Node2" />
        </rule>
        <nvpair id="IP-In-Subnet1" name="ip" value="192.168.1.102"/>
    </instance attributes>
    <instance attributes id="virtualip-instance_attributes2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node1" attribute="#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet2" name="ip" value="192.168.2.102"/>
    </instance attributes>
    ```
   
   In diesem Beispiel wird „boolean-op="or"“ verwendet, wenn das Subnetz über mehr als einen Server verfügt.


3. Importieren Sie die geänderte CIB, und konfigurieren Sie Pacemaker neu.

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

1. Nachdem die CIB mit der aktualisierten Konfiguration erfolgreich angewendet wurde, pingen Sie den DNS-Namen, der mit der IP-Adressressource in Pacemaker verknüpft ist. Dies sollte die IP-Adresse des Subnetzes widerspiegeln, das zurzeit die Verfügbarkeitsgruppe oder FCI hostet.

2. Führen Sie ein Failover der Verfügbarkeitsgruppe oder FCI zum anderen Subnetz aus.

3. Nachdem die Verfügbarkeitsgruppe oder FCI vollständig online ist, pingen Sie den DNS-Namen, der der IP-Adresse zugeordnet ist. Er sollte die IP-Adresse im zweiten Subnetz widerspiegeln.

4. Falls gewünscht, führen Sie ein Failback der Verfügbarkeitsgruppe oder FCI zum ursprünglichen Subnetz aus.

Im folgenden CSS-Beitrag wird ausführlich veranschaulicht, wie die CIB für drei Subnetze erstellt wird: [Konfigurieren der AlwaysOn-Verfügbarkeitsgruppe für mehrere Subnetze durch Bearbeiten der CIB](https://techcommunity.microsoft.com/t5/sql-server-support/configure-multiple-subnet-alwayson-availability-groups-by/ba-p/1544838).
