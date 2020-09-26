---
description: '&#x40;&#x40;PACK_RECEIVED (Transact-SQL)'
title: '@@PACK_RECEIVED (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@PACK_RECEIVED_TSQL'
- '@@PACK_RECEIVED'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@PACK_RECEIVED function'
- number of packets read
- packets [SQL Server], number read
ms.assetid: 5c0b3d36-bfad-4f0b-abb8-e8f6391b32cd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7b3bb37af363727d1eb41922979ee6f78a9fd008
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "91380820"
---
# <a name="x40x40pack_received-transact-sql"></a>&#x40;&#x40;PACK_RECEIVED (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Anzahl der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seit dem letzten Start aus dem Netzwerk gelesenen Eingabepakete zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
@@PACK_RECEIVED  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 **integer**  
  
## <a name="remarks"></a>Hinweise  
 Führen Sie **sp_monitor** aus, um einen Bericht anzuzeigen, der mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Statistiken enthält, einschließlich versandter und erhaltener Pakete.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung von `@@PACK_RECEIVED`.  
  
```sql  
SELECT @@PACK_RECEIVED AS 'Packets Received';   
```  
  
 Hier ist ein Beispielresultset.  
  
```  
Packets Received  
----------------  
128  
```  
  
## <a name="see-also"></a>Siehe auch  
 [@@PACK_SENT](../../t-sql/functions/pack-sent-transact-sql.md)   
 [sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Statistische Systemfunktionen](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
