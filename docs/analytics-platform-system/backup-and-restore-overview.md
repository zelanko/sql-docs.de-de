---
title: Sichern und Wiederherstellen
description: Beschreibt die Funktionsweise der Datensicherung und-Wiederherstellung für parallele Data Warehouse (PDW). Sicherungs-und Wiederherstellungs Vorgänge werden für die Notfall Wiederherstellung verwendet. Die Sicherung und Wiederherstellung kann auch verwendet werden, um eine Datenbank von einem Gerät auf ein anderes Gerät zu kopieren.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 01/19/2019
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: e7f106e462d3d1bb7848b15523ef3d3f7feed2a1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767209"
---
# <a name="backup-and-restore"></a>Sichern und Wiederherstellen

Beschreibt die Funktionsweise der Datensicherung und-Wiederherstellung für parallele Data Warehouse (PDW). Sicherungs-und Wiederherstellungs Vorgänge werden für die Notfall Wiederherstellung verwendet. Die Sicherung und Wiederherstellung kann auch verwendet werden, um eine Datenbank von einem Gerät auf ein anderes Gerät zu kopieren.  
    
## <a name="backup-and-restore-basics"></a><a name="BackupRestoreBasics"></a>Grundlagen zu Sicherung und Wiederherstellung

Eine PDW- *Datenbanksicherung* ist eine Kopie einer Appliance-Datenbank, die in einem Format gespeichert ist, sodass Sie zum Wiederherstellen der ursprünglichen Datenbank auf einem Gerät verwendet werden kann.  
  
Eine PDW-Datenbanksicherung wird mit der t-SQL-Anweisung [Backup Database](../t-sql/statements/backup-transact-sql.md?view=aps-pdw-2016) erstellt und für die Verwendung mit der [Restore Database](../t-sql/statements/restore-statements-transact-sql.md?view=aps-pdw-2016) -Anweisung formatiert. Er ist für andere Zwecke nicht verwendbar. Die Sicherung kann nur auf einem Gerät mit der gleichen Anzahl oder einer größeren Anzahl von Computeknoten wieder hergestellt werden.  
  
<!-- MISSING LINKS
The [master database](master-database.md) is a SMP SQL Server database. It is backed up with the BACKUP DATABASE statement. To restore master, use the [Restore the Master Database](configuration-manager-restore-master-database.md) page of the Configuration Manager tool.  
-->
  
PDW verwendet SQL Server Sicherungs Technologie zum Sichern und Wiederherstellen von Geräte Datenbanken. SQL Server Sicherungs Optionen sind für die Verwendung der Sicherungs Komprimierung vorkonfiguriert. Sie können keine Sicherungsoptionen wie Komprimierung, Prüfsumme, Blockgröße und Pufferanzahl festlegen.  
  
Datenbanksicherungen werden auf einem oder mehreren Sicherungs Servern gespeichert, die in Ihrem eigenen Kundennetzwerk vorhanden sind.  PDW schreibt eine Datenbanksicherung gleichzeitig direkt von den Computeknoten auf einen Sicherungs Server und stellt eine parallele Sicherung einer Benutzerdatenbank direkt vom Sicherungs Server auf den Computeknoten wieder her.  
  
Sicherungen werden auf dem Sicherungs Server als Satz von Dateien im Windows-Dateisystem gespeichert. Eine PDW-Datenbanksicherung kann nur in PDW wieder hergestellt werden. Sie können jedoch Datenbanksicherungen vom Sicherungs Server an einem anderen Speicherort archivieren, indem Sie standardmäßige Windows-Datei Sicherungs Prozesse verwenden. Weitere Informationen zu Sicherungs Servern finden Sie unter [erwerben und Konfigurieren eines Sicherungs Servers](acquire-and-configure-backup-server.md).  
  
## <a name="database-backup-types"></a><a name="BackupTypes"></a>Daten Bank Sicherungs Typen

