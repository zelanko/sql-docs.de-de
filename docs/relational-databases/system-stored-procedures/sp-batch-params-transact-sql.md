---
description: sp_batch_params (Transact-SQL)
title: sp_batch_params (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_batch_params
- sp_batch_params_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_batch_params
ms.assetid: 7b92fe9e-e755-4b7a-8a15-822c58a813d3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d385c34f58e7796d7ed09fe5d5ba644f32a6eff1
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548295"
---
# <a name="sp_batch_params-transact-sql"></a>sp_batch_params (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt ein Rowset zurück, das Informationen zu den Parametern enthält, die in einem Batch enthalten sind [!INCLUDE[tsql](../../includes/tsql-md.md)] . **sp_batch_params** analysiert nur den angegebenen Batch und gibt Informationen zu eingebetteten Parameterwerten zurück. Hiermit wird der Batch nicht ausgeführt, und die Ausführungsumgebung wird nicht geändert.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_batch_params [ [ @tsqlbatch = ] 'tsqlbatch' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @tsqlbatch = ] 'tsqlbatch'` Ist eine Unicode-Zeichenfolge, die eine- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung oder einen Batch enthält, für die Sie die gewünschten Parameterinformationen benötigen. " *sqlbatch* " ist vom Datentyp **nvarchar (max)** oder kann implizit in **nvarchar (max)** konvertiert werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**PARAMETER_NAME**|**sysname**|Name des Parameters, den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Batch gefunden hat|  
|**COLUMN_TYPE**|**smallint**|Dieses Feld gibt einen der folgenden Werte zurück:<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE<br /><br /> Diese Spalte hat immer den Wert 0.|  
|**DATA_TYPE**|**smallint**|Der Datentyp des Parameters (ein ganzzahliger Code für einen ODBC-Datentyp). Wenn dieser Datentyp keinem ISO-Datentyp zugeordnet werden kann, lautet der Wert NULL. Der Name des systemeigenen Datentyps wird in der **TYPE_NAME** Spalte zurückgegeben. Dieser Wert ist immer NULL.|  
|**TYPE_NAME**|**sysname**|Die Zeichenfolgendarstellung des Datentyps gemäß der Darstellung durch das zugrunde liegende DBMS. Dieser Wert ist NULL.|  
|**PRECISION**|**int**|Die Anzahl von signifikanten Stellen. Der Rückgabewert für die **Genauigkeits** Spalte ist in Basis 10.|  
|**LENGTH**|**int**|Die Übertragungsgröße der Daten. Dieser Wert ist NULL.|  
|**Migen**|**smallint**|Die Anzahl der Ziffern rechts vom Dezimalzeichen Dieser Wert ist NULL.|  
|**RADIX**|**smallint**|Die Basis für die Darstellung numerischer Datentypen. Dieser Wert ist NULL.|  
|**Werte zulässt**|**smallint**|Gibt die NULL-Zulässigkeit an:<br /><br /> 1 = Parameterdatentyp mit NULL-Werten ist zulässig.<br /><br /> 0 = NULL-Werte sind nicht zulässig.<br /><br /> Dieser Wert ist NULL.|  
|**SQL_DATA_TYPE**|**smallint**|Der Wert des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemdatentyps, wie er im TYPE-Feld des Deskriptors angezeigt wird. Diese Spalte entspricht der **DATA_TYPE**-Spalte mit Ausnahme der **datetime**- und ISO-**interval**-Datentypen. Diese Spalte gibt immer einen Wert zurück. Dieser Wert ist NULL.|  
|**SQL_DATETIME_SUB**|**smallint**|Der **DateTime** -oder ISO- **Intervall** -Subcode, wenn der Wert von **SQL_DATA_TYPE** SQL_DATETIME oder SQL_INTERVAL ist. Bei anderen Datentypen als **datetime** und ISO **interval** ist diese Spalte NULL. Dieser Wert ist NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Maximale Länge in Bytes eines **Zeichen** -oder **Binär** Datentyp Parameters. Bei allen anderen Datentypen gibt diese Spalte einen NULL-Wert zurück. Dieser Wert ist immer NULL.|  
|**ORDINAL_POSITION**|**int**|Die Ordnungsposition des Parameters innerhalb des Batches. Wenn der Parametername mehrmals wiederholt wird, enthält diese Spalte die Ordnungszahl des ersten Vorkommens. Der erste Parameter hat die Ordnungszahl 1. Diese Spalte gibt immer einen Wert zurück.|  
  
## <a name="permissions"></a>Berechtigungen  
 Die Berechtigung zum Ausführen von **sp_batch_params** wird **Public**erteilt.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie eine Abfrage an `sp_batch_params` übergeben wird. Im Resultset wird die Liste der eingebetteten Parameterwerte aufgezählt.  
  
```  
DECLARE @SQLString nvarchar(500);  
/* Build the SQL string */  
SET @SQLString =  
     N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
     WHERE BusinessEntityID = @BusinessEntityID';  
EXECUTE sp_batch_params @SQLString;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Gewusst-wie-Themen zur Ausführung gespeicherter Prozeduren &#40;ODBC&#41;](https://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)   
 [Ausführen gespeicherter Prozeduren &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)  
  
  
