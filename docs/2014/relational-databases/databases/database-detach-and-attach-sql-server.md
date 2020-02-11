---
title: Anfügen und Trennen von Datenbanken (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [SQL Server], detaching
- detach database [SQL Server]
- databases [SQL Server], attaching
- removing databases
- transaction logs [SQL Server], detaching
- databases [SQL Server], removing
- restoring [SQL Server], attached databases
- transaction logs [SQL Server], attaching
- differential backups, after detaching
- moving databases
- attach database [SQL Server]
- detaching databases [SQL Server]
- differential base [SQL Server]
- attaching databases [SQL Server]
- databases [SQL Server], moving
ms.assetid: d0de0639-bc54-464e-98b1-6af22a27eb86
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5eae331b064d83510d657f6f09a819955e6259a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62762419"
---
# <a name="database-detach-and-attach-sql-server"></a>Anfügen und Trennen von Datenbanken (SQL Server)
  Die Daten- und Transaktionsprotokolldateien einer Datenbank können getrennt und anschließend an dieselbe oder eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angefügt werden. Das Trennen und Anfügen einer Datenbank ist hilfreich, wenn Sie die Datenbank in eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf demselben Computer ändern oder wenn Sie die Datenbank verschieben möchten.  
  
 Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicherformat für Datenträger stimmt in 64-Bit- und in 32-Bit-Umgebungen überein. Daher können Anfügevorgänge für 32-Bit- und 64-Bit-Umgebungen übergreifend ausgeführt werden.  Eine Datenbank, die von einer in der einen Umgebung ausgeführten Serverinstanz getrennt wird, kann an eine Serverinstanz angefügt werden, die in einer anderen Umgebung ausgeführt wird.  
  
  
  
##  <a name="Security"></a> Sicherheit  
 Dateizugriffsberechtigungen werden während einer Reihe von Datenbankvorgängen festgelegt, einschließlich des Trennens oder Anfügens einer Datenbank.  
  
> [!IMPORTANT]  
>  Das Anfügen oder Wiederherstellen von Datenbanken aus unbekannten oder nicht vertrauenswürdigen Quellen wird nicht empfohlen. Solche Datenbanken können bösartigen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code ausführt oder Fehler verursacht, indem er das Schema oder die physische Datenbankstruktur ändert. Bevor Sie eine Datenbank aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, führen Sie [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) für die Datenbank auf einem nicht Produktionsserver aus, und überprüfen Sie außerdem den Code, z. b. gespeicherte Prozeduren oder anderen benutzerdefinierten Code, in der Datenbank.  
  
##  <a name="DetachDb"></a>Trennen einer Datenbank  
 Durch das Trennen einer Datenbank wird diese aus der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt. Die Datenbank selbst bleibt jedoch innerhalb der Daten- und Transaktionsprotokolldateien intakt. Diese Dateien können anschließend verwendet werden, um die Datenbank einer beliebigen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]anzufügen. Darin eingeschlossen ist der Server, von dem die Datenbank ursprünglich getrennt wurde.  
  
 Eine Datenbank kann in folgenden Fällen nicht getrennt werden:  
  
-   Die Datenbank ist repliziert und veröffentlicht. Wenn die Datenbank repliziert ist, muss deren Veröffentlichung aufgehoben werden. Bevor Sie die Datenbank trennen können, müssen Sie die Veröffentlichung deaktivieren, indem Sie [sp_replicationdboption](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)ausführen.  
  
    > [!NOTE]  
    >  Wenn Sie **sp_replicationdboption**nicht verwenden können, können Sie die Replikation durch Ausführen von [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)entfernen.  
  
-   Eine Datenbankmomentaufnahme ist in der Datenbank vorhanden.  
  
     Bevor Sie die Datenbank trennen können, müssen Sie alle Momentaufnahmen löschen. Weitere Informationen finden Sie unter [Löschen einer Datenbank-Momentaufnahme &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)angefügt werden.  
  
    > [!NOTE]  
    >  Eine Datenbankmomentaufnahme kann nicht getrennt oder angefügt werden.  
  
