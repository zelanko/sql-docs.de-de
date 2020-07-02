---
title: sp_helpindex (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpindex_TSQL
- sp_helpindex
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpindex
ms.assetid: c7f73ba0-ec35-4b10-aa5f-f1487e51fbf7
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 43bf9b75af8cc43af8c45e4cc2fe4f9d4e66e595
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733174"
---
# <a name="sp_helpindex-transact-sql"></a>sp_helpindex (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt Informationen zu den Indizes in einer Tabelle oder Sicht zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpindex [ @objname = ] 'name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @objname = ] 'name'`Der qualifizierte oder nicht qualifizierte Name einer benutzerdefinierten Tabelle oder Sicht. Anführungszeichen sind nur erforderlich, wenn ein qualifizierter Tabellen- oder Sichtname angegeben wird. Bei Angabe eines vollqualifizierten Namens, einschließlich eines Datenbanknamens, muss es sich bei dem Datenbanknamen um den Namen der aktuellen Datenbank handeln. *name* ist vom Datentyp **nvarchar(776)** und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**index_name**|**sysname**|Indexname.|  
|**index_description**|**varchar (210)**|Beschreibung des Indexes einschließlich der Dateigruppe, in der er sich befindet.|  
|**index_keys**|**nvarchar (2078)**|Die Spalten der Tabelle oder Sicht, für die der Index erstellt wird.|  
  
 Eine absteigende indizierte Spalte wird im Resultset mit einem Minuszeichen (-) hinter dem Namen aufgelistet. Eine aufsteigende indizierte Spalte, der Standard, wird nur mit dem Namen aufgelistet.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Indizes mithilfe der NORECOMPUTE-Option von Update Statistics festgelegt wurden, sind diese Informationen in der Spalte **index_description** enthalten.  
  
 **sp_helpindex** macht nur sortierbare Index Spalten verfügbar. Daher werden keine Informationen über XML-Indizes oder räumliche Indizes bereitgestellt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die Indextypen in der `Customer`-Tabelle aus.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpindex N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys. Indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys. index_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
  
  
