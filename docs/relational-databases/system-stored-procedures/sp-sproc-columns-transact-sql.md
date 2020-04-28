---
title: sp_sproc_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_sproc_columns
- sp_sproc_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_sproc_columns
ms.assetid: 62c18c21-35c5-4772-be0d-ffdcc19c97ab
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6739d9bcff2639b4b4f3562624beaf2cb3a76507
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68032821"
---
# <a name="sp_sproc_columns-transact-sql"></a>sp_sproc_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Spalteninformationen für eine einzelne gespeicherte Prozedur oder benutzerdefinierte Funktion in der aktuellen Umgebung zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_sproc_columns [[@procedure_name = ] 'name']   
    [ , [@procedure_owner = ] 'owner']   
    [ , [@procedure_qualifier = ] 'qualifier']   
    [ , [@column_name = ] 'column_name']  
    [ , [@ODBCVer = ] 'ODBCVer']  
    [ , [@fUsePattern = ] 'fUsePattern']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @procedure_name = ] 'name'`Der Name der Prozedur, die zum Zurückgeben von Katalog Informationen verwendet wird. *Name ist vom Datentyp* **nvarchar (** 390 **)**. der Standardwert ist%, d. h. alle Tabellen in der aktuellen Datenbank. Mustervergleiche mit Platzhalterzeichen werden unterstützt.  
  
`[ @procedure_owner = ] 'owner'`Der Name des Besitzers der Prozedur. *Owner*ist vom Datentyp **nvarchar (** 384 **)** und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden unterstützt. Wenn *owner* nicht angegeben wird, gelten die Standardregeln für die Sichtbarkeit von Prozeduren des zugrunde liegenden DBMS.  
  
 Wenn der aktuelle Benutzer eine Prozedur mit dem angegebenen Namen besitzt, werden Informationen zu dieser Prozedur zurückgegeben. Wenn *Owner*nicht angegeben wird und der aktuelle Benutzer keine Prozedur mit dem angegebenen Namen besitzt, sucht **sp_sproc_columns** nach einer Prozedur mit dem angegebenen Namen, die im Besitz des Daten Bank Besitzers ist. Sofern die Prozedur vorhanden ist, werden Information zu deren Spalten zurückgegeben.  
  
`[ @procedure_qualifier = ] 'qualifier'`Der Name des Prozedur Qualifizierers. *qualifier* ist vom Datentyp **sysname**und hat den Standardwert NULL. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (*Qualifier.Owner.Name*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entspricht dieser Parameter dem Datenbanknamen. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar.  
  
`[ @column_name = ] 'column_name'`Bei handelt es sich um eine einzelne Spalte, die verwendet wird, wenn nur eine Spalte mit Katalog Informationen gewünscht wird. *column_name* ist vom Datentyp **nvarchar (** 384 **)** und hat den Standardwert NULL. Wenn *column_name* weggelassen wird, werden alle Spalten zurückgegeben. Mustervergleiche mit Platzhalterzeichen werden unterstützt. Für eine optimale Interoperabilität sollte der Gatewayclient nur einen ISO-Standardmustervergleich voraussetzen (die Platzhalterzeichen % und _).  
  
`[ @ODBCVer = ] 'ODBCVer'`Die verwendete ODBC-Version. *ODBCVer* ist vom Datentyp **int**. der Standardwert ist 2. dieser gibt ODBC-Version 2,0 an. Weitere Informationen zu den Unterschieden zwischen ODBC-Version 2,0 und ODBC, Version 3,0, finden Sie in der ODBC **sqlprocedurecolenns** -Spezifikation für ODBC, Version 3,0  
  
`[ @fUsePattern = ] 'fUsePattern'`Bestimmt, ob die Zeichen Unterstrich (_), Prozentzeichen (%) und eckige Klammern ([]) als Platzhalter Zeichen interpretiert werden. Gültige Werte sind 0 (Mustervergleich ist deaktiviert) und 1 (Mustervergleich ist aktiviert). *fUsePattern* ist vom Datentyp **bit**. Der Standardwert ist 1.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**PROCEDURE_QUALIFIER**|**sysname**|Der Name des Prozedurqualifizierers. Diese Spalte kann NULL enthalten.|  
|**PROCEDURE_OWNER**|**sysname**|Der Name des Prozedurbesitzers. Diese Spalte gibt immer einen Wert zurück.|  
|**PROCEDURE_NAME**|**nvarchar (** 134 **)**|Der Name der Prozedur. Diese Spalte gibt immer einen Wert zurück.|  
|**COLUMN_NAME**|**sysname**|Der Spaltenname für jede Spalte der zurückgegebenen **table_name** . Diese Spalte gibt immer einen Wert zurück.|  
|**COLUMN_TYPE**|**smallint**|Dieses Feld gibt immer einen Wert zurück:<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE|  
|**DATA_TYPE**|**smallint**|Ein ganzzahliger Code für einen ODBC-Datentyp. Wenn dieser Datentyp keinem ISO-Datentyp zugeordnet werden kann, lautet der Wert NULL. Der Name des systemeigenen Datentyps wird in der **TYPE_NAME** Spalte zurückgegeben.|  
|**TYPE_NAME**|**sysname**|Die Zeichenfolgendarstellung des Datentyps. Es handelt sich um die DBMS-spezifische Darstellung des Datentypnamens.|  
|**Präziser**|**int**|Die Anzahl von signifikanten Stellen. Der Rückgabewert für die **Genauigkeits** Spalte ist in Basis 10.|  
|**LENGTH**|**int**|Die Übertragungsgröße der Daten.|  
|**Migen**|**smallint**|Die Anzahl der Ziffern rechts vom Dezimalzeichen|  
|**RADIX**|**smallint**|Die Basis für die Darstellung numerischer Datentypen.|  
|**Werte zulässt**|**smallint**|Gibt die NULL-Zulässigkeit an:<br /><br /> 1 = Datentyp mit NULL-Werten ist zulässig.<br /><br /> 0 = NULL-Werte sind nicht zulässig.|  
|**HINWEISE**|**varchar (** 254 **)**|Beschreibung der Prozedurspalte. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt für diese Spalte keinen Wert zurück.|  
|**COLUMN_DEF**|**nvarchar (** 4000 **)**|Standardwert der Spalte|  
|**SQL_DATA_TYPE**|**smallint**|Der Wert des SQL-Datentyps, wie er im **Type** -Feld des Deskriptors angezeigt wird. Diese Spalte ist mit Ausnahme der Datentypen **DateTime** und ISO **Interval** identisch mit der Spalte **data_type** . Diese Spalte gibt immer einen Wert zurück.|  
|**SQL_DATETIME_SUB**|**smallint**|Wenn **SQL_DATA_TYPE** den Wert **SQL_DATETIME** oder **SQL_INTERVAL** aufweist, enthält diese Spalte den Subcode für **datetime** ISO **interval**. Für andere Datentypen als **DateTime** -und ISO- **Intervalle**ist dieses Feld NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Maximale Länge in Bytes für eine **Zeichen** -oder **Binär** Datentyp Spalte. Bei allen anderen Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|**ORDINAL_POSITION**|**int**|Die Position einer Spalte innerhalb der Tabelle. Die erste Spalte in der Tabelle ist "1". Diese Spalte gibt immer einen Wert zurück.|  
|**IS_NULLABLE**|**varchar (254)**|NULL-Zulässigkeit der Spalte in der Tabelle. Die NULL-Zulässigkeit wird gemäß den ISO-Regeln bestimmt. Ein DBMS nach ISO kann keine leere Zeichenfolge zurückgeben.<br /><br /> YES, wenn die Spalte NULL-Werte einschließen kann. NO, wenn die Spalte keine NULL-Werte einschließen kann.<br /><br /> Die Spalte gibt eine leere Zeichenfolge zurück, wenn die NULL-Zulässigkeit unbekannt ist.<br /><br /> Der für diese Spalte zurückgegebene Wert ist ein anderer als der für die NULLABLE-Spalte zurückgegebene Wert.|  
|**SS_DATA_TYPE**|**tinyint**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp, der von erweiterten gespeicherten Prozeduren verwendet wird. Weitere Informationen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_sproc_columns** entspricht **sqlprocedurecolrens** in ODBC. Die zurückgegebenen Ergebnisse werden nach **PROCEDURE_QUALIFIER**, **PROCEDURE_OWNER**, **procedure_name**und der Reihenfolge sortiert, in der die Parameter in der Prozedur Definition angezeigt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Katalog Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
