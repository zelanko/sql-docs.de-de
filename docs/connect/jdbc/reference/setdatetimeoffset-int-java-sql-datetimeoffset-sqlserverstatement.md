---
description: setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
title: setDateTimeOffset(int, java.sql.DateTimeOffset) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 219e9a2b275065af96c39d0b66094297e427aa40
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431992"
---
# <a name="setdatetimeoffsetint-javasqldatetimeoffset-sqlserverstatement"></a>setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf den angegebenen DateTimeOffset-Wert fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setDateTimeOffset(int parameterIndex, DateTimeOffset dateTime)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterIndex*  
  
 Der Index der festzulegenden Spalte.  
  
 *dateTimeOffset*  
  
 Ein DateTimeOffset-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Das DateTimeOffset-Format lautet "YYYY-MM-DD HH-MM-SS[.nnnnnnn] [+][-] HH:MM". Verwenden Sie die folgende Tabelle als Referenz.  
  
|SQL-Typ|Einfügen|  
|--------------|------------|  
|datetime|Kann nur Folgendes einfügen: "YYYY-MM-DD hh:mm:ss[.nnn]"|  
|smalldatetime|Kann nur Folgendes einfügen: "YYYY-MM-DD hh:mm:ss"|  
|Time|Kann nur Folgendes einfügen: "hh:mm:ss[.nnnnnnn]"|  
|Datum|Kann nur Folgendes einfügen: "YYYY-MM-DD"|  
|DateTime2|Kann nur Folgendes einfügen: "YYYY-MM-DD hh:mm:ss[.nnnnnnn]"|  
  
## <a name="see-also"></a>Weitere Informationen  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
