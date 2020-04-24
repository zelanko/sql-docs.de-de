---
title: CLOSE SYMMETRIC KEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CLOSE SYMMETRIC KEY
- CLOSE_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- closing symmetric keys
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], closing
- CLOSE SYMMETRIC KEY statement
- cryptography [SQL Server], symmetric keys
ms.assetid: 3b083cbb-3c6a-4f59-8d34-601db1efcc83
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ab39b255fdb60fac42357c61df0eb15675aebede
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632650"
---
# <a name="close-symmetric-key-transact-sql"></a>CLOSE SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Schließt einen symmetrischen Schlüssel oder schließt alle in der aktuellen Sitzung geöffneten symmetrischen Schlüssel.  
  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
CLOSE { SYMMETRIC KEY key_name | ALL SYMMETRIC KEYS }  
```  
  
## <a name="arguments"></a>Argumente  
 *Key_name*  
 Der Name des zu schließenden symmetrischen Schlüssels.  
  
## <a name="remarks"></a>Bemerkungen  
 Geöffnete symmetrische Schlüssel werden an die Sitzung gebunden und nicht an den Sicherheitskontext. Ein geöffneter Schlüssel ist weiterhin verfügbar, bis er entweder explizit geschlossen oder die Sitzung beendet wird. Mit CLOSE ALL SYMMETRIC KEYS werden alle in der aktuellen Sitzung geöffneten Datenbank-Hauptschlüssel mithilfe der [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md) -Anweisung geschlossen.  Informationen zu offenen Schlüsseln werden in der Katalogsicht [sys.openkeys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md) angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Schließen eines symmetrischen Schlüssels ist keine explizite Berechtigung erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-closing-a-symmetric-key"></a>A. Schließen eines symmetrischen Schlüssels  
 Im folgenden Beispiel wird der symmetrische Schlüssel `ShippingSymKey04`geschlossen.  
  
```  
CLOSE SYMMETRIC KEY ShippingSymKey04;  
GO  
```  
  
### <a name="b-closing-all-symmetric-keys"></a>B. Schließen aller symmetrischen Schlüssel  
 Im folgenden Beispiel werden alle in der aktuellen Sitzung geöffneten symmetrischen Schlüssel sowie der explizit geöffnete Datenbankhauptschlüssel geschlossen.  
  
```  
CLOSE ALL SYMMETRIC KEYS;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)  
  
  
