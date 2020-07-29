---
title: GETANSINULL (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GETANSINULL
- GETANSINULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], default
- GETANSINULL function
- default nullability
- database nullability [SQL Server]
ms.assetid: 189399e4-428d-4902-b3a8-94f07fdefc6a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8b464037ffb914b78dc95edbf33676820e849ca1
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87111521"
---
# <a name="getansinull-transact-sql"></a>GETANSINULL (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die Standard-NULL-Zulässigkeit für die Datenbank für diese Sitzung zurück.  
  
 ![Artikellinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GETANSINULL ( [ 'database' ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 '*database*'  
 Der Name der Datenbank, für die Informationen zur NULL-Zulässigkeit zurückgegeben werden sollen. *“database“ ist entweder vom Datentyp **char** oder vom Datentyp **nchar**. Wenn es sich um **char** handelt, wird *database* implizit in **nchar** konvertiert.  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="remarks"></a>Bemerkungen  
GETANSINULL gibt 1 zurück, wenn die NULL-Zulässigkeit der Datenbank Nullwerte zulässt. Dieser Rückgabewert erfordert auch, dass die NULL-Zulässigkeit der Spalte oder des Datentyps nicht explizit definiert ist. Der ANSI NULL-Standardwert ist 1. 
  
 Zur Aktivierung des ANSI NULL-Standardverhaltens muss eine der folgenden Bedingungen festgelegt werden:  
  
-   ALTER DATABASE *database_name* SET ANSI_NULL_DEFAULT ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET ANSI_NULL_DFLT_OFF OFF  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die standardmäßige NULL-Zulässigkeit für die `AdventureWorks2012`-Datenbank zurück.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT GETANSINULL('AdventureWorks2012')  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ------  
1  

(1 row(s) affected)
 ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
