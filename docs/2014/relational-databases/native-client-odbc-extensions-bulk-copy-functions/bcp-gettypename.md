---
title: Bcp_gettypename | Microsoft-Dokumentation
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
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086810"
---
# <a name="bcpgettypename"></a>bcp_gettypename
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
|`SQLDECIMAL`|Sowohl als auch|**decimal**|  
|`SQLNUMERIC`|Sowohl als auch|**numeric**|  
|`SQLINT1`|Sowohl als auch|**tinyint**|  
|`SQLINT2`|Sowohl als auch|**smallint**|  
|`SQLINT4`|Sowohl als auch|**int**|  
|`SQLMONEY`|Sowohl als auch|**money**|  
|`SQLFLT8`|Sowohl als auch|**float**|  
|`SQLDATETIME`|Sowohl als auch|**datetime**|  
|`SQLBITN`|Sowohl als auch|**bit-null**|  
|`SQLBIT`|Sowohl als auch|**bit**|  
|`SQLBIGCHAR`|nein|**char**|  
|`SQLCHARACTER`|nein|**char**|  
|`SQLBIGVARCHAR`|nein|**varchar**|  
|`SQLVARCHAR`|nein|**varchar**|  
|`SQLTEXT`|Sowohl als auch|**text**|  
|`SQLBIGBINARY`|nein|**binary**|  
|`SQLBINARY`|nein|**Binär (Binary)**|  
|`SQLBIGVARBINARY`|nein|**varbinary**|  
|`SQLVARBINARY`|nein|**varbinary**|  
|`SQLIMAGE`|Sowohl als auch|**Bild**|  
|`SQLINTN`|Sowohl als auch|**Int null**|  
|`SQLDATETIMN`|Sowohl als auch|**datetime-null**|  
|`SQLMONEYN`|Sowohl als auch|**Money-null**|  
|`SQLFLTN`|Sowohl als auch|**float-null**|  
|`SQLAOPSUM`|Sowohl als auch|**Sum**|  
|`SQLAOPAVG`|Sowohl als auch|**Avg**|  
|`SQLAOPCNT`|Sowohl als auch|**Count**|  
|`SQLAOPMIN`|Sowohl als auch|**Min**|  
|`SQLAOPMAX`|Sowohl als auch|**Max**|  
|`SQLDATETIM4`|Sowohl als auch|**smalldatetime**|  
|`SQLMONEY4`|Sowohl als auch|**smallmoney**|  
|`SQLFLT4`|Sowohl als auch|**Real**|  
|`SQLUNIQUEID`|Sowohl als auch|**uniqueidentifier**|  
|`SQLNCHAR`|nein|**NCHAR**|  
|`SQLNVARCHAR`|nein|**Nvarchar**|  
|`SQLNTEXT`|Sowohl als auch|**Ntext**|  
|`SQLVARIANT`|Sowohl als auch|**sql_variant**|  
|`SQLINT8`|Sowohl als auch|**Bigint**|  
|`SQLCHARACTER`|Benutzerkontensteuerung|**varchar(max)**|  
|`SQLBIGCHAR`|Benutzerkontensteuerung|**varchar(max)**|  
|`SQLBIGVARCHAR`|Benutzerkontensteuerung|**varchar(max)**|  
|`SQLVARCHAR`|Benutzerkontensteuerung|**varchar(max)**|  
|`SQLBINARY`|Benutzerkontensteuerung|**varbinary(max)**|  
|`SQLBIGBINARY`|Benutzerkontensteuerung|**varbinary(max)**|  
|`SQLBIGVARBINARY`|Benutzerkontensteuerung|**varbinary(max)**|  
|`SQLVARBINARY`|Benutzerkontensteuerung|**varbinary(max)**|  
|`SQLNCHAR`|Benutzerkontensteuerung|**nvarchar(max)**|  
|`SQLNVARCHAR`|Benutzerkontensteuerung|**nvarchar(max)**|  
|`SQLXML`|Benutzerkontensteuerung|**Xml**|  
|`SQLUDT`|Sowohl als auch|**UDT**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>bcp_gettypename-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die tokenparameterwerte für Datums-/Uhrzeittypen werden in der Spalte "Typ in sqlncli.h" der Tabelle im beschrieben [Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen &#40;OLEDB- und ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). Der zurückgegebene Wert ist in der entsprechenden Zeile der Spalte "Dateispeichertyp" angegeben.  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