-   Die Datenbank wird in einer Datenbank-Spiegelungssitzung gespiegelt.  
  
     Die Datenbank kann nur getrennt werden, wenn die Sitzung beendet wird. Weitere Informationen finden Sie unter [Entfernen der Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
-   Die Datenbank ist fehlerverdächtig. Eine fehlerverdächtige Datenbank kann nicht getrennt werden. Zum Trennen müssen Sie für die Datenbank den Notfallmodus aktivieren. Weitere Informationen zum Aktivieren des Notfallmodus für eine Datenbank finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
-   Die Datenbank ist eine Systemdatenbank.  
  
### <a name="backup-and-restore-and-detach"></a>Sichern, Wiederherstellen und Trennen  
 Beim Trennen einer schreibgeschützten Datenbank gehen Informationen zu den differenziellen Basen von differenziellen Sicherungen verloren. Weitere Informationen finden Sie unter [Differenzielle Sicherungen &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).  
  
### <a name="responding-to-detach-errors"></a>Antworten auf Fehler beim Trennen  
 Fehler beim Trennen einer Datenbank können verhindern, dass die Datenbank ordnungsgemäß geschlossen wird und das Transaktionsprotokoll neu erstellt wird. Führen Sie die folgenden Maßnahmen aus, falls eine Fehlermeldung angezeigt wird:  
  
1.  Fügen Sie alle zur Datenbank gehörenden Dateien neu an, nicht nur die primäre Datei.  
  
2.  Beheben Sie das Problem, das die Fehlermeldung verursacht hat.  
  
3.  Trennen Sie die Datenbank erneut.  
  
##  <a name="AttachDb"></a>Anfügen einer Datenbank  
 Eine kopierte oder getrennte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank kann angefügt werden. Wenn Sie eine [!INCLUDE[ssVersion2005](../../includes/sscurrent-md.md)] Serverinstanz anfügen, werden die Katalogdateien von Ihrem vorherigen Speicherort aus zusammen mit den anderen Datenbankdateien angefügt [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], wie in. Weitere Informationen finden Sie unter [Upgrade der Volltextsuche](../search/upgrade-full-text-search.md).  
  
 Wenn Sie eine Datenbank anfügen, müssen alle Datendateien (MDF- und NDF-Dateien) verfügbar sein. Wenn eine Datendatei einen anderen Pfad als beim Erstellen oder beim letzten Anfügen der Datenbank aufweist, müssen Sie den aktuellen Pfad der Datei angeben.  
  
> [!NOTE]  
>  Wenn die angefügte primäre Datendatei schreibgeschützt ist, geht [!INCLUDE[ssDE](../../includes/ssde-md.md)] davon aus, dass auch die Datenbank schreibgeschützt ist.  
  
 Wenn eine verschlüsselte Datenbank zum ersten Mal an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angefügt wird, muss der Datenbankbesitzer den Masterschlüssel der Datenbank öffnen, indem er die folgende Anweisung ausführt: Open Master Key entschlüsseln by password = **'*`password`*'**. Es empfiehlt sich, die automatische Entschlüsselung des Masterschlüssels zu aktivieren, indem folgende Anweisung ausgeführt wird: ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY. Weitere Informationen finden Sie unter [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) und [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).  
  
 Die Anforderungen für das Anfügen von Protokolldateien hängen wie im Folgenden beschrieben teilweise davon ab, ob die Datenbank Lese-/Schreibzugriff aufweist oder schreibgeschützt ist:  
  
-   Für eine Datenbank mit Lese-/Schreibzugriff können Sie gewöhnlich eine Protokolldatei in einem neuen Speicherort anfügen. In manchen Fällen sind zum erneuten Anfügen der Datenbank jedoch die vorhandenen Protokolldateien erforderlich. Bewahren Sie daher unbedingt immer alle getrennten Protokolldateien auf, bis die Datenbank erfolgreich ohne sie angefügt wurde.  
  
     Wenn eine Datenbank mit Lese-/Schreibzugriff eine einzige Protokolldatei aufweist und Sie keinen neuen Speicherort für die Protokolldatei angeben, wird beim Anfügen im alten Speicherort nach der Datei gesucht. Wenn sie gefunden wird, wird die alte Protokolldatei verwendet, unabhängig davon, ob die Datenbank ordnungsgemäß heruntergefahren wurde. Wenn allerdings die alte Protokolldatei nicht gefunden wird und die Datenbank ordnungsgemäß heruntergefahren wurde und keine aktive Protokollkette aufweist, wird beim Anfügen versucht, eine neue Protokolldatei für die Datenbank zu erstellen.  
  
-   Wenn die angefügte primäre Datendatei schreibgeschützt ist, [!INCLUDE[ssDE](../../includes/ssnoversion-md.md)] kann den in der primären Datei gespeicherten Protokoll Speicherort nicht aktualisieren.  
  
  
  
###  <a name="Metadata"></a>Metadatenänderungen beim Anfügen einer Datenbank  
 Wenn eine schreibgeschützte Datenbank getrennt und dann erneut angefügt wird, gehen die Sicherungsinformationen zur aktuellen differenziellen Basis verloren. Bei der *differenziellen Basis* handelt es sich um die letzte vollständige Sicherung aller Daten in der Datenbank oder einer Teilmenge ihrer Dateien oder Dateigruppen. Ohne die Basissicherungsinformationen ist die **master** -Datenbank nicht mehr mit der schreibgeschützten Datenbank synchronisiert. Daher können später erstellte differenzielle Sicherungen zu unerwarteten Ergebnissen führen. Wenn Sie deshalb differenzielle Sicherungen für eine schreibgeschützte Datenbank verwenden, sollten Sie nach dem erneuten Anfügen der Datenbank eine neue differenzielle Basis einrichten, indem Sie eine vollständige Sicherung erstellen. Informationen zum Verwenden von differenziellen Sicherungen finden Sie unter [Differenzielle Sicherungen &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).  
  
 Beim Anfügen wird die Datenbank gestartet. Im Allgemeinen wird die Datenbank beim Anfügen in genau demselben Status wieder verfügbar gemacht, in dem sie sich unmittelbar vor dem Trennen oder Kopieren befunden hat. Die datenbankübergreifenden Besitzketten für die Datenbank werden durch Trenn- und Anfügevorgänge jedoch deaktiviert. Informationen zum Aktivieren der Verkettung finden Sie unter [Datenbankübergreifende Besitzverkettung (Serverkonfigurationsoption)](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md). Außerdem wird TRUSTWORTHY auf OFF festgelegt, wenn die Datenbank angefügt wird. Informationen zum Festlegen von TRUSTWORTHY auf ON finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
### <a name="backup-and-restore-and-attach"></a>Sichern, Wiederherstellen und Anfügen  
 Eine Datenbank mit Wiederherstellungsdateien kann ebenso wie eine Datenbank, die vollständig oder teilweise offline ist, nicht angefügt werden. Sie können die Datenbank anfügen, wenn Sie die Wiederherstellungssequenz beenden. Sie können die Wiederherstellungssequenz anschließend erneut starten.  
  
###  <a name="OtherServerInstance"></a> Anfügen einer Datenbank an eine andere Serverinstanz  
  
> [!IMPORTANT]  
>  Eine Datenbank, die in einer neueren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt wurde, kann in früheren Versionen nicht angefügt werden.  
  
 Wenn Sie eine Datenbank an eine andere Serverinstanz anfügen, müssen Sie die Metadaten für die Datenbank, wie Anmeldenamen und Aufträge, auf der anderen Serverinstanz unter Umständen teilweise oder vollständig neu erstellen, um Benutzern und Anwendungen ein konsistentes Verhalten zu bieten. Weitere Informationen finden Sie unter [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Serverinstanz &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So trennen Sie eine Datenbank**  
  
-   [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [Trennen einer Datenbank](detach-a-database.md)  
  
 **So fügen Sie eine Datenbank an**  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [Anfügen einer Datenbank](attach-a-database.md)  
  
-   [sp_attach_db &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql)  
  
-   [sp_attach_single_file_db &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql)  
  
 **So aktualisieren Sie eine Datenbank mithilfe von Trenn-und Anfüge Vorgängen**  
  
-   [Aktualisieren einer Datenbank durchtrennen und Anfügen &#40;Transact-SQL-&#41;](upgrade-a-database-using-detach-and-attach-transact-sql.md)  
  
 **So verschieben Sie eine Datenbank mithilfe von Trenn-und Anfüge Vorgängen**  
  
-   [Verschieben einer Datenbank durchtrennen und Anfügen &#40;Transact-SQL-&#41;](move-a-database-using-detach-and-attach-transact-sql.md)  
  
 **So löschen Sie eine Daten Bank Momentaufnahme**  
  
-   [Löschen einer Datenbankmomentaufnahme &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankdateien und Dateigruppen](database-files-and-filegroups.md)  
  
  
