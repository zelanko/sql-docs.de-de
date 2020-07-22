---
title: catalog.execution_data_taps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 54226c01-5b8f-4730-8a5f-1da2613f9689
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a94d4ab27e8e92e4ec35b899485bb33962c0fde
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912582"
---
# <a name="catalogexecution_data_taps"></a>catalog.execution_data_taps 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt Informationen für jede in einer Ausführung definierte Datenabzweigung an.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|data_tap_id|**bigint**|Eindeutiger Bezeichner (ID) der Datenabzweigung.|  
|execution_id|**bigint**|Der eindeutige Bezeichner (ID) für die Instanz der Ausführung.|  
|package_path|**nvarchar(max)**|Der Paketpfad für den Datenflusstask, in dem Daten abgerufen werden.|  
|dataflow_path_id_string|**nvarchar(4000)**|Die Identifikationszeichenfolge des Datenflusspfads.|  
|dataflow_task_guid|**uniqueidentifier**|Eindeutiger Bezeichner (ID) des Datenflusstasks.|  
|max_rows|**int**|Die Anzahl an zu erfassenden Zeilen. Wenn dieser Wert nicht angegeben ist, werden alle Zeilen erfasst.|  
|filename|**nvarchar(4000)**|Der Name der Datendumpdatei. Weitere Informationen finden Sie unter [Generieren von Dumpdateien für die Paketausführung](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).|  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die Instanz der Ausführung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Generieren von Dumpdateien für die Paketausführung](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
