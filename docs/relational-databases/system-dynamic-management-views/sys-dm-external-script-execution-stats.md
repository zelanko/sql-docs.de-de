---
description: sys.dm_external_script_execution_stats
title: sys. dm_external_script_execution_stats | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/25/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_execution_stats
- sys.dm_external_script_execution_stats_TSQL
- dm_external_script_execution_stats
- dm_external_script_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_execution_stats dynamic management view
ms.assetid: 2e99f026-ceb2-42a2-a549-c71d31ed0cf4
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 9c8244de0efc2bdd3dc506e5e1ebcddcd4843dea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489920"
---
# <a name="sysdm_external_script_execution_stats"></a>sys.dm_external_script_execution_stats
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

Gibt eine Zeile für jeden Typ von externer Skriptanforderung zurück. Die externen Skriptanforderungen werden nach der unterstützten externen Skriptsprache gruppiert. Für jede externe Skriptfunktion wird eine Zeile generiert. Beliebige externe Skriptfunktionen werden nicht aufgezeichnet, sofern sie nicht von einem übergeordneten Prozess wie `rxExec`gesendet werden.
  
> [!NOTE]  
> Diese dynamische Verwaltungs Sicht (Dynamic Management View, DMV) ist nur verfügbar, wenn Sie die Funktion installiert und aktiviert haben, die die Ausführung externer Skripts unterstützt. Weitere Informationen finden Sie unter [r Services in SQL Server 2016](../../machine-learning/r/sql-server-r-services.md) [Machine Learning Services (r, python) in SQL Server 2017 und](../../machine-learning/sql-server-machine-learning-services.md) höher und [Azure verwaltete Instanz Machine Learning Services](/azure/azure-sql/managed-instance/machine-learning-services-overview).
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|language|**nvarchar**|Name der registrierten externen Skriptsprache. Jedes externe Skript muss die Sprache in der Skriptanforderung angeben, um das zugehörige Startprogramm zu starten. |  
|counter_name|**nvarchar**|Name einer registrierten externen Skriptfunktion. Lässt keine NULL-Werte zu.|  
|counter_value|**integer**|Gesamtanzahl der Instanzen, die von der registrierten externen Skriptfunktion auf dem Server aufgerufen wurden. Dieser Wert ist kumulativ und beginnt mit dem Zeitpunkt, zu dem das Feature auf der Instanz installiert wurde. Der Wert kann nicht zurückgesetzt werden.|  

## <a name="permissions"></a>Berechtigungen

 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
> [!NOTE]  
> Benutzer, die externe Skripts ausführen, müssen die zusätzliche Berechtigung EXECUTE ANY EXTERNAL SCRIPT haben, aber diese dynamische Verwaltungssicht kann von Administratoren ohne diese Berechtigung verwendet werden.
  
## <a name="remarks"></a>Bemerkungen

  Diese dynamische Verwaltungssicht wird für die interne Telemetrie bereitgestellt, um die Gesamtauslastung des neuen Features zur externen Skriptausführung in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]zu überwachen. Der Telemetriedienst wird mit Launchpad gestartet und inkrementiert jedes Mal einen datenträgerbasierten Zähler, wenn eine registrierte externe Skriptfunktion aufgerufen wird.

Leistungsindikatoren sind im Allgemeinen nur so lange gültig, wie der Prozess aktiv ist, der sie generiert hat. Daher kann eine Abfrage für eine DMV keine ausführlichen Daten für Dienste anzeigen, die beendet wurden. Wenn ein Start Programm z. b. ein externes Skript ausführt und es dennoch sehr schnell abschließt, zeigt eine konventionelle DMV möglicherweise keine Daten an.

Daher bleiben die von der DMV verfolgten Leistungsindikatoren aktiv und der Status für „sys.dm_external_script_requests“ wird beibehalten, indem Schreibvorgänge auf den Datenträger verwendet werden, auch wenn die Instanz heruntergefahren wird.

### <a name="counter-values"></a>Werte für Zählers

In SQL Server 2016 ist R die einzige unterstützte externe Sprache und die externen Skript Anforderungen werden von behandelt [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] . In SQL Server 2017 und höher sowie in Azure SQL verwaltete Instanz werden sowohl R als auch Python als externe Sprachen unterstützt, und die externen Skript Anforderungen werden von behandelt [!INCLUDE[rsql_productname_md](../../includes/rsql-productnamenew-md.md)] .

Für r verfolgt diese DMV die Anzahl von r-aufrufen, die auf einer-Instanz durchgeführt werden. Wenn `rxLinMod` z. B. parallel aufgerufen und ausgeführt wird, wird der Leistungsindikator um 1 erhöht.

Für die Sprache R stellen die im Feld *counter_name* angezeigten Leistungsindikatorwerte die Namen von registrierten ScaleR-Funktionen dar. Die Werte im Feld *counter_value* stellen die kumulierte Anzahl von Instanzen für die bestimmte ScaleR-Funktion dar. 

Für python verfolgt diese DMV die Anzahl von python-aufrufen, die auf einer Instanz von vorgenommen werden.

Die Zählung beginnt, wenn das Feature für die Instanz installiert und aktiviert wird und bleibt kumulativ, bis die Datei, die den Status verwaltet, von einem Administrator gelöscht oder überschrieben wird. Daher ist es im Allgemeinen nicht möglich, die Werte in *counter_value*zurückzusetzen. Zum Überwachen der Nutzung nach Sitzung, Kalenderzeiten oder anderen Intervallen wird empfohlen, dass Sie die Leistungsindikatoren in einer Tabelle erfassen.

### <a name="registration-of-external-script-functions-in-r"></a>Registrierung externer Skriptfunktionen in R

R unterstützt beliebige Skripts, und die r-Community stellt viele tausend Pakete bereit, die jeweils über eigene Funktionen und Methoden verfügen. Diese DMV überwacht jedoch nur die Scaler-Funktionen, die mit SQL Server 2016 R-Diensten installiert werden.

Die Registrierung dieser Funktionen wird beim Installieren des Features durchgeführt, und registrierte Funktionen können nicht hinzugefügt oder gelöscht werden.

## <a name="examples"></a>Beispiele  
  
### <a name="viewing-the-number-of-r-scripts-run-on-the-server"></a>Anzeigen der Anzahl der auf dem Server ausgeführten R-Skripts

 Im folgenden Beispiel wird die kumulative Anzahl von externen Skriptausführungen für die R-Sprache angezeigt.  
  
```sql
SELECT counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE language = 'R';
```  

### <a name="viewing-the-number-of-python-scripts-run-on-the-server"></a>Anzeigen der Anzahl von python-Skripts, die auf dem Server ausgeführt werden

Im folgenden Beispiel wird die kumulierte Anzahl externer Skript Ausführungen für die Python-Sprache angezeigt.  
  
```sql
SELECT counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE language = 'Python';
```  

## <a name="see-also"></a>Weitere Informationen

+ [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Execution Related Dynamic Management Views and Functions &#40;Transact-SQL&#41; (Dynamische Verwaltungssichten und Funktionen im Zusammenhang mit der Ausführung (Transact-SQL))](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)
+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
