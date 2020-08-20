---
description: Ziehpunkte
title: Handles | Microsoft-Dokumentation
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
ms.openlocfilehash: 6e9d2445dbbd676e8d48be519c1649d550fd89c5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465762"
---
# <a name="handles"></a>Ziehpunkte
Handles sind nicht transparente 32-Bit-Werte, die ein bestimmtes Element bezeichnen. in ODBC kann es sich bei diesem Element um eine Umgebung, eine Verbindung, eine Anweisung oder einen Deskriptor handeln. Wenn die Anwendung **sqlzugeteilt**aufruft, erstellt der Treiber-Manager oder Treiber ein neues Element vom angegebenen Typ und gibt dessen Handle an die Anwendung zurück. Die Anwendung verwendet das Handle später, um dieses Element beim Aufrufen von ODBC-Funktionen zu identifizieren. Der Treiber-Manager und der Treiber verwenden das Handle, um Informationen über das Element zu suchen.  
  
 Der folgende Code verwendet beispielsweise zwei Anweisungs Handles (*hstmtorder* und *hstmtline*), um die Anweisungen zu identifizieren, für die Resultsets von Verkaufsaufträgen und Bestell Zeilennummern erstellt werden sollen. Später werden diese Handles verwendet, um das Resultset zu identifizieren, aus dem Daten abgerufen werden sollen.  
  
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
  
 Handles sind nur für die ODBC-Komponente sinnvoll, von der Sie erstellt wurden. Das heißt, nur der Treiber-Manager kann Treiber-Manager-Handles interpretieren, und nur ein Treiber kann seine eigenen Handles interpretieren.  
  
 Nehmen wir beispielsweise an, dass der Treiber im vorherigen Beispiel eine-Struktur zum Speichern von Informationen über eine-Anweisung und den Zeiger auf diese-Struktur als Anweisungs Handle zurückgibt. Wenn die Anwendung **SQLPrepare**aufruft, übergibt Sie eine SQL-Anweisung und das Handle der Anweisung, die für Bestell Zeilennummern verwendet wird. Der Treiber sendet die SQL-Anweisung an die Datenquelle, die ihn vorbereitet und einen Zugriffs Plan Bezeichner zurückgibt. Der Treiber verwendet das Handle, um die Struktur zu suchen, in der dieser Bezeichner gespeichert werden soll.  
  
 Wenn die Anwendung später **SQLExecute** aufruft, um das Resultset von Zeilennummern für einen bestimmten Verkaufsauftrag zu generieren, übergibt Sie das gleiche handle. Der Treiber verwendet das Handle zum Abrufen des Zugriffs Plan Bezeichners aus der-Struktur. Der Bezeichner wird an die Datenquelle gesendet, um den auszuführenden Plan zu informieren.  
  
 ODBC verfügt über zwei Ebenen von Handles: Treiber-Manager-Handles und Treiber Handles. Die Anwendung verwendet Treiber-Manager-Handles beim Aufrufen von ODBC-Funktionen, da diese Funktionen im Treiber-Manager aufgerufen werden. Der Treiber-Manager verwendet dieses Handle, um das entsprechende Treiber Handle zu suchen, und verwendet das Treiber handle, wenn die Funktion im Treiber aufgerufen wird. Ein Beispiel für die Verwendung von Treiber-und Treiber-Manager-Handles finden Sie unter [Treiber-Manager-Rolle im Verbindungsprozess](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Es gibt zwei Ebenen von Handles, die ein Element der ODBC-Architektur sind; in den meisten Fällen ist es für die Anwendung oder den Treiber nicht relevant. Obwohl es in der Regel keinen Grund gibt, kann die Anwendung die Treiber Handles durch Aufrufen von **SQLGetInfo**ermitteln.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Umgebungshandles](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Anweisungshandles](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Deskriptorhandles](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Statusübergänge](../../../odbc/reference/develop-app/state-transitions.md)
