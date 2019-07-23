---
title: catalog.packages (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- packages view [Integration Services]
- catalog.packages view [Integration Services]
ms.assetid: a634e94d-f492-4dfd-9611-a35f545106a1
author: janinezhang
ms.author: janinez
ms.openlocfilehash: a921aaeebc57ab72f75c980b0877a9fa0723fdca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997848"
---
# <a name="catalogpackages-ssisdb-database"></a>catalog.packages (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt die Details für alle Pakete an, die im **SSISDB** -Katalog angezeigt werden.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|package_id|**bigint**|Der eindeutige Bezeichner (ID) des Pakets.|  
|NAME|**nvarchar(256)**|Der eindeutige Name des Pakets.|  
|package_guid|**uniqueidentifier**|Der global eindeutige Bezeichner (Globally Unique Identifier, GUID) für das Paket.|  
|description|**nvarchar(1024)**|Eine optionale Beschreibung des Pakets.|  
|package_format_version|**int**|Die Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mit der das Paket entwickelt wurde.|  
|version_major|**int**|Die Hauptversion des Pakets.|  
|version_minor|**int**|Die Nebenversion des Pakets.|  
|version_build|**int**|Die Buildversion des Pakets.|  
|version_comments|**nvarchar(1024)**|Optionale Kommentare zur Paketversion.|  
|version_guid|**uniqueidentifier**|Die GUID, die die Paketversion eindeutig identifiziert.|  
|project_id|**bigint**|Die eindeutige ID des Projekts.|  
|entry_point|**bit**|Der Wert `1` gibt an, dass das Paket direkt gestartet werden soll. Der Wert `0` gibt an, dass das Paket von einem anderen Paket mit dem Task Paket ausführen gestartet werden soll. Der Standardwert lautet `1`.|  
|validation_status|**char(1)**|Der Status der Überprüfung.|  
|last_validation_time|**datetimeoffset(7)**|Der Zeitpunkt der letzten Überprüfung.|  
  
## <a name="remarks"></a>Remarks  
 In dieser Sicht wird eine Zeile für jedes Paket im Katalog angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für das entsprechende Projekt  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die READ-Berechtigung für ein Projekt verfügen, verfügen Sie auch über die READ-Berechtigung für alle Pakete und Umgebungsverweise, die diesem Projekt zugeordnet sind. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
