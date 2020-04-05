---
title: sys.dm_external_script_requests | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_requests
- sys.dm_external_script_requests_TSQL
- dm_external_script_requests
- dm_external_script_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_requests dynamic management view
ms.assetid: e7e7c50f-b8b2-403c-b8c8-1955da5636c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67e24b9c5c4ccd5f6ab2159ed5924474ff77bc84
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664281"
---
# <a name="sysdm_external_script_requests"></a>sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Gibt eine Zeile für jedes aktive Workerkonto zurück, das ein externes Skript ausführt.
  
> [!NOTE] 
>  
> Diese dynamische Verwaltungsansicht (DMV) ist nur verfügbar, wenn Sie die Funktion installiert und aktiviert haben, die die Ausführung externer Skripts unterstützt. Weitere Informationen finden Sie unter [R-Dienste in SQL Server 2016](../../machine-learning/r/sql-server-r-services.md) und [Machine Learning Services (R, Python) in SQL Server 2017 und höher](../../machine-learning/what-is-sql-server-machine-learning.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**unique identifier**|Die ID des Prozesses, der die externe Skriptanforderung gesendet hat. Dies entspricht der Prozess-ID, die von[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|language|**Nvarchar**|Schlüsselwort, das einer unterstützten Skriptsprache entspricht. |  
|degree_of_parallelism|**int**|Zahl, die die Anzahl von parallelen Prozessen angibt, die erstellt wurden. Dieser Wert kann sich von der Anzahl von parallelen Prozessen unterscheiden, die angefordert wurden.|  
|external_user_name|**Nvarchar**|Das Windows-Workerkonto, unter dem das Skript ausgeführt wurde.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
> [!NOTE]
>   
>  Benutzer, die externe Skripts ausführen, müssen die zusätzliche Berechtigung EXECUTE ANY EXTERNAL SCRIPT haben, aber diese dynamische Verwaltungssicht kann von Administratoren ohne diese Berechtigung verwendet werden. 
  
## <a name="remarks"></a>Hinweise  

Diese Sicht kann über die Skriptsprachen-ID gefiltert werden.

Die Sicht gibt auch das Workerkonto zurück, unter dem das Skript ausgeführt wird. Informationen zu Workerkonten, die von den externen Skripts verwendet werden, finden Sie im Abschnitt Identitäten, die bei der Verarbeitung verwendet werden (SQLRUserGroup) in [der Sicherheitsübersicht für das Erweiterbarkeitsframework in SQL Server Machine Learning Services](../../machine-learning/concepts/security.md#sqlrusergroup).

Die GUID, die im **external_script_request_id** -Feld zurückgegeben wird, entspricht auch dem Dateinamen des geschützten Verzeichnisses, in dem temporäre Dateien gespeichert werden. Jedes Workerkonto, z. B. MSSQLSERVER01, entspricht einer einzelnen SQL-Anmeldung oder einem einzelnen Windows-Benutzer und kann dazu verwendet werden, mehrere Skriptanforderungen auszuführen. Standardmäßig werden diese temporären Dateien nach Abschluss des angeforderten Skripts gelöscht.
 
Diese dynamische Verwaltungssicht überwacht nur die aktiven Prozesse und kann nichts zu Skripts berichten, die bereits abgeschlossen wurden. Wenn Sie die Dauer von Skripts nachverfolgen müssen, empfiehlt es sich, Informationen zur zeitlichen Steuerung in Ihrem Skript hinzuzufügen und diese Informationen als Teil der Skriptausführung zu erfassen.

## <a name="examples"></a>Beispiele  
  
### <a name="viewing-the-currently-active-r-scripts-for-a-particular-process"></a>Anzeigen der derzeit aktiven R-Skripts für einen bestimmten Prozess 
 Im folgenden Beispiel wird die Anzahl von externen Skriptausführungen angezeigt, die für die aktuelle Instanz ausgeführt werden.  
  
```  
SELECT external_script_request_id 
  , [language]
  , degree_of_parallelism
  , external_user_name
FROM sys.dm_external_script_requests; 
```  

Ergebnisse  


external_script_request_id  |language  |degree_of_parallelism  |external_user_name  
---------|---------|---------|---------
183EE6FC-7399-4318-AA2E-7A6C68E435A8     |     R    |      1   |  MSSQLSERVER01       


  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungsansichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Execution Related Dynamic Management Views and Functions &#40;Transact-SQL&#41; (Dynamische Verwaltungssichten und Funktionen im Zusammenhang mit der Ausführung (Transact-SQL))](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

