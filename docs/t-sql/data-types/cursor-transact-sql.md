---
title: cursor (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1849a138410485a26be32e6a15603d5aa1a56de8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56024021"
---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Ein Datentyp für Variablen oder für OUTPUT-Parameter von gespeicherten Prozeduren, die einen Verweis auf einen Cursor enthalten.
  
## <a name="remarks"></a>Remarks  
Folgende Vorgänge können auf Variablen und Parameter vom Datentyp **cursor** verweisen:
-   Die Anweisungen DECLARE *@local_variable* und SET *@local_variable*.  
-   Die Cursoranweisungen OPEN, FETCH, CLOSE und DEALLOCATE.  
-   Ausgabeparameter der gespeicherten Prozedur.  
-   Die CURSOR_STATUS-Funktion.  
-   Die gespeicherten Systemprozeduren **sp_cursor_list**, **sp_describe_cursor**, **sp_describe_cursor_tables**und **sp_describe_cursor_columns** .  
  
Die **cursor_name** -Ausgabespalte von **sp_cursor_list** und **sp_describe_cursor** gibt den Namen der Cursorvariablen zurück.
  
Alle Variablen, die mit dem **cursor** -Datentyp erstellt wurden, lassen NULL zu.
  
Der **cursor** -Datentyp kann nicht für eine Spalte in einer CREATE TABLE-Anweisung verwendet werden.
  
## <a name="see-also"></a>Siehe auch
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CURSOR_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)  
[Datentypkonvertierung &#40;Datenbank-Engine&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
