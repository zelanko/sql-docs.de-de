---
title: Bereitstellen eines Pacemaker-Clusters für SQL Server für Linux
description: Erfahren Sie, wie Sie einen Linux Pacemaker-Cluster für eine SQL Server-Always On-Verfügbarkeitsgruppe oder -Failoverclusterinstanz bereitstellen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 12/11/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: ebee4156a89a7eb2464abbda997f20a99be30753
ms.sourcegitcommit: 3ea082c778f6771b17d90fb597680ed334d3e0ec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2020
ms.locfileid: "88088922"
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>Bereitstellen eines Pacemaker-Clusters für SQL Server für Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

In diesem Tutorial werden die Aufgaben dokumentiert, die zum Bereitstellen eines Linux Pacemaker-Clusters für eine [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Always On-Verfügbarkeitsgruppe oder eine Failoverclusterinstanz (FCI) durchgeführt werden müssen. Im Gegensatz zum eng gekoppelten Windows Server-/[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Stapel, kann die Erstellung des Pacemaker-Clusters und die Konfiguration der Verfügbarkeitsgruppe unter Linux sowohl vor als auch nach der Installation von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] durchgeführt werden. Die Integration und Konfiguration von Ressourcen für den Pacemaker-Teil der Bereitstellung einer Verfügbarkeitsgruppe oder Failoverclusterinstanz wird abgeschlossen, nachdem der Cluster konfiguriert wurde.
> [!IMPORTANT]
> Eine Verfügbarkeitsgruppe mit dem Clustertyp „None“ (Keiner) erfordert *keinen* Pacemaker-Cluster und kann auch nicht von Pacemaker verwaltet werden. 

> [!div class="checklist"]
> * Installieren von Pacemaker und des Hochverfügbarkeits-Add-Ons
> * Vorbereiten der Knoten für Pacemaker (nur RHEL und Ubuntu)
> * Erstellen eines Pacemaker-Clusters
> * Installieren der SQL Server-Hochverfügbarkeits- und -Agent-Pakete
 
## <a name="prerequisite"></a>Voraussetzung
[Installieren von SQL Server 2017](sql-server-linux-setup.md)

## <a name="install-the-high-availability-add-on"></a>Installieren des Hochverfügbarkeits-Add-Ons
Verwenden Sie die folgende Syntax, um die Pakete zu installieren, aus denen das Hochverfügbarkeits-Add-On für die verschiedenen Verteilungen von Linux besteht. 

**Red Hat Enterprise Linux (RHEL)**
1.  Registrieren Sie den Server mithilfe der folgenden Syntax. Daraufhin werden Sie zur Eingabe eines gültigen Benutzernamens und Kennworts aufgefordert.
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  Listen Sie die verfügbaren Pools für die Registrierung auf.
    
    ```bash
    sudo subscription-manager list --available
    ```

3.  Führen Sie den folgenden Befehl aus, um die Hochverfügbarkeit von RHEL zum Abonnement zuzuordnen:
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    Fügen Sie hierbei für *PoolId* die Pool-ID für das Hochverfügbarkeitsabonnement aus dem vorherigen Schritt ein.
    
4.  Aktivieren Sie die Verwendung des Hochverfügbarkeits-Add-Ons für das Repository.
    
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

Installieren Sie das Hochverfügbarkeitsmuster in YaST oder als Teil der Hauptinstallation des Servers. Die Installation kann mit einer ISO oder DVD als Quelle oder über das Internet durchgeführt werden.
> [!NOTE]
> In SLES wird das Hochverfügbarkeits-Add-On initialisiert, wenn der Cluster erstellt wird.

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>Vorbereiten der Knoten für Pacemaker (nur RHEL und Ubuntu)
Pacemaker verwendet eine von einem Benutzer erstellte Verteilung namens *hacluster*. Der Benutzer wird erstellt, wenn das Hochverfügbarkeits-Add-On unter RHEL und Ubuntu installiert wird.
1. Erstellen Sie auf jedem Server, der als Knoten des Pacemaker-Clusters fungieren soll, die Kennwörter für die Benutzer, die vom Cluster verwendet werden sollen. In den Beispielen dieses Artikels wird der Name *hacluster* verwendet, jedoch kann ein beliebiger Name verwendet werden. Der Name und das Kennwort muss auf allen Knoten, die am Pacemaker-Cluster teilnehmen, identisch sein.
   
    ```bash
    sudo passwd hacluster
    ```
    
2. Aktivieren und starten Sie den `pcsd`-Dienst mithilfe der folgenden Befehle (RHEL und Ubuntu) auf allen Knoten, die Teil des Pacemaker-Clusters sind:

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   Führen Sie dann den folgenden Befehl aus,
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   um sicherzustellen, dass `pcsd` gestartet wird.
3. Aktivieren Sie den Pacemaker-Dienst auf allen möglichen Knoten des Pacemaker-Clusters.
   
   ```bash
   sudo systemctl start pacemaker
   ```

   Die folgende Fehlermeldung wird Ihnen unter Ubuntu angezeigt:
   
   *pacemaker Default-Start contains no runlevels, aborting.* (Der Pacemaker-Standardstart enthält keine Ausführungsebenen, der Vorgang wird abgebrochen.)
   
   Bei diesem Fehler handelt es sich um ein bekanntes Problem. Die Aktivierung des Pacemaker-Diensts ist trotz der Fehlermeldung erfolgreich. Dieser Fehler wird zu einem späteren Zeitpunkt behoben.
   
4. Als Nächstes erstellen und starten Sie den Pacemaker-Cluster. Bei diesem Schritt gibt es einen Unterschied zwischen RHEL und Ubuntu. Bei der Installation von `pcs` wird zwar auf beiden Verteilungen eine Standardkonfigurationsdatei für den Pacemaker-Cluster konfiguriert, jedoch wird die vorhandene Konfiguration bei der Ausführung dieses Befehls unter RHEL gelöscht und ein neuer Cluster erstellt.

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>Erstellen eines Pacemaker-Clusters 
In diesem Abschnitt wird erläutert, wie der Cluster für jede Linux-Verteilung erstellt und konfiguriert wird.

**RHEL**

1. Autorisieren Sie die Knoten.
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 ... NodeN> -u hacluster
   ```
   
   Fügen Sie für *NodeX* den Namen des Knotens ein.
2. Erstellen Sie den Cluster.
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   *PMClusterName* entspricht dem Namen des Pacemaker-Clusters, und *Nodelist* entspricht der Liste der Namen der Knoten, die durch ein Leerzeichen voneinander getrennt sind.

**Ubuntu**

Die Konfiguration für Ubuntu ähnelt der für RHEL. Jedoch besteht ein wesentlicher Unterschied: bei der Installation der Pacemaker-Pakete wird eine Basiskonfiguration für den Cluster erstellt und `pcsd` wird aktiviert und gestartet. Wenn Sie versuchen, den Pacemaker-Cluster anhand der Anweisungen für RHEL zu konfigurieren, erhalten Sie eine Fehlermeldung. Führen Sie die folgenden Schritte aus, um dieses Problem zu beheben: 
1. Entfernen Sie die Pacemaker-Standardkonfiguration für alle Knoten.
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. Führen Sie die Schritte des RHEL-Abschnitts zum Erstellen des Pacemaker-Clusters aus.

**SLES**

Der Prozess zum Bereitstellen eines Pacemaker-Clusters unterscheidet sich unter SLES vollständig von der Bereitstellung unter RHEL und Ubuntu. In den folgenden Schritten wird das Erstellen eines Clusters mit SLES beschrieben.
1. Starten Sie den Cluster, indem Sie den Befehl 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   auf einem der Knoten ausführen. Möglicherweise werden Sie darauf hingewiesen, dass NTP nicht konfiguriert ist und kein Watchdog-Gerät gefunden wurde. Dies stellt für die Einrichtung kein Problem dar. Watchdog bezieht sich auf STONITH, wenn Sie das speicherbasierte, integrierte Fencing von SLES verwenden. NTP und Watchdog können später konfiguriert werden.
   
2. Sie werden aufgefordert, Corosync zu konfigurieren. Sie werden aufgefordert, die Netzwerkadresse für die Einbindung und die Multicastadresse und den -port anzugeben. Die Netzwerkadresse entspricht dem Subnetz, das Sie verwenden, z. B.192.191.190.0. Sie können die Standardwerte bei allen Eingabeaufforderungen übernehmen oder bei Bedarf ändern.
   
3. Als Nächstes werden Sie gefragt, ob Sie SBD, das datenträgerbasierte Fencing, konfigurieren möchten. Diese Konfiguration können Sie auch später vornehmen. Wenn SBD nicht konfiguriert ist, wird im Gegensatz zu RHEL und Ubuntu `stonith-enabled` standardmäßig auf FALSE festgelegt.
   
4. Schließlich werden Sie gefragt, ob Sie eine IP-Adresse für die Verwaltung konfigurieren möchten. Diese IP-Adresse ist optional. Sie funktioniert ähnlich wie die IP-Adresse für einen Windows Server-Failovercluster, in dem Sinne, dass eine IP-Adresse im Cluster erstellt wird, die zum Herstellen einer Verbindung über HAWK (High Availability Web Konsole) verwendet wird. Diese Konfiguration ist ebenfalls optional.
   
5. Stellen Sie mit dem folgenden Befehl sicher, dass der Cluster ausgeführt wird: 
   ```bash
   sudo crm status
   ```
   
6. Ändern Sie das Kennwort für *hacluster* mithilfe des folgenden Befehls: 
   ```bash
   sudo passwd hacluster
   ```
   
7. Wenn Sie eine IP-Adresse für die Verwaltung konfiguriert haben, können Sie diese in einem Browser testen. Dadurch wird auch das geänderte Kennwort für *hacluster* getestet.
   ![hacLuster](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. Führen Sie den folgenden Befehl auf einem anderen SLES-Server aus, der als Knoten des Clusters verwendet wird: 
   ```bash
   sudo ha-cluster-join
   ```
   
9. Geben Sie den Namen oder die IP-Adresse des Servers ein, der in den vorherigen Schritten als erster Knoten der Clusters konfiguriert wurde, wenn Sie dazu aufgefordert werden. Der Server wird dem vorhandenen Cluster als Knoten hinzugefügt.
   
10. Überprüfen Sie mithilfe des folgenden Befehls, ob der Knoten hinzugefügt wurde: 
   ```bash
   sudo crm status
   ```
   
11. Ändern Sie das Kennwort für *hacluster* mithilfe des folgenden Befehls: 
   ```bash
   sudo passwd hacluster
   ```
   
12. Wiederholen Sie die Schritte 8-11 für alle anderen Server, die dem Cluster hinzugefügt werden sollen.

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>Installieren der SQL Server-Hochverfügbarkeits- und -Agent-Pakete
Verwenden Sie die folgenden Befehle, um das SQL Server-Hochverfügbarkeits- und das [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Agent-Paket zu installieren, wenn diese noch nicht installiert sind. Wenn Sie das Hochverfügbarkeitspaket nach [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] installieren, ist ein Neustart von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] erforderlich. In diesen Anweisungen wird vorausgesetzt, dass die Repositorys für die Microsoft-Pakete bereits eingerichtet wurden, da [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] bereits installiert sein sollte.
> [!NOTE]
> - Wenn Sie den [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Agent nicht für den Protokollversand oder einen anderen Zweck verwenden, müssen Sie ihn nicht installieren. Das Paket *mssql-server-agent* kann also übersprungen werden.
> - Die anderen optionalen Pakete für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] für Linux, für die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Volltextsuche (*mssql-server-fts*) und für die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Integration Services (*mssql-server-is*) sind nicht für Hochverfügbarkeit erforderlich, und zwar weder für Failoverclusterinstanzen noch für Verfügbarkeitsgruppen.

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

In diesem Tutorial haben Sie gelernt, wie Sie einen Pacemaker-Cluster für SQL Server für Linux bereitstellen. Sie haben Folgendes gelernt:
> [!div class="checklist"]
> * Installieren von Pacemaker und des Hochverfügbarkeits-Add-Ons
> * Vorbereiten der Knoten für Pacemaker (nur RHEL und Ubuntu)
> * Erstellen eines Pacemaker-Clusters
> * Installieren der SQL Server-Hochverfügbarkeits- und -Agent-Pakete

Informationen zum Erstellen und Konfigurieren von Verfügbarkeitsgruppen für SQL Server für Linux finden Sie unter:

> [!div class="nextstepaction"]
> [Erstellen und Konfigurieren von Verfügbarkeitsgruppen für SQL Server für Linux](sql-server-linux-create-availability-group.md)

