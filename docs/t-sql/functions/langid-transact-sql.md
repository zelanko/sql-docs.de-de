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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c7da7b6f0bec6df0e20dcd73354af615631b0534
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47739378"
---
# <a name="x40x40langid-transact-sql"></a>&#x40;&#x40;LANGID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die lokale Sprachen-ID der zurzeit verwendeten Sprache zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
@@LANGID  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **smallint**  
  
## <a name="remarks"></a>Remarks  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Konfigurationsfunktionen (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [sp_helplanguage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)  
  
  
