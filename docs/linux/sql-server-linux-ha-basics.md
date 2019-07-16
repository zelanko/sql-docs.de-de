---
title: SQL Server-Verfügbarkeitsgrundlagen für Linux-Bereitstellungen
description: ''
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 11/27/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: d7d7d7eeacca4e18fe5b5fdc97331e24a6ca212d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952612"
---
# <a name="sql-server-availability-basics-for-linux-deployments"></a>SQL Server-Verfügbarkeitsgrundlagen für Linux-Bereitstellungen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Beginnend mit [!INCLUDE[sssql17-md](../includes/sssql17-md.md)], [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] wird auf Linux- und Windows unterstützt. Wie Sie die Windows-basierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Bereitstellungen [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Datenbanken und Instanzen unter Linux hochverfügbar sein müssen. Dieser Artikel behandelt die technischen Aspekte der Planung und Bereitstellung von hoch verfügbaren Linux-basierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Datenbanken und Instanzen sowie einige der Unterschiede vom Windows-basierten Installationen. Da [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] möglicherweise für Linux-Experten und Linux möglicherweise neu für neue [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -Experten, werden im Artikel zu Zeiten Konzepte, die möglicherweise für einige vertraute und an andere Personen nicht vertraut.

## <a name="includessnoversion-mdincludesssnoversion-mdmd-availability-options-for-linux-deployments"></a>[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Verfügbarkeitsoptionen für Linux-Bereitstellungen
Neben dem Sichern und Wiederherstellen werden die gleichen drei Verfügbarkeitsfunktionen unter Linux für Windows-basierten Bereitstellungen verfügbar:
-   Always On-Verfügbarkeitsgruppen (Verfügbarkeitsgruppen)
-   Always On-Failoverclusterinstanzen (FCIs)
-   [Protokollversand](sql-server-linux-use-log-shipping.md)

