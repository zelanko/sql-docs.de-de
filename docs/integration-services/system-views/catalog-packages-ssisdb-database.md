---
description: catalog.packages (SSISDB-Datenbank)
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25e397e3c3b85f401857b58bd51df456b08fdb37
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422004"
---
# <a name="catalogpackages-ssisdb-database"></a>catalog.packages (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt die Details für alle Pakete an, die im **SSISDB** -Katalog angezeigt werden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|package_id|**bigint**|Der eindeutige Bezeichner (ID) des Pakets.|  
|name|**nvarchar(256)**|Der eindeutige Name des Pakets.|  
|package_guid|**uniqueidentifier**|Der global eindeutige Bezeichner (Globally Unique Identifier, GUID) für das Paket.|  
|description|**nvarchar(1024)**|Eine optionale Beschreibung des Pakets.|  
|package_format_version|**int**|Die Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mit der das Paket entwickelt wurde.|  
|version_major|**int**|Die Hauptversion des Pakets.|  
|version_minor|**int**|Die Nebenversion des Pakets.|  
|version_build|**int**|Die Buildversion des Pakets.|  
|version_comments|**nvarchar(1024)**|Optionale Kommentare zur Paketversion.|  
|version_guid|**uniqueidentifier**|Die GUID, die die Paketversion eindeutig identifiziert.|  
|project_id|**bigint**|Die eindeutige ID des Projekts.|  
|entry_point|**bit**|Der Wert `1` gibt an, dass das Paket direkt gestartet werden soll. Der Wert `0` gibt an, dass das Paket von einem anderen Paket mit dem Task Paket ausführen gestartet werden soll. Der Standardwert ist `1`.|  
|validation_status|**char(1)**|Der Status der Überprüfung.|  
|last_validation_time|**datetimeoffset(7)**|Der Zeitpunkt der letzten Überprüfung.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Sicht wird eine Zeile für jedes Paket im Katalog angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für das entsprechende Projekt  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die READ-Berechtigung für ein Projekt verfügen, verfügen Sie auch über die READ-Berechtigung für alle Pakete und Umgebungsverweise, die diesem Projekt zugeordnet sind. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
