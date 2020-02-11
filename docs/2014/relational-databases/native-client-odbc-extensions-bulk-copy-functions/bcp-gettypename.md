---
title: bcp_gettypename | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5bc7caa063d14967e576fd009a23110b9647836b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62689028"
---
# <a name="bcp_gettypename"></a>bcp_gettypename
  Gibt den SQL-Typnamen für ein angegebenes BCP-Typtoken zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *toben*  
 Ein Wert, der ein BCP-Typtoken angibt.  
  
 *Flächen*  
 Gibt an, wenn ein angefordertes Token ein max-Typ ist.  
  
## <a name="returns"></a>Rückgabe  
 Eine Zeichenfolge, die den SQL-Typnamen enthält, der dem BCP-Typ entspricht. Wenn ein ungültiger BCP-Typ angegeben wird, wird eine leere Zeichenfolge zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die BCP-Typtoken werden in der sqlncli.h-Headerdatei und der sqlncli11.lib-Bibliothek definiert.  
  
 In der unten stehenden Tabelle werden die möglichen BCP-Typen aufgeführt, mit der Angabe, ob es sich um max-Typen handelt, sowie deren erwartete Ausgabe.  
  
|BCP-Typname|MaxType|Output|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|Sie können das|**Decimal**|  
|`SQLNUMERIC`|Sie können das|**isch**|  
|`SQLINT1`|Sie können das|**tinyint**|  
|`SQLINT2`|Sie können das|**smallint**|  
|`SQLINT4`|Sie können das|**int**|  
|`SQLMONEY`|Sie können das|**money**|  
|`SQLFLT8`|Sie können das|**float**|  
|`SQLDATETIME`|Sie können das|**datetime**|  
|`SQLBITN`|Sie können das|**bit-null**|  
|`SQLBIT`|Sie können das|**bit**|  
|`SQLBIGCHAR`|Nein|**Char**|  
|`SQLCHARACTER`|Nein|**Char**|  
|`SQLBIGVARCHAR`|Nein|**varchar**|  
|`SQLVARCHAR`|Nein|**varchar**|  
|`SQLTEXT`|Sie können das|**text**|  
|`SQLBIGBINARY`|Nein|**BINARY**|  
|`SQLBINARY`|Nein|**Ärer**|  
|`SQLBIGVARBINARY`|Nein|**Varbinary**|  
|`SQLVARBINARY`|Nein|**Varbinary**|  
|`SQLIMAGE`|Sie können das|**Image**|  
|`SQLINTN`|Sie können das|**int-null**|  
|`SQLDATETIMN`|Sie können das|**datetime-null**|  
|`SQLMONEYN`|Sie können das|**money-null**|  
|`SQLFLTN`|Sie können das|**float-null**|  
|`SQLAOPSUM`|Sie können das|**Pauschalen**|  
|`SQLAOPAVG`|Sie können das|**AVG**|  
|`SQLAOPCNT`|Sie können das|**Countdown**|  
|`SQLAOPMIN`|Sie können das|**Man**|  
|`SQLAOPMAX`|Sie können das|**Max**|  
|`SQLDATETIM4`|Sie können das|**smalldatetime**|  
|`SQLMONEY4`|Sie können das|**Smallmoney**|  
|`SQLFLT4`|Sie können das|**Wirkliche**|  
|`SQLUNIQUEID`|Sie können das|**uniqueidentifier**|  
|`SQLNCHAR`|Nein|**NCHAR**|  
|`SQLNVARCHAR`|Nein|**Nvarchar**|  
|`SQLNTEXT`|Sie können das|**Ntext**|  
|`SQLVARIANT`|Sie können das|**sql_variant**|  
|`SQLINT8`|Sie können das|**Bigint**|  
|`SQLCHARACTER`|Ja|**varchar(max)**|  
|`SQLBIGCHAR`|Ja|**varchar(max)**|  
|`SQLBIGVARCHAR`|Ja|**varchar(max)**|  
|`SQLVARCHAR`|Ja|**varchar(max)**|  
|`SQLBINARY`|Ja|**varbinary(max)**|  
|`SQLBIGBINARY`|Ja|**varbinary(max)**|  
|`SQLBIGVARBINARY`|Ja|**varbinary(max)**|  
|`SQLVARBINARY`|Ja|**varbinary(max)**|  
|`SQLNCHAR`|Ja|**nvarchar(max)**|  
|`SQLNVARCHAR`|Ja|**nvarchar(max)**|  
|`SQLXML`|Ja|**Basi**|  
|`SQLUDT`|Sie können das|**UDT**|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a>bcp_gettypename-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die Tokenparameterwerte für Datums-/Uhrzeittypen werden in der Spalte "Type in sqlncli. h" der Tabelle unter [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeittypen &#40;OLE DB und ODBC-&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)beschrieben. Der zurückgegebene Wert ist in der entsprechenden Zeile der Spalte "Dateispeichertyp" angegeben.  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
