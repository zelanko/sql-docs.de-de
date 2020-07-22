---
title: catalog.environment_variables (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de22e52f25658f467ed21952b1eb32356e4ff5af
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912668"
---
# <a name="catalogenvironment_variables-ssisdb-database"></a>catalog.environment_variables (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt die Umgebungsvariablendetails für alle Umgebungen im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog an.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|Der eindeutige Bezeichner (ID) der Umgebungsvariablen.|  
|environment_id|**bigint**|Die eindeutige ID der Umgebung, der die Variable zugeordnet ist.|  
|name|**sysname**|Der Name der Umgebungsvariablen.|  
|description|**nvarchar(1024)**|Die Beschreibung der Umgebungsvariablen.|  
|type|**nvarchar(128)**|Der Datentyp der Umgebungsvariablen.|  
|sensitive|**bit**|Wenn der Wert `1`lautet, ist die Variable vertraulich und wird beim Speichern verschlüsselt. Lautet der Wert `0`, ist die Variable nicht vertraulich, und der Wert wird als Nur-Text gespeichert.|  
|value|**sql_variant**|Der Wert der Umgebungsvariablen. Wenn `0` vertraulich ist, wird der Nur-Text-Wert angezeigt. Wenn `1` vertraulich ist, wird der Wert **NULL** angezeigt.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Sicht wird eine Zeile für jede Umgebungsvariable im Katalog angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die entsprechende Umgebung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
