---
title: 'Treiber-spezifische Typen: Daten-Deskriptor, Informationen Diagnose | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa17a5552855916798c78e0e7d371b58e58a401e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046920"
---
# <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute
Treiber können Treiber-spezifische Werte für Folgendes zuordnen:  
  
-   **SQL Data Type Indicators** dienen *ParameterType* in **SQLBindParameter** und *DataType* in **SQLGetTypeInfo** und zurückgegeben, indem **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLGetTypeInfo**,  **SQLDescribeParam**, **SQLProcedureColumns**, und **SQLSpecialColumns**.  
  
-   **Deskriptorfelder** dienen *FieldIdentifier* in **SQLColAttribute**, **SQLGetDescField**, und **SQLSetDescField**.  
  
-   **Diagnosefelder** dienen *DiagIdentifier* in **SQLGetDiagField** und **SQLGetDiagRec**.  
  
-   **Informationstypen** dienen *Informationsart* in **SQLGetInfo**.  
  
-   **Verbindungs- und Anweisungsattribute** dienen *Attribut* in **SQLGetConnectAttr**, **SQLGetStmtAttr**,  **SQLSetConnectAttr**, und **SQLSetStmtAttr**.  
  
 Für jedes dieser Elemente, es gibt zwei Sätze von Werten: Werte, die für die Verwendung von ODBC reserviert und die Werte, die für die Verwendung von Treibern reserviert. Vor der Implementierung-Treiber-spezifische Werte, muss ein Treiber Writer einen Wert für jeden Treiber-spezifischen Typ, ein Feld oder -Attribut von Open Group anfordern. Verwenden Sie für die Treiberentwicklung neuer den Bereich, in der folgenden Tabelle beschrieben. Der ODBC 3.8-Treiber-Manager generiert keine Fehler, wenn ein Unbekannter Wert, die nicht im Bereich verwendet wird unten beschrieben ist. Höhere Versionen des Treiber-Managers allerdings möglicherweise ein Fehler generiert, wenn unbekannte Werte empfangen werden, die nicht im Bereich enthalten sind.  
  
 Wenn diese Werte in eine ODBC-Funktion übergeben wird, muss der Treiber überprüfen Sie, ob der Wert gültig ist. Treiber zurückgeben SQLSTATE HYC00 (optionales Feature nicht implementiert) für treiberspezifische-Werte, die für andere Treiber gelten.  
  
 Beginnen mit der ODBC 3.8, können Treiber Writer treiberspezifischen Attribute in einem reservierten Bereich zuordnen.  
  
> [!NOTE]  
>  Der ODBC 3.8-Treiber-Manager überprüft weder erzwingt diese Bereiche für die Abwärtskompatibilität. Eine zukünftige Version des Treiber-Managers können sie jedoch erzwingen.  
  
|Attributtyp|ODBC-Datentyp|Treiberspezifische Bereich Basis|Treiberspezifische-Bereich|ODBC-Konstante für treiberspezifische Wertebereich Basis|  
|--------------------|--------------------|---------------------------------|----------------------------------|---------------------------------------------------------|  
|Indikatoren für SQL-Datentyp|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_SQL_TYPE_BASE|  
|Deskriptorfelder|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DESCRIPTOR_BASE|  
|Diagnosefelder|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DIAGNOSTIC_BASE|  
|Informationstypen|SQLUSMALLINT|0x4000|0x7FFF|SQL_DRIVER_INFO_TYPE_BASE|  
|Verbindungsattribute|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_CONNECT_ATTR_BASE|  
|Anweisungsattribute|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_STATEMENT_ATTR_BASE|  
  
> [!NOTE]  
>  Treiberspezifische Datentypen, deskriptorfelder, Diagnosefelder, Informationstypen, Anweisungsattribute und Verbindungsattribute müssen in der Treiberdokumentation beschrieben werden. Wenn diese Werte in eine ODBC-Funktion übergeben wird, muss der Treiber überprüfen Sie, ob der Wert gültig ist. Treiber zurückgeben SQLSTATE HYC00 (optionales Feature nicht implementiert) für treiberspezifische-Werte, die für andere Treiber gelten.  
  
 Die Basiswerte werden definiert, um Treiberentwicklung zu erleichtern. Bestimmte diagnostische Treiberattribute können z. B. im folgenden Format definiert werden:  
  
```  
SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1  
```
