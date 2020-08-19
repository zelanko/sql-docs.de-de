---
description: catalog.folders (SSISDB-Datenbank)
title: catalog.folders (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 21a37c16-60aa-4b3f-8bca-ac90ad1697ac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8ec7f8fad821c5c62d7b7ec58290050a52b0bf17
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422064"
---
# <a name="catalogfolders-ssisdb-database"></a>catalog.folders (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt die Ordner im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog an.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|id|**bigint**|Der eindeutige Bezeichner des Ordners.|  
|name|**sysname(nvarchar(128))**|Der Name des Ordners, der innerhalb des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalogs eindeutig ist.|  
|description|**nvarchar(1024)**|Die Beschreibung des Ordners.|  
|created_by_sid|**varbinary(85)**|Die Sicherheits-ID (SID) des Benutzers, der den Ordner erstellt hat|  
|created_by_name|**nvarchar(128)**|Der Name des Benutzers, der den Ordner erstellt hat.|  
|created_time|**datetimeoffset(7)**|Datum und Uhrzeit der Ordnererstellung.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Sicht wird eine Zeile für jeden Ordner im Katalog angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für den Ordner  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
