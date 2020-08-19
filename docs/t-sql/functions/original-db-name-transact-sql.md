---
description: ORIGINAL_DB_NAME (Transact-SQL)
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c22913dfea659c94b3e780d86272aabf55ccbd2b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459621"
---
# <a name="original_db_name-transact-sql"></a>ORIGINAL_DB_NAME (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt den Datenbanknamen zurück, der vom Benutzer in der Datenbankverbindungszeichenfolge angegeben ist. Diese Datenbank wird durch Verwendung der Option **sqlcmd-d** angegeben (USE *Datenbank*). Sie kann auch mithilfe des ODBC-ODBC-Datenquellenausdrucks (Open Database Connectivity) (Anfangskatalog = *Datenbankname*) angegeben werden.  
  
 Diese Datenbank unterscheidet sich von der standardmäßigen Benutzerdatenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
ORIGINAL_DB_NAME ()  
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="remarks"></a>Bemerkungen  
 Wenn die ursprüngliche Datenbank nicht angegeben wird, gibt die Funktion eine leere Zeichenfolge zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sqlcmd (Hilfsprogramm)](../../tools/sqlcmd-utility.md)   
 [Hilfsprogramm „osql“](../../tools/osql-utility.md)   
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
