---
title: Sql_variant-Unterstützung für Datums- und Uhrzeittypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 79b4999db83063e8096abce8a8e1c4dcd5e3a6b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639858"
---
# <a name="sqlvariant-support-for-date-and-time-types"></a>sql_variant-Unterstützung für Datums- und Uhrzeittypen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In diesem Thema wird beschrieben, wie die **Sql_variant** -Datentyp unterstützt die verbesserte Datums- und Uhrzeitfunktionalität.  
  
 Das Spaltenattribut SQL_CA_SS_VARIANT_TYPE wird zur Rückgabe des C-Typs einer Variant-Ergebnisspalte verwendet. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] führt zusätzlich das Attribut sql_ca_ss_variant_sql_type eingeführt, mit dem den SQL-Typ einer variant-Ergebnisspalte im den Implementierungszeilendeskriptor (IRD) festgelegt. SQL_CA_SS_VARIANT_SQL_TYPE kann auch in Implementation Parameter Descriptor (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) verwendet werden, um den SQL-Typ eines sql_ss_time2 anzugeben oder SQL_SS_TIMESTAMPOFFSET-Parameter, der vom C-Typ SQL_C_BINARY ist mit dem Typ SQL_SS_VARIANT gebunden.  
  
 Die neuen Typen SQL_SS_TIME2 und SQL_SS_TIMESTAMPOFFSET können vom SQLColAttribute festgelegt werden. SQL_CA_SS_VARIANT_SQL_TYPE kann durch SQLGetDescField zurückgegeben werden.  
  
 Für Ergebnisspalten konvertiert der Treiber Daten von Variant- zu Datum-/Uhrzeit-Typen. Weitere Informationen finden Sie unter [Konvertierungen von SQL-in C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Wenn Spalten an SQL_C_BINARY gebunden werden, muss die Pufferlänge so groß sein, dass der Puffer die dem SQL-Typ entsprechende Struktur aufnehmen kann.  
  
 Für die SQL_SS_TIME2 und SQL_SS_TIMESTAMPOFFSET-Parameter konvertiert der Treiber C-Werte in **Sql_variant** Werte, wie in der folgenden Tabelle beschrieben. Wenn ein Parameter als SQL_C_BINARY gebunden ist und der Servertyp SQL_SS_VARIANT lautet, dann wird er als Binärwert behandelt, sofern die Anwendung SQL_CA_SS_VARIANT_SQL_TYPE nicht auf einen anderen SQL-Typ festgelegt hat. In diesem Fall hat QL_CA_SS_VARIANT_SQL_TYPE Vorrang; d. h. wenn SQL_CA_SS_VARIANT_SQL_TYPE festgelegt wurde, wird damit das Standardverhalten überschrieben, wonach der SQL-Varianttyp vom C-Typ abgeleitet wird.  
  
|C-Typ|Servertyp|Kommentare|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_TINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_STINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SSHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_USHORT|ssNoversion|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_LONG|ssNoversion|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SLONG|ssNoversion|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_ULONG|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SBIGINT|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_FLOAT|REAL|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_DOUBLE|FLOAT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_UTINYINT|TINYINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE wird nicht festgelegt.|  
|SQL_C_BINARY|Uhrzeit|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Skalierungsgruppe wird auf SQL_DESC_PRECISION (den *DecimalDigits* Parameter **SQLBindParameter**).|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Skalierungsgruppe wird auf SQL_DESC_PRECISION (den *DecimalDigits* Parameter **SQLBindParameter**).|  
|SQL_C_TYPE_DATE|date|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Skalierungsgruppe wird auf SQL_DESC_PRECISION (den *DecimalDigits* Parameter **SQLBindParameter**).|  
|SQL_C_NUMERIC|Decimal|Precision wird auf SQL_DESC_PRECISION festgelegt (die *ColumnSize* Parameter **SQLBindParameter**).<br /><br /> Skalierungsgruppe auf SQL_DESC_SCALE (den *DecimalDigits* -Parameter von SQLBindParameter).|  
|SQL_C_SS_TIME2|Uhrzeit|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
