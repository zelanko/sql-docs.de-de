---
title: getFunctionColumns-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e2b0e0f7-717c-48e6-bcd2-a325d938a833
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e6c25349d6fbf9495647ae73773d984dfcd269f8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67982959"
---
# <a name="getfunctioncolumns-method-sqlserverdatabasemetadata"></a>getFunctionColumns-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der System- oder Benutzerfunktionsparameter des angegebenen Katalogs sowie den Rückgabetyp ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public ResultSet getFunctionColumns(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern  
                       java.lang.String columnNamePattern)  
```  
  
#### <a name="parameters"></a>Parameter  
 *catalog*  
  
 Ein **String-Objekt**, das den Katalognamen enthält. Bei einer leeren Zeichenfolge ("") enthält das Ergebnis die Funktionen ohne einen Katalog. Bei **NULL** wird der Katalogname nicht für die Suche verwendet.  
  
 *schemaPattern*  
  
 Ein **String-Objekt**, das das Schemanamenmuster enthält. Bei einer leeren Zeichenfolge ("") enthält das Ergebnis die Funktionen ohne ein Schema. Bei **NULL** wird der Schemaname nicht für die Suche verwendet.  
  
 *functionNamePattern*  
  
 Ein **String-Objekt**, das den Namen einer Funktion enthält.  
  
 *columnNamePattern*  
  
 Ein **String-Objekt**, das den Namen eines Parameters enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getFunctionColumns-Methode wird von der getFunctionColumns-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Von dieser Methode werden nur die Funktionen und Parameter zurückgegeben, die dem angegebenen Schema, Funktions- und Parameternamen innerhalb des angegebenen Katalogs entsprechen.  
  
 Jede Zeile im Resultset enthält die folgenden Spalten für eine Parameterbeschreibung, eine Spaltenbeschreibung oder einen Rückgabetyp:  
  
|Name|type|BESCHREIBUNG|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|Der Name der Datenbank, in der die Funktion gespeichert ist.|  
|FUNCTION_SCHEM|**String**|Das Schema für die Funktion.|  
|FUNCTION_NAME|**String**|Der Name der Funktion.|  
|COLUMN_NAME|**String**|Der Name eines Parameters oder einer Spalte.|  
|COLUMN_TYPE|**short**|**Der Spaltentyp. Weist einen der folgenden Werte auf:**<br /><br /> functionColumnUnknown (0): Unbekannter Typ.<br /><br /> functionColumnIn (1): Eingabeparameter<br /><br /> functionColumnInOut (2): Eingabe-/Ausgabeparameter<br /><br /> functionColumnOut (3): Ausgabeparameter<br /><br /> functionReturn (4): Funktionsrückgabewert<br /><br /> functionColumnResult (5): Parameter oder Spalte ist eine Spalte im Resultset|  
|DATA_TYPE|**smallint**|Der SQL-Datentypwert aus „Java.sql.Types“.|  
|TYPE_NAME|**String**|Der Name des Datentyps.|  
|PRECISION|**int**|Die Gesamtanzahl von signifikanten Stellen.|  
|LENGTH|**int**|Die Länge der Daten in Bytes|  
|SCALE|**short**|Die Anzahl der Ziffern rechts vom Dezimaltrennzeichen.|  
|RADIX|**short**|Die Basis für numerische Typen.|  
|NULLABLE|**short**|Gibt an, ob der Parameter- oder Rückgabewert einen **NULL**-Wert enthalten kann.<br /><br /> **Weist einen der folgenden Werte auf:**<br /><br /> functionNoNulls (0): Ein NULL-Wert ist nicht zulässig.<br /><br /> functionNullable (1): Ein NULL-Wert ist zulässig.<br /><br /> functionNullableUnknown (2): Unbekannt|  
|ANMERKUNGEN|**String**|Die Kommentare zu einer Spalte oder einem Parameter.|  
|COLUMN_DEF|**String**|Der Standardwert der Spalte.<br /><br /> **Hinweis:** Diese Information steht in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügbar und ist gilt spezifisch für den JDBC-Treiber.|  
|SQL_DATA_TYPE|**smallint**|Diese Spalte entspricht der **DATA_TYPE**-Spalte mit Ausnahme der **datetime**- und ISO-**interval**-Datentypen.<br /><br /> **Hinweis:** Diese Information steht in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügbar und ist gilt spezifisch für den JDBC-Treiber.|  
|SQL_DATETIME_SUB|**smallint**|Wenn **SQL_DATA_TYPE** den Wert **SQL_DATETIME** oder **SQL_INTERVAL** aufweist, enthält diese Spalte den Subcode für **datetime** ISO **interval**. Bei anderen Datentypen als **datetime** und ISO **interval** ist diese Spalte NULL.<br /><br /> **Hinweis:** Diese Angabe ist in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügbar und gilt nur für den JDBC-Treiber.|  
|CHAR_OCTET_LENGTH|**int**|Die maximale Länge von binären oder zeichenbasierten Parametern oder Spalten. Für andere Datentypen ist der Wert NULL.|  
|ORDINAL_POSITION|**int**|Stellt für Eingabe- und Ausgabeparameter die Position (beginnend mit "1") dar.<br /><br /> Für Resultsetspalten handelt es sich hierbei um die Position der Spalte im Resultset. Beginn ist der Wert "1".<br /><br /> Für den Rückgabewert ist der Wert "0".|  
|IS_NULLABLE|**String**|Bestimmt die NULL-Zulässigkeit eines Parameters oder einer Spalte.<br /><br /> Es kann sich um einen der folgenden Werte handeln:<br /><br /> **JA:** Der Parameter bzw. die Spalte kann NULL-Werte aufweisen.<br /><br /> **NEIN:** Der Parameter bzw. die Spalte darf keine NULL-Werte aufweisen.<br /><br /> Leere Zeichenfolge (""): Unbekannt|  
|SS_TYPE_CATALOG_NAME|**String**|Der Name des Katalogs, der den benutzerdefinierten Typ (UDT) enthält.|  
|SS_TYPE_SCHEMA_NAME|**String**|Der Name des Schemas, der den benutzerdefinierten Typ (UDT) enthält.|  
|SS_UDT_CATALOG_NAME|**String**|Der benutzerdefinierte Typ (UDT) für den vollqualifizierten Namen.|  
|SS_UDT_SCHEMA_NAME|**String**|Der Name des Katalogs, in dem ein XML-Schemasammlungsname definiert ist. Wenn der Katalogname nicht gefunden werden kann, enthält diese Variable eine leere Zeichenfolge.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|Der Name des Schemas, in dem eine XML-Schemaauflistung definiert ist. Wenn der Schemaname nicht gefunden werden kann, handelt es sich dabei um eine leere Zeichenfolge.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|Name der XML-Schemaauflistung. Wenn der Name nicht gefunden werden kann, handelt es sich dabei um eine leere Zeichenfolge.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|Der Name des Katalogs, der den benutzerdefinierten Typ (UDT) enthält.|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|Der Name des Schemas, der den benutzerdefinierten Typ (UDT) enthält.|  
|SS_DATA_TYPE|**tinyint**|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp, der von erweiterten gespeicherten Prozeduren verwendet wird.<br /><br /> **Hinweis:** Weitere Informationen zu den Datentypen, die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „Datentypen (Transact-SQL)“.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
