---
title: SQLGetTypeInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc2287678e7fd3e481c3eaf1d33af64e9ea7dad8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48186080"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber-Berichte, die die zusätzliche Spalte USERTYPE im Resultset von Satz `SQLGetTypeInfo`. USERTYPE gibt die DB-Library-Datentypdefinition aus und ist für Entwickler nützlich, die bestehende DB-Library-Anwendungen nach ODBC portieren.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] behandelt die Identität als Attribut, wohingegen ODBC die Identität als Datentyp behandelt. Zum Auflösen dieser fehlenden Übereinstimmung `SQLGetTypeInfo` gibt die Datentypen zurück: **Intidentity**, **Smallintidentity**, **Tinyintidentity**, **Decimalidentity** , und **Numericidentity**. Die `SQLGetTypeInfo` Resultsetspalte auto_unique_value enthält, gibt den Wert "true" für diese Datentypen.  
  
 Für **Varchar**, **Nvarchar** und **Varbinary**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber weiterhin 8000, 4000 bzw. 8000 bzw. für die COLUMN_SIZE meldet der Wert, obwohl es eigentlich unbegrenzt ist. Damit soll die Rückwärtskompatibilität sichergestellt werden.  
  
 Für die **Xml** -Datentyp, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber meldet SQL_SS_LENGTH_UNLIMITED für COLUMN_SIZE aus, um eine unbegrenzte Größe anzugeben.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo und Tabellenwertparameter  
 Der Tabellentyp für Tabellenwertparameter ist effektiv Metatyp, d. h. einen Typ verwendet, um andere Typen definieren. Aus diesem Grund muss er nicht über SQLGetTypeInfo verfügbar gemacht werden. Anwendungen müssen SQLTables, anstatt SQLGetTypeInfo, zum Abrufen von Metadaten mit Tabellenwertparametern verwendeten Tabellentypen verwenden.  
  
 Weitere Informationen zum Abrufen von Metadaten für Tabellenwertparameter, finden Sie unter [Anweisungsattribute, Parameter Affect Table-Valued](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>SQLGetTypeInfo-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die zurückgegebenen Werte für Datum/Uhrzeit-Typen, finden Sie unter [Katalogmetadaten](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>SQLGetTypeInfo-Unterstützung für große CLR-UDTs  
 `SQLGetTypeInfo` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLGetTypeInfo-Funktion](http://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
