---
title: Verkleinern einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkdatabase.f1
helpviewer_keywords:
- shrinking databases
- databases [SQL Server], shrinking
- decreasing database size
- database shrinking [SQL Server]
- reducing database size
ms.assetid: 83afbf74-fd50-4c39-831c-b1f473a50620
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 21f58cd6991b760edeefb81c37e02c617f8e09cd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62917007"
---
# <a name="shrink-a-database"></a>Verkleinern einer Datenbank
  In diesem Thema wird beschrieben, wie eine Datenbank mit dem Objekt-Explorer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]verkleinert wird.  
  
 Mit dem Verkleinern von Datendateien wird Platz gewonnen, indem Datenseiten vom Ende der Datei an nicht belegten Platz weiter am Dateianfang verschoben werden. Wurde am Ende der Datei ausreichend Platz geschaffen, kann die Zuordnung der Datenseiten am Ende der Datei aufgehoben und die Datenseiten können ins Dateisystem zurückgegeben werden.  
  

  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Die Datenbank kann nicht unter die Mindestgröße der Datenbank verkleinert werden. Die Mindestgröße stellt die Größe dar, die bei der ursprünglichen Erstellung der Datenbank angegeben wurde, bzw. die letzte explizite Größe, die bei einer Dateigrößenänderung, z. B. mit DBCC SHRINKFILE, festgelegt wurde. Wenn z. B. eine Datenbank ursprünglich mit einer Größe von 10 MB erstellt und auf 100 MB vergrößert wurde, kann die Datenbank höchstens auf 10 MB verkleinert werden, auch wenn alle Daten in der Datenbank gelöscht wurden.  
  
-   Während einer Datenbanksicherung können Sie die Datenbank nicht verkleinern. Umgekehrt können Sie eine Datenbank nicht sichern, während ein Verkleinerungsvorgang für die Datenbank ausgeführt wird.  
  
-   Bei DBCC SHRINKDATABASE tritt ein Fehler auf, wenn ein speicheroptimierter xVelocity-columnstore-Index gefunden wird. Vor dem Aufeinandertreffen mit dem columnstore-Index erledigte Arbeiten werden erfolgreich durchgeführt, die Datenbank ist daher möglicherweise kleiner. Zum Abschließen von DBCC SHRINKDATABASE deaktivieren Sie alle columnstore-Indizes, bevor Sie DBCC SHRINKDATABASE ausführen, und erstellen die columnstore-Indizes dann neu.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Zum Anzeigen des aktuellen freien (nicht zugeordneten) Speicherplatzes in der Datenbank. Weitere Informationen finden Sie unter [Anzeigen von Informationen zum Daten- und Protokollspeicherplatz einer Datenbank](display-data-and-log-space-information-for-a-database.md)  
  
-   Berücksichtigen Sie die folgenden Informationen, wenn Sie eine Datenbank verkleinern möchten:  
  
    -   Ein Verkleinerungsvorgang ist am effektivsten nach einem Vorgang, durch den umfangreicher nicht verwendeter Speicherplatz bereitgestellt wird, z. B. das Abschneiden oder Löschen einer Tabelle.  
  
    -   Die meisten Datenbanken erfordern verfügbaren freien Speicherplatz für die normalen alltäglichen Vorgänge. Wenn Sie eine Datenbank wiederholt verkleinern und feststellen, dass die Datenbankgröße wieder zunimmt, deutet dies darauf hin, dass der verkleinerte Speicherplatz für regelmäßige Vorgänge benötigt wird. In diesem Fall ist das Verkleinern der Datenbank vergeblich.  
  
    -   Bei einem Verkleinerungsvorgang bleibt der Fragmentierungszustand der Indizes in der Datenbank nicht erhalten. Im Allgemeinen wird die Fragmentierung zu einem gewissen Grad verstärkt. Dies ist ein weiterer Grund, die Datenbank nicht wiederholt zu verkleinern.  
  
    -   Legen Sie die Datenbankoption AUTO_SHRINK nicht auf ON fest, es sei denn, besondere Anforderungen machen dies erforderlich.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** oder der festen Datenbankrolle **db_owner** .  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-shrink-a-database"></a>So verkleinern Sie eine Datenbank  
  
1.  Stellen Sie in **Objekt-Explorer**eine Verbindung mit einer Instanz [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]von her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, und klicken Sie dann mit der rechten Maustaste auf die Datenbank, die Sie verkleinern möchten.  
  
3.  Zeigen Sie auf **Tasks**, zeigen Sie auf **Verkleinern**, und klicken Sie dann auf **Datenbank**.  
  
     **Datenbank**  
     Zeigt den Namen der ausgewählten Datenbank an.  
  
     **Aktuell zugewiesener Speicherplatz**  
     Zeigt den gesamten verwendeten und nicht verwendeten Speicherplatz für die ausgewählte Datenbank an.  
  
     **Verfügbarer freier Speicherplatz**  
     Zeigt die Summe des freien Speicherplatzes in den Protokoll- und Datendateien der ausgewählten Datenbank an.  
  
     **Dateien vor dem Freigeben von nicht verwendetem Speicherplatz neu organisieren**  
     Wenn diese Option ausgewählt wird, entspricht dies dem Ausführen von DBCC SHRINKDATABASE mit der Angabe einer Option zur Prozentvorgabe. Das Deaktivieren dieser Option entspricht dem Ausführen von DBCC SHRINKDATABASE mit der Option TRUNCATEONLY. Standardmäßig ist diese Option beim Öffnen des Dialogfelds nicht ausgewählt. Wenn diese Option ausgewählt ist, muss der Benutzer eine Option zur Prozentvorgabe angeben.  
  
     **Maximal verfügbarer Speicherplatz in Dateien nach dem Verkleinern**  
     Geben Sie den Maximalwert für den freien Speicherplatz in Prozent an, der in den Datenbankdateien übrig bleiben soll, nachdem die Datenbank verkleinert wurde. Der zulässige Wert liegt zwischen 0 und 99.  
  
4.  Klicken Sie auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-shrink-a-database"></a>So verkleinern Sie eine Datenbank  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) verwendet, um die Größe der Daten- und Protokolldateien in der Datenbank `UserDB` zu verringern und für `10` Prozent freien Speicherplatz in der Datenbank zu sorgen.  
  
 [!code-sql[DBCC#DBCC_SHRINKDB1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkdb1)]  
  
##  <a name="FollowUp"></a>Nachverfolgung: nach dem Verkleinern einer Datenbank  
 Die zum Verkleinern einer Datei verschobenen Daten können an beliebigen freien Platz in der Datei verschoben werden. Dies führt zur Indexfragmentierung und kann die Leistung von Abfragen, die einen Bereich des Indexes suchen, verlangsamen. Zur Vermeidung von Fragmentierung sollten die Dateiindizes nach der Verkleinerung neu erstellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verkleinern einer Datei](shrink-a-file.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)   
 [DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql)   
 [DBCC SHRINKFILE &#40;Transact-SQL-&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql)   
 [Datenbankdateien und Dateigruppen](database-files-and-filegroups.md)  
  
  
