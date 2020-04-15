---
title: Treiberspezifische Typen - Daten, Deskriptor, Informationen, Diagnose | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver-specific diagnostic values [ODBC]
- diagnostic information [ODBC], driver-specific values
- ODBC drivers [ODBC], driver-specific diagnostic values
ms.assetid: ad4c76d3-5191-4262-b47c-5dd1d19d1154
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19bb2dd113fbeae871892ea510713c638c886e5a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305765"
---
# <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute
Treiber können treiberspezifische Werte für Folgendes zuweisen:  
  
-   **SQL-Datentypindikatoren** Diese werden in *ParameterType* in **SQLBindParameter** und in *DataType* in **SQLGetTypeInfo** verwendet und von **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLGetTypeInfo**, **SQLDescribeParam**, **SQLProcedureColumns**und **SQLSpecialColumns**zurückgegeben.  
  
-   **Deskriptorfelder** Diese werden in *FieldIdentifier* in **SQLColAttribute**, **SQLGetDescField**und **SQLSetDescField**verwendet.  
  
-   **Diagnosefelder** Diese werden in *DiagIdentifier* in **SQLGetDiagField** und **SQLGetDiagRec**verwendet.  
  
-   **Informationstypen** Diese werden in *InfoType* in **SQLGetInfo**verwendet.  
  
-   **Verbindungs- und Anweisungsattribute** Diese werden in *Attribute* in **SQLGetConnectAttr**, **SQLGetStmtAttr**, **SQLSetConnectAttr**und **SQLSetStmtAttr**verwendet.  
  
 Für jedes dieser Elemente gibt es zwei Wertesätze: Werte, die für die Verwendung durch ODBC reserviert sind, und Werte, die für die Verwendung durch Treiber reserviert sind. Vor dem Implementieren treiberspezifischer Werte muss ein Treiberschreiber einen Wert für jeden treiberspezifischen Typ, jedes Feld oder jedes Attribut von Open Group anfordern. Für die Entwicklung neuer Treiber verwenden Sie den in der folgenden Tabelle beschriebenen Bereich. Der ODBC 3.8-Treiber-Manager generiert keinen Fehler, wenn ein unbekannter Wert verwendet wird, der sich nicht in dem unten beschriebenen Bereich befindet. Spätere Versionen des Treiber-Managers können jedoch einen Fehler generieren, wenn unbekannte Werte empfangen werden, die sich nicht im Bereich befinden.  
  
 Wenn einer dieser Werte an eine ODBC-Funktion übergeben wird, muss der Treiber überprüfen, ob der Wert gültig ist. Treiber geben SQLSTATE HYC00 (Optionale Funktion nicht implementiert) für treiberspezifische Werte zurück, die für andere Treiber gelten.  
  
 Ab ODBC 3.8 können Treiberautoren treiberspezifische Attribute innerhalb eines reservierten Bereichs zuweisen.  
  
> [!NOTE]  
>  Der ODBC 3.8 Treiber-Manager überprüft und erzwingt diese Bereiche weder auf Abwärtskompatibilität. Eine zukünftige Version des Treiber-Managers kann sie jedoch erzwingen.  
  
|Attributtyp|ODBC-Datentyp|Treiberspezifische Reichweitenbasis|Treiberspezifische Reichweitenbegrenzung|ODBC-Konstante für treiberspezifische Wertebereichsbasis|  
|--------------------|--------------------|---------------------------------|----------------------------------|---------------------------------------------------------|  
|SQL-Datentypindikatoren|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_SQL_TYPE_BASE|  
|Deskriptorfelder|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DESCRIPTOR_BASE|  
|Diagnosefelder|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DIAGNOSTIC_BASE|  
|Informationstypen|SQLUSMALLINT|0x4000|0x7FFF|SQL_DRIVER_INFO_TYPE_BASE|  
|Verbindungsattribute|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_CONNECT_ATTR_BASE|  
|Anweisungsattribute|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_STATEMENT_ATTR_BASE|  
  
> [!NOTE]  
>  Treiberspezifische Datentypen, Deskriptorfelder, Diagnosefelder, Informationstypen, Anweisungsattribute und Verbindungsattribute müssen in der Treiberdokumentation beschrieben werden. Wenn einer dieser Werte an eine ODBC-Funktion übergeben wird, muss der Treiber überprüfen, ob der Wert gültig ist. Treiber geben SQLSTATE HYC00 (Optionale Funktion nicht implementiert) für treiberspezifische Werte zurück, die für andere Treiber gelten.  
  
 Die Basiswerte werden definiert, um die Fahrerentwicklung zu erleichtern. Beispielsweise können treiberspezifische Diagnoseattribute im folgenden Format definiert werden:  
  
```  
SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1  
```
