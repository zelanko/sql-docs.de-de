---
title: PARSENAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PARSENAME_TSQL
- PARSENAME
dev_langs:
- TSQL
helpviewer_keywords:
- PARSENAME function
- parsing [SQL Server], PARSENAME function
- names [SQL Server], objects
- objects [SQL Server], names
- part of object names [SQL Server]
ms.assetid: abf34f99-9ee9-460b-85b2-930ca5c4b5ae
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 915cf95799a80a0d8841206f4b23b04fba5fec5f
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87112375"
---
# <a name="parsename-transact-sql"></a>PARSENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Gibt den angegebenen Teil eines Objektnamens zurück. Die Teile eines Objekts, die abgerufen werden können, sind der Objektname, der Schemaname, der Datenbankname und der Servername. 
  
> [!NOTE]  
>  Die PARSENAME-Funktion zeigt nicht an, ob ein Objekt mit dem angegebenen Namen vorhanden ist. PARSENAME gibt lediglich den angegebenen Teil des gegebenen Objektnamens zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql 
PARSENAME ('object_name' , object_piece )
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente

*'object_name'* ist der Parameter, der den Namen des Objekts beinhaltet, für das der angegebene Objektteil abgerufen werden soll. Dieser Parameter ist ein optional gekennzeichneter Objektname. Wenn alle Teile des Objektnamens gekennzeichnet sind, besteht dieser Name aus vier Teilen: dem Server-, Datenbank, Schema- und Objektnamen.  Jeder Teil der Zeichenfolge 'object_name' ist vom Typ *sysname*, was nvarchar(128) oder 256 Byte entspricht. Wenn ein beliebiger Teil der Zeichenfolge 256 Byte überschreitet, gibt PARSENAME NULL für diesen Teil zurück, da es sich nicht um einen gültigen sysname-Typ handelt.
  
*object_piece*  
Der Objektteil, der zurückgegeben werden soll. *object_piece* ist vom Datentyp **int** und kann folgende Werte haben:  
    1 = Objektname  
    2 = Schemaname  
    3 = Datenbankname  
    4 = Servername  
  
## <a name="return-type"></a>Rückgabetyp

 **sysname**
  
## <a name="remarks"></a>Bemerkungen

 PARSENAME gibt NULL zurück, wenn eine der folgenden Bedingungen wahr ist:  
  
-   Entweder für *object_name* oder für *object_piece* wird NULL zurückgegeben.  
  
-   Ein Syntaxfehler tritt auf.  
  
 Der angeforderte Objektteil hat eine Länge von 0 und ist kein gültiger [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Bezeichner. Ein Objektname mit der Länge 0 macht den gesamten qualifizierten Namen ungültig.  
  
## <a name="examples"></a>Beispiele

 Im folgenden Beispiel wird `PARSENAME` verwendet, um Informationen zur `Person`-Tabelle in der `AdventureWorks2012`-Datenbank zurückzugeben.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 1) AS 'Object Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 2) AS 'Schema Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 3) AS 'Database Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 4) AS 'Server Name';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
```
Object Name
------------------------------
DimCustomer

(1 row(s) affected)

Schema Name
------------------------------
dbo

(1 row(s) affected)

Database Name
------------------------------
AdventureWorksPDW2012

(1 row(s) affected)

Server Name
------------------------------
(null)

(1 row(s) affected)
```
  
## <a name="see-also"></a>Weitere Informationen

- [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
- [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
- [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
- [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  

