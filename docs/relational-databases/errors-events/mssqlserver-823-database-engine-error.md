---
title: MSSQLSERVER-Fehler 823 | mssqlserver_823
description: Eine Beschreibung und einige gängige Lösungen für dem Microsoft SQL Server-Fehler 823 (mssqlserver_823), bei dem es sich um einen schwerwiegenden Systemfehler handelt, der die Datenbankintegrität bedroht und sofort behoben werden muss.
ms.custom: ''
ms.date: 01/27/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57850e8b54ef0f99895e558616b22089af266895
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767856"
---
# <a name="mssqlserver-error-823"></a>MSSQLSERVER-Fehler 823
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|823|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|B_HARDERR|  
|Meldungstext|Das Betriebssystem hat während eines %S_MSG bei Offset %#016I64x in der Datei '%4!s!' den Fehler '%ls' an SQL Server zurückgegeben. Weitere Informationen finden Sie möglicherweise in zusätzlichen Meldungen im SQL Server-Fehlerprotokoll und im Systemereignisprotokoll. Dieser Fehler kann die Datenbankintegrität beeinträchtigen und muss behoben werden. Führen Sie eine vollständige Datenbankkonsistenzprüfung (DBCC CHECKDB) aus. Dieser Fehler kann viele Ursachen haben. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
SQL Server nutzt Windows-APIs (zum Beispiel [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile), [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile), [ReadFileScatter](/windows/win32/api/fileapi/nf-fileapi-readfilescatter), [WriteFileGather](/windows/win32/api/fileapi/nf-fileapi-writefilegather)), um Datei-E/A-Vorgänge durchzuführen. Nachdem diese E/A-Vorgänge durchgeführt wurden, prüft SQL Server nach Fehlerbedingungen im Zusammenhang mit diesen API-Aufrufen. Wenn die API-Aufrufe mit einem Betriebssystemfehler fehlschlagen, meldet SQL Server den Fehler 823.

 Die 823-Fehlermeldung enthält folgende Informationen:
 - Die Datenbankdatei, für die der E/A-Vorgang durchgeführt wurde.
 - Das Offset in der Datei, an dem versucht wurde, den E/A-Vorgang durchzuführen. Dies ist das physische Byte-Offset vom Beginn der Datei. Wenn Sie diese Zahl durch 8192 teilen, erhalten Sie die logische Seitenzahl, die vom Fehler betroffen ist.
 - Die Information, ob der E/A-Vorgang eine Lese- oder Schreibanforderung ist.
 - Der Fehlercode für den Betriebssystemfehler und die zugehörige Fehlerbeschreibung in Klammern.
 

**Betriebssystemfehler:** Ein Windows API-Aufruf für einen Lese- oder Schreibvorgang ist nicht erfolgreich und SQL Server ermittelt einen Betriebssystemfehler im Zusammenhang mit dem Windows API-Aufruf. In der folgenden Beispielmeldung wird ein 823-Fehler veranschaulicht:

```
Error: 823, Severity: 24, State: 2.
2010-03-06 22:41:19.55 spid58 The operating system returned error 1117 (The request could not be performed because of an I/O device error.) to SQL Server during a read at offset 0x0000002d460000 in file 'e:\program files\Microsoft SQL Server\mssql\data\mydb.MDF'. Additional messages in the SQL Server error log and system event log may provide more detail. This is a severe, system-level error condition that threatens database integrity and must be corrected immediately. It is recommended to complete a full database consistency check (DBCC CHECKDB). This error can be caused by many factors; for more information, see SQL Server Books Online.
```

Fehler der DBCC CHECKDB-Anweisung für die Datenbank, die der in der Fehlermeldung genannten Datei zugeordnet ist, werden möglicherweise nicht angezeigt. Sie können die DBCC CHECKDB-Anweisung ausführen, wenn ein 823-Fehler auftritt. Wenn die DBCC CHECKDB-Anweisung keine Fehler zurückgibt, liegt vermutlich ein vorübergehendes Systemproblem oder ein Datenträgerproblem vor.

