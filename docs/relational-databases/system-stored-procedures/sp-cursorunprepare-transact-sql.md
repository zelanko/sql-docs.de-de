---
description: sp_cursorunprepare (Transact-SQL)
title: sp_cursorunprepare (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursorunprepare_TSQL
- sp_cursorunprepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorunprepare
ms.assetid: b46d4813-c4a9-4f9d-9979-2b5082ecf06a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0662e6f600e9627c3d3498144425f34917d6cfb0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486134"
---
# <a name="sp_cursorunprepare-transact-sql"></a>sp_cursorunprepare (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Verwirft den Ausführungsplan, der in der gespeicherten Prozedur sp_cursorprepare entwickelt wurde. sp_cursorunprepare wird aufgerufen, indem ID = 6 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursorunprepare handle  
```  
  
## <a name="arguments"></a>Argumente  
 *bewältigen*  
 Der *handle* -Wert, der von sp_cursorprepare zurückgegeben wird, wenn die-Anweisung vorbereitet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_cursorprepare &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursorprepare-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
