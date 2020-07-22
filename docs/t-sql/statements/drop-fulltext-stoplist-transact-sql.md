---
title: DROP FULLTEXT STOPLIST (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_FULLTEXT_STOPLIST_TSQL
- DROP FULLTEXT STOPLIST
dev_langs:
- TSQL
helpviewer_keywords:
- DROP FULLTEXT STOPLIST statement
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 3ee2a2bb-1dfb-4e7c-90e9-9d917cd84a15
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e7ecfcce3c2805091bd605d5870c85d948d0619e
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2020
ms.locfileid: "86484376"
---
# <a name="drop-fulltext-stoplist-transact-sql"></a>DROP FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Löscht eine Volltext-Stoppliste aus der Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!IMPORTANT]  
>  CREATE FULLTEXT STOPLIST wird nur bei einem Kompatibilitätsgrad von mindestens 100 unterstützt. Bei Kompatibilitätsgraden von 80 und 90 wird die Systemstoppliste immer der Datenbank zugewiesen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP FULLTEXT STOPLIST stoplist_name  
;  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *stoplist_name*  
 Der Name der Volltextstoppliste, die aus der Datenbank gelöscht werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 DROP FULLTEXT STOPLIST schlägt fehl, wenn Volltextindizes auf die Volltextstoppliste verweisen, die gelöscht wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Löschen einer Stoppliste ist eine DROP-Berechtigung für die Stoppliste oder eine Mitgliedschaft in der festen Datenbankrolle **db_owner** oder **db_ddladmin** erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Volltextstoppliste mit dem Namen `myStoplist` gelöscht.  
  
```  
DROP FULLTEXT STOPLIST myStoplist;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
  
  
