---
title: Sp_datatype_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/25/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_datatype_info_TSQL
- sp_datatype_info
dev_langs:
- TSQL
helpviewer_keywords:
- sp_datatype_info
ms.assetid: 045f3b5d-6bb7-4748-8b4c-8deb4bc44147
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3eadc5efc471f44998abddc596f1acc5c6e378ca
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527932"
---
# <a name="spdatatypeinfo-transact-sql"></a>sp_datatype_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Gibt Informationen zu den von der aktuellen Umgebung unterstützten Datentypen zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_datatype_info [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @data_type = ] data_type` Ist die Nummer für den angegebenen Datentyp. Um eine Liste aller Datentypen abzurufen, lassen Sie diesen Parameter weg. *Data_type* ist **Int**, hat den Standardwert 0.  
  
`[ @ODBCVer = ] odbc_version` Ist die Version von ODBC, der verwendet wird. *Odbc_version* ist **Tinyint**, hat den Standardwert von 2.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 None  
  
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
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel ruft Informationen für die **Sysname** und **Nvarchar** Datentypen durch Angabe der *Data_type* Wert `-9`.  
  
```  
USE master;  
GO  
EXEC sp_datatype_info -9;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
