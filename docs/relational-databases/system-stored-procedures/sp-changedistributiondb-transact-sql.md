---
description: sp_changedistributiondb (Transact-SQL)
title: sp_changedistributiondb (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fb52176989ef6e90eb132da21abcd299444aec8d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464444"
---
# <a name="sp_changedistributiondb-transact-sql"></a>sp_changedistributiondb (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Ändert die Eigenschaften der Verteilungsdatenbank. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changedistributiondb [ @database= ] 'database'   
    [ , [ @property= ] 'property' ]   
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @database = ] 'database'` Der Name der Verteilungs Datenbank. *Database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @property = ] 'property'` Die Eigenschaft, die für die angegebene Datenbank geändert werden soll. *Property* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**history_retention**|Beibehaltungsdauer für die Verlaufstabelle.|  
|**max_distretention**|Maximale Beibehaltungsdauer für die Verteilung.|  
|**min_distretention**|Minimale Beibehaltungsdauer für die Verteilung.|  
|NULL (Standard)|Alle verfügbaren *Eigenschafts* Werte werden gedruckt.|  
  
`[ @value = ] 'value'` Der neue Wert für die angegebene Eigenschaft. der Wert ist vom Datentyp **nvarchar (255)** und hat den Standard *Wert* NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_changedistributiondb** wird bei allen Replikations Typen verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_changedistributiondb](../../relational-databases/replication/codesnippet/tsql/sp-changedistributiondb-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_changedistributiondb**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributiondb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
