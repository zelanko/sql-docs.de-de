---
title: sql_variant Unterstützung für Datums-und Uhrzeit Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4dcca38ab5b7b67ca92cf35b49852bcd88437328
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705421"
---
# <a name="sql_variant-support-for-date-and-time-types"></a>sql_variant-Unterstützung für Datums- und Uhrzeittypen
  In diesem Thema wird beschrieben, in welcher Weise der `sql_variant`-Datentyp die erweiterte Datums- und Uhrzeitfunktionalität unterstützt.  
  
 Das Spaltenattribut SQL_CA_SS_VARIANT_TYPE wird zur Rückgabe des C-Typs einer Variant-Ergebnisspalte verwendet. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] wurde zusätzlich das Attribut SQL_CA_SS_VARIANT_SQL_TYPE eingeführt, mit dem der SQL-Typ einer Variant-Ergebnisspalte im IRD festgelegt wird. SQL_CA_SS_VARIANT_SQL_TYPE kann auch im IPD zur Angabe des SQL-Typs eines SQL_SS_TIME2- oder SQL_SS_TIMESTAMPOFFSET-Parameters verwendet werden, der vom C-Typ SQL_C_BINARY ist und an den Typ SQL_SS_VARIANT gebunden wurde.  
  
 Die neuen Typen SQL_SS_TIME2 und SQL_SS_TIMESTAMPOFFSET können von SQLColAttribute festgelegt werden. SQL_CA_SS_VARIANT_SQL_TYPE können von SQLGetDescField zurückgegeben werden.  
  
 Für Ergebnisspalten konvertiert der Treiber Daten von Variant- zu Datum-/Uhrzeit-Typen. Weitere Informationen finden Sie unter [Konvertierungen von SQL in C](datetime-data-type-conversions-from-sql-to-c.md). Beim Binden an SQL_C_BINARY muss die Pufferlänge groß genug sein, um die Struktur zu empfangen, die dem SQL-Typ entspricht.  
  
 Für die SQL_SS_TIME2- und SQL_SS_TIMESTAMPOFFSET-Parameter konvertiert der Treiber, wie in der nachfolgenden Tabelle beschrieben, C-Werte in `sql_variant`-Werte. Wenn ein Parameter als SQL_C_BINARY gebunden ist und der Servertyp SQL_SS_VARIANT lautet, dann wird er als Binärwert behandelt, sofern die Anwendung SQL_CA_SS_VARIANT_SQL_TYPE nicht auf einen anderen SQL-Typ festgelegt hat. In diesem Fall hat QL_CA_SS_VARIANT_SQL_TYPE Vorrang; d. h. wenn SQL_CA_SS_VARIANT_SQL_TYPE festgelegt wurde, wird damit das Standardverhalten überschrieben, wonach der SQL-Varianttyp vom C-Typ abgeleitet wird.  
  
|C-Typ|Servertyp|Kommentare|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_TINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_STINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SSHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_USHORT|INT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_LONG|INT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SLONG|INT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_ULONG|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SBIGINT|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_FLOAT|real|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_DOUBLE|float|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_UTINYINT|TINYINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE wird nicht festgelegt.|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Die Skala ist auf SQL_DESC_PRECISION (der *DecimalDigits* -Parameter von) festgelegt `SQLBindParameter` .|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Die Skala ist auf SQL_DESC_PRECISION (der *DecimalDigits* -Parameter von) festgelegt `SQLBindParameter` .|  
|SQL_C_TYPE_DATE|Datum|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Die Skala ist auf SQL_DESC_PRECISION (der *DecimalDigits* -Parameter von) festgelegt `SQLBindParameter` .|  
|SQL_C_NUMERIC|Decimal|Die Genauigkeit wird auf SQL_DESC_PRECISION (der *ColumnSize* -Parameter von) festgelegt `SQLBindParameter` .<br /><br /> Skalierungs Gruppe auf SQL_DESC_SCALE (der *DecimalDigits* -Parameter von SQLBindParameter).|  
|SQL_C_SS_TIME2|time|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datums-und Uhrzeit Verbesserungen &#40;ODBC-&#41;](date-and-time-improvements-odbc.md)  
  
  
