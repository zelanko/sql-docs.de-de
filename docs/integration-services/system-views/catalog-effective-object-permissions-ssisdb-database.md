---
title: catalog.effective_object_permissions (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- catalog.effective_object_permissions views [Integration Services]
- effective_object_permissions view [Integration Services]
ms.assetid: e70c4ce9-79f5-44df-ac75-6c29b6e38776
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7e3cca42b69d32b324c0ddb749a5fb4ef8550c13
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58272319"
---
# <a name="catalogeffectiveobjectpermissions-ssisdb-database"></a>catalog.effective_object_permissions (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt die gültigen Berechtigungen des aktuellen Prinzipals für alle Objekte im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog an.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|Der Typ des sicherungsfähigen Objekts. Typen sicherungsfähiger Objekte lauten Ordner (`1`), Projekt (`2`), Umgebung (`3`) und Vorgang (`4`).|  
|object_id|**bigint**|Der eindeutige Bezeichner (ID) oder der Primärschlüssel des Objekts.|  
|permission_type|**smallint**|Art der Berechtigung.|  
  
## <a name="remarks"></a>Remarks  
 In dieser Sicht werden die in der folgenden Tabelle aufgeführten Berechtigungstypen angezeigt:  
  
|permission_type-Wert|Berechtigungsname|Berechtigungsbeschreibung|Anwendbare Objekttypen|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|Ermöglicht es dem Prinzipal, Informationen zu lesen, die als Teil des Objekts angesehen werden, z. B. Eigenschaften. Ermöglicht es dem Prinzipal nicht, den Inhalt von anderen Objekten innerhalb des Objekts aufzuzählen oder zu lesen.|Ordner, Projekt, Umgebung, Vorgang|  
|`2`|MODIFY|Ermöglicht es dem Prinzipal, Informationen zu ändern, die als Teil des Objekts angesehen werden, z. B. Eigenschaften. Ermöglicht es dem Prinzipal nicht, andere Objekte innerhalb des Objekts zu ändern.|Ordner, Projekt, Umgebung, Vorgang|  
|`3`|Führen Sie|Ermöglicht es dem Prinzipal, alle Pakete im Projekt auszuführen.|Projekt|  
|`4`|MANAGE_PERMISSIONS|Ermöglicht es dem Prinzipal, den Objekten Berechtigungen zuzuweisen.|Ordner, Projekt, Umgebung, Vorgang|  
|`100`|CREATE_OBJECTS|Ermöglicht es dem Prinzipal, Objekte im Ordner zu erstellen.|Ordner|  
|`101`|READ_OBJECTS|Ermöglicht es dem Prinzipal, alle Objekte im Ordner zu lesen.|Ordner|  
|`102`|MODIFY_OBJECTS|Ermöglicht es dem Prinzipal, alle Objekte im Ordner zu ändern.|Ordner|  
|`103`|EXECUTE_OBJECTS|Ermöglicht es dem Prinzipal, alle Pakete aus allen Projekten im Ordner auszuführen.|Ordner|  
|`104`|MANAGE_OBJECT_PERMISSIONS|Ermöglicht es dem Prinzipal, Berechtigungen für alle Objekte im Ordner zu verwalten.|Ordner|  
  
 Es werden nur Objekte ausgewertet, für die der Aufrufer über Berechtigungen verfügt. Die Berechtigungen werden auf Grundlage der folgenden Kriterien berechnet:  
  
-   Explizite Berechtigungen  
  
-   Geerbte Berechtigungen  
  
-   Mitgliedschaft des Prinzipals in Rollen  
  
-   Mitgliedschaft des Prinzipals in Gruppen  
  
## <a name="permissions"></a>Berechtigungen  
 Benutzer können gültige Berechtigungen nur für sich und für Rollen anzeigen, denen sie als Mitglied angehören.  
  
  
