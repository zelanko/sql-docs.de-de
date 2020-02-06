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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c5c52edfde8a0cde06ec5a0f2f154df06b6b6c12
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "73843716"
---
# <a name="getansinull-transact-sql"></a>GETANSINULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die Standard-NULL-Zulässigkeit für die Datenbank für diese Sitzung zurück.  
  
 ![Artikellinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GETANSINULL ( [ 'database' ] )  
```  
  
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
  
  
