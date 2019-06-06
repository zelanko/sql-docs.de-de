---
title: sys.fn_helpcollations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_helpcollations
- fn_helpcollations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_helpcollations function
- collations [SQL Server], supported
- fn_helpcollations function
ms.assetid: b5082e81-1fee-4e2c-b567-5412eaee41c1
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 157cb3b24d04337c4949e3d6cfe38337895b3bea
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719427"
---
# <a name="sysfnhelpcollations-transact-sql"></a>sys.fn_helpcollations (Transact-SQL)

[!INCLUDE[appliesto-ss-asdb-xxxx-pdw-md](../../includes/appliesto-ss-asdb-xxxx-pdw-md.md)]

  Gibt eine Liste aller unterstützten Sortierungen zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```
fn_helpcollations ()  
```  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen

 **Fn_helpcollations** die folgenden Informationen zurückgegeben.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|Name|**sysname**|Standardsortierungsname|  
|Description|**nvarchar(1000)**|Beschreibung der Sortierung|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Windows-Sortierungen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt auch eine begrenzte Anzahl (< 80) wird aufgerufen, Sortierungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sortierungen, die entwickelt wurden, bevor Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützte Windows-Sortierungen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sortierungen werden für die Abwärtskompatibilität weiterhin unterstützt, aber für neue Entwicklungen nicht verwendet werden sollten. Weitere Informationen zur Windows-Sortierung finden Sie unter [Name der Windows-Sortierung &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md). Weitere Informationen zur Sortierung finden Sie unter [Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Beispiele

 Im folgenden Beispiel werden alle Sortierungsnamen zurückgegeben, die mit dem Buchstaben `L` beginnen und die binäre Sortierungen darstellen.  
  
```sql  
SELECT Name, Description FROM fn_helpcollations()  
WHERE Name like 'L%' AND Description LIKE '% binary sort';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Name                   Description  
 -------------------    ------------------------------------  
 Lao_100_BIN            Lao-100, binary sort  
 Latin1_General_BIN     Latin1-General, binary sort  
 Latin1_General_100_BIN Latin1-General-100, binary sort  
 Latvian_BIN            Latvian, binary sort  
 Latvian_100_BIN        Latvian-100, binary sort  
 Lithuanian_BIN         Lithuanian, binary sort  
 Lithuanian_100_BIN     Lithuanian-100, binary sort  
  
 (7 row(s) affected)  
 ```
  
## <a name="see-also"></a>Siehe auch

[COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md)   
[COLLATIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/collation-functions-collationproperty-transact-sql.md)  
[Unterstützung der Datenbank-Sortierung für Azure SQL Data Warehouse](https://azure.microsoft.com/blog/database-collation-support-for-azure-sql-data-warehouse-2)  