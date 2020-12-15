---
description: sp_execute (Transact-SQL)
title: sp_execute (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_execute
- sp_cursor_execute_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute
ms.assetid: 2009acd3-0d92-435a-a8fb-057e50dc7146
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 72018e5e064a3d3f35fb8495f3b32d7a3e76d4fd
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472711"
---
# <a name="sp_execute-transact-sql"></a>sp_execute (Transact-SQL)
[!INCLUDE [sql-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdbmi-asa-pdw.md)]

  Führt eine vorbereitete [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung mithilfe eines angegebenen Handles und optionalen Parameter Werts aus. sp_execute wird aufgerufen, indem ID = 12 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server, Azure Synapse Analytics, Parallel Data Warehouse  
  
sp_execute handle OUTPUT  
    [,bound_param  ]  [,...n ]  ]  
```  
  
## <a name="arguments"></a>Argumente  
 *bewältigen*  
 Der von sp_prepare zurückgegebene *handle* -Wert. *handle* ist ein erforderlicher Parameter, der den **int** -Eingabe Wert aufruft.  
  
 *bound_param*  
 Gibt die Verwendung zusätzlicher Parameter an. *bound_param* ist ein erforderlicher Parameter, der Eingabewerte eines beliebigen Datentyps aufruft, um zusätzliche Parameter für die Prozedur anzugeben.  
  
> [!NOTE]  
>  *bound_param* müssen mit den Deklarationen identisch sein, die durch den Wert des sp_prepare *para* Metern vorgenommen werden, und die Form *@name = value* oder *value* aufweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_prepare &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)  
  
  
