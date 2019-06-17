---
title: Verwalten der Größe der Transaktionsprotokolldatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], size management
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b2ebcd653adebed5541b1d2cdf814f638d0af683
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63144331"
---
# <a name="manage-the-size-of-the-transaction-log-file"></a>Verwalten der Größe der Transaktionsprotokolldatei
  In einigen Fällen kann sich das physische Verkleinern oder Vergrößern der physischen Protokolldatei des Transaktionsprotokolls einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank als nützlich erweisen. Dieses Thema enthält Informationen zum Überwachen der Größe eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Transaktionsprotokolls, Verkleinern des Transaktionsprotokolls, Hinzufügen oder Vergrößern einer Transaktionsprotokolldatei, Optimieren der Wachstumsrate des **tempdb** -Transaktionsprotokolls und Steuern der Vergrößerung einer Transaktionsprotokolldatei.  
  
  
##  <a name="MonitorSpaceUse"></a> Überwachen der Verwendung von Protokollspeicherplatz  
 Der Protokollspeicherplatz kann mit DBCC SQLPERF (LOGSPACE) überwacht werden. Dieser Befehl gibt Informationen zum derzeit belegten Protokollspeicherplatz zurück und zeigt an, wann das Transaktionsprotokoll abgeschnitten werden muss. Weitere Informationen finden Sie unter [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql). Informationen zur aktuellen Größe einer Protokolldatei, ihrer maximalen Größe sowie der für die Datei festgelegten automatischen Vergrößerungsoption können Sie auch den Spalten **size**, **max_size**, and **growth** für die betreffende Protokolldatei in **sys.database_files** entnehmen. Weitere Informationen finden Sie unter [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).  
  
> [!IMPORTANT]  
>  Vermeiden Sie das Überlasten des Protokolldatenträgers.  
  
  
##  <a name="ShrinkSize"></a> Verkleinern der Protokolldatei.  
 Sie müssen zum Reduzieren der physischen Größe einer physischen Protokolldatei die Protokolldatei verkleinern. Dies ist nützlich, wenn Sie wissen, dass eine Transaktionsprotokolldatei nicht verwendeten und nicht benötigten Speicherplatz enthält. Das Verkleinern einer Protokolldatei kann nur stattfinden, wenn die Datenbank online und mindestens eine virtuelle Protokolldatei frei ist. In einigen Fällen ist eine Verkleinerung des Protokolls möglicherweise erst nach der nächsten Protokollkürzung möglich.  
  
> [!NOTE]  
>  Faktoren, wie z. B. lang andauernde Transaktionen, die virtuelle Protokolldateien über einen längeren Zeitraum hinweg aktiv halten, können die Protokollverkleinerung einschränken oder sogar gänzlich verhindern. Informationen zu Faktoren, die eine Protokollkürzung verzögern können, finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](the-transaction-log-sql-server.md).  
  
 Beim Verkleinern einer Protokolldatei werden virtuelle Protokolldateien entfernt, die keinen Teil des logischen Protokolls enthalten (d. h. *inaktive virtuelle Protokolldateien*). Beim Verkleinern einer Transaktionsprotokolldatei werden ausreichend viele inaktive, virtuelle Protokolldateien vom Ende der Protokolldatei entfernt, um das Protokoll in etwa auf die Zielgröße zu verkleinern.  
  
 **So verkleinern eine Protokolldatei (ohne das Verkleinern von Datenbankdateien)**  
  
-   [DBCC SHRINKFILE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql)  
  
-   [Verkleinern einer Datei](../databases/shrink-a-file.md)  
  
 **Zum Überwachen von Ereignissen für Protokolldatei verkleinern**  
  
-   [Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md).  
  
 `To monitor log space`  
  
-   [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)  
  
-   [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) (Informationen finden Sie in den Spalten **size**, **max_size** und **growth** für die Protokolldateien.)  
  
