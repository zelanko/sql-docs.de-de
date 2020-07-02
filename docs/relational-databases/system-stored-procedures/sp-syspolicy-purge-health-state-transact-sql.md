---
title: sp_syspolicy_purge_health_state (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_purge_health_state_TSQL
- sp_syspolicy_purge_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_purge_health_state
ms.assetid: 4ba4aa91-4c19-41c7-b70d-5fd9d0e89a5e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6c07d71e2ab4c9fe39882476eef25674718a17c7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85639568"
---
# <a name="sp_syspolicy_purge_health_state-transact-sql"></a>sp_syspolicy_purge_health_state (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht die Richtlinienzustandsstatus in der richtlinienbasierten Verwaltung. Richtlinienzustandsstatus sind visuelle Indikatoren (ein Bildlaufsymbol mit einem roten "X") innerhalb des Objekt-Explorers, mit denen Sie bestimmen können, für welche Knoten die Richtlinienauswertung fehlerhaft ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_purge_health_state [ @target_tree_root_with_id = ] 'target_tree_root_with_id'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @target_tree_root_with_id = ] 'target_tree_root_with_id'`Stellt den Knoten in Objekt-Explorer dar, auf dem Sie den Integritäts Status löschen möchten. *target_tree_root_with_id* ist vom Datentyp **nvarchar (400)** und hat den Standardwert NULL.  
  
 Sie können in der Spalte target_query_expression_with_id der Systemsicht msdb.dbo.syspolicy_system_health_state Werte angeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_purge_health_state im Kontext der Systemdatenbank msdb ausführen.  
  
 Wenn Sie diese gespeicherte Prozedur ganz ohne Parameter ausführen, wird der Systemzustandsstatus für alle Knoten im Objekt-Explorer gelöscht.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer mit der Rolle PolicyAdministratorRole können Servertrigger erstellen und die Ausführung von Richtlinien planen. Dies kann sich auf die Arbeitsweise der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz auswirken. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmelde Informationen sollte die PolicyAdministratorRole-Rolle nur Benutzern gewährt werden, die mit dem Steuern der Konfiguration von vertraut sind [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die verschiedenen Zustandsstatus für einen bestimmten Knoten im Objekt-Explorer gelöscht.  
  
```  
EXEC msdb.dbo.sp_syspolicy_purge_health_state @target_tree_root_with_id = 'Server/Database[@ID=7]';  
  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren der Richtlinien basierten Verwaltung &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
