---
title: GETANSINULL (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 29
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cd29e887f85d58d5680e064a419e6382d121bafb
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781131"
---
# <a name="getansinull-transact-sql"></a>GETANSINULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die Standard-NULL-Zulässigkeit für die Datenbank für diese Sitzung zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GETANSINULL ( [ 'database' ] )  
```  
  
## <a name="arguments"></a>Argumente  
 '*database*'  
 Der Name der Datenbank, für die Informationen zur NULL-Zulässigkeit zurückgegeben werden sollen. *database* ist entweder vom Datentyp **char** oder vom Datentyp **nchar**. Wenn es sich um **char** handelt, wird *database* implizit in **nchar** konvertiert.  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="remarks"></a>Remarks  
 Wenn die NULL-Zulässigkeit der angegebenen Datenbank NULL-Werte zulässt und die NULL-Zulässigkeit von Spalten oder Datentypen nicht explizit definiert wurde, gibt GETANSINULL den Wert 1 zurück. Dies ist der ANSI NULL-Standard.  
  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
