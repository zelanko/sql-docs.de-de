---
title: catalog.executables | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: bae22d0c-e190-426f-a074-c1d1170e8dd8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 495a60de43826e633ee6c8eb2bcc7d38cf07706b
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912616"
---
# <a name="catalogexecutables"></a>catalog.executables 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In dieser Sicht wird eine Zeile für jede ausführbare Datei in der angegebenen Ausführung angezeigt.  
  
 Eine ausführbare Datei ist ein Task oder ein Container, den Sie der Ablaufsteuerung eines Pakets hinzufügen.  
  
|Spaltenname|**Datentyp**|BESCHREIBUNG|  
|-----------------|-------------------|-----------------|  
|executable_id|**bigint**|Der eindeutige Bezeichner für die ausführbare Datei.|  
|execution_id|**bigint**|Der eindeutige Bezeichner für die Instanz der Ausführung.|  
|executable_name|**nvarchar(4000)**|Der Name der ausführbaren Datei.|  
|executable_guid|**nvarchar(38)**|Die GUID der ausführbaren Datei.|  
|package_name|**nvarchar(260)**|Der Name des Pakets.|  
|package_path|**nvarchar(max)**|Der Pfad des Pakets.|  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die Instanz der Ausführung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
## <a name="remarks"></a>Bemerkungen  
  