Es gibt zwei Arten von Daten, die eine Sicherung erfordern: Benutzer Datenbanken und System Datenbanken (z. b. die Master-Datenbank). PDW sichert das Transaktionsprotokoll nicht.  
  
Eine vollständige Datenbanksicherung ist eine Sicherung einer gesamten PDW-Datenbank. Dies ist der Standard Sicherungstyp. Eine vollständige Sicherung einer Benutzerdatenbank umfasst Datenbankbenutzer und Daten bankrollen. Eine Sicherung von Master enthält Anmeldungen.  
  
Eine differenzielle Sicherung enthält alle Änderungen seit der letzten vollständigen Sicherung. Eine differenzielle Sicherung nimmt normalerweise weniger Zeit in Anspruch als eine vollständige Sicherung und kann häufiger ausgeführt werden. Wenn mehrere differenzielle Sicherungen auf derselben vollständigen Sicherung basieren, enthält jede differenzielle Sicherung alle Änderungen in der vorherigen differenziellen Sicherung.  
  
Beispielsweise können Sie wöchentlich eine vollständige Sicherung und eine differenzielle Sicherung pro Tag erstellen. Zum Wiederherstellen der Benutzerdatenbank muss die vollständige Sicherung und die letzte differenzielle Sicherung (sofern vorhanden) wieder hergestellt werden.  
  
Eine differenzielle Sicherung wird nur für Benutzer Datenbanken unterstützt. Eine Sicherungskopie der Master-Sicherung ist immer eine vollständige Sicherung.  
  
Um das gesamte Gerät zu sichern, müssen Sie eine Sicherung aller Benutzer Datenbanken und eine Sicherung der Master-Datenbank durchführen.  
  
## <a name="database-backup-process"></a><a name="BackupProc"></a>Daten Bank Sicherungsprozess

Das folgende Diagramm zeigt den Datenfluss während einer Datenbanksicherung.  
  
![PDW-Sicherungsprozess](media/backup-process.png "PDW-Sicherungsprozess")  
  
Der Sicherungs Vorgang funktioniert wie folgt:  
  
1.  Der Benutzer sendet eine Sicherungs Datenbank-zql-Anweisung an den Steuer Knoten.  
  
    -   Die Sicherung ist entweder eine vollständige oder eine differenzielle Sicherung.  
  
2.  Für Benutzer Datenbanken erstellt der Steuerungs Knoten (MPP-Engine) einen verteilten Abfrageplan, um eine parallele Datenbanksicherung auszuführen.  
  
3.  Jeder Knoten, der in der Sicherung beteiligt ist, kopiert die Sicherungsdatei mithilfe SQL Server Sicherungsfunktionen auf den Sicherungs Server.  
  
    -   Jeder betroffene Knoten kopiert eine Sicherungsdatei auf den Sicherungs Server.  
  
    -   Die Benutzerdaten Bank Sicherung (vollständig oder differenziell) umfasst eine Sicherung des Teils der Datenbank, die auf jedem Computeknoten gespeichert ist, sowie eine Sicherung der Datenbankbenutzer und Daten bankrollen.  
  
4.  Die Appliance führt die Sicherung parallel über das InfiniBand-Netzwerk aus.  
  
    -   PDW führt jede vollständige und differenzielle Sicherung gleichzeitig aus. Mehrere Datenbanksicherungen werden jedoch nicht gleichzeitig ausgeführt. Jede Sicherungs Anforderung muss warten, bis zuvor übermittelte Sicherungen abgeschlossen sind.  
  
    -   Eine Sicherung der Master-Datenbank sichert nur Daten aus dem Steuerungs Knoten. Dieser Sicherungstyp wird serialisiert ausgeführt.  
  
5.  Eine PDW-Datenbanksicherung ist eine Gruppe von Dateien, die in einem Verzeichnis gespeichert sind, das sich außerhalb des Geräts befindet. Der Verzeichnisname wird als Netzwerkpfad und Verzeichnisname angegeben. Das Verzeichnis darf kein lokaler Pfad sein, und es darf sich nicht auf dem Gerät befinden.  
  
