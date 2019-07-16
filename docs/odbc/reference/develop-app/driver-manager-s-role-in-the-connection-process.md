---
title: Treiber-Manager&#39;s-Rolle in der Verbindungsprozess | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fdc7f82059579f23c9a1a1203aee5e45c87693e9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046942"
---
# <a name="driver-manager39s-role-in-the-connection-process"></a>Treiber-Manager&#39;s-Rolle in der Verbindungsprozess
Denken Sie daran, dass Anwendungen Treiberfunktionen nicht direkt aufrufen. Stattdessen rufen Sie diese Treiber-Manager-Funktionen, mit dem gleichen Namen und der Treiber-Manager ruft der Treiberfunktionen. Dies geschieht normalerweise fast unmittelbar. Die Anwendung beispielsweise Aufrufe **SQLExecute** im Treiber-Manager und nach ein paar Überprüfungen auf Fehler aus, ruft der Treiber-Manager **SQLExecute** im Treiber.  
  
 Der Verbindungsprozess unterscheidet. Wenn die Anwendung ruft **SQLAllocHandle** mit den SQL_HANDLE_ENV und SQL_HANDLE_DBC auf, weist der Funktion behandelt nur im Treiber-Manager. Der Treiber-Manager ruft diese Funktion im Treiber nicht auf, da er nicht, welcher Treiber weiß für das aufrufen. Auf ähnliche Weise, wenn die Anwendung das Handle einer nicht verbundenen Verbindung mit übergibt **SQLSetConnectAttr** oder **SQLGetConnectAttr**, nur die Treiber-Manager die Funktion ausgeführt wird. Sie speichert, oder ruft den Wert des Attributs aus der Verbindung behandelt, und gibt Sie SQLSTATE 08003 (Verbindung nicht geöffnet) zurück, beim Abrufen eines Werts für ein Attribut, das nicht festgelegt wurde und für welche ODBC definiert keinen Standardwert.  
  
 Wenn die Anwendung ruft **SQLConnect**, **SQLDriverConnect**, oder **SQLBrowseConnect**, bestimmt der Treiber-Manager zuerst, den zu verwendenden Treiber. Es wird dann überprüft, um zu bestimmen, ob ein Treiber für die Verbindung derzeit geladen wird:  
  
-   Wenn für die Verbindung keine Treiber geladen wurde, überprüft der Treiber-Manager an, ob der angegebene Treiber auf eine andere Verbindung in der gleichen Umgebung geladen wird. Wenn nicht der Fall, der Treiber-Manager für den Treiber auf die Verbindung und ruft lädt **SQLAllocHandle** im Treiber mit der Option SQL_HANDLE_ENV auf.  
  
     Der Treiber-Manager ruft dann **SQLAllocHandle** im Treiber mit der Option SQL_HANDLE_DBC auf, und zwar unabhängig davon, ob es gerade geladen wurde. Wenn die Anwendung Verbindungsattribute festgelegt wird, ruft der Treiber-Manager **SQLSetConnectAttr** im Treiber; Wenn ein Fehler auftritt, der Treiber-Manager-Verbindungsfunktion gibt SQLSTATE IM006 (des Treibers  **SQLSetConnectAttr** Fehler). Schließlich ruft der Treiber-Manager die Verbindungsfunktion im Treiber.  
  
-   Wenn der angegebene Treiber für die Verbindung geladen wird, ruft der Treiber-Manager nur die Verbindungsfunktion im Treiber. In diesem Fall muss der Treiber sicherstellen, alle Verbindungsattribute für die Verbindung ihre aktuellen Einstellungen zu verwalten.  
  
-   Wenn für die Verbindung ein anderen Treiber geladen wird, ruft der Treiber-Manager **SQLFreeHandle** im Treiber, die Verbindung freizugeben. Wenn es keine anderen Verbindungen sind, die Treiber verwenden, ruft der Treiber-Manager **SQLFreeHandle** im Treiber auf die Umgebung kostenlos und entlädt den Treiber. Der Treiber-Manager führt dann die gleichen Vorgänge wie wenn ein Treiber für die Verbindung nicht geladen wird.  
  
 Der Treiber-Manager wird das Umgebungshandle gesperrt (*Henv*) vor dem Aufrufen des Treibers **SQLAllocHandle** und **SQLFreeHandle** beim *HandleType* nastaven NA hodnotu **SQL_HANDLE_DBC auf**.  
  
 Wenn die Anwendung ruft **SQLDisconnect**, die Treiber-Manager ruft **SQLDisconnect** im Treiber. Allerdings bleibt den Treiber geladen wird, für den Fall, dass die Anwendung an den Treiber erneut eine Verbindung herstellt. Wenn die Anwendung ruft **SQLFreeHandle** mit der Option SQL_HANDLE_DBC auf, ruft der Treiber-Manager **SQLFreeHandle** im Treiber. Wenn der Treiber nicht durch alle anderen Verbindungen verwendet wird, ruft der Treiber-Manager klicken Sie dann **SQLFreeHandle** -option in den Treiber mit der SQL_HANDLE_ENV und entlädt den Treiber.
