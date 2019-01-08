---
title: Failovercluster-Instanzen – SQLServer unter Linux | Microsoft-Dokumentation
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: cabebb91ecb7d276066cb0f1c6a2f09c633d0ba0
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52420531"
---
# <a name="failover-cluster-instances---sql-server-on-linux"></a>Failovercluster-Instanzen – SQLServer unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel erläutert die Konzepte im Zusammenhang mit SQL Server Failoverclusterinstanzen (FCI) unter Linux. 

Zum Erstellen einer SQL Server-FCI unter Linux finden Sie unter [Konfigurieren von SQL Server-FCI unter Linux](sql-server-linux-shared-disk-cluster-configure.md)

## <a name="the-clustering-layer"></a>Der Clustering-Ebene

* In RHEL, basiert die clustering-Ebene auf Red Hat Enterprise Linux (RHEL) [HA-Add-On](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf). 

    > [!NOTE] 
    > Zugriff auf Red Hat-HA-Add-On und Dokumentation erfordert ein Abonnement. 

* Bei SLES, die clustering-Ebene auf SUSE Linux Enterprise basiert [hohe Verfügbarkeit-Erweiterung (HAE)](https://www.suse.com/products/highavailability).

    Weitere Informationen für die Clusterkonfiguration, Ressourcenoptionen-Agent, Management, bewährte Methoden und Empfehlungen finden Sie unter [SUSE Linux Enterprise hohe Verfügbarkeit Erweiterung 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

Sowohl für das RHEL-HA-Add-On als auch für die SUSE HAE basieren auf [Pacemaker](https://clusterlabs.org/).

Wie das folgende Diagramm zeigt, wird der Speicher auf zwei Servern angezeigt. Clustering Komponenten - Corosync und Pacemaker - Kommunikation und ressourcenverwaltung zu koordinieren. Einer der Server hat die aktive Verbindung mit dem Storage-Ressourcen und der SQL Server. Wenn Pacemaker ein Fehler erkannt wird verwalten die Clusterkomponenten an, die Ressourcen auf dem anderen Knoten verschieben.  

![Red Hat Enterprise Linux 7 freigegebene Datenträgercluster für SQL](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 


> [!NOTE]
> SQL Server Integration mit Pacemaker unter Linux ist an diesem Punkt nicht als gekoppelt als mit WSFC unter Windows. Von in SQL, besteht keine Kenntnisse über das Vorhandensein des Clusters, alle Orchestrierung befindet sich außerhalb im und der Dienst wird als eigenständige Instanz von Pacemaker gesteuert. Darüber hinaus Name des virtuellen Netzwerks ist spezifisch für die WSFC, es gibt keine Entsprechung desselben in Pacemaker. Es wird erwartet, @@servername und sys.servers des Knotennamens zurückgegeben, während die Cluster-Dmvs Sys. dm_os_cluster_nodes und dm_os_cluster_properties keine Datensätze werden. Eine Verbindungszeichenfolge, die auf einem Zeichenfolgennamen für den Server verweist und nicht die IP-Adresse verwenden, müssen sie in ihren DNS-Server die IP-Adresse verwendet, um die virtuelle IP-Adressressource erstellen (wie in den folgenden Abschnitten erläutert wird) mit dem ausgewählten Server registrieren.

## <a name="number-of-instances-and-nodes"></a>Anzahl der Instanzen und Knoten

Ein Hauptunterschied mit SQL Server unter Linux ist, dass es kann nur eine Installation von SQL Server / Linux-Server vorhanden sein. Diese Installation wird als Instanz bezeichnet. Dies bedeutet, dass im Gegensatz zu Windows Server unterstützt bis zu 25 FCIs pro Windows Server-Failovercluster (WSFC), eine Linux-basierten FCI nur eine einzelne Instanz hat. Diese eine Instanz ist auch eine Standardinstanz; Es gibt kein Konzept für eine benannte Instanz unter Linux. 

Ein Pacemaker-Cluster kann nur bis zu 16 Knoten haben Wenn Corosync beteiligt ist, sodass bis zu 16 Server mit eine einzelne FCI einbeziehen kann. Eine FCI implementiert, mit der Standard Edition von SQL Server unterstützt bis zu zwei Knoten eines Clusters aus, auch wenn der Pacemaker-Clusters die maximale Anzahl von 16 Knoten hat.

In einer SQL Server-FCI ist SQL Server-Instanz auf einem Knoten oder anderen aktiv.

## <a name="ip-address-and-name"></a>IP-Adresse und den Namen
In einem Cluster mit Linux Pacemaker benötigt jeder SQL Server-FCI eine eigene eindeutige IP-Adresse und den Namen. Wenn die FCI-Konfiguration über mehrere Subnetze erstreckt, werden eine IP-Adresse pro Subnetz erforderlich. Der eindeutige Name und IP-Adressen werden verwendet, die FCI auf, sodass Anwendungen und Endbenutzern nicht wissen, welche zugrunde liegenden-Server des Pacemaker-Clusters müssen.

Der Name der FCI in DNS muss identisch mit den Namen der der FCI-Ressource, die in der Pacemaker-Cluster erstellt wird.
Die Namens- und IP-Adresse müssen in DNS registriert werden.

## <a name="shared-storage"></a>Freigegebener Speicher
Alle FCIs, ob diese unter Linux oder Windows Server sind eine Art von gemeinsam genutzten Speicher erfordern. Dieser Speicher wird angezeigt, auf allen Servern, die möglicherweise die FCI hosten können, aber nur ein einzelner Server kann den Speicher für die FCI verwenden, zu jedem Zeitpunkt. Die Optionen für den freigegebenen Speicher unter Linux verfügbar sind:

- iSCSI
- Network File System (NFS)
- Server Message Block (SMB) unter Windows Server leicht unterschiedliche Optionen stehen. Eine Möglichkeit, die derzeit nicht unterstützt für Linux-basierten FCIs ist die Möglichkeit, einen Datenträger zu verwenden, der lokal auf den Knoten für die tempdb-Datenbank ist die SQL Server temporäre Arbeitsbereich ist.

In einer Konfiguration, die mehrere Standorte umfasst, muss was in einem Rechenzentrum gespeichert ist mit den anderen synchronisiert werden. Bei einem Failover wird die FCI wird online geschaltet werden und des Speichers als identisch sein. Erreichen Sie dies erfordert eine externe Methode für die Storage-Replikation, ob sie über die zugrunde liegende Speicherhardware oder softwarebasierten Dienstprogramm durchgeführt wird. 

>[!NOTE]
>Für SQL Server müssen die Linux-basierten Bereitstellungen mithilfe von Datenträgern, die angezeigt wird, direkt auf einem Server mit XFS oder EXT4 formatiert sein. Andere Dateisysteme werden derzeit nicht unterstützt. Hier werden alle Änderungen übernommen.

Der Prozess zum Darstellen von freigegebenen Speichers ist für die verschiedenen unterstützten Methoden identisch:

- Konfigurieren Sie den freigegebenen Speicher
- Einbinden des Speichers als Ordner mit den Servern, die als Knoten des Pacemaker-Clusters, für die FCI dienen
- Falls erforderlich, verschieben Sie die SQL Server-Systemdatenbanken in freigegebenen Speicher
- Test, der Funktionsweise von SQL Server von jedem Server verbunden, auf freigegebenen Speicher

Ein Hauptunterschied mit SQL Server unter Linux ist, während Sie am Standarddateispeicherort Benutzer Daten- und Protokolldateien konfigurieren können, die Systemdatenbanken immer am vorhanden sein müssen `/var/opt/mssql/data`. In Windows Server besteht die Möglichkeit, verschieben die Systemdatenbanken, einschließlich TempDB zur Verfügung. Diese Tatsache spielt in der Verwendung von freigegebenem Speicher für eine FCI konfiguriert ist.

Die Standardpfade für nicht-System-Datenbanken können geändert werden, mithilfe der `mssql-conf` Hilfsprogramm. Informationen zum Ändern der Standardwerte, [ändern Sie die Daten- oder Protokolldatei den Speicherort des Standardverzeichnisses](sql-server-linux-configure-mssql-conf.md#datadir). Sie können auch SQL Server-Daten und Transaktionsprotokolle an anderen Orten speichern, solange sie die richtigen Sicherheitseinstellungen besitzen, auch wenn es sich nicht um einen Standardspeicherort ist; der Speicherort muss angegeben werden.

In den folgenden Themen wird erläutert, wie so konfigurieren Sie die unterstützten Speichertypen für eine Linux-SQL Server-FCI basierte wird:

- [Konfigurieren von Failover-Clusterinstanz - iSCSI - SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [Konfigurieren Sie Failoverclusterinstanz – NFS - SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [Konfigurieren der Failoverclusterinstanz – SMB – SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)
