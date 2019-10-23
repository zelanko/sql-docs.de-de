---
title: bcp_gettypename | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_gettypename
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4e80c1703ece500e849a8c107d858222eea45f6f
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707466"
---
# <a name="bcp_gettypename"></a>bcp_gettypename
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
|**SQLBIGCHAR**|Nein|**char**|  
|**SQLCHARACTER**|Nein|**char**|  
|**SQLBIGVARCHAR**|Nein|**varchar**|  
|**SQLVARCHAR**|Nein|**varchar**|  
|**SQLTEXT**|Sowohl als auch|**text**|  
|**SQLBIGBINARY**|Nein|**binary**|  
|**SQLBINARY**|Nein|**Binär (Binary)**|  
|**SQLBIGVARBINARY**|Nein|**Varbinary**|  
|**SQLVARBINARY**|Nein|**Varbinary**|  
|**SQLIMAGE**|Sowohl als auch|**Image**|  
|**SQLINTN**|Sowohl als auch|**int-null**|  
|**SQLDATETIMN**|Sowohl als auch|**datetime-null**|  
|**SQLMONEYN**|Sowohl als auch|**Money-NULL**|  
|**SQLFLTN**|Sowohl als auch|**float-null**|  
|**SQLAOPSUM**|Sowohl als auch|**Sum**|  
|**SQLAOPAVG**|Sowohl als auch|**Avg**|  
|**SQLAOPCNT**|Sowohl als auch|**Count**|  
|**SQLAOPMIN**|Sowohl als auch|**Min**|  
|**SQLAOPMAX**|Sowohl als auch|**Max**|  
|**SQLDATETIM4**|Sowohl als auch|**smalldatetime**|  
|**SQLMONEY4**|Sowohl als auch|**Smallmoney**|  
|**SQLFLT4**|Sowohl als auch|**Wirkliche**|  
|**SQLUNIQUEID**|Sowohl als auch|**uniqueidentifier**|  
|**SQLNCHAR**|Nein|**Nchar**|  
|**SQLNVARCHAR**|Nein|**Nvarchar**|  
|**SQLNTEXT**|Sowohl als auch|**Ntext**|  
|**SQLVARIANT**|Sowohl als auch|**sql_variant**|  
|**SQLINT8**|Sowohl als auch|**Bigint**|  
|**SQLCHARACTER**|Ja|**varchar(max)**|  
|**SQLBIGCHAR**|Ja|**varchar(max)**|  
|**SQLBIGVARCHAR**|Ja|**varchar(max)**|  
|**SQLVARCHAR**|Ja|**varchar(max)**|  
|**SQLBINARY**|Ja|**varbinary(max)**|  
|**SQLBIGBINARY**|Ja|**varbinary(max)**|  
|**SQLBIGVARBINARY**|Ja|**varbinary(max)**|  
|**SQLVARBINARY**|Ja|**varbinary(max)**|  
|**SQLNCHAR**|Ja|**nvarchar(max)**|  
|**SQLNVARCHAR**|Ja|**nvarchar(max)**|  
|**SQLXML**|Ja|**Xml**|  
|**SQLUDT**|Sowohl als auch|**UDT**|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a>bcp_gettypename-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die Tokenparameterwerte für Datums-/Uhrzeittypen werden in der Spalte "Type in sqlncli. h" der Tabelle unter [Massen Kopier Änderungen für verbesserte Datums &#40;-und Uhrzeittypen OLE DB und ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)beschrieben. Der zurückgegebene Wert ist in der entsprechenden Zeile der Spalte "Dateispeichertyp" angegeben.  
  
 Weitere Informationen finden Sie unter [Verbesserungen &#40;bei Datum und&#41;Uhrzeit (ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
