---
title: Griffe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- handles [ODBC]
- driver handles [ODBC]
- driver manager [ODBC], handles
- handles [ODBC], about handles
ms.assetid: f663101e-a4cc-402b-b9d7-84d5e975be71
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 713c2a71ec195b75d682b97239413e98d07b5861
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300210"
---
# <a name="handles"></a>Ziehpunkte
Handles sind undurchsichtige 32-Bit-Werte, die ein bestimmtes Element identifizieren. In ODBC kann es sich bei diesem Element um eine Umgebung, eine Verbindung, eine Anweisung oder einen Deskriptor handelt. Wenn die Anwendung **SQLAllocHandle**aufruft, erstellt der Treiber-Manager oder -Treiber ein neues Element des angegebenen Typs und gibt dessen Handle an die Anwendung zurück. Die Anwendung verwendet später das Handle, um dieses Element beim Aufrufen von ODBC-Funktionen zu identifizieren. Der Treiber-Manager und der Treiber verwenden das Handle, um Informationen über das Element zu finden.  
  
 Der folgende Code verwendet z. B. zwei Anweisungshandles (*hstmtOrder* und *hstmtLine*), um die Anweisungen zu identifizieren, für die Ergebnissätze von Aufträgen und Auftragszeilennummern erstellt werden sollen. Später werden diese Handles verwendet, um zu identifizieren, aus welchem Resultset Daten abgerufen werden sollen.  
  
```  
SQLHSTMT      hstmtOrder, hstmtLine; // Statement handles.  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
SQLRETURN     rc;  
  
// Prepare the statement that retrieves line number information.  
SQLPrepare(hstmtLine, "SELECT * FROM Lines WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter in the preceding statement.  
SQLBindParameter(hstmtLine, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
               &OrderID, 0, &OrderIDInd);  
  
// Bind the result sets for the Order table and the Lines table. Bind  
// OrderID to the OrderID column in the Orders table. When each row is  
// fetched, OrderID will contain the current order ID, which will then be  
// passed as a parameter to the statement tofetch line number  
// information. Code not shown.  
  
// Create a result set of sales orders.  
SQLExecDirect(hstmtOrder, "SELECT * FROM Orders", SQL_NTS);  
  
// Fetch and display the sales order data. Code to check if rc equals  
// SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmtOrder)) != SQL_NO_DATA) {  
   // Display the sales order data. Code not shown.  
  
   // Create a result set of line numbers for the current sales order.  
   SQLExecute(hstmtLine);  
  
   // Fetch and display the sales order line number data. Code to check  
   // if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLFetch(hstmtLine)) != SQL_NO_DATA) {  
      // Display the sales order line number data. Code not shown.  
   }  
  
   // Close the sales order line number result set.  
   SQLCloseCursor(hstmtLine);  
}  
  
// Close the sales order result set.  
SQLCloseCursor(hstmtOrder);  
```  
  
 Handles sind nur für die ODBC-Komponente sinnvoll, die sie erstellt hat. Das heißt, nur der Treiber-Manager kann Driver Manager-Handles interpretieren, und nur ein Treiber kann seine eigenen Handles interpretieren.  
  
 Angenommen, der Treiber im vorherigen Beispiel weist eine Struktur zum Speichern von Informationen zu einer Anweisung zu und gibt den Zeiger auf diese Struktur als Anweisungshandle zurück. Wenn die Anwendung **SQLPrepare**aufruft, übergibt sie eine SQL-Anweisung und das Handle der Anweisung, die für Auftragszeilennummern verwendet wird. Der Treiber sendet die SQL-Anweisung an die Datenquelle, die sie vorbereitet und einen Zugriffsplanbezeichner zurückgibt. Der Treiber verwendet das Handle, um die Struktur zu finden, in der dieser Bezeichner gespeichert werden soll.  
  
 Wenn die Anwendung **später SQLExecute** aufruft, um das Resultset von Zeilennummern für einen bestimmten Auftrag zu generieren, wird dasselbe Handle übergibt. Der Treiber verwendet das Handle, um den Zugriffsplanbezeichner aus der Struktur abzurufen. Es sendet den Bezeichner an die Datenquelle, um ihm mitzuteilen, welcher Plan ausgeführt werden soll.  
  
 ODBC hat zwei Ebenen von Griffen: Driver Manager-Handles und Treibergriffe. Die Anwendung verwendet Treiber-Manager-Handles beim Aufrufen von ODBC-Funktionen, da sie diese Funktionen im Treiber-Manager aufruft. Der Treiber-Manager verwendet dieses Handle, um den entsprechenden Treibergriff zu finden, und verwendet das Treiberhandle beim Aufrufen der Funktion im Treiber. Ein Beispiel für die Verwendung von Treiber- und Treiber-Manager-Handles finden Sie unter [Rolle des Treiber-Managers im Verbindungsprozess](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Dass es zwei Ebenen von Handles gibt, ist ein Artefakt der ODBC-Architektur; in den meisten Fällen ist es weder für die Anwendung noch für den Treiber relevant. Obwohl es in der Regel keinen Grund dafür gibt, ist es für die Anwendung möglich, die Treiberhandles durch Aufrufen von **SQLGetInfo**zu bestimmen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Umgebungshandles](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Anweisungshandles](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Deskriptorhandles](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Statusübergänge](../../../odbc/reference/develop-app/state-transitions.md)
