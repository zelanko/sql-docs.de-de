---
title: Bcp_gettypename | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_gettypename
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 90b98b23bff869b0fbf0498669d389a7d834a84d
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39539680"
---
# <a name="bcpgettypename"></a>bcp_gettypename
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Gibt den SQL-Typnamen für ein angegebenes BCP-Typtoken zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_gettypename (  
        INT token,  
        DBBOOL fIsMaxType);  
```  
  
## <a name="arguments"></a>Argumente  
 *token*  
 Ein Wert, der ein BCP-Typtoken angibt.  
  
 *field*  
 Gibt an, wenn ein angefordertes Token ein max-Typ ist.  
  
## <a name="returns"></a>Rückgabewert  
 Eine Zeichenfolge, die den SQL-Typnamen enthält, der dem BCP-Typ entspricht. Wenn ein ungültiger BCP-Typ angegeben wird, wird eine leere Zeichenfolge zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die BCP-Typtoken werden in der sqlncli.h-Headerdatei und der sqlncli11.lib-Bibliothek definiert.  
  
 In der unten stehenden Tabelle werden die möglichen BCP-Typen aufgeführt, mit der Angabe, ob es sich um max-Typen handelt, sowie deren erwartete Ausgabe.  
  
|BCP-Typname|MaxType|Ausgabe|  
|-------------------|-------------|------------|  
|**SQLDECIMAL**|Sowohl als auch|**decimal**|  
|**SQLNUMERIC**|Sowohl als auch|**numeric**|  
|**SQLINT1**|Sowohl als auch|**tinyint**|  
|**SQLINT2**|Sowohl als auch|**smallint**|  
|**SQLINT4**|Sowohl als auch|**int**|  
|**SQLMONEY**|Sowohl als auch|**money**|  
|**SQLFLT8**|Sowohl als auch|**float**|  
|**SQLDATETIME**|Sowohl als auch|**datetime**|  
|**SQLBITN**|Sowohl als auch|**bit-null**|  
|**SQLBIT**|Sowohl als auch|**bit**|  
|**SQLBIGCHAR**|nein|**char**|  
|**SQLCHARACTER**|nein|**char**|  
|**SQLBIGVARCHAR**|nein|**varchar**|  
|**SQLVARCHAR**|nein|**varchar**|  
|**SQLTEXT**|Sowohl als auch|**text**|  
|**SQLBIGBINARY**|nein|**binary**|  
|**SQLBINARY**|nein|**Binär (Binary)**|  
|**SQLBIGVARBINARY**|nein|**varbinary**|  
|**SQLVARBINARY**|nein|**varbinary**|  
|**SQLIMAGE**|Sowohl als auch|**Bild**|  
|**SQLINTN**|Sowohl als auch|**Int null**|  
|**SQLDATETIMN**|Sowohl als auch|**datetime-null**|  
|**SQLMONEYN**|Sowohl als auch|**Money-null**|  
|**SQLFLTN**|Sowohl als auch|**float-null**|  
|**SQLAOPSUM**|Sowohl als auch|**Sum**|  
|**SQLAOPAVG**|Sowohl als auch|**Avg**|  
|**SQLAOPCNT**|Sowohl als auch|**Count**|  
|**SQLAOPMIN**|Sowohl als auch|**Min**|  
|**SQLAOPMAX**|Sowohl als auch|**Max**|  
|**SQLDATETIM4**|Sowohl als auch|**smalldatetime**|  
|**SQLMONEY4**|Sowohl als auch|**smallmoney**|  
|**SQLFLT4**|Sowohl als auch|**Real**|  
|**SQLUNIQUEID**|Sowohl als auch|**uniqueidentifier**|  
|**SQLNCHAR**|nein|**NCHAR**|  
|**SQLNVARCHAR**|nein|**Nvarchar**|  
|**SQLNTEXT**|Sowohl als auch|**Ntext**|  
|**SQLVARIANT**|Sowohl als auch|**sql_variant**|  
|**SQLINT8**|Sowohl als auch|**Bigint**|  
|**SQLCHARACTER**|Benutzerkontensteuerung|**varchar(max)**|  
|**SQLBIGCHAR**|Benutzerkontensteuerung|**varchar(max)**|  
|**SQLBIGVARCHAR**|Benutzerkontensteuerung|**varchar(max)**|  
|**SQLVARCHAR**|Benutzerkontensteuerung|**varchar(max)**|  
|**SQLBINARY**|Benutzerkontensteuerung|**varbinary(max)**|  
|**SQLBIGBINARY**|Benutzerkontensteuerung|**varbinary(max)**|  
|**SQLBIGVARBINARY**|Benutzerkontensteuerung|**varbinary(max)**|  
|**SQLVARBINARY**|Benutzerkontensteuerung|**varbinary(max)**|  
|**SQLNCHAR**|Benutzerkontensteuerung|**nvarchar(max)**|  
|**SQLNVARCHAR**|Benutzerkontensteuerung|**nvarchar(max)**|  
|**SQLXML**|Benutzerkontensteuerung|**Xml**|  
|**SQLUDT**|Sowohl als auch|**UDT**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>bcp_gettypename-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die tokenparameterwerte für Datums-/Uhrzeittypen werden in der Spalte "Typ in sqlncli.h" der Tabelle im beschrieben [Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen &#40;OLEDB- und ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). Der zurückgegebene Wert ist in der entsprechenden Zeile der Spalte "Dateispeichertyp" angegeben.  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
