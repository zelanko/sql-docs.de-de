---
title: catalog.environments (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6b2aa0ce2b9fe4d61d9a2fc2f81b2a41e23ab488
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71295220"
---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt die Umgebungsdetails für alle Umgebungen im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog an. Umgebungen enthalten Variablen, auf die von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekten verwiesen werden kann.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|environment_id|**bigint**|Der eindeutige Bezeichner (ID) der Umgebung.|  
|name|**sysname**|Der Name der Umgebung.|  
|folder_id|**bigint**|Die eindeutige ID des Ordners, in der sich die Umgebung befindet.|  
|description|**nvarchar(1024)**|Die Beschreibung der Umgebung. Dieser Wert ist optional.|  
|created_by_sid|**varbinary(85)**|Die Sicherheits-ID (SID) des Benutzers, der die Umgebung erstellt hat|  
|created_by_name|**nvarchar(128)**|Der Name des Benutzers, der die Umgebung erstellt hat.|  
|created_time|**datetimeoffset**|Datum und Uhrzeit der Umgebungserstellung.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Sicht wird eine Zeile für jede Umgebung im Katalog angezeigt. Umgebungsnamen sind nur in Bezug auf den Ordner eindeutig, in dem sie sich befinden. Beispielsweise kann eine Umgebung mit dem Namen `E1` in mehreren Ordnern im Katalog vorhanden sein, jedoch kann jeder Ordner nur eine Umgebung mit dem Namen `E1`enthalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die Umgebung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
