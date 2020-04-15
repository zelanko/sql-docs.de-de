---
title: Treiber-Manager&#39;Rolle im Verbindungsprozess | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], role in connection process
- connecting to data source [ODBC], driver manager
- connecting to driver [ODBC], driver manager
- ODBC driver manager [ODBC]
ms.assetid: 77c05630-5a8b-467d-b80e-c705dc06d601
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0227a4063573cb05ecaa9434605ba35f2811bd06
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305801"
---
# <a name="driver-manager39s-role-in-the-connection-process"></a>Treiber-Manager&#39;Rolle im Verbindungsprozess
Denken Sie daran, dass Anwendungen Treiberfunktionen nicht direkt aufrufen. Stattdessen rufen sie Treiber-Manager-Funktionen mit demselben Namen auf, und der Treiber-Manager ruft die Treiberfunktionen auf. In der Regel geschieht dies fast sofort. Beispielsweise ruft die Anwendung **SQLExecute** im Treiber-Manager auf, und nach einigen Fehlerüberprüfungen ruft der Treiber-Manager **SQLExecute** im Treiber auf.  
  
 Der Verbindungsprozess ist anders. Wenn die Anwendung **SQLAllocHandle** mit den Optionen SQL_HANDLE_ENV und SQL_HANDLE_DBC aufruft, weist die Funktion Handles nur im Treiber-Manager zu. Der Treiber-Manager ruft diese Funktion im Treiber nicht auf, da er nicht weiß, welchen Treiber er aufrufen soll. Wenn die Anwendung das Handle einer nicht verbundenen Verbindung zu **SQLSetConnectAttr** oder **SQLGetConnectAttr**übergibt, führt nur der Treiber-Manager die Funktion aus. Es speichert oder ruft den Attributwert aus seinem Verbindungshandle ab und gibt SQLSTATE 08003 (Verbindung nicht geöffnet) zurück, wenn ein Wert für ein Attribut abruft, das nicht festgelegt wurde und für das ODBC keinen Standardwert definiert.  
  
 Wenn die Anwendung **SQLConnect**, **SQLDriverConnect**oder **SQLBrowseConnect**aufruft, bestimmt der Treiber-Manager zuerst, welcher Treiber verwendet werden soll. Anschließend wird überprüft, ob ein Treiber derzeit auf die Verbindung geladen ist:  
  
-   Wenn kein Treiber auf die Verbindung geladen wird, überprüft der Treiber-Manager, ob der angegebene Treiber auf eine andere Verbindung in derselben Umgebung geladen wird. Ist dies nicht der Fall, lädt der Treiber den Treiber auf der Verbindung und ruft **SQLAllocHandle** im Treiber mit der Option SQL_HANDLE_ENV auf.  
  
     Der Treiber-Manager ruft dann **SQLAllocHandle** im Treiber mit der Option SQL_HANDLE_DBC auf, unabhängig davon, ob es gerade geladen wurde oder nicht. Wenn die Anwendung Verbindungsattribute festgelegt hat, ruft der Treiber-Manager **SQLSetConnectAttr** im Treiber auf. Wenn ein Fehler auftritt, gibt die Verbindungsfunktion des Treiber-Managers SQLSTATE IM006 zurück **(SQLSetConnectAttr** des Treibers ist fehlgeschlagen). Schließlich ruft der Treiber-Manager die Verbindungsfunktion im Treiber auf.  
  
-   Wenn der angegebene Treiber auf die Verbindung geladen wird, ruft der Treiber-Manager nur die Verbindungsfunktion im Treiber auf. In diesem Fall muss der Treiber sicherstellen, dass alle Verbindungsattribute auf der Verbindung ihre aktuellen Einstellungen beibehalten.  
  
-   Wenn ein anderer Treiber auf die Verbindung geladen wird, ruft der Treiber-Manager **SQLFreeHandle** im Treiber auf, um die Verbindung freizugeben. Wenn keine anderen Verbindungen vorhanden sind, die den Treiber verwenden, ruft der Treiber-Manager **SQLFreeHandle** im Treiber auf, um die Umgebung freizugeben und den Treiber zu entladen. Der Treiber-Manager führt dann die gleichen Vorgänge aus, wie wenn ein Treiber nicht auf die Verbindung geladen wird.  
  
 Der Treiber-Manager sperrt das Umgebungshandle (*henv*), bevor **SQLAllocHandle** und **SQLFreeHandle** eines Treibers aufgerufen werden, wenn *HandleType* auf **SQL_HANDLE_DBC**festgelegt ist.  
  
 Wenn die Anwendung **SQLDisconnect**aufruft, ruft der Treiber-Manager **SQLDisconnect** im Treiber auf. Der Treiber wird jedoch geladen, falls die Anwendung erneut eine Verbindung mit dem Treiber herstellt. Wenn die Anwendung **SQLFreeHandle** mit der Option SQL_HANDLE_DBC aufruft, ruft der Treiber-Manager **SQLFreeHandle** im Treiber auf. Wenn der Treiber nicht von anderen Verbindungen verwendet wird, ruft der Treiber-Manager **SQLFreeHandle** im Treiber mit der Option SQL_HANDLE_ENV auf und entlädt den Treiber.
