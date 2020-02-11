---
title: sp_invalidate_textptr (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_invalidate_textptr_TSQL
- sp_invalidate_textptr
dev_langs:
- TSQL
helpviewer_keywords:
- sp_invalidate_textptr
ms.assetid: dd9920e1-7064-4c05-93d8-9303103fa1d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81df88f6e451d71dc5778e49162db97def7ed27d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68113191"
---
# <a name="sp_invalidate_textptr-transact-sql"></a>sp_invalidate_textptr (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erklärt den angegebenen Textzeiger in Zeilen oder alle Textzeiger in Zeilen in der Transaktion für ungültig. **sp_invalidate_textptr** können nur für Text Zeiger in Zeilen verwendet werden. Diese Zeiger stammen aus Tabellen, in denen die Option **Text in row** aktiviert ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_invalidate_textptr [ [ @TextPtrValue = ] textptr_value ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @TextPtrValue = ] textptr_value`Der Text Zeiger in Zeilen, der für ungültig erklärt werden soll. *textptr_value* ist vom Datentyp **varbinary (** 16 **)** und hat den Standardwert NULL. Wenn der Wert NULL ist, wird **sp_invalidate_textptr** alle Text Zeiger in Zeilen in der Transaktion für ungültig erklären.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt pro Transaktion und Datenbank maximal 1.024 aktive gültige Textzeiger in Zeilen zu. Eine Transaktion, die mehrere Datenbanken umfasst, kann jedoch pro Datenbank 1.024 Textzeiger in Zeilen enthalten. **sp_invalidate_textptr** können verwendet werden, um Text Zeiger in Zeilen ungültig zu machen und damit zusätzlichen Text Zeigern in Zeilen freizugeben.  
  
 Weitere Informationen zur Option text in row finden Sie unter [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_tableoption &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)   
 [TEXTPTR &#40;Transact-SQL-&#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [TEXTVALID &#40;Transact-SQL-&#41;](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)  
  
  
