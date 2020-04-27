---
title: sys. fn_helpcollations (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>=aps-pdw-2016|| = azure-sqldw-latest ||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ee626b9eef8cf2f2e80217b2a3709271a227f293
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67906124"
---
# <a name="sysfn_helpcollations-transact-sql"></a>sys.fn_helpcollations (Transact-SQL)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Gibt eine Liste aller unterstützten Sortierungen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```
fn_helpcollations ()  
```  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen

 **fn_helpcollations** gibt die folgenden Informationen zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|Name|**sysname**|Standardsortierungsname|  
|Beschreibung|**nvarchar (1000)**|Beschreibung der Sortierung|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Windows-Sortierungen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt auch eine begrenzte Anzahl (<80) von Sortierungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die als Sortierungen bezeichnet werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die vor unterstützten Windows-Sortierungen entwickelt wurden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Sortierungen werden weiterhin aus Gründen der Abwärtskompatibilität unterstützt, sollten aber nicht für neue Entwicklungsarbeiten verwendet werden. Weitere Informationen zur Windows-Sortierung finden Sie unter [Name der Windows-Sortierung &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md). Weitere Informationen zur Sortierung finden Sie unter [Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Beispiele

 Im folgenden Beispiel werden alle Sortierungsnamen zurückgegeben, die mit dem Buchstaben `L` beginnen und die binäre Sortierungen darstellen.

> [!Note]
> Azure SQL Data Warehouse Abfragen für fn_helpcollations () müssen in der Master-Datenbank ausgeführt werden.  
  
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
  
## <a name="see-also"></a>Weitere Informationen

[COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md)   
[COLLATIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/collation-functions-collationproperty-transact-sql.md)  
[Unterstützung der Datenbanksortierung für Azure SQL Data Warehouse](https://azure.microsoft.com/blog/database-collation-support-for-azure-sql-data-warehouse-2)  