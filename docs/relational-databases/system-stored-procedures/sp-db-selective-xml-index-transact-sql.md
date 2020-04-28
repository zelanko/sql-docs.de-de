---
title: sp_db_selective_xml_index (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 1648cca415f37f9c54f13857d25af90a65372c04
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108231"
---
# <a name="sp_db_selective_xml_index-transact-sql"></a>sp_db_selective_xml_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Aktiviert und deaktiviert die Funktion des selektiven XML-Indexes in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank. Wenn diese ohne Parameter aufgerufen wird, gibt die gespeicherte Prozedur 1 zurück, wenn der selektive XML-Index in einer bestimmten Datenbank aktiviert ist.  
  
> [!NOTE]  
>  Um den selektiven XML-Index mithilfe dieser gespeicherten Prozedur zu deaktivieren, muss die Datenbank mithilfe des Befehls [ALTER DATABASE Set options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) in den einfachen Wiederherstellungs Modus versetzt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
  
      sys.sp_db_selective_xml_index[[ @db_name = ] 'db_name'],   
[[ @action = ] 'action']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @ db_name = ] 'db_name'`Der Name der Datenbank, für die der selektive XML-Index aktiviert oder deaktiviert werden soll. Wenn *db_name* NULL ist, wird die aktuelle Datenbank angenommen.  
  
`[ @action = ] 'action'`Bestimmt, ob der Index aktiviert oder deaktiviert werden soll. Wenn ein anderer Wert mit Ausnahme von ' on ', ' true ', ' off ' oder ' false ' überschritten wird, wird ein Fehler ausgelöst.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Selektive XML-Indizes &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  
