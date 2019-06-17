---
title: Sp_syspolicy_purge_health_state (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 2e7e9622fdd45362da9782798c7af82ff9112745
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63000793"
---
# <a name="spsyspolicypurgehealthstate-transact-sql"></a>sp_syspolicy_purge_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Löscht die Richtlinienzustandsstatus in der richtlinienbasierten Verwaltung. Richtlinienzustandsstatus sind visuelle Indikatoren (ein Bildlaufsymbol mit einem roten "X") innerhalb des Objekt-Explorers, mit denen Sie bestimmen können, für welche Knoten die Richtlinienauswertung fehlerhaft ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_purge_health_state [ @target_tree_root_with_id = ] 'target_tree_root_with_id'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @target_tree_root_with_id = ] 'target_tree_root_with_id'` Stellt den Knoten im Objekt-Explorer, in denen den Integritätsstatus gelöscht werden soll. *Target_tree_root_with_id* ist **nvarchar(400)** , hat den Standardwert NULL.  
  
 Sie können in der Spalte target_query_expression_with_id der Systemsicht msdb.dbo.syspolicy_system_health_state Werte angeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_purge_health_state im Kontext der Systemdatenbank msdb ausführen.  
  
 Wenn Sie diese gespeicherte Prozedur ganz ohne Parameter ausführen, wird der Systemzustandsstatus für alle Knoten im Objekt-Explorer gelöscht.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer der Rolle PolicyAdministratorRole können Servertrigger erstellen und Ausführung von Richtlinien planen, die den Betrieb der Instanz von beeinflussen, können die [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmeldeinformationen, sollte die PolicyAdministratorRole-Rolle gewährt werden nur für Benutzer, die mit der Kontrolle der Konfiguration von vertrauenswürdigen sind die [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die verschiedenen Zustandsstatus für einen bestimmten Knoten im Objekt-Explorer gelöscht.  
  
```  
EXEC msdb.dbo.sp_syspolicy_purge_health_state @target_tree_root_with_id = 'Server/Database[@ID=7]';  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Richtlinie der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