Auf Windows erfordern FCIs immer einem zugrunde liegenden Windows Server-Failovercluster (WSFC). Je nach Bereitstellungsszenario eine Verfügbarkeitsgruppe in der Regel erfordert einem zugrunde liegenden WSFC, mit Ausnahme der neuen keine Variante in [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Ein WSFC unter Linux ist nicht vorhanden. Implementierung in Linux-Clustering wird im Abschnitt erläutert [Pacemaker für AlwaysOn-Verfügbarkeitsgruppen und Failover-Cluster unter Linux-Instanzen](#pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux).

## <a name="a-quick-linux-primer"></a>Eine kurze Einführung für Linux
Während einige Linux-Installationen mit einer Schnittstelle installiert werden können, sind die meisten nicht, was bedeutet, dass fast alle Elemente auf der Betriebssystemebene über die Befehlszeile abgeschlossen ist. Der allgemeine Begriff für diese Befehlszeile in der Linux-Welt ist eine *bash-Shell*.

Unter Linux müssen viele Befehle mit erweiterten Berechtigungen ausgeführt werden, ähnlich wie viele Dinge, die in Windows Server als Administrator ausgeführt werden müssen. Es gibt zwei Hauptmethoden zum Ausführen mit erhöhten Rechten aus:
1. Im Kontext des entsprechenden Benutzers ausgeführt. Um in einem anderen Benutzer ändern, verwenden Sie den Befehl `su`. Wenn `su` ausgeführt wird, selbst ohne einen Benutzernamen, solange Sie wissen, dass das Kennwort, Sie werden in einer Shell als *Stamm*.
   
2. Die weitere häufige und Sicherheit die Möglichkeit zum bewusste zum Ausführen von Aufgaben ist die Verwendung `sudo` vor der Ausführung etwas. Viele der Beispiele in diesem Artikel verwenden `sudo`.

Einige häufig verwendete Befehle, von denen jeder über verschiedene Switches und Optionen, die online untersucht werden können:
-   `cd` – Ändern Sie das Verzeichnis
-   `chmod` – Ändern Sie die Berechtigungen einer Datei oder Verzeichnis
-   `chown` – Ändern des Besitzers einer Datei oder eines Verzeichnisses
-   `ls` – Zeigen Sie den Inhalt eines Verzeichnisses
-   `mkdir` – Erstellen Sie einen Ordner (Verzeichnis) auf einem Laufwerk
-   `mv` -Verschieben einer Datei von einem Speicherort in einen anderen
-   `ps` -Anzeigen aller Prozesse arbeiten
-   `rm` – Löschen einer Datei lokal auf einem Server
-   `rmdir` -Löschen eines Ordners (Verzeichnis)
-   `systemctl` -Starten, beenden oder -Dienste aktivieren
-   Text-Editor-Befehlen. Es gibt verschiedene Text-Editor-Optionen wie vi und Emacs, unter Linux.

## <a name="common-tasks-for-availability-configurations-of-includessnoversion-mdincludesssnoversion-mdmd-on-linux"></a>Häufige Aufgaben für Konfigurationen für Verfügbarkeit der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] unter Linux
Dieser Abschnitt enthält Aufgaben, die für alle Linux-basierten gelten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Bereitstellungen.

### <a name="ensure-that-files-can-be-copied"></a>Stellen Sie sicher, dass die Dateien kopiert werden können
Kopieren von Dateien von einem Server in eine andere ist eine Aufgabe, die alle mit [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sollte unter Linux möglich sein. Diese Aufgabe ist sehr wichtig für die AG-Konfigurationen.

Dinge wie Berechtigungsprobleme können sowohl für Linux als auch auf Windows-basierten Installationen vorhanden sein. Allerdings mit der Vorgehensweise beim Kopieren von Server zu Server für Windows vertraut sind möglicherweise nicht vertraut sind, mit der Vorgehensweise unter Linux. Eine gängige Methode ist, verwenden Sie das Befehlszeile-Hilfsprogramm `scp`, das steht für das sichere kopieren. Hinter den Kulissen `scp` OpenSSH verwendet. SSH ist die Abkürzung für secure Shell. OpenSSH selbst kann je nach Linux-Distribution nicht installiert werden. Wenn sie nicht der Fall ist, muss OpenSSH zuerst installiert werden. Weitere Informationen zum Konfigurieren von OpenSSH finden Sie die Informationen unter den folgenden Links für jede Verteilung:
-   [Red Hat Enterprise Linux (RHEL)](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/ch-openssh)
-   [SUSE Linux Enterprise Server (SLES)](https://en.opensuse.org/SDB:Configure_openSSH)
-   [Ubuntu](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Bei Verwendung `scp`, müssen Sie die Anmeldeinformationen des Servers angeben, wenn es sich nicht um die Quelle oder das Ziel ist. Verwenden Sie beispielsweise

```bash
scp MyAGCert.cer username@servername:/folder/subfolder
```

die Datei MyAGCert.cer kopiert zu dem Ordner auf dem anderen Server. Beachten Sie, dass Sie benötigen Berechtigungen – und möglicherweise Besitz - der Datei, kopieren Sie also `chown` müssen möglicherweise auch vor dem Kopieren eingesetzt werden. Auf der Empfangsseite benötigt die richtige Benutzer auf ähnliche Weise Zugriff auf die Datei zu bearbeiten. Beispielsweise, um diese Zertifikatdatei Wiederherstellen der `mssql` Benutzer muss darauf zugreifen können.

Samba, der die Linux-Variante von Server Message Block (SMB) ist, kann auch verwendet werden, zum Erstellen von Freigaben, z. B. von UNC-Pfade zugegriffen `\\SERVERNAME\SHARE`. Weitere Informationen zum Konfigurieren von Samba finden Sie die Informationen unter den folgenden Links für jede Verteilung:
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Managing_Confined_Services/chap-Managing_Confined_Services-Samba.html)
-   [SLES](https://www.suse.com/documentation/sles11/book_sle_admin/data/cha_samba.html)
-   [Ubuntu](https://help.ubuntu.com/community/Samba)

Windows-basierten SMB-Freigaben können auch verwendet werden. SMB-Freigaben müssen sich nicht auf Linux-basiert, werden so lange der Teil des Samba Clients ordnungsgemäß, auf dem Linux läuft konfiguriert ist [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] und die Freigabe hat die richtige Zugriffsrechte. Für diejenigen in einer gemischten Umgebung, wäre dies eine Möglichkeit zum Nutzen der vorhandenen Infrastruktur für Linux-basierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Bereitstellungen.

Eine Sache, die wichtig ist, dass die Version der bereitgestellten Samba SMB 3.0-kompatibel sein soll. Wenn die Unterstützung von SMB in hinzugefügt wurde [!INCLUDE[sssql11-md](../includes/sssql11-md.md)], es erforderlich, dass alle Freigaben zur Unterstützung von SMB 3.0. Wenn Samba für die Freigabe und nicht auf Windows Server verwenden möchten, sollten die Freigabe Samba-basierte Samba 4.0 oder höher, und im Idealfall 4.3 oder höher, verwenden die SMB 3.1.1 unterstützt. Ist eine gute Quelle für Informationen zu SMB und Linux [SMB3 in Samba](https://events.linuxfoundation.org/sites/events/files/slides/smb3-in-samba.pr__0.pdf).

Schließlich ist die Verwendung einer Dateifreigabe im Netzwerk-System (NFS) eine Option. Verwenden Sie stattdessen NFS ist die Option nicht auf Windows-basierten Bereitstellungen von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], und kann nur für Linux-basierten Bereitstellungen verwendet werden.

### <a name="configure-the-firewall"></a>Konfigurieren der Firewall
Ähnlich wie Windows, Linux-Distributionen müssen eine integrierte Firewall. Wenn Ihr Unternehmen mit eine externe Firewall auf dem Server verwendet wird, kann das Deaktivieren der Firewalls unter Linux akzeptabel sein. Allerdings unabhängig davon, in dem die Firewall aktiviert ist, müssen die Ports geöffnet werden. Der folgenden Tabelle sind die allgemeinen erforderlichen Ports für hoch verfügbare [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Bereitstellungen unter Linux.

| Portnummer | Typ     | Beschreibung                                                                                                                 |
|-------------|----------|-----------------------------------------------------------------------------------------------------------------------------|
| 111         | TCP/UDP  | NFS - `rpcbind/sunrpc`                                                                                                    |
| 135         | TCP      | Samba (sofern verwendet) - Endpunkt-Mapper                                                                                          |
| 137         | UDP      | Samba (sofern verwendet) - NetBIOS-Namensdienst                                                                                      |
| 138         | UDP      | Samba (sofern verwendet) - NetBIOS-Datagramm                                                                                          |
| 139         | TCP      | Samba (sofern verwendet) - NetBIOS-Sitzung                                                                                           |
| 445         | TCP      | Samba (sofern verwendet) - SMB über TCP                                                                                              |
| 1433        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -Standardport; Falls gewünscht, können mit ändern. `mssql-conf set network.tcpport <portnumber>`                       |
| 2049        | TCP, UDP | NFS (sofern verwendet)                                                                                                               |
| 2224        | TCP      | Pacemaker - verwendet von `pcsd`                                                                                                |
| 3121        | TCP      | Pacemaker - erforderlich, wenn Pacemaker entfernten Knoten vorhanden sind                                                                    |
| 3260        | TCP      | iSCSI-Initiator (sofern verwendet) – kann geändert werden, `/etc/iscsi/iscsid.config` (RHEL), aber der Port des iSCSI-Ziels entsprechen muss |
| 5022        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] – Der Standardport für einen Endpunkt Verfügbarkeitsgruppe verwendet kann geändert werden, wenn Sie den Endpunkt erstellen                                |
| 5403        | TCP      | Pacemaker                                                                                                                   |
| 5404        | UDP      | Pacemaker - von Corosync erforderlich, wenn multicast-UDP verwenden                                                                     |
| 5405        | UDP      | Pacemaker - Corosync erforderlich                                                                                            |
| 21064       | TCP      | Pacemaker - Ressourcen mithilfe von DLM erforderlich                                                                                 |
| Variable    | TCP      | AG Endpunktport; Standardwert ist 5022                                                                                           |
| Variable    | TCP      | NFS - port für `LOCKD_TCPPORT` (finden Sie im `/etc/sysconfig/nfs` unter RHEL)                                              |
| Variable    | UDP      | NFS - port für `LOCKD_UDPPORT` (finden Sie im `/etc/sysconfig/nfs` unter RHEL)                                              |
| Variable    | TCP/UDP  | NFS - port für `MOUNTD_PORT` (finden Sie im `/etc/sysconfig/nfs` unter RHEL)                                                |
| Variable    | TCP/UDP  | NFS - port für `STATD_PORT` (finden Sie im `/etc/sysconfig/nfs` unter RHEL)                                                 |

Zusätzliche Ports, die von Samba verwendet werden können, finden Sie unter [Samba-Portverwendung](https://wiki.samba.org/index.php/Samba_Port_Usage).

Im Gegensatz dazu kann der Namen des Diensts unter Linux auch den Port, sondern als Ausnahme hinzugefügt werden. z. B. `high-availability` für Pacemaker. Verweisen Sie auf den Verteilungspunkt für die Namen, ist dies die Richtung, die Sie verfolgen möchten. Beispielsweise ist unter RHEL der Befehl zum Hinzufügen in Pacemaker

```bash
sudo firewall-cmd --permanent --add-service=high-availability
```

**Dokumentation der Firewall:**
-   [RHEL](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/high_availability_add-on_reference/s1-firewalls-haar)
-   [SLES](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html)

### <a name="install-includessnoversion-mdincludesssnoversion-mdmd-packages-for-availability"></a>Installieren Sie [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -Pakete für Verfügbarkeit
Auf einem Windows-basierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Installation einige Komponenten sind auch in einer basic-Engine-Installation installiert, andere hingegen nicht. Unter Linux, nur die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -Engine als Teil des Installationsvorgangs installiert ist. Alles ist optional. Für hoch verfügbare [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Instanzen unter Linux, zwei Pakete installiert werden mit [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]: [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent (*Mssql-Server-Agent*) und die hohe Verfügbarkeit (HA)-Paket (*Mssql-Server-ha*). Während [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent ist technisch optional [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]der Scheduler für Aufträge und muss Protokollversand, damit die Installation empfohlen wird. Auf Windows basierenden Installationen sowie [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent ist nicht optional.

>[!NOTE]
>Für diejenigen, die noch nicht mit [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]des integrierten Auftragsplaner. Es ist eine gängige Methode für DBAs zum Planen von Aufgaben wie Sicherungen und andere [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Wartung. Im Gegensatz zu einer Windows-basierten Installation von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] , in denen [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent ist ein völlig anderen Dienst, unter Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -Agent ausgeführt wird, im Kontext der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] selbst.

Bei Verfügbarkeitsgruppen oder FCIs, die auf einer Windows-basierten Konfiguration konfiguriert werden, sind sie mit Clusterunterstützung. Clusterinformationen bedeutet, dass [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] verfügt über bestimmte Ressourcen-DLLs, die ein WSFC ("sqagtres.dll" und sqsrvres.dll für FCIs, "hadrres.dll" für Verfügbarkeitsgruppen) bekannt sind, und werden von der WSFC verwendet, um sicherzustellen, dass die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] gruppierten Funktionen ist, ausgeführt, und ordnungsgemäß funktioniert. Da clustering externen nicht nur zu ist [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] aber Linux selbst, Microsoft musste das Äquivalent einer Ressourcen-DLL für Linux-basierten AG und FCI-Bereitstellungen zu codieren. Dies ist die *Mssql-Server-ha* Verpacken, auch bekannt als die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Ressourcen-Agent für Pacemaker. So installieren Sie die *Mssql-Server-ha* Verpacken, finden Sie unter [installieren Sie die hohe Verfügbarkeit und SQL Server-Agent-Pakete](sql-server-linux-deploy-pacemaker-cluster.md#install-the-sql-server-ha-and-sql-server-agent-packages).

Die optionalen Pakete für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] unter Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Full-Text Search (*Mssql-Server-Volltextsuche*) und [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Integration Services (*Mssql-Server ist*), sind nicht für hohe Verfügbarkeit für eine FCI oder Verfügbarkeitsgruppe erforderlich.

## <a name="pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux"></a>Pacemaker für AlwaysOn-Verfügbarkeitsgruppen und fcis unter Linux
Wie bisher angegeben, der einzige clustering Mechanismus, der derzeit von Microsoft für Verfügbarkeitsgruppen und FCIs unterstützt Pacemaker mit Corosync ist. Dieser Abschnitt behandelt die grundlegende Informationen zum Verständnis der Lösung sowie das Planen und Bereitstellen für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Konfigurationen.

### <a name="ha-add-onextension-basics"></a>Grundlagen der HA-add-on/Erweiterung
Alle derzeit unterstützten Verteilungen liefern eine add-on/Erweiterung für hohe Verfügbarkeit, basierend auf den Stapel clustering Pacemaker. Dieser Stapel umfasst zwei Hauptkomponenten: Pacemaker und Corosync. Alle Komponenten des Stapels sind:
-   Pacemaker - die wichtigsten Failoverclustering-Komponente, die Dinge wie Koordinate für den Clustercomputer.
-   Corosync - ein Framework und eine Reihe von APIs, die Dinge wie das Quorum, die Möglichkeit, Fehler beim Neustart usw. enthält.
-   LibQB - Dinge wie Protokollierung bietet.
-   Ressourcen-Agent - spezifischen Funktionen, damit eine Anwendung in Pacemaker integriert werden kann.
-   Zaun Agent - Skripts und Funktionen, die bei der Isolierung von Knoten und mit ihnen arbeiten, wenn sie Probleme haben.
    
> [!NOTE]
> Der clusterstapel wird häufig als Pacemaker in der Linux-Welt bezeichnet.

Diese Lösung ist in gewisser Weise ähnelt, aber in vielerlei Hinsicht von der Bereitstellung von Clusterkonfigurationen, die mithilfe von Windows unterschiedliche. In Windows basiert die verfügbarkeitsformular des Clusterings, einen Windows Server-Failovercluster (WSFC) wird aufgerufen, in das Betriebssystem und die Funktion, die die Erstellung von einem WSFC Failover-Clusterunterstützung ermöglicht, ist standardmäßig deaktiviert. In Windows, Verfügbarkeitsgruppen und FCIs basieren auf einem WSFC und teilen Sie eine enge Integration aufgrund der bestimmten Ressourcen-DLL, die von bereitgestellte [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Diese eng gekoppelten Lösung ist im großen und möglich, da es alle von einem Anbieter ist.

![](./media/sql-server-linux-ha-basics/image1.png)

Unter Linux während jede unterstützte Distribution Pacemaker verfügbar ist, hat kann jede Verteilung angepasst und verfügen über geringfügig verschiedene Implementierungen und Versionen. Einige der Unterschiede werden in den Anweisungen in diesem Artikel übernommen. Die clustering-Ebene ist open Source, damit, obwohl es in die Verteilungen enthalten ist, es nicht streng auf die gleiche Weise integriert ist ein WSFC unter Windows. Aus diesem Grund Microsoft bietet ist *Mssql-Server-ha*, sodass [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] und bieten der Pacemaker-Stapel nahe, aber nicht genau die gleiche, Erfahrung für Verfügbarkeitsgruppen und FCIs unter Windows.

Die vollständige Dokumentation für Pacemaker einschließlich eine tiefer greifende Erklärung, was alles mit vollständigen Verweisinformationen, für RHEL und SLES ist:
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-overview-HAAR.html)
-   [SLES](https://www.suse.com/documentation/sle_ha/book_sleha/data/book_sleha.html)

Eine Anleitung für die Verfügbarkeit keinen Ubuntu.

Weitere Informationen zu den gesamten Stapel, auch finden Sie auf der offiziellen [Pacemaker-Dokumentationsseite](https://clusterlabs.org/doc/) auf der Website Clusterlabs.

### <a name="pacemaker-concepts-and-terminology"></a>Pacemaker-Konzepte und Terminologie
In diesem Abschnitt dokumentiert die allgemeinen Konzepte und Terminologie für eine Implementierung von Pacemaker.

#### <a name="node"></a>Knoten
Ein Knoten ist ein Server, die Teil des Clusters. Ein Pacemaker-Cluster unterstützt bis zu 16 Knoten. Diese Zahl kann überschritten werden, wenn Corosync auf zusätzlichen Knoten nicht ausgeführt wird, aber Corosync erforderlich, damit ist [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Aus diesem Grund die maximale Anzahl von Knoten ein Clusters sich für eine beliebige haben [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Basis Konfiguration ist 16, dies ist der Grenzwert für die Pacemaker und hat nichts zu tun mit Obergrenzen für Verfügbarkeitsgruppen oder FCIs seitens [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. 

#### <a name="resource"></a>Ressource
Sowohl auf einem WSFC und Pacemaker-Clusters müssen das Konzept einer Ressource an. Eine Ressource ist, bestimmte Funktionen, die im Rahmen des Clusters, z.B. einen Datenträger oder eine IP-Adresse ausgeführt wird. Beispielsweise unter Pacemaker können sowohl FCI-Verfügbarkeitsgruppe Ressourcen erstellt. Dies ist kein unterschiedlicher, was in einem WSFC ausgeführt wird, sodass Sie sehen eine [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Ressource für eine FCI oder eine AG-Ressource, die beim Konfigurieren einer Verfügbarkeitsgruppe, aber ist nicht der gleiche aufgrund der zugrunde liegenden Unterschiede bei [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Pacemaker integriert.

Pacemaker über Standard "und" Clone Ressourcen verfügt. Klon-Ressourcen sind solche, die gleichzeitig auf allen Knoten ausgeführt werden. Ein Beispiel wäre eine IP-Adresse, die auf mehreren Knoten für den Lastenausgleich ausgeführt wird. Alle Ressourcen, die für FCIs Erstellungsweise verwendet eine standard-Ressource aus, da zu jedem Zeitpunkt nur ein Knoten ein eine FCI gehostet werden kann.

Wenn eine Verfügbarkeitsgruppe erstellt wurde, ist eine spezielle Form von einem Klon Ressource mit dem Namen einer mehrstufigen Ressource erforderlich. Während eine Verfügbarkeitsgruppe nur ein primäres Replikat verfügt, wird die Verfügbarkeitsgruppe selbst in allen Knoten ausgeführt, die sie abarbeiten konfiguriert ist, und potenziell möglich, z. B. schreibgeschützten Zugriff. Da dies ein "live" des Knotens verwendet wird, wird durch die Ressourcen verfügen, das Konzept von zwei Status: Primär- und sekundärgerät. Weitere Informationen finden Sie unter [mehrstufigen Ressourcen: Ressourcen, die mehrere Modi](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/s1-multistateresource-HAAR.html).

#### <a name="resource-groupssets"></a>Ressourcen-Gruppen oder legt sie fest
Ähnlich wie Rollen in einem WSFC ein Pacemaker-Clusters hat das Konzept einer Ressourcengruppe. Eine Ressourcengruppe (in SLES als einen Satz bezeichnet) ist eine Sammlung von Ressourcen, die zusammen funktionieren, und können ein Failover von einem Knoten in ein anderes als eine Einheit. Ressourcengruppen können keine Ressourcen enthalten, die als Master/Slave konfiguriert werden; Daher können sie für Verfügbarkeitsgruppen verwendet werden. Während Sie eine Ressourcengruppe für FCIs verwendet werden kann, ist es nicht in der Regel eine empfohlene Konfiguration.

#### <a name="constraints"></a>Einschränkungen
WSFCs haben verschiedene Parameter für die Ressourcen als auch Dinge wie Abhängigkeiten auf, die den WSFC von einer über-/unterordnungsbeziehung zwischen den zwei verschiedene Ressourcen zu informieren. Eine Abhängigkeit ist nur eine Regel, die dem WSFC mitteilen, welche Ressource muss zuerst online sein.

Ein Pacemaker-Cluster verfügt nicht über das Konzept der Abhängigkeiten, aber es gibt Einschränkungen. Es gibt drei Arten von Einschränkungen: zusammenstellen, den Speicherort und Reihenfolge.
-   Eine Zusammenstellung Einschränkung erzwingt, und zwar unabhängig davon, ob zwei Ressourcen, die auf demselben Knoten ausgeführt werden sollen.
-   Eine speicherorteinschränkung weist die Pacemaker-Clusters, in dem eine Ressource ausgeführt werden können (oder nicht).
-   Eine Sortierung Einschränkung weist die Pacemaker-Clusters die Reihenfolge, in der die Ressourcen gestartet werden soll.

> [!NOTE]
> Zusammenstellung Einschränkungen sind nicht für Ressourcen in einer Ressourcengruppe erforderlich, da alle diese als einzelne Einheit angezeigt werden.

#### <a name="quorum-fence-agents-and-stonith"></a>Quorum, Fence-Agents und STONITH
Quorum in Pacemaker ähnelt einem WSFC Konzept. Der gesamte Zweck einen Cluster-Quorum-Mechanismus wird sichergestellt, dass der Cluster betriebsbereit bleibt. Sowohl auf einem WSFC und der HA-Add-Ons für die Linux-Distributionen müssen das Konzept der abstimmungsknoten, wobei jeder Knoten gegenüber dem Quorum zählt. Soll eine Mehrheit der stimmen, andernfalls im schlimmsten Fall, wird der Cluster beendet werden.

Es gibt keine Zeugenressource mit Quorum arbeiten, im Gegensatz zu einem WSFC. Einem WSFC ähnelt das Ziel, die Anzahl an Stimmberechtigten ungerade beschränken. Quorumkonfiguration verfügt über verschiedene Überlegungen für Verfügbarkeitsgruppen als FCIs.

WSFCs Überwachen des Status der Knoten und behandelt werden, wenn ein Problem auftritt. Höhere Versionen von WSFCs bieten Funktionen wie gesäubert einen Knoten, der fehlerhaften oder nicht verfügbar ist (der Knoten ist nicht auf, die Netzwerkkommunikation wird nach unten, usw.). Auf der Seite Linux ist diese Art von Funktionalität durch einen Fence Agent bereitgestellt. Das Konzept wird manchmal als Umgrenzung bezeichnet. Jedoch diese Fence-Agents für die Bereitstellung in der Regel spezifisch sind, und häufig von Hardwareherstellern und einige Softwarehersteller, z. B. diejenigen, die Bereitstellen von Hypervisoren bereitgestellt. VMware bietet beispielsweise einen Fence Agent, der für virtuelle Linux-Computer mithilfe von vSphere virtualisiert verwendet werden kann.

Quorum für das umgrenzen der Ties in ein anderes Konzept STONITH aufgerufen und dafür den anderen Knoten im Kopf. STONITH ist erforderlich, um einen unterstützten Pacemaker-Cluster für alle Linux-Distributionen zu erhalten. Weitere Informationen finden Sie unter [in einem Red Hat für hohe Verfügbarkeit-Cluster für das Umgrenzen](https://access.redhat.com/solutions/15575) (RHEL).

#### <a name="corosyncconf"></a>corosync.conf
Die `corosync.conf` Datei enthält die Konfiguration des Clusters. Befindet sich im `/etc/corosync`. Im Verlauf der normalen alltäglichen Betrieb sollten diese Datei nicht bearbeitet werden, wenn der Cluster ordnungsgemäß eingerichtet ist, müssen.

#### <a name="cluster-log-location"></a>Cluster-Protokollspeicherort
Protokollspeicherorte für Pacemaker-Cluster unterscheiden sich je nach der Verteilung.
-   RHEL und SLES- `/var/log/cluster/corosync.log`
-   Ubuntu - `/var/log/corosync/corosync.log`

Um den Standardspeicherort für die Protokollierung zu ändern, ändern `corosync.conf`.

## <a name="plan-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Planen für die Pacemaker-Cluster [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Dieser Abschnitt beschreibt die Planung wichtigen Punkte für einen Pacemaker-Cluster.

### <a name="virtualizing-linux-based-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Virtualisierenden Linux-basierten Pacemaker-Cluster für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Mithilfe von virtuellen Computern zum Bereitstellen von Linux-basierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Bereitstellungen für Verfügbarkeitsgruppen und FCIs wird durch die gleichen Regeln wie für ihren Windows-basierten äquivalenten abgedeckt. Es gibt ein grundlegender Satz von Regeln für die Unterstützung von virtualisierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Bereitstellungen von Microsoft bereitgestellten [Microsoft Support-KB-956893](https://support.microsoft.com/help/956893/support-policy-for-microsoft-sql-server-products-that-are-running-in-a-hardware-virtualization-environment). Andere Hypervisoren wie von Microsoft Hyper-V und VMware ESXi möglicherweise unterschiedliche Varianzen auf, aufgrund von Unterschieden bei den Plattformen selbst.

Bei Verfügbarkeitsgruppen und FCIs unter Virtualisierung, stellen Sie sicher, dass Anti-Affinität für die Knoten eines bestimmten Pacemaker-Clusters festgelegt wird. Wenn für hohe Verfügbarkeit in einer Verfügbarkeitsgruppe oder einer FCI-Konfiguration konfiguriert die virtuellen Computer hostet [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sollte nie auf demselben hypervisorhost ausgeführt werden. Z. B. wenn eine FCI zwei Knoten bereitgestellt wird, es müssten werden *mindestens* drei Hypervisor-Hosts, die es gibt also an einer beliebigen Stelle für eine der virtuellen Computer einen Knoten hostet zu Ausfall eines Hosts insbesondere dann, wenn Funktionen wie Live Migration oder vMotion.

Weitere Informationen finden Sie in:
-   Hyper-V-Dokumentation – [Verwenden von Gastclustering für hohe Verfügbarkeit](https://technet.microsoft.com/library/dn440540(v=ws.11).aspx)
-   Whitepaper (geschrieben für Windows-basierten Bereitstellungen, aber die meisten Konzepte, die noch anwenden) - [planen hoher Verfügbarkeit, unternehmenskritische kritische SQL Server-Bereitstellungen mit VMware vSphere](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/solutions/vmware-vsphere-highly-available-mission-critical-sql-server-deployments.pdf)

>[!NOTE]
>RHEL mit einen Pacemaker-Cluster mit STONITH wird von Hyper-V noch nicht unterstützt. Bis dies, um weitere Informationen und Updates unterstützt wird, wenden Sie sich an [Supportrichtlinien für RHEL High Availability Cluster](https://access.redhat.com/articles/29440#3physical_host_mixing).

### <a name="networking"></a>Netzwerk
Im Gegensatz zu einem WSFC erfordert Pacemaker einen dedizierten Namen oder mindestens eine dedizierte IP-Adresse für den Pacemaker-Cluster selbst keine. Verfügbarkeitsgruppen und FCIs benötigen die IP-Adressen (siehe die Dokumentation für jede weitere Informationen), aber keine Namen, da keine Netzwerk-Namensressource vorhanden ist. SLES lässt die Konfiguration einer IP-Adresse für Verwaltungszwecke, aber es ist nicht erforderlich ist, wie in der angezeigt werden [Erstellen des Pacemaker-Clusters](sql-server-linux-deploy-pacemaker-cluster.md#create).

Wie einem WSFC Pacemaker bevorzugen redundante Netzwerken, d. h. unterschiedlichen Netzwerkkarten (NICs oder pNICs physisch) mit einzelnen IP-Adressen. Im Hinblick auf die Clusterkonfiguration müsste jede IP-Adresse als eigene Ring bezeichnet wird. Allerdings mit WSFCs heute viele Implementierungen virtualisiert werden oder in der öffentlichen Cloud, es wirklich ist virtualisiert nur eine einzige Netzwerkkarte (vNIC) an den Server angezeigt. Wenn alle pNICs und vNICs mit dem gleichen physischen oder virtuellen Switch verbunden sind, ist es kein echter Redundanz auf der Netzwerkebene daher Konfigurieren von mehreren Netzwerkkarten etwas Illusion an den virtuellen Computer. Netzwerkredundanz ist in der Regel von der Hypervisor für virtualisierte Bereitstellungen integriert, und auf jeden Fall der öffentlichen Cloud integriert ist.

Ein besteht Unterschied mit mehreren NICs und Pacemaker im Vergleich zu einem WSFC darin, dass Pacemaker mehrere IP-Adressen im gleichen Subnetz ermöglicht während ein WSFC nicht der Fall ist. Weitere Informationen in mehreren Subnetzen und Linux-Clustern finden Sie im Artikel [Konfigurieren mehrerer Subnetze](sql-server-linux-configure-multiple-subnet.md).

### <a name="quorum-and-stonith"></a>Quorum und STONITH
Quorumkonfiguration und Anforderungen beziehen sich auf die Verfügbarkeitsgruppe oder FCI-spezifische Bereitstellungen von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

STONITH wird für einen unterstützten Pacemaker-Cluster benötigt. Verwenden Sie die Dokumentation der Distribution, konfigurieren. Ein Beispiel hierfür ist, am [speicherbasierte Umgrenzung](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_storage_protect_fencing.html) für SLES. Es gibt auch ein STONITH-Agent für VMware vCenter für ESXI-basierten Lösungen. Weitere Informationen finden Sie unter [Stonith-Plug-in-Agent für die VMWare-VM VCenter SOAP für das Umgrenzen (Unofficial)](https://github.com/olafrv/fence_vmware_soap).

> [!NOTE]
> Zum Zeitpunkt der Verfassung dieses Artikels, Hyper-V eine Lösung für STONITH keinen. Dies gilt auch für lokale Bereitstellungen und wirkt sich auch auf Azure-basierte Pacemaker-Bereitstellungen, die mit bestimmten Distributionen wie RHEL.

### <a name="interoperability"></a>Interoperabilität
Dieser Abschnitt beschreibt, wie auf ein Linux-basierten Cluster mit einem WSFC oder andere Linux-Distributionen interagieren kann.

#### <a name="wsfc"></a>WSFC
Derzeit besteht keine direkte Möglichkeit für einen WSFC und Pacemaker-Clusters zusammenarbeiten. Dies bedeutet, dass es keine Möglichkeit zum Erstellen einer Verfügbarkeitsgruppe oder FCI, die auf einem WSFC und Pacemaker funktioniert. Es gibt jedoch zwei Interoperabilität-Lösungen, die beide für Verfügbarkeitsgruppen konzipiert sind. Die einzige Möglichkeit, die eine FCI in einer Konfiguration mit plattformübergreifenden teilnehmen kann ist, wenn es als eine Instanz in einem dieser beiden Szenarien ist:
-   Eine Verfügbarkeitsgruppe mit dem Clustertyp None. Weitere Informationen finden Sie in der Windows [Verfügbarkeitsgruppen Dokumentation](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).
-   Eine verteilte Verfügbarkeitsgruppe, die eine besondere Art der verfügbarkeitsgruppe ist, die zwei verschiedene Verfügbarkeitsgruppen als ihrer eigenen verfügbarkeitsgruppe konfiguriert werden können. Weitere Informationen zu verteilten Verfügbarkeitsgruppen, finden Sie in der Dokumentation [von verteilten Verfügbarkeitsgruppen](../database-engine/availability-groups/windows/distributed-availability-groups.md).

#### <a name="other-linux-distributions"></a>Andere Linux-Distributionen
Unter Linux müssen alle Knoten eines Pacemaker-Clusters in der gleichen Verteilung sein. Beispielsweise bedeutet dies, dass ein RHEL-Knoten Teil eines Pacemaker-Clusters sein kann, die über einen SLES-Knoten verfügt. Der Hauptgrund hierfür wurde bereits erwähnt: die Verteilungen möglicherweise unterschiedliche Versionen und Funktionalität, damit nicht ordnungsgemäß funktionieren kann. Das Kombinieren von Verteilungen hat den gleichen Text befindet wie das Kombinieren von WSFCs und Linux: Verwenden Sie keine oder verteilten Verfügbarkeitsgruppen.

## <a name="next-steps"></a>Nächste Schritte
[Bereitstellen eines Clusters Schrittmacher für SQL Server on Linux](sql-server-linux-deploy-pacemaker-cluster.md)
