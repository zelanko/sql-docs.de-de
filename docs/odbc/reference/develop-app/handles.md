---
title: Behandelt | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d31d36f315291d6826712771d0e3b6b1d8fbc496
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139038"
---
# <a name="handles"></a>Ziehpunkte
Handles sind nicht transparenten, 32-Bit-Werten, die ein bestimmtes Element zu identifizieren. in ODBC kann dieses Element aus einer Umgebung, Verbindung, Anweisung oder Deskriptor sein. Wenn die Anwendung ruft **SQLAllocHandle**, wird der Treiber-Manager oder der Treiber erstellt ein neues Element vom angegebenen Typ und sein Handle an die Anwendung zurück. Die Anwendung weiter unten verwendet das Handle zum Identifizieren dieses Elements, beim Aufrufen von ODBC-Funktionen. Der Treiber-Manager und der Treiber verwenden das Handle, um Informationen über das Element zu suchen.  
  
 Der folgende Code verwendet beispielsweise zwei Anweisungshandles (*HstmtOrder* und *HstmtLine*) um die Anweisungen zu identifizieren, für die Resultsets von Sales erstellt Bestellungen "und" Sales Zeilennummern Order. Später wird diese Handles verwendet, um zu identifizieren, welches Resultset zum Abrufen von Daten aus.  
  
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
  
 Handles sind sinnvoll, nur für die ODBC-Komponente, die sie erstellt wurden. Das heißt, nur die Treiber-Manager interpretieren, verarbeitet der Treiber-Manager und nur ein Treiber kann eine eigene Handles interpretieren.  
  
 Nehmen wir beispielsweise an der Treiber im obigen Beispiel weist eine Struktur zum Speichern von Informationen zu einer Anweisung, und gibt den Zeiger auf diese Struktur als das Anweisungshandle zurück. Wenn die Anwendung ruft **SQLPrepare**, eine SQL-Anweisung übergibt und das Handle der Anweisung verwendet werden, damit die Zeilennummern der Bestellung. Der Treiber sendet die SQL-Anweisung mit der Datenquelle, die vorbereitet werden kann, und gibt eine Access-Plan-ID zurück. Der Treiber verwendet das Handle, um die Struktur zum Speichern dieser Bezeichner zu suchen.  
  
 Wenn die Anwendung ruft später **SQLExecute** um das Resultset der Zeilennummern für einen bestimmten Verkaufsauftrag zu generieren, übergibt er das gleiche Handle. Der Treiber verwendet das Handle, um die Access-Plan-ID aus der Struktur abrufen. Er sendet die ID mit der Datenquelle anzuweisen, die ausführen möchten.  
  
 ODBC verfügt über zwei Ebenen von Handles: Treiber-Manager-Handles und Treiber verarbeitet. Die Anwendung verwendet-Treiber-Manager verarbeitet, wenn ODBC-Funktionen aufrufen, da sie diese Funktionen im Treiber-Manager aufruft. Der Treiber-Manager verwendet dieses Handle finden Sie die entsprechenden Treiber-Handle und das Handle der Treiber beim Aufrufen der Funktion im Treiber. Ein Beispiel wie Treiber und Treiber-Manager-Handles verwendet werden, finden Sie unter [Treiber-Manager-Rolle in der Verbindungsprozess](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Es gibt zwei Ebenen von Handles ist ein Artefakt der ODBC-Architektur; in den meisten Fällen ist es nicht relevant für die Anwendung oder den Treiber. Obwohl in der Regel keinen Grund dafür vorliegt, kann für die Anwendung aus, um zu bestimmen, die Treiber-Handles durch Aufrufen von **SQLGetInfo**.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Umgebungshandles](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Anweisungshandles](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Deskriptorhandles](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Statusübergänge](../../../odbc/reference/develop-app/state-transitions.md)
