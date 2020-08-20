---
description: MSSQLSERVER_824
title: MSSQLSERVER_824 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 824 (Database Engine error)
ms.assetid: 2aa22246-2712-4fdb-9744-36e7e6f3175e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e2242b539f5fadb18beb54115e2cbad95336497
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499520"
---
# <a name="mssqlserver_824"></a>MSSQLSERVER_824
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|824|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|B_HARDSSERR|  
|Meldungstext|SQL Server hat einen logischen, konsistenzbasierten E/A-Fehler gefunden: %ls Der Fehler ist beim %S_MSG von Seite %S_PGID in der Datenbank mit der ID %d bei Offset %#016I64x in der Datei '%ls' aufgetreten.  Weitere Informationen finden Sie möglicherweise in anderen Fehlermeldungen im SQL Server-Fehlerprotokoll oder im Systemereignisprotokoll.|  
  
## <a name="symptom"></a>Symptom  


Möglicherweise tritt die folgende Fehlermeldung im SQL Server-Fehlerprotokoll oder dem Windows-Anwendungsereignisprotokoll auf, wenn eine logische Konsistenzprüfung fehlschlägt, nachdem eine Datenbankseite gelesen oder geschrieben wurde:
 
``` 
2009-11-02 15:46:42.90 spid51      Error: 824, Severity: 24, State: 2.
2009-11-02 15:46:42.90 spid51      SQL Server detected a logical consistency-based I/O error: incorrect pageid (expected 1:43686; actual 0:0). It occurred during a read of page (1:43686) in database ID 23 at offset 0x0000001554c000 in file 'H:\MSSQL.SQL2008\MSSQL\DATA\my_db.mdf'.  Additional messages in the SQL Server error log or system event log may provide more detail. This is a severe error condition that threatens database integrity and must be corrected immediately. Complete a full database consistency check (DBCC CHECKDB). This error can be caused by many factors; for more information, see SQL Server Books Online.
```
 
Wenn diese Meldung beim Abfragen oder Ändern von Daten in einer Anwendung auftritt, wird die Fehlermeldung an die Anwendung zurückgegeben und die Datenbankverbindung wird beendet. 
  
## <a name="cause"></a>Ursache
Mit diesem Fehler wird angegeben, dass in Windows eine Meldung ausgegeben wurde, gemäß der die Seite erfolgreich vom Datenträger gelesen, aber in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Fehler auf der Seite festgestellt wurde. Dieser Fehler ähnelt Fehler 823, mit der Ausnahme, dass der Fehler von Windows nicht erkannt wurde. Dies deutet meist auf ein Problem im E/A-Subsystem hin, z. B. ein fehlerhaftes Laufwerk, Firmwareprobleme des Datenträgers, einen fehlerhaften Gerätetreiber usw. Weitere Informationen zu E/A-Fehlern finden Sie unter [Microsoft SQL Server I/O Basics, Chapter 2 (E/A-Grundlagen von Microsoft SQL Server, Kapitel 2)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).  

SQL Server nutzt Windows-APIs, z. B. ReadFile, WriteFile, ReadFileScatter und WriteFileGather, um die E/A-Vorgänge durchzuführen. Nachdem diese E/A-Vorgänge durchgeführt wurden, prüft SQL Server nach Fehlerbedingungen im Zusammenhang mit diesen API-Aufrufen. Wenn diese API-Aufrufe mit einem Betriebssystemfehler fehlschlagen, meldet SQL Server den Fehler 823. Es kann Situationen geben, in denen ein Windows-API-Aufruf tatsächlich erfolgreich durchgeführt wird, aber die vom E/A-Vorgang übertragenen Daten möglicherweise ein logisches Konsistenzproblem aufweisen. Solche logischen Konsistenzprobleme werden von Fehler 824 gemeldet.
 
Der Fehler 824 enthält die folgenden Informationen:

- Die Datenbankdatei, für die der E/A-Vorgang durchgeführt wurde
- Das Offset mit der Datei, in der der E/A-Vorgang versucht wurde
- Die Datenbank, zu der die Datei gehört
- Die Seitenzahl, die am E/A-Vorgang beteiligt war
- Ob es sich bei dem Vorgang um einen Lese- oder Schreibvorgang handelte
- Details zur fehlgeschlagenen logischen Konsistenzprüfung [Die Art der Prüfung, der tatsächliche Wert und der erwartete Wert für diese Überprüfung]
 
Bei diesen logischen Konsistenzprüfungen handelt es um zusätzliche Integritätsprüfungen, die von SQL Server durchgeführt werden, um sicherzustellen, dass gewisse Schlüsselaspekte der Daten, die an der Datenübertragung beteiligt waren, während des E/A-Vorgangs beibehalten wurden. Zu den Überprüfungen gehören: Prüfsumme, zerrissene Seiten, Kurztransfer, fehlerhafte Seiten-ID, veraltete Lesevorgänge und Seitenüberwachungsfehler. Die Art der durchgeführten Prüfungen variiert abhängig von den verschiedenen Konfigurationsoptionen auf Datenbank- und Serverebene. 
 
