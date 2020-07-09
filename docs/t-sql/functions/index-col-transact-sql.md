---
title: INDEX_COL (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- INDEX_COL_TSQL
- INDEX_COL
dev_langs:
- TSQL
helpviewer_keywords:
- displaying column names
- INDEX_COL function
- viewing column names
- column names [SQL Server]
- names [SQL Server], columns
ms.assetid: 4db1fb3b-e46f-43fb-b269-a5b6e8b39ed0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c82aae8312d19606853a3a676e98c6ca14c821f0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85752345"
---
# <a name="index_col-transact-sql"></a>INDEX_COL (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt den Namen einer indizierten Spalte zurück. Gibt für XML-Indizes NULL zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
INDEX_COL ( '[ database_name . [ schema_name ] .| schema_name ]  
    table_or_view_name', index_id , key_id )   
```  
  
## <a name="arguments"></a>Argumente  
 *database_name*  
 Der Name der Datenbank.  
  
 *schema_name*  
 Ist der Name des Schemas, zu dem der Index gehört.  
  
 *table_or_view_name*  
 Der Name der Tabelle oder indizierten Sicht. *table_or_view_name* muss in einfache Anführungszeichen gesetzt werden und kann durch Datenbank- und Schemanamen voll qualifiziert werden.  
  
 *index_id*  
 Die ID des Indexes. *index_ID* ist vom Datentyp **int**.  
  
 *key_id*  
 Die Position der Indexschlüsselspalte. *key_ID* ist vom Datentyp **int**.  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar (128** **)**  
  
## <a name="exceptions"></a>Ausnahmen  
 Gibt NULL bei einem Fehler zurück oder wenn ein Aufrufer nicht über Berechtigungen zum Anzeigen des Objekts verfügt.  
  
 Ein Benutzer kann nur die Metadaten sicherungsfähiger Elemente anzeigen, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Dies bedeutet, dass Metadaten ausgebende integrierte Funktionen, z. B. INDEX_COL, möglicherweise NULL zurückgeben, wenn dem Benutzer für das Objekt keine Berechtigung erteilt wurde. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-index_col-to-return-an-index-column-name"></a>A. Zurückgeben eines Indexspaltennamens mit INDEX_COL  
 Im folgenden Beispiel werden die Spaltennamen der beiden Schlüsselspalten im Index `PK_SalesOrderDetail_SalesOrderID_LineNumber` zurückgegeben.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   
    INDEX_COL (N'AdventureWorks2012.Sales.SalesOrderDetail', 1,1) AS  
        [Index Column 1],   
    INDEX_COL (N'AdventureWorks2012.Sales.SalesOrderDetail', 1,2) AS  
        [Index Column 2]  
;  
GO  
```  
  
 Im Folgenden wird das Resultset aufgeführt:  
  
```  
Index Column 1      Index Column 2  
-----------------------------------------------  
SalesOrderID        SalesOrderDetailID  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Metadata Functions &#40;Transact-SQL&#41; (Metadatenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
