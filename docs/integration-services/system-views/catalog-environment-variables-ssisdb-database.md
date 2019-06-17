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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7abae509ebd99757dcac51571353a38386f9e7d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65715230"
---
# <a name="catalogenvironmentvariables-ssisdb-database"></a>catalog.environment_variables (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt die Umgebungsvariablendetails für alle Umgebungen im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog an.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|Der eindeutige Bezeichner (ID) der Umgebungsvariablen.|  
|environment_id|**bigint**|Die eindeutige ID der Umgebung, der die Variable zugeordnet ist.|  
|NAME|**sysname**|Der Name der Umgebungsvariablen.|  
|description|**nvarchar(1024)**|Die Beschreibung der Umgebungsvariablen.|  
|Typ|**nvarchar(128)**|Der Datentyp der Umgebungsvariablen.|  
|sensitive|**bit**|Wenn der Wert `1`lautet, ist die Variable vertraulich und wird beim Speichern verschlüsselt. Lautet der Wert `0`, ist die Variable nicht vertraulich, und der Wert wird als Nur-Text gespeichert.|  
|Wert|**sql_variant**|Der Wert der Umgebungsvariablen. Wenn `0` vertraulich ist, wird der Nur-Text-Wert angezeigt. Wenn `1` vertraulich ist, wird der Wert **NULL** angezeigt.|  
  
## <a name="remarks"></a>Remarks  
 In dieser Sicht wird eine Zeile für jede Umgebungsvariable im Katalog angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die entsprechende Umgebung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