Die Fehlermeldung 824 deutet in der Regel auf ein Problem mit dem zugrunde liegenden Speichersystem, der Hardware oder einem Treiber hin, der sich im Pfad der E/A-Anforderung befindet. Dieser Fehler kann auftreten, wenn Inkonsistenzen im Dateisystem vorliegen oder wenn die Datenbankdatei beschädigt ist.

## <a name="resolution"></a>Lösung  

Wenn bei Ihnen der Fehler 824 auftritt, können Sie die folgenden Lösungen ausprobieren: 

- Überprüfen Sie die Tabelle [suspect_pages](../backup-restore/manage-the-suspect-pages-table-sql-server.md) in MSDB, um zu überprüfen, ob andere Seiten [in derselben Datenbank oder verschiedenen Datenbanken] dieses Problem aufweisen.
- Überprüfen Sie mithilfe des Befehls DBCC CHECKDB die Konsistenz der Datenbanken, die sich auf dem gleichen Volume befinden, [das in der 824-Fehlermeldung genannt wird]. Wenn Sie mit dem Befehl DBCC CHECKDB Inkonsistenzen ermitteln, befolgen Sie die Anweisungen im Knowledge Base-Artikel [How to troubleshoot database consistency errors reported by DBCC CHECKB (Problembehandlung für von DBCC CHECKDB gemeldete Datenbankkonsistenzfehler)](https://support.microsoft.com/help/2015748/how-to-troubleshoot-database-consistency-errors-reported-by-dbcc-check).
- Wenn die Datenbankoption PAGE_VERIFY CHECKSUM nicht für die Datenbank aktiviert ist, bei der die 824-Fehler auftreten, sollten Sie sie umgehend aktivieren. Für 824-Fehler können andere Gründe als für Prüfsummenfehler vorliegen, jedoch bietet CHECKSUM die beste Option zum Überprüfen der Konsistenz der Seite, nachdem sie auf den Datenträger geschrieben wurde.
- Überprüfen Sie das Windows-Ereignisprotokoll auf Fehler und Meldungen vom Betriebssystem, einem Speichergerät oder einem Gerätetreiber. Wenn Sie Fehler ermitteln, die im Zusammenhang mit diesem Fehler stehen, sollten Sie diese zuerst beheben. Wenn Sie neben der 824-Fehlermeldung beispielsweise ein Ereignis wie „Der Treiber hat einen Controllerfehler auf „\Device\Harddisk4\DR4“ gefunden“ finden, das im Ereignisprotokoll von der Datenträgerquelle gemeldet wurde. In diesem Fall müssen Sie ermitteln, ob sich diese Datei auf dem Gerät befindet, und zuerst diese Datenträgerfehler beheben.
- Verwenden Sie das Hilfsprogramm [SQLIOSim](https://support.microsoft.com/help/231619/how-to-use-the-sqliosim-utility-to-simulate-sql-server-activity-on-a-d), um herauszufinden, ob die 824-Fehler außerhalb der regulären E/A-Anforderungen von SQL Server reproduziert werden können. SQLIOSim ist in SQL Server 2008 enthalten, ab dieser Version ist also kein separater Download erforderlich.
- Wenden Sie sich an Ihren Hardware- oder Gerätehersteller, um Folgendes sicherzustellen:
   - Die Hardwaregeräte und ihre Konfiguration entsprechen den [E/A-Voraussetzungen von SQL Server](https://support.microsoft.com/help/967576/microsoft-sql-server-database-engine-input-output-requirements).
   - Die Gerätetreiber und andere unterstützende Softwarekomponenten aller Geräte im E/A-Pfad sind auf dem neuesten Stand.
- Wenn der Hardware- oder Gerätehersteller Ihnen Diagnoseprogramme bereitgestellt hat, verwenden Sie diese, um die Integrität des E/A-Systems auszuwerten.
- Ermitteln Sie, ob Filtertreiber im Pfad der E/A-Anforderungen enthalten sind, bei denen Probleme auftreten.
   - Überprüfen Sie, ob es Updates für diese Filtertreiber gibt.
   - Überprüfen Sie, ob diese Filtertreiber entfernt oder deaktiviert werden können, um zu testen, ob das Problem, das zum 824-Fehler führt, dadurch behoben wird.
- Wenn das Problem nicht hardwarebedingt ist und eine bekanntermaßen fehlerfreie Sicherung zur Verfügung steht, stellen Sie die Datenbank mithilfe der Sicherung wieder her.  

## <a name="see-also"></a>Weitere Informationen  
[Verwalten der suspect_pages-Tabelle &#40;SQL Server&#41;](~/relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