Wenn Sie das Ablaufverfolgungsflag 818 verwenden, werden möglicherweise zusätzliche Diagnoseinformationen für 823-Fehler in die SQL Server-Fehlerprotokolldatei geschrieben.
Weitere Informationen finden Sie unter [KB 826433: Additional SQL Server diagnostics added to detect unreported I/O problems (KB 826433: Weitere SQL Server-Diagnose zum Ermitteln nicht gemeldeter E/A-Probleme wurde hinzugefügt)](https://support.microsoft.com/help/826433/sql-server-diagnostics-added-to-detect-unreported-i-o-problems-due-to).


## <a name="cause"></a>Ursache
Die 823-Fehlermeldung weist in der Regel darauf hin, dass ein Problem mit dem zugrunde liegenden Speichersystem, der Hardware oder einem Treiber vorliegt, der sich im Pfad der E/A-Anforderung befindet. Dieser Fehler kann auftreten, wenn Inkonsistenzen im Dateisystem vorliegen oder wenn die Datenbankdatei beschädigt ist. Bei Dateilesevorgängen wiederholt SQL Server die Leseanforderung viermal, bevor der 823-Fehler zurückgegeben wird. Wenn der Wiederholungsvorgang erfolgreich durchgeführt wird, schlägt die Abfrage nicht fehl, aber die Meldung [825](mssqlserver-825-database-engine-error.md) wird in ERRORLOG und das Ereignisprotokoll geschrieben.

## <a name="user-action"></a>Benutzeraktion  
 - Überprüfen Sie die Tabelle [suspect_pages](../system-tables/suspect-pages-transact-sql.md) in MSDB auf weitere Seiten, bei denen dieses Problem auftritt (in der gleichen Datenbank oder in anderen).
 - Überprüfen Sie mithilfe des Befehls DBCC CHECKDB die Konsistenz der Datenbanken, die sich auf demselben Volume (das in der 823-Fehlermeldung genannt wird) befinden. Wenn Sie mit dem Befehl DBCC CHECKDB Inkonsistenzen ermitteln, befolgen Sie die Anweisungen unter [How to troubleshoot database consistency errors reported by DBCC CHECKB (Problembehandlung für von DBCC CHECKDB gemeldete Datenbankkonsistenzfehler)](https://support.microsoft.com/help/2015748/how-to-troubleshoot-database-consistency-errors-reported-by-dbcc-check). 
 - Überprüfen Sie das Windows-Ereignisprotokoll auf Fehler und Meldungen vom Betriebssystem, einem Speichergerät oder einem Gerätetreiber. Wenn Sie Fehler ermitteln, die im Zusammenhang mit dem 823-Fehler stehen, sollten Sie diese zuerst beheben. Abgesehen von der 823-Fehlermeldung finden Sie im Ereignisprotokoll möglicherweise ein Ereignis wie „Der Treiber hat einen Controllerfehler auf „\Device\Harddisk4\DR4“ gefunden, das vom Quelldatenträger gemeldet wurde. In diesem Fall müssen Sie ermitteln, ob sich diese Datei auf dem Gerät befindet, und zuerst diese Datenträgerfehler beheben.
 - Verwenden Sie das Hilfsprogramm [SQLIOSim](https://support.microsoft.com/help/231619/how-to-use-the-sqliosim-utility-to-simulate-sql-server-activity-on-a-d), um herauszufinden, ob die 823-Fehler außerhalb der regulären E/A-Anforderungen von SQL Server reproduziert werden können. Das SQLIOSim-Hilfsprogramm ist in SQL Server 2008 und höheren Versionen enthalten. Es ist also kein separater Download erforderlich. Normalerweise befindet es sich im Ordner `C:\Program Files\Microsoft SQL Server\MSSQLxx.MSSQLSERVER\MSSQL\Binn`.
 - Wenden Sie sich an Ihren Hardware- oder Gerätehersteller, um Folgendes sicherzustellen:
   - Die Hardwaregeräte und Konfiguration entsprechen den E/A-Voraussetzungen von SQL Server.
   - Die Gerätetreiber und andere unterstützende Softwarekomponenten aller Geräte im E/A-Pfad sind auf dem neuesten Stand.
 - Wenn der Hardware- oder Gerätehersteller Ihnen Diagnoseprogramme bereitgestellt hat, verwenden Sie diese um die Integrität des E/A-Systems auszuwerten.
 - Ermitteln Sie, ob [Filtertreiber](https://support.microsoft.com/help/2454053/use-of-system-filter-drivers-can-lead-to-sql-server-database-engine-pe) im Pfad der E/A-Anforderungen enthalten sind, bei denen Probleme auftreten.
   - Überprüfen Sie, ob es Updates für diese Filtertreiber gibt.
   - Überprüfen Sie, ob diese Filtertreiber entfernt oder deaktiviert werden können, um zu testen, ob das Problem, das zum 823-Fehler führt, dadurch behoben wird.  
