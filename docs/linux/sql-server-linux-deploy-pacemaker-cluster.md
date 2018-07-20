---
title: Bereitstellen ein Pacemaker-Clusters für SQL Server unter Linux | Microsoft-Dokumentation
description: In diesem Tutorial zeigt, wie Sie einen Pacemaker-Cluster für SQL Server unter Linux bereitstellen.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/11/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: afb076c2883751728c6528dc1a2266b8ec214895
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087232"
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>Bereitstellen eines Pacemaker-Clusters für SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieses Tutorial beschreibt die erforderlichen Aufgaben zum Bereitstellen eines Linux Pacemaker-Clusters für eine [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Always On-verfügbarkeitsgruppe (AG) oder einer Failoverclusterinstanz (FCI). Im Gegensatz zu den eng verknüpfte Windows-Server /[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Stapel, Erstellung eines Pacemaker-Clusters als auch (AG) Konfiguration von Verfügbarkeitsgruppen unter Linux kann durchgeführt werden, vor oder nach der Installation von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Die Integration und die Konfiguration von Ressourcen für den Pacemaker-Teil einer Verfügbarkeitsgruppe oder einer FCI-Bereitstellung wird ausgeführt, nachdem der Cluster konfiguriert ist.
> [!IMPORTANT]
> Eine Verfügbarkeitsgruppe mit dem Clustertyp None ist *nicht* erfordern einen Pacemaker-Cluster, noch kann er von Pacemaker verwaltet werden. 

> [!div class="checklist"]
> * Installieren Sie das Add-on für hochverfügbarkeit und installieren Sie Pacemaker.
> * Bereiten Sie den Knoten für Pacemaker (RHEL und nur für Ubuntu) vor.
> * Erstellen des Pacemaker-Clusters an.
> * Installieren Sie die SQL Server-HA- und SQL Server-Agent-Pakete.
 
## <a name="prerequisite"></a>Voraussetzung
[Installieren von SQLServer 2017](sql-server-linux-setup.md).

## <a name="install-the-high-availability-add-on"></a>Installieren Sie das Add-on für hochverfügbarkeit
Verwenden Sie die folgende Syntax, um die Pakete zu installieren, die die hochverfügbarkeit (HA)-Add-On für jede Linux-Distribution bilden. 

**Red Hat Enterprise Linux (RHEL)**
1.  Registrieren Sie den Server, die mit der folgenden Syntax an. Sie werden für einen gültigen Benutzernamen und Kennwort aufgefordert.
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  Listet die verfügbare Pools für die Registrierung.
    
    ```bash
    sudo subscription-manager list --available
    ```

3.  Führen Sie den folgenden Befehl zum Zuordnen von RHEL-hochverfügbarkeit mit dem Abonnement
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    wo *PoolId* ist die Pool-ID für das Abonnement "hochverfügbarkeit" aus dem vorherigen Schritt.
    
4.  Aktivieren Sie das Repository, um das Add-on für hochverfügbarkeit verwenden zu können.
    
    ```bash
    sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
    ```
    
5.  Installieren Sie Pacemaker.
    
    ```bash
    sudo yum install pacemaker pcs fence-agents-all resource-agents
    ```

**Ubuntu**

```bash
sudo apt-get install pacemaker pcs fence-agents resource-agents
```

**SUSE Linux Enterprise Server (SLES)**

Installieren Sie das Muster für hohe Verfügbarkeit in YaST zu oder es als Teil der Basisinstallation des Servers. Die Installation kann mit einer ISO/DVD als Quelle oder indem Sie es online abrufen erfolgen.
> [!NOTE]
> Unter SLES ruft der HA-Add-On initialisiert, wenn der Cluster erstellt wird.

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>Vorbereiten der Knotens für Pacemaker (RHEL und nur für Ubuntu)
Pacemaker verwendet die Erstellung der Verteilung, die mit dem Namen ein Benutzers *"hacluster"*. Der Benutzer wird erstellt, wenn die HA-Add-On für RHEL und Ubuntu installiert ist.
1. Erstellen Sie auf jedem Server, die als einen Knoten des Pacemaker-Clusters verwendet wird das Kennwort für einen Benutzer, die vom Cluster verwendet werden. Der Name in den Beispielen verwendete *"hacluster"*, aber einen beliebigen Namen verwendet werden kann. Den Namen und das Kennwort müssen auf allen Knoten, die Teil des Pacemaker-Clusters identisch sein.
   
    ```bash
    sudo passwd hacluster
    ```
    
2. Aktivieren Sie auf jedem Knoten, die Teil des Pacemaker-Clusters sein wird, und starten Sie den `pcsd` Dienst mit den folgenden Befehlen (RHEL und Ubuntu):

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   Führen Sie dann
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   um sicherzustellen, dass `pcsd` gestartet wird.
3. Aktivieren Sie den Pacemaker-Dienst auf jedem möglichen Knoten des Pacemaker-Clusters.
   
   ```bash
   sudo systemctl start pacemaker
   ```

   Unter Ubuntu können Sie die Fehlermeldung angezeigt:
   
   *Pacemaker-Standard-Start enthält keine Ausführungsstufe, abgebrochen wird.*
   
   Dieser Fehler ist ein bekanntes Problem. Trotz des Fehlers aktivieren den Pacemaker-Dienst erfolgreich ist, und dieser Fehler wird an einem bestimmten Punkt in der Zukunft behoben werden.
   
4. Als Nächstes erstellen Sie und starten Sie den Pacemaker-Cluster. Es ist ein Unterschied zwischen RHEL und Ubuntu in diesem Schritt ein. Klicken Sie auf beiden-Distributionen installieren `pcs` eine standardmäßige Konfigurationsdatei konfiguriert, für die Pacemaker-Clusters unter RHEL, die bei Ausführung dieses Befehls keine vorhandene Konfiguration zerstört, und erstellt einen neuen Cluster.

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>Erstellen Sie den Pacemaker-cluster 
Dieser Abschnitt beschreibt das Erstellen und Konfigurieren des Clusters für jede Linux-Distribution.

**RHEL**

1. Autorisieren Sie die Knoten
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 … NodeN> -u hacluster
   ```
   
   wo *NodeX* ist der Name des Knotens.
2. Erstellen des Clusters
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   wo *PMClusterName* ist der Name des Pacemaker-Clusters und *Nodelist* ist die Liste der Namen der Knoten getrennt durch ein Leerzeichen.

**Ubuntu**

Konfigurieren von Ubuntu ähnelt RHEL. Es ist jedoch einen wesentlichen Unterschied: Installieren der Pacemaker-Pakete erstellt eine Basiskonfiguration für die Cluster, und aktiviert und startet `pcsd`. Wenn Sie versuchen, den Pacemaker-Cluster zu konfigurieren, indem Sie die RHEL-Anweisungen genau befolgen, erhalten Sie eine Fehlermeldung an. Um dieses Problem zu beheben, führen Sie die folgenden Schritte aus: 
1. Entfernen Sie die Pacemaker-Standardkonfiguration auf jedem Knoten.
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. Führen Sie die Schritte im Abschnitt zu RHEL zum Erstellen des Pacemaker-Clusters aus.

**SLES**

Der Prozess zum Erstellen eines Pacemaker-Clusters unterscheidet sich vollständig auf SLES statt für RHEL und Ubuntu. Die folgenden Schritte beschreiben das Erstellen eines Clusters mit SLES.
1. Führen Sie zunächst den Konfigurationsprozess für cluster 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   auf einem der Knoten. Sie werden möglicherweise aufgefordert, dass NTP nicht konfiguriert ist und keine Watchdog-Gerät gefunden wird. Das ist gut für Dinge einrichten und ausführen. Watchdog bezieht sich auf STONITH, wenn Sie integrierte SLESs-Umgrenzung verwenden, die Speicher-basiert ist. NTP und Watchdog können später konfiguriert werden.
   
2. Sie werden aufgefordert, Corosync konfigurieren. Sie werden für die Netzwerkadresse an, sowie die multicast-Adresse und Port binden aufgefordert. Die Netzwerkadresse ist das Subnetz, das Sie verwenden. Beispiel: 192.191.190.0. Sie können die Standardeinstellungen an jeder Eingabeaufforderung oder bei Bedarf ändern.
   
3. Als Nächstes werden Sie aufgefordert, wenn SBD, konfigurieren, ist die datenträgerbasierte Umgrenzung werden sollen. Diese Konfiguration kann bei Bedarf später erfolgen. SBD ist nicht konfiguriert, im Gegensatz zu RHEL und Ubuntu, `stonith-enabled` wird standardmäßig auf "false" festgelegt.
   
4. Schließlich werden Sie aufgefordert, wenn Sie eine IP-Adresse für die Verwaltung konfigurieren möchten. Diese IP-Adresse ist optional, aber es funktioniert ähnlich wie die IP-Adresse für einen Windows Server-Failovercluster (WSFC) in dem Sinne, das erstellt wird eine IP-Adresse des Clusters zum Herstellen einer Verbindung über HA Web Konsole (HAWK) verwendet werden soll. Diese Konfiguration ist ebenfalls optional.
   
5. Stellen Sie sicher, dass der Cluster betriebsbereit hierzu ist 
   ```bash
   sudo crm status
   ```
   
6. Ändern der *"hacluster"* Kennwort 
   ```bash
   sudo passwd hacluster
   ```
   
7. Wenn Sie eine IP-Adresse für die Verwaltung konfiguriert haben, können Sie es testen, in einem Browser, der getestet wird auch die Änderung des Kennworts für *"hacluster"*.
   ![](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. Führen Sie auf einen anderen SLES-Server, der einem Knoten des Clusters sein wird, 
   ```bash
   sudo ha-cluster-join
   ```
   
9. Wenn Sie dazu aufgefordert werden, geben Sie den Namen oder IP-Adresse des Servers, der als erster Knoten des Clusters in den vorherigen Schritten konfiguriert wurde. Der Server wird als Knoten zum vorhandenen Cluster hinzugefügt.
   
10. Stellen Sie sicher, dass der Knoten hierzu hinzugefügt wurde 
   ```bash
   sudo crm status
   ```
   
11. Ändern der *"hacluster"* Kennwort 
   ```bash
   sudo passwd hacluster
   ```
   
12. Wiederholen Sie die Schritte 8 bis 11 für alle anderen Server mit dem Cluster hinzugefügt werden.

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>Installieren Sie die SQL Server-HA- und SQL Server-Agent-Pakete
Verwenden Sie die folgenden Befehle zum Installieren des SQL Server-HA-Pakets und [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -Agent, wenn sie nicht bereits installiert sind. Installieren die HA-Pakets nach der Installation von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] erfordert einen Neustart des [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] dafür verwendet werden. Diese Anweisungen setzen voraus, dass die Repositorys für die Microsoft-Pakete bereits, da festgelegten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] an diesem Punkt installiert werden soll.
> [!NOTE]
> - Wenn Sie nicht verwenden möchten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -Agent, Protokollversand oder jede andere Verwendung, es muss nicht installiert werden, also Packen *Mssql-Server-Agent* übersprungen werden kann.
> - Die optionalen Pakete für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] unter Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Full-Text Search (*Mssql-Server-Volltextsuche*) und [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Integration Services (*Mssql-Server ist*), sind nicht für hohe Verfügbarkeit für eine FCI oder Verfügbarkeitsgruppe erforderlich.

**RHEL**

```bash
sudo yum install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**Ubuntu**

```bash
sudo apt-get install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**SLES**

```bash
sudo zypper install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie einen Pacemaker-Cluster für SQL Server unter Linux bereitstellen. Sie haben gelernt, wie auf:
> [!div class="checklist"]
> * Installieren Sie das Add-on für hochverfügbarkeit und installieren Sie Pacemaker.
> * Bereiten Sie den Knoten für Pacemaker (RHEL und nur für Ubuntu) vor.
> * Erstellen des Pacemaker-Clusters an.
> * Installieren Sie die SQL Server-HA- und SQL Server-Agent-Pakete.

Zum Erstellen und Konfigurieren einer verfügbarkeitsgruppe für SQL Server unter Linux, finden Sie unter:

> [!div class="nextstepaction"]
> [Erstellen und konfigurieren Sie eine verfügbarkeitsgruppe für SQL Server unter Linux](sql-server-linux-create-availability-group.md).

