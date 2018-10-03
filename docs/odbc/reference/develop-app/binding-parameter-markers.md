---
title: Binden von Parametermarkierungen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c71967bd72f7f13a725d47517cb9e66eee7da87f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645988"
---
# <a name="binding-parameter-markers"></a>Binden von Parametermarkern
Die Anwendung bindet Parameter durch den Aufruf **SQLBindParameter**. **SQLBindParameter** bindet einen Parameter zu einem Zeitpunkt. Es gibt die Anwendung Folgendes an:  
  
-   Der Parameter mit der Nummer. Parameter werden in Reihenfolge der zunehmenden Parameter in der SQL-Anweisung beginnt mit der Zahl 1 nummeriert. Während es zulässig ist, geben Sie einen Parameter mit der Nummer, die höher als die Anzahl von Parametern in der SQL-Anweisung, der Wert des Parameters wird ignoriert, wenn die Anweisung ausgeführt wird.  
  
-   Der Parametertyp (Eingabe, Eingabe/Ausgabe- oder Ausgabe). Mit Ausnahme von Parametern in Prozeduraufrufen sind alle Parameter Eingabeparameter an. Weitere Informationen finden Sie unter [Prozedurparameter](../../../odbc/reference/develop-app/procedure-parameters.md)weiter unten in diesem Abschnitt.  
  
-   Die C-Daten Typ, Adresse und Byte der Länge der Variablen, die an den Parameter gebunden werden. Der Treiber muss in der Lage, die Daten aus der C-Datentyp in der SQL-Datentyp zu konvertieren, oder ein Fehler zurückgegeben. Eine Liste der unterstützten Konvertierungen, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) in Anhang D:-Datentypen.  
  
-   Die SQL-Datentyp, Genauigkeit und Dezimalstellen des Parameters selbst.  
  
-   Die Adresse des ein Längen-/Indikatorpuffer. Es enthält-die Bytelänge der Binär-oder Zeichendatentypen, gibt an, dass die Daten NULL sind, oder gibt an, dass die Daten mit gesendet werden, **SQLPutData**. Weitere Informationen finden Sie unter [mit Längenindikator/Werten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Beispielsweise der folgende code bindet *Vertriebsmitarbeiter* und *CustID* Parametern für die Vertriebsmitarbeiter und CustID Spalten. Da *Vertriebsmitarbeiter* Zeichendaten, die eine Variable Länge aufweist, enthält der Code gibt an, die Bytelänge der *Vertriebsmitarbeiter* (11) und bindet *SalesPersonLenOrInd* auf enthalten die Bytelänge der Daten in *Vertriebsmitarbeiter*. Diese Informationen sind nicht erforderlich für *CustID* , da sie ganzzahlige Daten enthält, die feste Länge aufweist.  
  
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
  
 Wenn **SQLBindParameter** wird aufgerufen, der Treiber speichert diese Informationen in der Struktur für die Anweisung. Wenn die Anweisung ausgeführt wird, verwendet er die Informationen der Parameterdaten abgerufen und an die Datenquelle zu senden.  
  
> [!NOTE]  
>  In ODBC-1.0, Parameter gebunden waren **SQLSetParam**. Der Treiber-Manager ordnet Aufrufe zwischen **SQLSetParam** und **SQLBindParameter**, je nachdem, auf die Versionen von ODBC, die von der Anwendung und der Treiber verwendet.