6.  Nachdem die Sicherung abgeschlossen ist, können Sie das Windows-Dateisystem verwenden, um das Sicherungs Verzeichnis bei Bedarf an einen anderen Speicherort zu kopieren.  
  
    -   Eine Sicherung kann nur in einer PDW-Appliance wieder hergestellt werden, die eine gleich große oder größere Anzahl von Computeknoten aufweist.  
  
    -   Sie können den Namen der Sicherung nicht ändern, bevor Sie eine Wiederherstellung durchführen. Der Name des Sicherungs Verzeichnisses muss mit dem Namen des ursprünglichen Namens der Sicherung identisch sein. Der ursprüngliche Name der Sicherung befindet sich in der backup.xml-Datei im Sicherungs Verzeichnis. Zum Wiederherstellen einer Datenbank mit einem anderen Namen können Sie den neuen Namen im RESTORE-Befehl angeben. Beispiel: `RESTORE DATABASE MyDB1 FROM DISK = ꞌ\\10.192.10.10\backups\MyDB2ꞌ`.  
  
## <a name="database-restore-modes"></a><a name="RestoreModes"></a>Daten Bank Wiederherstellungsmodi

Bei einer vollständigen Daten Bank Wiederherstellung wird die PDW-Datenbank mithilfe der Daten in der Datenbanksicherung neu erstellt. Die Daten Bank Wiederherstellung wird durchgeführt, indem zuerst eine vollständige Sicherung wieder hergestellt und dann optional eine differenzielle Sicherung wieder hergestellt wird. Die Daten Bank Wiederherstellung umfasst die Datenbankbenutzer und Daten bankrollen.  
  
Bei einer nur-Header-Wiederherstellung werden die Header Informationen für eine Datenbank zurückgegeben. Es werden keine Daten auf dem Gerät wieder hergestellt.  
  
Eine Geräte Wiederherstellung ist eine Wiederherstellung des gesamten Geräts. Dies schließt die Wiederherstellung aller Benutzer Datenbanken und der Master-Datenbank ein.  
  
## <a name="restore-process"></a><a name="RestoreProc"></a>Wiederherstellungsvorgang

Das folgende Diagramm zeigt den Datenfluss während einer Daten Bank Wiederherstellung.  
  
![Wiederherstellungsprozess](media/restore-process.png "Wiederherstellungsprozess")  
  
## <a name="restoring-to-an-appliance-with-the-same-number-of-compute-nodes"></a>Wiederherstellen auf einer Appliance mit der gleichen Anzahl von Computeknoten * *  
  
Beim Wiederherstellen von Daten erkennt das Gerät die Anzahl der Computeknoten auf dem Quellgerät und dem Zielgerät. Wenn beide Geräte über die gleiche Anzahl von Computeknoten verfügen, funktioniert der Wiederherstellungs Vorgang wie folgt:  
  
1.  Die wieder herzustellende Datenbanksicherung ist auf einer Windows-Dateifreigabe auf einem Sicherungs Server ohne Appliance verfügbar. Um die beste Leistung zu erzielen, ist dieser Server mit dem InfiniBand-Netzwerkgerät verbunden.  
  
2.  Der Benutzer sendet eine zql-Anweisung der [Restore-Datenbank](../t-sql/statements/restore-statements-transact-sql.md?view=aps-pdw-2016) an den Steuer Knoten.  
  
    -   Die Wiederherstellung ist entweder eine vollständige Wiederherstellung oder eine Header Wiederherstellung. Bei der vollständigen Wiederherstellung wird eine vollständige Sicherung wieder hergestellt und anschließend optional eine differenzielle Sicherung wieder hergestellt  
  
