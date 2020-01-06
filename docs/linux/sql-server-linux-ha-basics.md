---
title: Grundlagen zur SQL Server-Verfügbarkeit für Linux-Bereitstellungen
description: ''
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 11/27/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: d597033e6ad09a735e621518883cedda6bef29a2
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243585"
---
# <a name="sql-server-availability-basics-for-linux-deployments"></a>Grundlagen zur SQL Server-Verfügbarkeit für Linux-Bereitstellungen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ab [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] wird [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sowohl unter Linux als auch Windows unterstützt. Ebenso wie bei Windows-basierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Bereitstellungen müssen auch [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Datenbanken und -Instanzen unter Linux hochverfügbar sein. In diesem Artikel werden die technischen Aspekte der Planung und Bereitstellung von hochverfügbaren Linux-basierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Datenbanken und -Instanzen sowie einige Unterschiede zu Windows-basierten Installationen beschrieben. Da Linux-Experten möglicherweise noch nicht mit [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] vertraut sind und sich [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Experten unter Umständen noch nie mit Linux befasst haben, werden in diesem Artikel an einigen Stellen Konzepte vorgestellt, die für die ein oder andere Zielgruppe neu sind.

## <a name="includessnoversion-mdincludesssnoversion-mdmd-availability-options-for-linux-deployments"></a>[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Verfügbarkeitsoptionen für Linux-Bereitstellungen
Neben der Sicherung und Wiederherstellung sind die folgenden drei Features sowohl für Linux als auch für Windows-basierte Bereitstellungen verfügbar:
-   Always On-Verfügbarkeitsgruppen
-   Always On-Failoverclusterinstanzen
-   [Protokollversand](sql-server-linux-use-log-shipping.md)

