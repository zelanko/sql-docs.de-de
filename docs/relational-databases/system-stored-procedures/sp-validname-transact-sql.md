---
description: sp_validname (Transact-SQL)
title: sp_validname (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_validname
- sp_validname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validname
ms.assetid: d51c53c2-1332-407f-b725-4983f2e710eb
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e73d8f6345be199c44278cb15aa43c6ada7f91c0
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97466791"
---
# <a name="sp_validname-transact-sql"></a>sp_validname (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Überprüft die Gültigkeit von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Bezeichnernamen. Alle nicht binären und nicht-NULL-Daten, einschließlich Unicode-Daten, die mithilfe der Datentypen **NCHAR**, **nvarchar** oder **ntext** gespeichert werden können, werden als gültige Zeichen für Bezeichnernamen akzeptiert.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_validname [@name =] 'name'   
     [, [@raise_error =] raise_error]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'` Der Name der Bezeichner [, für die die Gültigkeit](../../relational-databases/databases/database-identifiers.md) überprüft werden soll. *Name ist vom Datentyp* **vom Datentyp sysname** und hat keinen Standardwert. der *Name* darf nicht NULL sein, darf keine leere Zeichenfolge sein und darf kein binäres NULL-Zeichen enthalten.  
  
`[ @raise_error = ] raise_error` Gibt an, ob ein Fehler ausgegeben werden soll. *raise_error* ist vom Typ **Bit** und hat den Standardwert 1. Dies bedeutet, dass Fehler auftreten. 0 bewirkt, dass keine Fehlermeldungen angezeigt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [NCHAR &#40;Transact-SQL&#41;](../../t-sql/functions/nchar-transact-sql.md)   
 [nchar und nvarchar &#40;Transact-SQL-&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)   
 [ntext, Text und Image &#40;Transact-SQL-&#41;](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
