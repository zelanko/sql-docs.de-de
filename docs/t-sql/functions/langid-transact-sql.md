---
title: '@@LANGID (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@LANGID'
- '@@LANGID_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- languages [SQL Server], current in use
- '@@LANGID function'
- current language in use
- ID for language in use
- local language IDs [SQL Server]
ms.assetid: 7a0fc089-2a48-4a81-9d78-2aaedb540d37
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6098c5fc8eab31bd567390656d27cc13a5862086
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87110936"
---
# <a name="x40x40langid-transact-sql"></a>&#x40;&#x40;LANGID (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die lokale Sprachen-ID der zurzeit verwendeten Sprache zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
@@LANGID  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 **smallint**  
  
## <a name="remarks"></a>Bemerkungen  
 Zum Anzeigen von Informationen zu Spracheinstellungen, einschließlich Sprach-ID-Nummern, führen Sie **sp_helplanguage** ohne Angabe von Parametern aus.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Sprache für die aktuelle Sitzung auf `Italian` festgelegt und dann `@@LANGID` zur Rückgabe der ID für Italienisch verwendet.  
  
```  
SET LANGUAGE 'Italian'  
SELECT @@LANGID AS 'Language ID'  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Changed language setting to Italiano.  
Language ID  
-----------  
6            
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurationsfunktionen (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [sp_helplanguage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)  
  
  