Unter Windows ist für Failoverclusterinstanzen immer ein Windows Server-Failovercluster (WSFC) erforderlich. Abhängig vom Bereitstellungsszenario ist für eine Verfügbarkeitsgruppe in der Regel ein WSFC notwendig. Eine Ausnahme bildet die neue Variante „None“ (Keine) in [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Unter Linux gibt es keinen WSFC. Die Clusteringimplementierung in Linux wird im Abschnitt [Pacemaker für Always On-Verfügbarkeitsgruppen und -Failoverclusterinstanzen unter Linux](#pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux)erläutert.

## <a name="a-quick-linux-primer"></a>Linux-Grundlagen
Für die meisten Linux-Installationen wird keine Benutzeroberfläche verwendet. Auf der Betriebssystemebene wird für fast alle Aufgaben die Befehlszeile genutzt. Diese wird unter Linux in der Regel als *Bash* bezeichnet.

Unter Windows Server müssen viele Vorgänge als Administrator ausgeführt werden. Analog dazu sind unter Linux für viele Befehle erhöhte Rechte erforderlich. Üblicherweise nutzen Sie eine der folgenden Möglichkeiten, Befehle mit erhöhten Rechten auszuführen:
1. Sie wechseln zu einem Benutzer mit den notwendigen Berechtigungen und führen anschließend den Befehl aus. Mit dem Befehl `su` können Sie zu einem anderen Benutzer wechseln. Wenn Sie `su` ohne einen Benutzernamen ausführen und anschließend das Kennwort eingeben, haben Sie in der Shell *Rootberechtigungen*.
   
2. Üblicher und sicherer ist es aber, zuerst `sudo` auszuführen. In vielen Beispielen in diesem Artikel wird `sudo` verwendet.

In der folgenden Liste sind einige gängige Befehle aufgeführt. Für diese sind jeweils unterschiedliche Optionen und Parameter verfügbar, die Sie online recherchieren können:
-   `cd`: Verzeichnis ändern.
-   `chmod`: Berechtigungen einer Datei oder eines Verzeichnisses ändern.
-   `chown`: Anderen Besitzer für eine Datei oder für ein Verzeichnis festlegen.
-   `ls`: Inhalt eines Verzeichnisses anzeigen.
-   `mkdir`: Ordner (Verzeichnis) auf einem Laufwerk erstellen.
-   `mv`: Datei von einem Speicherort zu einem anderen verschieben.
-   `ps`: Alle Arbeitsprozesse anzeigen.
-   `rm`: Datei lokal auf einem Server löschen.
-   `rmdir`: Ordner (Verzeichnis) löschen.
-   `systemctl`: Dienste starten, stoppen oder aktivieren.
-   Text-Editor-Befehle. Unter Linux gibt es verschiedene Text-Editoren, z. B. vi und emacs.

## <a name="common-tasks-for-availability-configurations-of-includessnoversion-mdincludesssnoversion-mdmd-on-linux"></a>Übliche Aufgaben bei Verfügbarkeitskonfigurationen von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] unter Linux
In diesem Abschnitt werden Aufgaben beschrieben, die für alle Linux-basierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Bereitstellungen üblicherweise anfallen.

### <a name="ensure-that-files-can-be-copied"></a>Sicherstellen, dass Dateien kopiert werden können
Jeder [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Benutzer unter Linux sollte in der Lage sein, Dateien eines Servers auf einen anderen Server zu kopieren. Diese Aufgabe ist für die Konfiguration von Verfügbarkeitsgruppen sehr wichtig.

Sowohl unter Linux als auch bei Windows-basierten Installationen können beispielsweise Probleme mit Berechtigungen auftreten. Wenn Windows-Benutzer Dateien von einem Server auf den anderen kopieren können, bedeutet das jedoch nicht, dass sie diese Aufgabe auch unter Linux durchführen können. Oft wird das Befehlszeilen-Hilfsprogramm `scp` (Secure Copy, sicheres Kopieren) verwendet. Im Hintergrund verwendet `scp` OpenSSH (Secure Shell). Abhängig von der Linux-Distribution ist OpenSSH möglicherweise nicht installiert. In diesem Fall muss das Tool zuerst installiert werden. Weitere Informationen zum Konfigurieren von OpenSSH finden Sie unter den folgenden Links für verschiedene Distributionen:
-   [Red Hat Enterprise Linux (RHEL)](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/deployment_guide/ch-openssh)
-   [SUSE Linux Enterprise Server (SLES)](https://en.opensuse.org/SDB:Configure_openSSH)
-   [Ubuntu](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Wenn Sie `scp`verwenden, müssen Sie die Anmeldeinformationen des Servers angeben, wenn es sich nicht um die Quelle oder das Ziel handelt. Beispiel:

```bash
scp MyAGCert.cer username@servername:/folder/subfolder
```

Mit diesem Befehl wird die Datei „MyAGCert.cer“ in den angegebenen Ordner kopiert, der sich auf einem anderen Server befindet. Beachten Sie, dass Sie über die notwendigen Berechtigungen verfügen und möglicherweise Besitzer der Datei sein müssen, um sie zu kopieren. Unter Umständen müssen Sie deswegen zuerst `chown` ausführen. Auch auf dem Zielserver muss der richtige Benutzer auf die Datei zugreifen können, um sie zu ändern. Wenn der `mssql`-Benutzer beispielsweise die Zertifikatdatei wiederherstellen möchte, muss er auf sie zugreifen können.

Auch mit Samba, der Linux-Variante von Server Message Block (SMB), können Freigaben erstellt werden, auf die über UNC-Pfade wie `\\SERVERNAME\SHARE` zugegriffen werden kann. Weitere Informationen zum Konfigurieren von Samba finden Sie unter den folgenden Links für verschiedene Distributionen:
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Managing_Confined_Services/chap-Managing_Confined_Services-Samba.html)
-   [SLES](https://www.suse.com/documentation/sles11/book_sle_admin/data/cha_samba.html)
-   [Ubuntu](https://help.ubuntu.com/community/Samba)

Sie können auch SMB-Freigaben verwenden, die auf Windows statt Linux basieren. Die Voraussetzungen dafür sind, dass der Samba-Client auf dem Linux-Server richtig konfiguriert ist, der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] hostet, und dass die Freigabe über die richtigen Zugriffsberechtigungen verfügt. In einer Umgebung mit mehreren Betriebssystemen kann so beispielsweise eine vorhandene Infrastruktur für Linux-basierte [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Bereitstellungen verwendet werden.

Wichtig ist, dass die bereitgestellte Samba-Version mit SMB 3.0 kompatibel sein sollte. Seit der Einführung der SMB-Unterstützung in [!INCLUDE[sssql11-md](../includes/sssql11-md.md)] müssen alle Freigaben SMB 3.0 unterstützen. Wenn Sie für die Freigabe Samba statt Windows Server verwenden, sollte die Samba-basierte Freigabe mindestens Samba 4.0 verwenden. Idealerweise sollte jedoch die Version 4.3 oder höher eingesetzt werden, da diese SMB 3.1.1 unterstützt. Viele hilfreiche Informationen zu SMB und Linux finden Sie unter [SMB3 in Samba (SMB 3.0 für Samba)](https://events.static.linuxfound.org/sites/events/files/slides/smb3-in-samba.pr__0.pdf).

Eine weitere Option ist eine NFS-Freigabe (Network File System). Diese kann allerdings nur für Linux-basierte, nicht aber für Windows-basierte Bereitstellungen von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] verwendet werden.

### <a name="configure-the-firewall"></a>Konfigurieren der Firewall
Linux-Distributionen verfügen ähnlich wie Windows über eine integrierte Firewall. Wenn Ihr Unternehmen eine externe Firewall für Server verwendet, ist es möglicherweise akzeptabel, die Linux-Firewall zu deaktivieren. Unabhängig davon, welche Firewall wo aktiviert wird, müssen bestimmte Ports geöffnet werden. In der folgenden Tabelle werden die Ports aufgeführt, die üblicherweise für hochverfügbare [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Bereitstellungen unter Linux erforderlich sind.

| Portnummer | type     | BESCHREIBUNG                                                                                                                 |
|-------------|----------|-----------------------------------------------------------------------------------------------------------------------------|
| 111         | TCP/UDP  | NFS: `rpcbind/sunrpc`                                                                                                    |
| 135         | TCP      | Samba (falls verwendet): Endpunktzuordnung                                                                                          |
| 137         | UDP      | Samba (falls verwendet): NetBIOS-Namensdienst                                                                                      |
| 138         | UDP      | Samba (falls verwendet): NetBIOS-Datagramm                                                                                          |
| 139         | TCP      | Samba (falls verwendet): NetBIOS-Sitzung                                                                                           |
| 445         | TCP      | Samba (falls verwendet): SMB über TCP                                                                                              |
| 1433        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]: Standardport; kann bei Bedarf mit `mssql-conf set network.tcpport <portnumber>` geändert werden                       |
| 2049        | TCP, UDP | NFS (falls verwendet)                                                                                                               |
| 2224        | TCP      | Pacemaker: wird von `pcsd` verwendet                                                                                                |
| 3121        | TCP      | Pacemaker: erforderlich, wenn Pacemaker Remote-Knoten vorhanden sind                                                                    |
| 3260        | TCP      | iSCSI-Initiator (falls verwendet): kann in `/etc/iscsi/iscsid.config` geändert werden (RHEL); der Port sollte jedoch mit dem des iSCSI-Ziels übereinstimmen |
| 5022        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]: Standardport für den Endpunkt einer Verfügbarkeitsgruppe; kann bei der Erstellung des Endpunkts geändert werden                                |
| 5403        | TCP      | Pacemaker                                                                                                                   |
| 5404        | UDP      | Pacemaker: für Corosync erforderlich, wenn Multicast-UDP verwendet wird                                                                     |
| 5405        | UDP      | Pacemaker: für Corosync erforderlich                                                                                            |
| 21064       | TCP      | Pacemaker: für Ressourcen erforderlich, die DLM verwenden                                                                                 |
| Variable    | TCP      | Endpunktport der Verfügbarkeitsgruppe; der Standardport ist 5022                                                                                           |
| Variable    | TCP      | NFS: Port für `LOCKD_TCPPORT` (befindet sich unter RHEL in `/etc/sysconfig/nfs`)                                              |
| Variable    | UDP      | NFS: Port für `LOCKD_UDPPORT` (befindet sich unter RHEL in `/etc/sysconfig/nfs`)                                              |
| Variable    | TCP/UDP  | NFS: Port für `MOUNTD_PORT` (befindet sich unter RHEL in `/etc/sysconfig/nfs`)                                                |
| Variable    | TCP/UDP  | NFS: Port für `STATD_PORT` (befindet sich unter RHEL in `/etc/sysconfig/nfs`)                                                 |

Weitere Ports, die von Samba genutzt werden können, finden Sie unter [Samba Port Usage (Verwendung von Samba-Ports)](https://wiki.samba.org/index.php/Samba_Port_Usage).

Umgekehrt kann unter Linux anstelle des Ports auch der Name des Diensts als Ausnahme hinzugefügt werden (beispielsweise `high-availability` für Pacemaker). Wenn Sie diese Möglichkeit nutzen möchten, müssen Sie die Dienstnamen Ihrer Distribution verwenden. Unter RHEL können Sie beispielsweise mit dem folgenden Befehl eine Ausnahme in Pacemaker hinzufügen:

```bash
sudo firewall-cmd --permanent --add-service=high-availability
```

**Firewalldokumentation:**
-   [RHEL](https://access.redhat.com/documentation/red_hat_enterprise_linux/7/html/high_availability_add-on_reference/s1-firewalls-haar)
-   [SLES](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html)

### <a name="install-includessnoversion-mdincludesssnoversion-mdmd-packages-for-availability"></a>Installieren von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Verfügbarkeitspaketen
Bei einer einfachen Windows-basierten Installation von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] werden neben der Engine noch einige zusätzliche Komponenten installiert. Unter Linux wird hingegen nur die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Engine installiert. Weitere Komponenten sind optional. Für hochverfügbare [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Instanzen unter Linux sollten zwei Pakete mit [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] installiert werden: der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Agent (*mssql-server-agent*) und das Hochverfügbarkeitspaket (*mssql-server-ha*). Der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Agent ist prinzipiell optional. Da er jedoch der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Auftragsplaner ist und für den Protokollversand benötigt wird, sollte er installiert werden. Auf Windows-basierten Installationen ist der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Agent nicht optional.

>[!NOTE]
>[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Benutzer ohne Vorwissen sollten den [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Agent kennen, da er der integrierte Auftragsplaner von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] ist. Datenbankadministratoren führen mit ihm häufig Sicherungen und andere [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Wartungsaufgaben durch. Während bei einer Windows-basierten Installation von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Agent ein eigener Dienst ist, wird der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Agent unter Linux im Kontext von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] selbst ausgeführt.

Wenn eine Windows-basierte Konfiguration für Verfügbarkeitsgruppen oder Failoverclusterinstanzen verwendet wird, sind diese clusterfähig. Das bedeutet, dass [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] über bestimmte Ressourcen-DLLs verfügt, die einem WSFC bekannt sind („sqagtres.dll“ und „sqsrvres.dll“ für Failoverclusterinstanzen, „hadrres.dll“ für Verfügbarkeitsgruppen) und von diesem verwendet werden, um die Clusterfunktionen von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] fehlerfrei auszuführen. Da das Clustering sowohl außerhalb von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] als auch von Linux selbst stattfindet, musste Microsoft das Äquivalent einer Ressourcen-DLL für Linux-basierte Bereitstellungen von Verfügbarkeitsgruppen und Failoverclusterinstanzen programmieren. Das Ergebnis ist das *mssql-server-ha*-Paket, das auch als [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Ressourcen-Agent für Pacemaker bekannt ist. Informationen zur Installation des *mssql-server-ha*-Pakets finden Sie unter [Installieren der Hochverfügbarkeits- und SQL Server-Agent-Pakete](sql-server-linux-deploy-pacemaker-cluster.md#install-the-sql-server-ha-and-sql-server-agent-packages).

Die anderen optionalen Pakete für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] für Linux, für die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Volltextsuche (*mssql-server-fts*) und für die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Integration Services (*mssql-server-is*) sind nicht für Hochverfügbarkeit erforderlich, und zwar weder für Failoverclusterinstanzen noch für Verfügbarkeitsgruppen.

## <a name="pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux"></a>Pacemaker für Always On-Verfügbarkeitsgruppen und -Failoverclusterinstanzen unter Linux
Aktuell unterstützt Microsoft für Verfügbarkeitsgruppen und Failoverclusterinstanzen ausschließlich die Clusteringlösung Pacemaker mit Corosync. In diesem Abschnitt werden grundlegende Informationen zum Verständnis dieser Lösung bereitgestellt. Außerdem wird deren Planung und Bereitstellung für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Konfigurationen behandelt.

### <a name="ha-add-onextension-basics"></a>Grundlagen zu Hochverfügbarkeits-Add-Ons und -erweiterungen
Alle derzeit unterstützten Distributionen verfügen über ein Hochverfügbarkeits-Add-On oder eine -erweiterung, die auf dem Pacemaker-Clusteringstapel basiert. Dieser enthält zwei Hauptkomponenten: Pacemaker und Corosync. Insgesamt umfasst der Stapel die folgenden Komponenten:
-   Pacemaker: die Hauptkomponente für das Clustering. Sie koordiniert beispielsweise Clustercomputer.
-   Corosync: ein System, das aus einem Framework und aus mehreren APIs besteht, die beispielsweise das Quorum bereitstellen oder fehlgeschlagene Prozesse neu starten können.
-   libQB: eine Bibliothek, die beispielsweise Protokollierungsfunktionen bereitstellt.
-   Ressourcen-Agent: ein Feature, das spezifische Funktionen zur Anwendungsintegration mit Pacemaker bereitstellt.
-   Fence-Agent: ein Feature, das Skripte und Funktionen umfasst, mit denen sich Knoten isolieren und fehlerhafte Knoten verwalten lassen.
    
> [!NOTE]
> Der Clusterstapel wird unter Linux üblicherweise als Pacemaker bezeichnet.

Diese Lösung ähnelt zwar in gewisser Weise der Bereitstellung von Clusterkonfigurationen mit Windows, weist aber gleichzeitig zahlreiche Unterschiede auf. Unter Windows wird für das Clustering der Windows Server-Failovercluster (WSFC) verwendet, der in das Betriebssystem integriert ist. Das Feature zur Erstellung eines WSFC (Failoverclustering) ist standardmäßig deaktiviert. Verfügbarkeitsgruppen und Failoverclusterinstanzen basieren in Windows auf einem WSFC. In diesen sind sie aufgrund der spezifischen Ressourcen-DLL, die von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] bereitgestellt wird, fest integriert. Eine Lösung mit einer solch engen Kopplung ist vor allem deshalb möglich, weil sie von nur einem Anbieter bereitgestellt wird.

![](./media/sql-server-linux-ha-basics/image1.png)

Pacemaker ist für jede unterstützte Linux-Distribution verfügbar. Die Clusteringkomponente kann allerdings an verschiedene Distributionen angepasst sein und unterschiedliche Implementierungen und Versionen aufweisen. Auf einige Unterschiede wird in den Anweisungen in diesem Artikel eingegangen. Die Clusteringebene ist eine Open-Source-Komponente. Sie ist zwar Bestandteil der Distributionen, allerdings nicht so nahtlos integriert wie WSFC unter Windows. Aus diesem Grund stellt Microsoft *mssql-server-ha* zur Verfügung. Dadurch können [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] und der Pacemaker-Stapel fast die gleichen Funktionen für Verfügbarkeitsgruppen und Failoverclusterinstanzen wie unter Windows bereitstellen.

Die vollständige Pacemaker-Dokumentation mit ausführlichen Beschreibungen und Referenzinformationen für RHEL und SLES finden Sie unter:
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-overview-HAAR.html)
-   [SLES](https://www.suse.com/documentation/sle_ha/book_sleha/data/book_sleha.html)

Für Ubuntu steht kein Leitfaden zum Thema Verfügbarkeit bereit.

Weitere Informationen zum gesamten Stapel finden Sie auch in der offiziellen [Pacemaker-Dokumentation](https://clusterlabs.org/doc/) auf der Website von Clusterlabs.

### <a name="pacemaker-concepts-and-terminology"></a>Pacemaker-Konzepte und -Terminologie
In diesem Abschnitt werden allgemeine Konzepte und die Terminologie einer Pacemaker-Implementierung beschrieben.

#### <a name="node"></a>Node
Ein Knoten ist ein Server in einem Cluster. Ein Pacemaker-Cluster unterstützt nativ bis zu 16 Knoten. Diese Zahl kann überschritten werden, wenn Corosync nicht auf zusätzlichen Knoten ausgeführt wird. Da Corosync aber für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] erforderlich ist, ist die maximale Anzahl von Knoten, über die ein Cluster für eine [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-basierte Konfiguration verfügen kann, auf 16 beschränkt. Dieses Limit wird von Pacemaker vorgegeben und hat nichts mit den maximalen Werten für Verfügbarkeitsgruppen oder Failoverclusterinstanzen zu tun, die von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] erzwungen werden. 

#### <a name="resource"></a>Resource
Sowohl bei WSFCs als auch bei Pacemaker-Clustern gibt es das Konzept einer Ressource. Eine Ressource ist eine bestimmte Funktion, die im Kontext des Clusters ausgeführt wird. Dies kann beispielsweise ein Datenträger oder eine IP-Adresse sein. In Pacemaker können z. B. sowohl Ressourcen für Failoverclusterinstanzen als auch für Verfügbarkeitsgruppen erstellt werden. Diese Vorgehensweise ähnelt der für einen WSFC, da hier beim Konfigurieren einer Verfügbarkeitsgruppe eine [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Ressource für eine Failoverclusterinstanz oder Verfügbarkeitsgruppe verwendet wird. Der Unterschied besteht jedoch darin, dass die Pacemaker-Integration von [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] anders funktioniert.

In Pacemaker gibt es Standard- und Klonressourcen. Klonressourcen werden auf allen Knoten gleichzeitig ausgeführt. Ein Beispiel ist eine IP-Adresse, die für den Lastenausgleich auf mehreren Knoten verwendet wird. Für Failoverclusterinstanzen wird eine Standardressource erstellt, da jeweils nur ein Knoten eine Failoverclusterinstanz hosten kann.

Wenn eine Verfügbarkeitsgruppe erstellt wird, ist eine besondere Art der Klonressource erforderlich, die als Ressource mit mehreren Zuständen bezeichnet wird. Eine Verfügbarkeitsgruppe enthält zwar nur ein primäres Replikat, wird aber auf allen Knoten ausgeführt, für die sie konfiguriert wurde. Außerdem kann sie möglicherweise Vorgänge wie schreibgeschützte Zugriffe zulassen. Da hierbei Knoten in Echtzeit verwendet werden, gibt es für Ressourcen die beiden Zustände Master und Slave. Weitere Informationen finden Sie unter [Multi-state resources: Resources that have multiple modes (Ressourcen mit mehreren Zuständen: Ressourcen, die über mehrere Modi verfügen)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/s1-multistateresource-HAAR.html).

#### <a name="resource-groupssets"></a>Ressourcengruppen und -sets
In Pacemaker gibt es das Konzept einer Ressourcengruppe, das mit Rollen auf einem WSFC vergleichbar ist. Eine Ressourcengruppe (unter SLES auch als „Set“ bezeichnet) ist eine Sammlung von Ressourcen, die zusammenarbeiten und als eine einzelne Einheit ein Failover von einem Knoten zu einem anderen ausführen können. Ressourcengruppen dürfen keine Ressourcen enthalten, die als Master oder Slave konfiguriert sind. Daher können sie nicht für Verfügbarkeitsgruppen verwendet werden. Eine Ressourcengruppe kann prinzipiell für Failoverclusterinstanzen verwendet werden. Diese Konfiguration wird jedoch nicht empfohlen.

#### <a name="constraints"></a>Einschränkungen
Auf einem WSFC gibt es verschiedene Ressourcenparameter und Abhängigkeiten. Mit Letzteren wird für den WSFC die Beziehung zwischen einer unter- und einer übergeordneten Ressource definiert. Eine Abhängigkeit ist eine Regel, die dem WSFC mitteilt, welche Ressource zuerst online sein muss.

Auf einem Pacemaker-Cluster gibt es zwar keine Abhängigkeiten, dafür jedoch Einschränkungen. Unterschieden werden Kollokations-, Orts- und Sortierungseinschränkungen.
-   Mit einer Kollokationseinschränkung wird festgelegt, ob die Ausführung von Ressourcen auf demselben Knoten erzwungen werden soll.
-   Mit einer Ortseinschränkung wird dem Pacemaker-Cluster mitgeteilt, an welcher Stelle eine Ressource ausgeführt oder nicht ausgeführt werden darf.
-   Mit einer Sortierungseinschränkung wird dem Pacemaker-Cluster die Reihenfolge mitgeteilt, in der die Ressourcen gestartet werden sollen.

> [!NOTE]
> Für Ressourcen in einer Ressourcengruppe sind keine Kollokationseinschränkungen erforderlich, da diese Ressourcen als Einheit betrachtet werden.

#### <a name="quorum-fence-agents-and-stonith"></a>Quorum, Fence-Agents und STONITH
Ein Quorum in Pacemaker ähnelt konzeptionell dem eines WSFC. Mit einem Clusterquorum soll sichergestellt werden, dass der Cluster dauerhaft ausgeführt wird. Sowohl WSFCs als auch Hochverfügbarkeits-Add-Ons für Linux-Distributionen nutzen Abstimmungen, bei denen jeder Knoten für das Quorum berücksichtigt wird. Dabei sollte immer eine Mehrheit der Stimmen angestrebt werden, da ansonsten im schlimmsten Fall der Cluster heruntergefahren wird.

Anders als bei einem WSFC gibt es keine Zeugenressource für das Quorum. Das Ziel besteht aber ebenso wie bei einem WSFC darin, eine ungerade Anzahl abstimmender Knoten sicherzustellen. Die Quorumkonfiguration für Verfügbarkeitsgruppen unterscheidet sich von der für Failoverclusterinstanzen.

WSFCs überwachen den Teilnahmestatus von Knoten und greifen bei Problemen ein. In neueren WSFC-Versionen gibt es beispielsweise Features, mit denen ein Knoten in die Quarantäne verschoben werden kann, wenn sich dieser nicht wie erwartet verhält oder nicht verfügbar ist (etwa dann, wenn der Knoten inaktiv oder die Netzwerkverbindung unterbrochen ist). Unter Linux wird diese Funktion von einem Fence-Agent bereitgestellt. Dieses Konzept wird manchmal als Fencing (Umgrenzung) bezeichnet. Fence-Agents sind normalerweise an die Bereitstellung angepasst und werden häufig von Hardwareanbietern und einigen Softwareanbietern (beispielsweise Anbietern von Hypervisoren) bereitgestellt. VMware stellt beispielsweise einen Fence-Agent zur Verfügung, der für Linux-VMs verwendet werden kann, die mit vSphere virtualisiert werden.

Quorum und Fencing sind eng mit einem weiteren Konzept verknüpft, das unter dem Namen STONITH (Shoot the Other Node in the Head) bekannt ist. STONITH ist erforderlich, damit ein Pacemaker-Cluster auf allen Linux-Distributionen unterstützt wird. Weitere Informationen finden Sie unter [Fencing in a Red Hat High Availability Cluster (Fencing in einem Red Hat-Hochverfügbarkeitscluster)](https://access.redhat.com/solutions/15575) (RHEL).

#### <a name="corosyncconf"></a>corosync.conf
Die Datei `corosync.conf` enthält die Konfiguration des Clusters und befindet sich im Verzeichnis `/etc/corosync`. Wenn der Cluster richtig eingerichtet wurde, müssen Sie die Datei für Routinevorgänge nicht ändern.

#### <a name="cluster-log-location"></a>Speicherort der Clusterprotokolldatei
Die Speicherorte für Protokolle von Pacemaker-Clustern unterscheiden sich je nach Distribution.
-   RHEL und SLES: `/var/log/cluster/corosync.log`
-   Ubuntu: `/var/log/corosync/corosync.log`

Wenn Sie den Standardspeicherort für Protokolle ändern möchten, müssen Sie `corosync.conf` anpassen.

## <a name="plan-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Planen von Pacemaker-Clustern für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
In diesem Abschnitt werden die wichtigen Punkte beschrieben, die Sie bei der Planung eines Pacemaker-Clusters berücksichtigen müssen.

### <a name="virtualizing-linux-based-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Virtualisieren von Linux-basierten Pacemaker-Clustern für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Wenn Sie virtuelle Computer für Linux-basierte [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Bereitstellungen für Verfügbarkeitsgruppen und Failoverclusterinstanzen nutzen, gelten dieselben Regeln wie für ihre Windows-basierten Gegenstücke. Microsoft stellt für virtualisierte [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Bereitstellungen grundlegende Supportrichtlinien im Artikel [Microsoft-Support: KB 956893](https://support.microsoft.com/help/956893/support-policy-for-microsoft-sql-server-products-that-are-running-in-a-hardware-virtualization-environment) bereit. Darüber hinaus gelten für verschiedene Hypervisoren wie Microsoft Hyper-V und VMware ESXi möglicherweise noch andere Regeln aufgrund plattformspezifischer Unterschiede.

Bei der Virtualisierung von Verfügbarkeitsgruppen und Failoverclusterinstanzen müssen Sie sicherstellen, dass für die Knoten eines bestimmten Pacemaker-Clusters Antiaffinität festgelegt ist. Wenn in einer Verfügbarkeitsgruppe oder Failoverclusterinstanz die VMs, die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] hosten, für Hochverfügbarkeit konfiguriert sind, sollten diese niemals auf demselben Hypervisorhost ausgeführt werden. Wenn z. B. eine Failoverclusterinstanz mit zwei Knoten bereitgestellt wird, müssen *mindestens* drei Hypervisorhosts vorhanden sein, damit eine VM, die einen Knoten hostet, bei einem Hostausfall an anderer Stelle platziert werden kann. Das ist vor allem dann wichtig, wenn Features wie die Livemigration oder vMotion verwendet werden.

Weitere Informationen finden Sie in den folgenden Dokumenten:
-   Hyper-V-Dokumentation: [Verwenden von Gastclustering für Hochverfügbarkeit](https://technet.microsoft.com/library/dn440540(v=ws.11).aspx)
-   Whitepaper (für Windows-basierte Bereitstellungen geschrieben; die meisten Informationen sind aber auf Linux übertragbar): [Planning Highly Available, Mission Critical SQL Server Deployments with VMware vSphere (Planen hochverfügbarer, unternehmenskritischer SQL Server-Bereitstellungen mit VMware vSphere)](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/solutions/vmware-vsphere-highly-available-mission-critical-sql-server-deployments.pdf)

### <a name="networking"></a>Netzwerk
Ein Pacemaker-Cluster benötigt im Gegensatz zu einem WSFC keinen dedizierten Namen und auch keine dedizierte IP-Adresse für den Cluster selbst. Für Verfügbarkeitsgruppen und Failoverclusterinstanzen sind IP-Adressen (siehe jeweilige Dokumentation für weitere Informationen), aber keine Namen erforderlich, da keine Netzwerknamensressource vorhanden ist. Unter SLES kann eine IP-Adresse zwar zu Verwaltungszwecken konfiguriert werden, jedoch ist dies nicht erforderlich (siehe [Erstellen des Pacemaker-Clusters](sql-server-linux-deploy-pacemaker-cluster.md#create)).

Eine Gemeinsamkeit zwischen einem WSFC und Pacemaker besteht darin, dass Pacemaker prinzipiell redundante Netzwerke und damit verschiedene (virtuelle oder physische) Netzwerkadapter mit unterschiedlichen IP-Adressen bevorzugt. Bei der Clusterkonfiguration verfügt dann jede IP-Adresse über einen eigenen Ring. Ebenso wie im Fall von WSFCs sind viele Implementierungen aktuell jedoch virtualisiert oder befinden in der öffentlichen Cloud, wo nur ein einziger virtueller Netzwerkadapter für den Server verfügbar ist. Wenn alle physischen und virtuellen Netzwerkadapter mit demselben physischen oder virtuellen Switch verbunden sind, gibt es keine tatsächliche Redundanz auf der Netzwerkebene. Genau genommen können deswegen für den virtuellen Computer nicht mehrere Netzwerkadapter konfiguriert werden. Netzwerkredundanz für virtualisierte Bereitstellungen wird in der Regel durch den Hypervisor selbst sichergestellt. Wenn eine öffentliche Cloud genutzt wird, wird die Redundanz immer dort sichergestellt.

Wenn Pacemaker mit mehreren Netzwerkadaptern verwendet wird, besteht ein Unterschied zu einem WSFC darin, dass Pacemaker mehrere IP-Adressen in einem Subnetz zulässt. Das ist bei einem WSFC nicht der Fall. Weitere Informationen zu mehreren Subnetzen und Linux-Clustern finden Sie im Artikel [Konfigurieren mehrerer Subnetze](sql-server-linux-configure-multiple-subnet.md).

### <a name="quorum-and-stonith"></a>Quorum und STONITH
Die Quorumkonfiguration und -anforderungen beziehen sich auf spezifische [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-Bereitstellungen für Verfügbarkeitsgruppen und Failoverclusterinstanzen.

Für Pacemaker-Cluster ist STONITH erforderlich. Wie Sie STONITH konfigurieren, erfahren Sie in der Dokumentation Ihrer Distribution. Ein Beispiel für SLES finden Sie unter [Storage-based Fencing (Speicherbasiertes Fencing)](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_storage_protect_fencing.html). Für VMware vCenter für ESXI-basierte Lösungen ist auch ein STONITH-Agent verfügbar. Weitere Informationen finden Sie unter [Stonith Plugin Agent for VMWare VM VCenter SOAP Fencing (Unofficial) (STONITH-Plug-In-Agent für SOAP-Fencing in VMware vCenter (inoffiziell))](https://github.com/olafrv/fence_vmware_soap).

### <a name="interoperability"></a>Interoperabilität
In diesem Abschnitt wird beschrieben, wie ein Linux-basierter Cluster mit einem WSFC oder mit anderen Linux-Distributionen interagieren kann.

#### <a name="wsfc"></a>WSFC
Derzeit kann ein WSFC nicht direkt mit einem Pacemaker-Cluster interagieren. Es ist daher nicht möglich, eine Verfügbarkeitsgruppe oder Failoverclusterinstanz zu erstellen, die für einen WSFC und für Pacemaker verwendet werden kann. Es gibt jedoch zwei Interoperabilitätslösungen, die für Verfügbarkeitsgruppen entwickelt wurden. Eine Failoverclusterinstanz kann nur dann Teil einer plattformübergreifenden Konfiguration sein, wenn sie als Instanz in einem der folgenden beiden Szenarios verwendet wird:
-   Eine Verfügbarkeitsgruppe mit dem Clustertyp „None“ (Keine) ist vorhanden. Weitere Informationen finden Sie in der [Dokumentation zu Windows-Verfügbarkeitsgruppen](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).
-   Eine verteilte Verfügbarkeitsgruppe ist vorhanden. Bei dieser handelt es sich um eine besondere Art der Verfügbarkeitsgruppe, mit der zwei unterschiedliche Verfügbarkeitsgruppen als Einheit konfiguriert werden können. Weitere Informationen finden Sie in der [Dokumentation zu verteilten Verfügbarkeitsgruppen](../database-engine/availability-groups/windows/distributed-availability-groups.md).

#### <a name="other-linux-distributions"></a>Andere Linux-Distributionen
Unter Linux müssen sich alle Knoten eines Pacemaker-Clusters auf derselben Distribution befinden. Ein RHEL-Knoten kann beispielsweise nicht Teil eines Pacemaker-Clusters sein, der über einen SLES-Knoten verfügt. Der Hauptgrund dafür wurde bereits erwähnt: Da Distributionen möglicherweise unterschiedliche Versionen und Funktionen aufweisen, kann dies die Funktionsfähigkeit beeinträchtigen. Wenn Sie unterschiedliche Distributionen verwenden, hat dies dieselben Auswirkungen, wie wenn Sie WSFCs und Linux kombinieren. Verwenden Sie daher den Clustertyp „None“ oder verteilte Verfügbarkeitsgruppen.

## <a name="next-steps"></a>Nächste Schritte
[Bereitstellen eines Pacemaker-Clusters für SQL Server für Linux](sql-server-linux-deploy-pacemaker-cluster.md)
