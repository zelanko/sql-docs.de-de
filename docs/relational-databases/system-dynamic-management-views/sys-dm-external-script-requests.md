---
title: sys. dm_external_script_requests | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/26/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
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
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 64a21295da9b399cc212848c83d93657199c3536
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180197"
---
# <a name="sysdm_external_script_requests"></a>sys.dm_external_script_requests
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

Gibt eine Zeile für jedes aktive Workerkonto zurück, das ein externes Skript ausführt.
  
> [!NOTE]
> Diese dynamische Verwaltungs Sicht (Dynamic Management View, DMV) ist nur verfügbar, wenn Sie die Funktion installiert und aktiviert haben, die die Ausführung externer Skripts unterstützt. Weitere Informationen finden Sie unter [Machine Learning Services (r, python) in SQL Server 2017 und](../../machine-learning/sql-server-machine-learning-services.md)höher, [R Services in SQL Server 2016](../../machine-learning/r/sql-server-r-services.md)und [Machine Learning Services in Azure SQL verwaltete Instanz](/azure/azure-sql/managed-instance/machine-learning-services-overview).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**eindeutiger Bezeichner**|Die ID des Prozesses, der die externe Skriptanforderung gesendet hat. Dies entspricht der Prozess-ID, die von der SQL-Instanz empfangen wurde.|  
|language|**nvarchar**|Schlüsselwort, das einer unterstützten Skriptsprache entspricht. |  
|degree_of_parallelism|**int**|Zahl, die die Anzahl von parallelen Prozessen angibt, die erstellt wurden. Dieser Wert kann sich von der Anzahl von parallelen Prozessen unterscheiden, die angefordert wurden.|  
|external_user_name|**nvarchar**|Das Windows-Workerkonto, unter dem das Skript ausgeführt wurde.|  
  
## <a name="permissions"></a>Berechtigungen

 Erfordert die- `VIEW SERVER STATE` Berechtigung auf dem Server.  
  
> [!NOTE]
> Benutzer, die externe Skripts ausführen, müssen über die zusätzliche Berechtigung verfügen `EXECUTE ANY EXTERNAL SCRIPT` . Diese DMV kann jedoch von Administratoren ohne diese Berechtigung verwendet werden. 
  
## <a name="remarks"></a>Bemerkungen  

Diese Sicht kann über die Skriptsprachen-ID gefiltert werden.

Die Sicht gibt auch das Workerkonto zurück, unter dem das Skript ausgeführt wird. Informationen zu workerkonten, die von externen Skripts verwendet werden, finden Sie im Abschnitt "Identitäten in Verarbeitung (sqlrusergroup)" in der [Sicherheitsübersicht für das Erweiterbarkeit Framework in SQL Server Machine Learning Services](../../machine-learning/concepts/security.md#sqlrusergroup).

Die GUID, die im **external_script_request_id** -Feld zurückgegeben wird, entspricht auch dem Dateinamen des geschützten Verzeichnisses, in dem temporäre Dateien gespeichert werden. Jedes Workerkonto (z. b. MSSQLSERVER01) stellt einen einzelnen SQL-Anmelde Namen oder Windows-Benutzer dar und kann zum Ausführen mehrerer Skript Anforderungen verwendet werden. Standardmäßig werden diese temporären Dateien nach Abschluss des angeforderten Skripts gelöscht.

Diese dynamische Verwaltungssicht überwacht nur die aktiven Prozesse und kann nichts zu Skripts berichten, die bereits abgeschlossen wurden. Wenn Sie die Dauer von Skripts nachverfolgen müssen, empfiehlt es sich, Informationen zur zeitlichen Steuerung in Ihrem Skript hinzuzufügen und diese Informationen als Teil der Skriptausführung zu erfassen.

## <a name="examples"></a>Beispiele  
  
### <a name="viewing-the-currently-active-scripts-for-a-particular-process"></a>Anzeigen der derzeit aktiven Skripts für einen bestimmten Prozess

 Im folgenden Beispiel wird die Anzahl von externen Skriptausführungen angezeigt, die für die aktuelle Instanz ausgeführt werden.  
  
```sql
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

## <a name="see-also"></a>Siehe auch

+ [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Execution Related Dynamic Management Views and Functions &#40;Transact-SQL&#41; (Dynamische Verwaltungssichten und Funktionen im Zusammenhang mit der Ausführung (Transact-SQL))](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
+ [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
