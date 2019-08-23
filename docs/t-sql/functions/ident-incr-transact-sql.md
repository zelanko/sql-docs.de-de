---
title: IDENT_INCR (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IDENT_INCR
- IDENT_INCR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- incremental values [SQL Server]
- IDENT_INCR function
- identity columns [SQL Server], IDENT_INCR function
ms.assetid: e13b491f-4f1f-4cb6-8b63-5084120f98cf
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6edd1cb219f7250a6f9e5671efdb076c6e0a0349
ms.sourcegitcommit: 316c25fe7465b35884f72928e91c11eea69984d5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2019
ms.locfileid: "68969477"
---
# <a name="ident_incr-transact-sql"></a>IDENT_INCR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt den inkrementellen Wert zurück, der beim Erstellen einer Identitätsspalte in einer Tabelle oder Ansicht festgelegt wurde.  
  
![Artikellinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
IDENT_INCR ( 'table_or_view' )  
```  
  
## <a name="arguments"></a>Argumente  
**'** *table_or_view* **'**  
Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md), der die Tabelle oder Sicht angibt, die auf einen gültigen inkrementellen Wert für die Identitätsspalte überprüft werden soll. *table_or_view* kann eine Zeichenfolgenkonstante in Anführungszeichen sein. Es kann auch eine Variable, eine Funktion oder ein Spaltenname sein. *table_or_view* ist vom Datentyp **char**, **nchar**, **varchar** oder **nvarchar**.  
  
## <a name="return-types"></a>Rückgabetypen  
**numeric**([@@MAXPRECISION](../../t-sql/functions/max-precision-transact-sql.md),0))  
  
## <a name="exceptions"></a>Ausnahmen  
Gibt NULL zurück, wenn ein Fehler auftritt oder ein Aufrufer nicht über die Berechtigungen zum Anzeigen des Objekts verfügt.  
  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann ein Benutzer nur die Metadaten von sicherungsfähigen Elementen anzeigen, die er besitzt oder für die er Berechtigungen hat. Ohne Objektberechtigung des Benutzers kann eine Metadaten emittierende, eingebaute Funktion, wie z.B. IDENT_INCR, NULL zurückgeben. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-the-increment-value-for-a-specified-table"></a>A. Zurückgeben des inkrementellen Werts für eine angegebene Tabelle  
 Im folgenden Beispiel wird der inkrementelle Wert für die `Person.Address`-Tabelle in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank zurückgegeben.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT IDENT_INCR('Person.Address') AS Identity_Increment;  
GO  
```  
  
### <a name="b-returning-the-increment-value-from-multiple-tables"></a>B. Zurückgeben des inkrementellen Werts aus mehreren Tabellen  
 Im folgenden Beispiel werden die Tabellen in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank zurückgegeben, die eine Identitätsspalte mit einem inkrementellen Wert enthalten.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT TABLE_SCHEMA, TABLE_NAME,   
   IDENT_INCR(TABLE_SCHEMA + '.' + TABLE_NAME) AS IDENT_INCR  
FROM INFORMATION_SCHEMA.TABLES  
WHERE IDENT_INCR(TABLE_SCHEMA + '.' + TABLE_NAME) IS NOT NULL;  
```  
  
 Dies ist ein Auszug aus dem Resultset.  
  
 ```
 TABLE_SCHEMA        TABLE_NAME                IDENT_INCR  
------------        ------------------------  ----------  
Person              Address                            1  
Production          ProductReview                      1  
Production          TransactionHistory                 1  
Person              AddressType                        1  
Production          ProductSubcategory                 1  
Person              vAdditionalContactInfo             1  
dbo                 AWBuildVersion                     1  
Production          BillOfMaterials                    1
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [IDENT_CURRENT &#40;Transact-SQL&#41;](../../t-sql/functions/ident-current-transact-sql.md)   
 [IDENT_SEED &#40;Transact-SQL&#41;](../../t-sql/functions/ident-seed-transact-sql.md)   
 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [sys.identity_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-identity-columns-transact-sql.md)  
  
  
