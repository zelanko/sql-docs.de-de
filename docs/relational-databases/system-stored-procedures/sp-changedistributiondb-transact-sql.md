---
title: Sp_changedistributiondb (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedistributiondb_TSQL
- sp_changedistributiondb
helpviewer_keywords:
- sp_changedistributiondb
ms.assetid: 66f73185-ea9e-43f9-86ed-9dd933cee2f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2966a784f647d402b849d5899b76b0614122b932
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62997051"
---
# <a name="spchangedistributiondb-transact-sql"></a>sp_changedistributiondb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Eigenschaften der Verteilungsdatenbank. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changedistributiondb [ @database= ] 'database'   
    [ , [ @property= ] 'property' ]   
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @database = ] 'database'` Ist der Name der Verteilungsdatenbank. *Datenbank* ist **Sysname**, hat keinen Standardwert.  
  
`[ @property = ] 'property'` Ist die Eigenschaft für die angegebene Datenbank zu ändern. *Eigenschaft* ist **Sysname**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**history_retention**|Beibehaltungsdauer für die Verlaufstabelle.|  
|**max_distretention**|Maximale Beibehaltungsdauer für die Verteilung.|  
|**min_distretention**|Minimale Beibehaltungsdauer für die Verteilung.|  
|NULL (Standard)|Alle verfügbaren *Eigenschaft* Werte ausgegeben werden.|  
  
`[ @value = ] 'value'` Ist der neue Wert für die angegebene Eigenschaft. *Wert* ist **nvarchar(255)** , hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changedistributiondb** wird in allen Replikationstypen verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_changedistributiondb](../../relational-databases/replication/codesnippet/tsql/sp-changedistributiondb-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_changedistributiondb**.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
