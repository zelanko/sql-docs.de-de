---
description: ROLLBACK WORK (Transact-SQL)
title: ROLLBACK WORK (Transact-SQL)
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ROLLBACK WORK
- ROLLBACK_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transaction rollbacks [SQL Server]
- erasing data modifications [SQL Server]
- ROLLBACK WORK statement
- roll back transactions [SQL Server]
- rolling back transactions, ROLLBACK WORK
- savepoints [SQL Server]
ms.assetid: 2071dbd3-53d5-4510-be8d-26e80f2553b4
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 38388c9d697bc3f7d2fddd8d6ff162ff7b306f08
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459302"
---
# <a name="rollback-work-transact-sql"></a>ROLLBACK WORK (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Führt für eine benutzerdefinierte Transaktion einen Rollback zum Anfang der Transaktion aus.  
  
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
ROLLBACK [ WORK ]  
[ ; ]  
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="remarks"></a>Bemerkungen  
 Diese Anweisung funktioniert genau wie ROLLBACK TRANSACTION, mit der Ausnahme, dass ROLLBACK TRANSACTION einen benutzerdefinierten Transaktionsnamen akzeptiert. Die ROLLBACK-Syntax ist ISO-kompatibel, unabhängig davon, ob das optionale WORK-Schlüsselwort angegeben wurde.  
  
 Wenn Transaktionen geschachtelt werden, führt ROLLBACK WORK immer einen Rollback bis zur äußersten BEGIN TRANSACTION-Anweisung durch und verringert die @@TRANCOUNT-Systemfunktion auf 0.  
  
## <a name="permissions"></a>Berechtigungen  
 Alle gültigen Benutzer erhalten standardmäßig ROLLBACK WORK-Berechtigungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [COMMIT WORK &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  
