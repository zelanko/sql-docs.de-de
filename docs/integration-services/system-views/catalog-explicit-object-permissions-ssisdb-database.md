---
title: catalog.explicit_object_permissions (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 49b09e0f-06e8-451f-b979-a0d91000bfe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa3c4060f0d82ff590b6307bc35a3c11a86b3201
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71296596"
---
# <a name="catalogexplicit_object_permissions-ssisdb-database"></a>catalog.explicit_object_permissions (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt nur die Berechtigungen an, die dem Benutzer explizit zugewiesen wurden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|Der Typ des sicherungsfähigen Objekts. Typen sicherungsfähiger Objekte lauten Ordner (`1`), Projekt (`2`), Umgebung (`3`) und Vorgang (`4`).|  
|object_id|**bigint**|Der eindeutige Bezeichner (ID) oder der Primärschlüssel des sicherungsfähigen Objekts.|  
|principal_id|**int**|Die ID des Datenbankprinzipals.|  
|permission_type|**smallint**|Art der Berechtigung.|  
|is_deny|**bit**|Gibt an, ob die Berechtigung verweigert oder gewährt wurde. Wenn der Wert `1`ist, wurde die Berechtigung verweigert. Wenn der Wert `0`ist, wurde die Berechtigung nicht verweigert.|  
|grantor_id|**int**|Die ID des Prinzipals, der die Berechtigung gewährt hat.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Sicht werden die in der folgenden Tabelle aufgeführten Berechtigungstypen angezeigt:  
  
|permission_type-Wert|Berechtigungsname|Berechtigungsbeschreibung|Anwendbare Objekttypen|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|Ermöglicht es dem Prinzipal, Informationen zu lesen, die als Teil des Objekts angesehen werden, z. B. Eigenschaften. Ermöglicht es dem Prinzipal nicht, den Inhalt von anderen Objekten innerhalb des Objekts aufzuzählen oder zu lesen.|Ordner, Projekt, Umgebung, Vorgang|  
|`2`|MODIFY|Ermöglicht es dem Prinzipal, Informationen zu ändern, die als Teil des Objekts angesehen werden, z. B. Eigenschaften. Ermöglicht es dem Prinzipal nicht, andere Objekte innerhalb des Objekts zu ändern.|Ordner, Projekt, Umgebung, Vorgang|  
|`3`|Führen Sie|Ermöglicht es dem Prinzipal, alle Pakete im Projekt auszuführen.|Project|  
|`4`|MANAGE_PERMISSIONS|Ermöglicht es dem Prinzipal, den Objekten Berechtigungen zuzuweisen.|Ordner, Projekt, Umgebung, Vorgang|  
|`100`|CREATE_OBJECTS|Ermöglicht es dem Prinzipal, Objekte im Ordner zu erstellen.|Ordner|  
|`101`|READ_OBJECTS|Ermöglicht es dem Prinzipal, alle Objekte im Ordner zu lesen.|Ordner|  
|`102`|MODIFY_OBJECTS|Ermöglicht es dem Prinzipal, alle Objekte im Ordner zu ändern.|Ordner|  
|`103`|EXECUTE_OBJECTS|Ermöglicht es dem Prinzipal, alle Pakete aus allen Projekten im Ordner auszuführen.|Ordner|  
|`104`|MANAGE_OBJECT_PERMISSIONS|Ermöglicht es dem Prinzipal, Berechtigungen für alle Objekte im Ordner zu verwalten.|Ordner|  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht bietet keine vollständige Sicht der Berechtigungen für den aktuellen Prinzipal. Der Benutzer muss außerdem überprüfen, ob der Prinzipal ein Mitglied von Rollen und Gruppen ist, denen Berechtigungen zugewiesen sind.  
  
  
