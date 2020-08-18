---
description: Treiber-Manager-&#39;s-Rolle im Verbindungsprozess
title: Treiber-Manager-&#39;s-Rolle im Verbindungsprozess | Microsoft-Dokumentation
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
ms.openlocfilehash: 6fb4eea978604960d87ef6c5b621e5801121c5f1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483043"
---
# <a name="driver-manager39s-role-in-the-connection-process"></a>Treiber-Manager-&#39;s-Rolle im Verbindungsprozess
Beachten Sie, dass Anwendungen Treiberfunktionen nicht direkt aufzurufen. Stattdessen rufen Sie Treiber-Manager-Funktionen mit demselben Namen auf, und der Treiber-Manager ruft die Treiberfunktionen auf. Dies geschieht normalerweise fast sofort. Beispielsweise ruft die Anwendung **SQLExecute** im Treiber-Manager auf, und nach einigen Fehlerprüfungen ruft der Treiber-Manager **SQLExecute** im Treiber auf.  
  
 Der Verbindungsvorgang ist unterschiedlich. Wenn die Anwendung **sqlzugewiesene CHandle** mit den Optionen SQL_HANDLE_ENV und SQL_HANDLE_DBC aufruft, ordnet die Funktion Handles nur im Treiber-Manager zu. Der Treiber-Manager ruft diese Funktion nicht im Treiber auf, weil er nicht weiß, welcher Treiber aufgerufen werden soll. Wenn die Anwendung das Handle einer nicht verbundenen Verbindung an **SQLSetConnectAttr** oder **SQLGetConnectAttr**übergibt, wird die Funktion nur vom Treiber-Manager ausgeführt. Beim Abrufen eines Werts für ein Attribut, das nicht festgelegt wurde und für das ODBC keinen Standardwert definiert, wird SQLSTATE 08003 (Verbindung nicht geöffnet) zurückgegeben.  
  
 Wenn von der Anwendung **SQLCONNECT**, **SQLDriverConnect**oder **sqlbrowseconnetct**aufgerufen wird, bestimmt der Treiber-Manager zunächst, welcher Treiber verwendet werden soll. Anschließend wird überprüft, ob ein Treiber zurzeit auf der Verbindung geladen ist:  
  
-   Wenn kein Treiber für die Verbindung geladen wird, überprüft der Treiber-Manager, ob der angegebene Treiber auf eine andere Verbindung in derselben Umgebung geladen wird. Wenn dies nicht der Wert ist, lädt der Treiber-Manager den Treiber für die Verbindung und ruft **sqlzuweisung** im Treiber mit der SQL_HANDLE_ENV-Option auf.  
  
     Der Treiber-Manager ruft dann **sqlzugewiesene CHandle** im Treiber mit der SQL_HANDLE_DBC-Option auf, unabhängig davon, ob er soeben geladen wurde. Wenn die Anwendung Verbindungs Attribute festlegen, ruft der Treiber-Manager **SQLSetConnectAttr** im Treiber auf. Wenn ein Fehler auftritt, gibt die Verbindungsfunktion des Treiber-Managers SQLSTATE IM006 ( **SQLSetConnectAttr** des Treibers) zurück. Schließlich ruft der Treiber-Manager die Verbindungsfunktion im Treiber auf.  
  
-   Wenn der angegebene Treiber für die Verbindung geladen wird, ruft der Treiber-Manager nur die Verbindungsfunktion im Treiber auf. In diesem Fall muss der Treiber sicherstellen, dass alle Verbindungs Attribute der Verbindung die aktuellen Einstellungen beibehalten.  
  
-   Wenn ein anderer Treiber für die Verbindung geladen wird, ruft der Treiber-Manager **SQLFreeHandle** im Treiber auf, um die Verbindung freizugeben. Wenn keine anderen Verbindungen vorhanden sind, die den Treiber verwenden, ruft der Treiber-Manager **SQLFreeHandle** im Treiber auf, um die Umgebung freizugeben und den Treiber zu entladen. Der Treiber-Manager führt dann dieselben Vorgänge aus, als wenn ein Treiber nicht für die Verbindung geladen wird.  
  
 Der Treiber-Manager sperrt das Umgebungs Handle (Don*v*) vor dem Aufrufen von **sqlzuzugschandle** und **SQLFreeHandle** eines Treibers, wenn der- *Typ* auf **SQL_HANDLE_DBC**festgelegt ist.  
  
 Wenn die Anwendung **SQLDisconnect**aufruft, ruft der Treiber-Manager **SQLDisconnect** im Treiber auf. Der Treiber wird jedoch weiterhin geladen, wenn die Anwendung erneut eine Verbindung mit dem Treiber herstellt. Wenn die Anwendung **SQLFreeHandle** mit der SQL_HANDLE_DBC-Option aufruft, ruft der Treiber-Manager **SQLFreeHandle** im Treiber auf. Wenn der Treiber nicht von anderen Verbindungen verwendet wird, ruft der Treiber-Manager dann **SQLFreeHandle** im Treiber mit der SQL_HANDLE_ENV-Option auf und entlädt den Treiber.
