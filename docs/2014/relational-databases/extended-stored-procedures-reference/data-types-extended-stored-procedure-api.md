---
title: Datentypen (API für die erweiterte gespeicherte Prozedur) \| Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
author: rothja
ms.author: jroth
ms.openlocfilehash: 57b9c5b8929f6af33546a55e848a75e4243b4973
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050813"
---
# <a name="data-types-extended-stored-procedure-api"></a>Datentypen (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Um die API-Datentypen für erweiterte gespeicherte Prozeduren zu verwenden, schließen Sie die Headerdatei Srv.h ins Programm ein.  
  
|Datentyp|SQL Server-Datentyp|BESCHREIBUNG|  
|---------------|--------------------------|-----------------|  
|SRVBIGBINARY|`binary`|`binary`-Datentyp mit einer Länge von 0 bis 8000 Byte.|  
|SRVBIGCHAR|`char`|`character`-Datentyp mit einer Länge von 0 bis 8000 Byte.|  
|SRVBIGVARBINARY|`varbinary`|`binary`-Datentyp mit variabler Länge zwischen 0 und 8000 Byte.|  
|SRVBIGVARCHAR|`varchar`|`character`-Datentyp mit variabler Länge zwischen 0 und 8000 Byte.|  
|SRVBINARY|`binary`|`binary`-Datentyp.|  
|SRVBIT|`Bit`|`bit`-Datentyp.|  
|SRVBITN|`bit null`|`bit`-Datentyp, NULL-Werte sind zulässig.|  
|SRVCHAR|`char`|`character`-Datentyp.|  
|SRVDATETIME|`datetime`|`datetime`-Datentyp der Länge 8 Byte.|  
|SRVDATETIM4|`smalldatetime`|`smalldatetime`-Datentyp der Länge 4 Byte.|  
|SRVDATETIMN|**datetime null**|`smalldatetime`- oder `datetime`-Datentyp, NULL-Werte sind zulässig.|  
|SRVDECIMAL|`decimal`|`decimal`-Datentyp.|  
|SRVDECIMALN|`decimal null`|`decimal`-Datentyp, NULL-Werte sind zulässig.|  
|SRVFLT4|`real`|`real`-Datentyp der Länge 4 Byte.|  
|SRVFLT8|`float`|`float`-Datentyp der Länge 8 Byte.|  
|SRVFLTN|`real` &#124; `float null`|`real`- oder `float`-Datentyp, NULL-Werte sind zulässig.|  
|SRVIMAGE|`image`|`image`-Datentyp.|  
|SRVINT1|`tinyint`|`tinyint`-Datentyp der Länge 1 Byte.|  
|SRVINT2|`smallint`|`smallint`-Datentyp der Länge 2 Byte.|  
|SRVINT4|`int`|`int`-Datentyp der Länge 4 Byte.|  
|SRVINTN|`tinyint` &#124; `smallint` &#124; `int null`|`tinyint`-, `smallint`- oder `int`-Datentyp, NULL-Werte sind zulässig.|  
|SRVMONEY4|`smallmoney`|`smallmoney`-Datentyp der Länge 4 Byte.|  
|SRVMONEY|`money`|`money`-Datentyp der Länge 8 Byte.|  
|SRVMONEYN|`money` &#124; `smallmoney null`|`smallmoney`- oder `money`-Datentyp, NULL-Werte sind zulässig.|  
|SRVNCHAR|**nchar**|`character`-Unicode-Datentyp.|  
|SRVNTEXT|`ntext`|`text`-Unicode-Datentyp.|  
|SRVNUMERIC|`numeric`|`numeric`-Datentyp.|  
|SRVNUMERICN|`numeric null`|`numeric`-Datentyp, NULL-Werte sind zulässig.|  
|SRVNVARCHAR|**nvarchar**|`character`-Datentyp mit Unicode-Zeichen von variabler Länge.|  
|SRVTEXT|`text`|`text`-Datentyp.|  
|SRVVARBINARY|`varbinary`|`binary`-Datentyp mit variabler Länge.|  
|SRVVARCHAR|`varchar`|`character`-Datentyp mit variabler Länge.|  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