> [!NOTE]  
>  Für das Verkleinern von Datenbank- und Protokolldateien kann eine automatische Ausführung festgelegt werden. Es wird jedoch von einer automatischen Verkleinerung abgeraten, und die `autoshrink`-Datenbankeigenschaft ist in den Standardeinstellungen auf FALSE festgelegt. Wenn `autoshrink` auf TRUE festgelegt ist, wird die Größe einer Datei nur dann automatisch verkleinert, wenn mehr als 25 Prozent des Speicherplatzes ungenutzt sind. Die Datei wird entweder auf eine Größe verkleinert, bei der 25 Prozent der Datei aus nicht verwendetem Speicherplatz bestehen, oder auf die ursprüngliche Dateigröße, je nachdem, welcher Wert größer ist. Informationen zum Ändern der Einstellung der der `autoshrink` -Eigenschaft finden Sie unter [anzeigen oder Ändern der Eigenschaften einer Datenbank](../databases/view-or-change-the-properties-of-a-database.md)-verwenden Sie die **Auto Shrink** Eigenschaft auf die **Optionen**Seite – oder [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)-verwenden Sie die AUTO_SHRINK-Option.  
  
  
##  <a name="AddOrEnlarge"></a> Hinzufügen oder Vergrößern einer Protokolldatei  
 Alternativ können Sie auch Speicherplatz schaffen, indem Sie entweder die vorhandene Protokolldatei vergrößern (sofern der Speicherplatz dies zulässt) oder der Datenbank eine neue Protokolldatei hinzufügen, wofür normalerweise ein anderer Datenträger verwendet wird.  
  
-   Sie können der Datenbank eine Protokolldatei hinzufügen, indem Sie die ADD LOG FILE-Klausel der ALTER DATABASE-Anweisung verwenden. Durch das Hinzufügen einer Protokolldatei kann das Protokoll vergrößert werden.  
  
-   Sie können die Protokolldatei vergrößern, indem Sie die MODIFY FILE-Klausel der ALTER DATABASE-Anweisung verwenden und die SIZE- und MAXSIZE-Syntax angeben. Weitere Informationen zu dieser Einstellung finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
  
##  <a name="tempdbOptimize"></a> Optimieren der Größe von Tempdb-Transaktionsprotokolls  
 Beim Neustarten einer Serverinstanz wird das Transaktionsprotokoll der **tempdb** -Datenbank auf seine ursprüngliche Größe (vor einer automatischen Größenerweiterung) zurückgesetzt. Dies kann eine Leistungsminderung des **tempdb** -Transaktionsprotokolls zur Folge haben. Der damit verbundene Verwaltungsaufwand lässt sich vermeiden, indem Sie nach dem Starten oder erneuten Starten der Serverinstanz die Größe des **tempdb** -Transaktionsprotokolls erhöhen. Weitere Informationen finden Sie unter [tempdb Database](../databases/tempdb-database.md).  
  
  
##  <a name="ControlGrowth"></a> Steuern der Vergrößerung einer Transaktionsprotokolldatei  
 Sie können die [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)-Anweisung verwenden, um die Vergrößerung einer Transaktionsprotokolldatei zu verwalten. Beachten Sie Folgendes:  
  
-   Verwenden Sie die Option SIZE, um die aktuelle Dateigröße in KB-, MB-, GB- und TB-Einheiten zu ändern.  
  
-   Verwenden Sie die Option FILEGROWTH, um die Vergrößerungsschrittweite zu ändern. Der Wert 0 gibt an, dass die automatische Vergrößerung deaktiviert und kein zusätzlicher Speicherplatz zulässig ist. Die Einstellung der kleinen automatischen Vergrößerungsschrittweite einer Protokolldatei kann ebenfalls die Leistung beeinträchtigen. Die Schrittweite für die Dateivergrößerung sollte für eine Protokolldatei stets groß genug sein, um häufige Erweiterungen zu vermeiden. Die standardmäßige Vergrößerungsschrittweite von 10 Prozent ist hierfür im Allgemeinen gut geeignet.  
  
     Informationen zum Ändern der dateivergrößerung-Eigenschaft in einer Protokolldatei finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
-   Verwenden Sie die Option MAXSIZE, um die maximale Größe einer Protokolldatei in KB-, MB-, GB- und TB-Einheiten zu steuern oder die Vergrößerung auf UNLIMITED festzulegen.  
  
  
## <a name="see-also"></a>Siehe auch  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Problembehandlung bei vollen Transaktionsprotokollen &#40;SQL Server-Fehler 9002&#41;](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
  
