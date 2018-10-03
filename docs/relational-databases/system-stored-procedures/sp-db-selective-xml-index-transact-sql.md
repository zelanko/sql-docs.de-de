---
title: Sp_db_selective_xml_index (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_db_selective_xml_index_TSQL
- sp_db_selective_xml_index
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_selective_xml_index procedure
ms.assetid: 017301a2-4a23-4e68-82af-134f3d4892b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07145e608c850a877a984c7467da6b8974f0d151
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47744598"
---
# <a name="spdbselectivexmlindex-transact-sql"></a>sp_db_selective_xml_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Aktiviert und deaktiviert die Funktion des selektiven XML-Indexes in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank. Wenn diese ohne Parameter aufgerufen wird, gibt die gespeicherte Prozedur 1 zurück, wenn der selektive XML-Index in einer bestimmten Datenbank aktiviert ist.  
  
> [!NOTE]  
>  Um den selektiven XML-Index, die mit dieser gespeicherten Prozedur zu deaktivieren, die Datenbank muss werden im einfachen Wiederherstellungsmodus mit versetzt die [ALTER DATABASE SET Options &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) Befehl.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
  
      sys.sp_db_selective_xml_index[[ @db_name = ] 'db_name'],   
[[ @action = ] 'action']  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@ Db_name =** ] **"***Db_name***"**  
 Der Name der Datenbank, in der der selektive XML-Index aktiviert oder deaktiviert wird. Wenn *Db_name* NULL ist, wird die aktuelle Datenbank angenommen.  
  
 [  **@action =** ] **"***Aktion***"**  
 Bestimmt, ob der Index aktivieren oder deaktiviert wird. Wenn ein anderer Wert außer 'on', 'true', 'off', oder 'false' übergeben wird, wird ein Fehler ausgelöst.  
  
```  
  
Allowed values: 'on', 'off', 'true', 'false'  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **1** , wenn der selektive XML-Index für eine bestimmte Datenbank aktiviert ist.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-enable-selective-xml-index-functionality"></a>A. Aktivieren der Funktion für den selektiven XML-Index  
 Im folgenden Beispiel wird der selektive XML-Index in der aktuellen Datenbank aktiviert.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'on';  
GO  
```  
  
 Im folgenden Beispiel wird der selektive XML-Index in der AdventureWorks2012-Datenbank aktiviert.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'true';  
GO  
```  
  
### <a name="b-disable-selective-xml-index-functionality"></a>B. Deaktivieren der Funktion für den selektiven XML-Index  
 Im folgenden Beispiel wird der selektive XML-Index in der aktuellen Datenbank deaktiviert.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'off';  
GO  
```  
  
 Im folgenden Beispiel wird der selektive XML-Index in der der AdventureWorks2012-Datenbank deaktiviert.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'false';  
GO  
```  
  
### <a name="c-detect-if-selective-xml-index-is-enabled"></a>C. Ermitteln, ob der selektive XML-Index aktiviert ist  
 Im folgenden Beispiel wird ermittelt, ob der selektive XML-Index aktiviert ist. Gibt 1 zurück, wenn der selektive XML-Index aktiviert ist.  
  
```  
EXECUTE sys.sp_db_selective_xml_index;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Selektive XML-Indizes &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  
