---
title: ORIGINAL_DB_NAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ORIGINAL_DB_NAME
- ORIGINAL_DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ORIGINAL_DB_NAME function
ms.assetid: 7dadc40a-1287-4f31-8487-434ee477144d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee1644e34964a41a8e6ee97897bcce6a1783e536
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47743988"
---
# <a name="originaldbname-transact-sql"></a>ORIGINAL_DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den Datenbanknamen zurück, der vom Benutzer in der Datenbankverbindungszeichenfolge angegeben wird. Hierbei handelt es sich um die Datenbank, die mit der **sqlcmd-d**-Option (USE *Datenbank*) oder dem ODBC-Datenquellenausdruck (Anfangskatalog =*Datenbankname*) angegeben wird.  
  
 Diese Datenbank ist nicht mit der standardmäßigen Benutzerdatenbank identisch.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ORIGINAL_DB_NAME ()  
```  
  
## <a name="remarks"></a>Remarks  
 Wenn die ursprüngliche Datenbank nicht angegeben wird, gibt die Funktion eine leere Zeichenfolge zurück.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sqlcmd (Hilfsprogramm)](../../tools/sqlcmd-utility.md)   
 [Hilfsprogramm „osql“](../../tools/osql-utility.md)   
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
