---
description: catalog.executable_statistics
title: catalog.executable_statistics | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 3dda28d6-10d8-4294-9b5e-a6048c07faf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2690d60c080f3a565e45ee1bcc4cac10d07cf42
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88495253"
---
# <a name="catalogexecutable_statistics"></a>catalog.executable_statistics 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt eine Zeile für jede ausführbare Datei an, die ausgeführt wird, einschließlich der einzelnen Iterationen einer ausführbaren Datei.  
  
 Eine ausführbare Datei ist ein Task oder ein Container, den Sie der Ablaufsteuerung eines Pakets hinzufügen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|Statistics_id|BIGINT|Eindeutige ID der Daten.|  
|Execution_id|BIGINT|Eindeutige ID für die Instanz der Ausführung.<br /><br /> Die catalog.executions-Sicht enthält weitere Informationen zu Ausführungen. Weitere Informationen finden Sie unter [catalog.executions (SSISDB Database)](../../integration-services/system-views/catalog-executions-ssisdb-database.md) (catalog.executions [SSISDB-Datenbank]).|  
|Executable_id|BIGINT|Eindeutige ID für die Paketkomponente.<br /><br /> Die catalog.executables-Sicht enthält weitere Informationen zu ausführbaren Dateien. Weitere Informationen finden Sie unter [catalog.executables](../../integration-services/system-views/catalog-executables.md).|  
|Execution_path|nvarchar(max)|Der vollständige Ausführungspfad der Paketkomponente, einschließlich der einzelnen Iterationen der Komponente.|  
|Start_time|datetimeoffset(7)|Der Zeitpunkt, zu dem die ausführbare Datei in die Phase vor der Ausführung eintritt.|  
|End_time|datetimeoffset(7)|Der Zeitpunkt, zu dem die ausführbare Datei in die Phase nach der Ausführung eintritt.|  
|Execution_duration|INT|Der Zeitraum, über den sich die ausführbare Datei in der Ausführung befunden hat. Der Wert ist in Millisekunden angegeben.|  
|Execution_result|SMALLINT|Folgende Werte sind möglich:<br /><br /> 0 (Erfolg)<br /><br /> 1 (Fehler)<br /><br /> 2 (Abschluss)<br /><br /> 3 (Abgebrochen)|  
|Execution_value|sql_variant|Der von der Ausführung zurückgegebene Wert. Dies ist ein benutzerdefinierter Wert.|  
  
## <a name="permissions"></a>Berechtigungen  
 Die Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die Instanz der Ausführung.  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin** .  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
  