3.  Der Steuer Knoten (MPP-Engine) erstellt einen verteilten Abfrageplan, um eine parallele Daten Bank Wiederherstellung auszuführen.  
  
    -   SQL serverpdw führt eine parallele Wiederherstellung einer Benutzerdatenbank durch. Mehrere Datenbanksicherungen und-Wiederherstellungen werden jedoch nicht gleichzeitig ausgeführt. Die MPP-Engine fügt jede RESTORE-Anweisung in eine Warteschlange ein. Es muss gewartet werden, bis zuvor gesendete Sicherungs-und Wiederherstellungs Anforderungen abgeschlossen sind.  
  
    -   Beim Wiederherstellen der Master-Datenbank werden nur die Daten im Steuer Knoten wieder hergestellt. die Wiederherstellung erfolgt serialisiert.  
  
    -   Eine Wiederherstellung der Header Informationen ist ein schneller Vorgang, bei dem keine Daten auf den COMPUTE-oder Steuerungs Knoten wieder hergestellt werden. Stattdessen gibt der Steuer Knoten die Ergebnisse als Abfrageausgabe zurück.  
  
4.  Die Sicherungsdateien werden parallel auf die richtigen Computeknoten kopiert, normalerweise über das InfiniBand-Netzwerk der Anwendung.  
  
5.  Jeder Computeknoten stellt seinen Teil der Benutzerdatenbank wieder her. Wenn eine der Wiederherstellungen nicht erfolgreich abgeschlossen wird, werden alle Datenbanken entfernt, und die Wiederherstellung wird nicht erfolgreich abgeschlossen.  
  
## <a name="restoring-to-an-appliance-with-a-larger-number-of-compute-nodes"></a>Wiederherstellen auf einer Appliance mit einer größeren Anzahl von Computeknoten  
  
Beim Wiederherstellen einer Sicherung auf einer Appliance mit einer größeren Anzahl von Computeknoten wächst die Größe der zugeordneten Datenbank entsprechend der Anzahl der Computeknoten.  
  
Wenn Sie z. b. eine Datenbank mit einer Größe von 60 GB von einem Gerät mit zwei Knoten (30 GB pro Knoten) auf einem Gerät mit 6 Knoten wiederherstellen, erstellt SQL Server PDW eine 180-GB-Datenbank (6 Knoten mit 30 GB pro Knoten) auf der 6-Knoten-Appliance. SQL Server PDW stellt die Datenbank anfänglich auf zwei Knoten wieder her, damit Sie der Quell Konfiguration entspricht, und verteilt die Daten dann auf alle 6 Knoten.  
  
Nach der erneuten Verteilung enthält jeder Computeknoten weniger tatsächliche Daten und mehr freien Speicherplatz als die einzelnen Computeknoten auf der kleineren Quell Appliance. Dank des zusätzlichen Speicherplatzes können Sie der Datenbank weitere Daten hinzufügen. Wenn die wiederhergestellte Datenbankgröße größer ist als Sie benötigen, können Sie die Größe der Datenbankdateien mit [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) verkleinern.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Sicherungs-und Wiederherstellungs Task|Beschreibung|  
|---------------------------|---------------|  
|Bereiten Sie einen Server als Sicherungs Server vor.|[Erwerben und Konfigurieren eines Sicherungsservers](acquire-and-configure-backup-server.md)|  
|Sichern einer Datenbank.|[BACKUP DATABASE](../t-sql/statements/backup-transact-sql.md?view=aps-pdw-2016)|  
|Stellen Sie eine Datenbank wieder her.|[Datenbank wiederherstellen](../t-sql/statements/restore-statements-transact-sql.md?view=aps-pdw-2016)|    

<!-- MISSING LINKS

|Create a disaster recovery plan.|[Create a Disaster Recovery Plan](create-disaster-recovery-plan.md)|
|Restore the master database.|To restore the master database, use the [Restore the master database](configuration-manager-restore-master-database.md) page in the Configuration Manager tool.| 
|Copy a database from one appliance to another appliance.|[Copy a PDW database to another appliance](copy-pdw-database-to-another-appliance.md).|  
|Monitor backups and restores.|[Monitor backups and restores](monitor-backup-and-restore.md)|  

-->
