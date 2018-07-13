---
title: sp_datatype_info_90 (SQL Datawarehouse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1d043964-dc6e-4c3e-ab61-bc444d5e25ae
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 349297399955dd9b3f43f4507f38918507f64cff
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926721"
---
# <a name="spdatatypeinfo90-sql-data-warehouse"></a>sp_datatype_info_90 (SQL Datawarehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Gibt Informationen zu den von der aktuellen Umgebung unterstützten Datentypen zurück.  
  
 ![Symbol zum Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol zum Themenlink") [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41; (Transact-SQL-Syntaxkonventionen (Transact-SQL))](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_datatype_info_90 [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  
  
## <a name="arguments"></a>Argumente  
 [ **@data_type=** ] *data_type*  
 Die Codenummer für den angegebenen Datentyp. Um eine Liste aller Datentypen abzurufen, lassen Sie diesen Parameter weg. *Data_type* ist **Int**, hat den Standardwert 0.  
  
 [ **@ODBCVer=** ] *odbc_version*  
 Die verwendete ODBC-Version. *Odbc_version* ist **Tinyint**, hat den Standardwert von 2.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 InclusionThresholdSetting  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|TYPE_NAME|**sysname**|Der DBMS-abhängige Datentyp.|  
|DATA_TYPE|**smallint**|Der Code für den ODBC-Datentyp, dem alle Spalten dieses Datentyps zugeordnet sind.|  
|PRECISION|**int**|Die maximale Genauigkeit des Datentyps bezüglich der Datenquelle. NULL wird für Datentypen zurückgegeben, auf die die Genauigkeit nicht anwendbar ist. Der Rückgabewert für die PRECISION-Spalte hat die Basis 10.|  
|LITERAL_PREFIX|**Varchar (** 32 **)**|Das oder die Zeichen, die einer Konstante vorangestellt werden. Beispielsweise eine einfaches Anführungszeichen (**"**) bei Zeichentypen und 0 X bei Binärtypen.|  
|LITERAL_SUFFIX|**Varchar (** 32 **)**|Das oder die Zeichen, die eine Konstante beenden. Beispielsweise eine einfaches Anführungszeichen (**"**) bei Zeichentypen und keine Anführungszeichen bei Binärtypen.|  
|CREATE_PARAMS|**Varchar (** 32 **)**|Die Beschreibung der Erstellungsparameter für diesen Datentyp. Z. B. **decimal** ist "Precision, Scale", **"float"** NULL ist, und **Varchar** "max_length".|  
|NULLABLE|**smallint**|Gibt die NULL-Zulässigkeit an.<br /><br /> 1 = Lässt NULL-Werte zu.<br /><br /> 0 = NULL ist nicht zulässig.|  
|CASE_SENSITIVE|**smallint**|Gibt die Unterscheidung nach Groß-/Kleinschreibung an.<br /><br /> 1 = Bei allen Spalten dieses Typs wird nach Groß-/Kleinschreibung unterschieden (für Sortierungen).<br /><br /> 0 = Bei allen Spalten dieses Typs wird nicht nach Groß-/Kleinschreibung unterschieden.|  
|SEARCHABLE|**smallint**|Gibt die Suchfunktion des Spaltentyps an:<br /><br /> 1 = Kann nicht durchsucht werden.<br /><br /> 2 = Durchsuchbar mit LIKE<br /><br /> 3 = Durchsuchbar mit WHERE<br /><br /> 4 = Durchsuchbar mit WHERE oder LIKE|  
|UNSIGNED_ATTRIBUTE|**smallint**|Gibt das Vorzeichen des Datentyps an.<br /><br /> 1 = Datentyp ohne Vorzeichen<br /><br /> 0 = Datentyp mit Vorzeichen|  
|MONEY|**smallint**|Gibt an, die **Geld** -Datentyp.<br /><br /> 1 = **Geld** -Datentyp.<br /><br /> 0 = keine **Geld** -Datentyp.|  
|AUTO_INCREMENT|**smallint**|Gibt die automatische Inkrementierung an.<br /><br /> 1 = Automatische Inkrementierung<br /><br /> 0 = Keine automatische Inkrementierung<br /><br /> NULL = Attribut nicht zutreffend.<br /><br /> Eine Anwendung kann zwar Werte in eine Spalte einfügen, die dieses Attribut aufweist, kann jedoch die Werte in der Spalte nicht aktualisieren. Mit Ausnahme von der **Bit** Datentyp AUTO_INCREMENT ist nur für Datentypen, die der genauen numerischen oder ungefähren numerischen Datentypkategorien angehören.|  
|LOCAL_TYPE_NAME|**sysname**|Lokalisierte Version des von der Datenquelle abhängigen Datentypamens. Beispielsweise lautet DECIMAL auf Französisch DECIMALE. NULL wird zurückgegeben, wenn ein lokalisierter Name nicht von der Datenquelle unterstützt wird.|  
|MINIMUM_SCALE|**smallint**|Die minimalen Dezimalstellen des Datentyps bezüglich der Datenquelle. Weist ein Datentyp Feste Dezimalstellen, enthalten die Spalten MINIMUM_SCALE und MAXIMUM_SCALE diesen Wert an. NULL wird zurückgegeben, wenn Dezimalstellen auf den Datentyp nicht anwendbar sind.|  
|MAXIMUM_SCALE|**smallint**|Die maximalen Dezimalstellen des Datentyps bezüglich der Datenquelle. Wenn die maximale Dezimalstellen für die Datenquelle nicht separat definiert, aber es wird stattdessen definiert der maximalen Genauigkeit entsprechen, enthält diese Spalte den gleichen Wert wie die PRECISION-Spalte.|  
|SQL_DATA_TYPE|**smallint**|Der Wert des SQL-Datentyps, wie er im TYPE-Feld des Deskriptors angezeigt wird. Diese Spalte entspricht der DATA_TYPE-Spalte mit Ausnahme der **"DateTime"** und ANSI **Intervall** -Datentypen. Dieses Feld gibt immer einen Wert zurück.|  
|SQL_DATETIME_SUB|**smallint**|**"DateTime"** oder ANSI **Intervall** subcode, wenn der Wert des SQL_DATA_TYPE SQL_DATETIME oder SQL_INTERVAL hat. Bei allen Datentypen außer **"DateTime"** und ANSI **Intervall**, dieses Feld ist NULL.|  
|NUM_PREC_RADIX|**int**|Die Anzahl der Bits oder Stellen für das Berechnen der höchsten Zahl, die eine Spalte enthalten kann. Wenn es sich um einen ungefähren numerischen Datentyp handelt, enthält diese Spalte den Wert 2 für mehrere Bits. Bei exakten numerischen Datentypen enthält diese Spalte den Wert 10 für mehrere Dezimalstellen. Andernfalls ist diese Spalte NULL. Aus der Kombination von Genauigkeit und Basis kann die Anwendung die höchste Zahl berechnen, die die Spalte enthalten kann.|  
|INTERVAL_PRECISION|**smallint**|Wenn Genauigkeit für anführenden Intervallwert *Data_type* ist **Intervall**; andernfalls NULL.|  
|USERTYPE|**smallint**|**Usertype** Wert aus der Systypes-Tabelle.|  
  
## <a name="remarks"></a>Hinweise  
 Sp_datatype_info ist gleichbedeutend mit SQLGetTypeInfo in ODBC. Die zurückgegebenen Ergebnisse sind nach DATA_TYPE und dann nach wie genau die Daten mit den entsprechenden ODBC SQL-Datentyp geordnet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
 Das folgende Beispiel ruft Informationen für die **Sysname** und **Nvarchar** Datentypen durch Angabe der *Data_type* Wert `-9`.  
  
```  
USE master;  
GO  
EXEC sp_datatype_info_90 -9;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für SQL Data Warehouse](../../relational-databases/system-stored-procedures/sql-data-warehouse-stored-procedures.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

