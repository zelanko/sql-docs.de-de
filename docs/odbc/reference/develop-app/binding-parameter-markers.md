---
title: Bindungsparametermarker | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- parameter markers [ODBC]
- binding parameter markers [ODBC]
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be99bc884a8baa66f3d632ee4731985f0cc85732
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306391"
---
# <a name="binding-parameter-markers"></a>Binden von Parametermarkern
Die Anwendung bindet Parameter durch Aufrufen von **SQLBindParameter**. **SQLBindParameter** bindet jeweils einen Parameter. Damit gibt die Anwendung Folgendes an:  
  
-   Die Parameternummer. Parameter werden in der SQL-Anweisung in steigender Parameterreihenfolge nummeriert, beginnend mit der Zahl 1. Obwohl es zulässig ist, eine Parameternummer anzugeben, die höher als die Anzahl der Parameter in der SQL-Anweisung ist, wird der Parameterwert ignoriert, wenn die Anweisung ausgeführt wird.  
  
-   Der Parametertyp (Eingang, Eingang/Ausgang oder Ausgang). Mit Ausnahme von Parametern in Prozeduraufrufen sind alle Parameter Eingabeparameter. Weitere Informationen finden Sie unter [Prozedurparameter](../../../odbc/reference/develop-app/procedure-parameters.md)weiter unten in diesem Abschnitt.  
  
-   Der C-Datentyp, die Adresse und die Bytelänge der Variablen, die an den Parameter gebunden ist. Der Treiber muss in der Lage sein, die Daten vom Datentyp C in den SQL-Datentyp zu konvertieren, oder es wird ein Fehler zurückgegeben. Eine Liste der unterstützten Konvertierungen finden Sie unter Konvertieren von [Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) in Anhang D: Datentypen.  
  
-   Der SQL-Datentyp, die Genauigkeit und der Maßstab des Parameters selbst.  
  
-   Die Adresse eines Längen-/Indikatorpuffers. Es stellt die Bytelänge von Binär- oder Zeichendaten bereit, gibt an, dass die Daten NULL sind, oder gibt an, dass die Daten mit **SQLPutData**gesendet werden. Weitere Informationen finden Sie unter [Verwenden von Längen-/Indikatorwerten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Der folgende Code bindet beispielsweise *SalesPerson* und *CustID* an Parameter für die Spalten SalesPerson und CustID. Da *SalesPerson* Zeichendaten mit variabler Länge enthält, gibt der Code die Bytelänge von *SalesPerson* (11) an und bindet *SalesPersonLenOrInd,* um die Bytelänge der Daten in *SalesPerson*zu enthalten. Diese Informationen sind für *CustID* nicht erforderlich, da sie ganzzahlige Daten von fester Länge enthalten.  
  
```  
SQLCHAR       SalesPerson[11];  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLUINTEGER   CustID;  
  
// Bind SalesPerson to the parameter for the SalesPerson column and  
// CustID to the parameter for the CustID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 10, 0,  
                  SalesPerson, sizeof(SalesPerson), &SalesPersonLenOrInd);  
SQLBindParameter(hstmt1, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &CustID, 0, &CustIDInd);  
  
// Set values of salesperson and customer ID and length/indicators.  
strcpy_s((char*)SalesPerson, _countof(SalesPerson), "Garcia");  
SalesPersonLenOrInd = SQL_NTS;  
CustID = 1331;  
CustIDInd = 0;  
  
// Execute a statement to get data for all orders made to the specified  
// customer by the specified salesperson.  
SQLExecDirect(hstmt1,"SELECT * FROM Orders WHERE SalesPerson=? AND CustID=?",SQL_NTS);  
```  
  
 Wenn **SQLBindParameter** aufgerufen wird, speichert der Treiber diese Informationen in der Struktur für die Anweisung. Wenn die Anweisung ausgeführt wird, verwendet sie die Informationen, um die Parameterdaten abzurufen und an die Datenquelle zu senden.  
  
> [!NOTE]  
>  In ODBC 1.0 wurden Parameter mit **SQLSetParam**gebunden. Der Treiber-Manager ordnet Aufrufe zwischen **SQLSetParam** und **SQLBindParameter**zu, abhängig von den Versionen von ODBC, die von der Anwendung und dem Treiber verwendet werden.
