---
title: SQLSetConnectOption-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetConnectOption
ms.assetid: a1b325cf-0c42-41c1-b141-b5a4fee7e708
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 757b50c7e18133e02b4cf6addaa327b2053f5439
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287470"
---
# <a name="sqlsetconnectoption-mapping"></a>SQLSetConnectOption-Zuordnung
Bei ODBC 2. die *x* -Anwendung ruft **SQLSetConnectOption** über einen ODBC 3 *. x* -Treiber auf, der Aufruf von  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 führt zu folgenden Ergebnissen:  
  
-   Wenn " *f-Option* " ein ODBC-definiertes Verbindungs Attribut angibt, das eine Zeichenfolge erfordert, ruft der Treiber-Manager  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Wenn " *f-Option* " ein ODBC-definiertes Verbindungs Attribut angibt, das einen ganzzahligen Wert von 32 Bit zurückgibt, ruft der Treiber-Manager  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Wenn " *f Option* " ein Treiber definiertes Verbindungs Attribut angibt, ruft der Treiber-Manager  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 In den vorangegangenen drei Fällen wird das *connectionHandle* -Argument auf den Wert in *hdbc*festgelegt, das *Attribut* Argument wird auf den Wert in *fOption*festgelegt, und das *ValuePtr* -Argument wird auf denselben Wert wie *vParam*festgelegt.  
  
 Da der Treiber-Manager nicht weiß, ob das vom Treiber definierte Verbindungs Attribut eine Zeichenfolge oder einen ganzzahligen 32-Bit-Wert erfordert, muss ein gültiger Wert für das *BufferLength* -Argument von **SQLSetConnectAttr**übergeben werden. Wenn der Treiber eine spezielle Semantik für Treiber definierte Connect-Attribute definiert hat und mithilfe von **SQLSetConnectOption**aufgerufen werden muss, muss **SQLSetConnectOption**unterstützt werden.  
  
 Bei ODBC 2. die *x* -Anwendung ruft **SQLSetConnectOption** auf, um eine Treiber spezifische Anweisungs Option in einem ODBC 3 *. x* -Treiber festzulegen, und die Option wurde in ODBC 2 definiert. *x* -Version des Treibers, muss für die Option im ODBC 3 *. x* -Treiber eine neue Manifest-Konstante definiert werden. Wenn die alte Manifest-Konstante beim Aufrufen von **SQLSetConnectOption**verwendet wird, ruft der Treiber-Manager **SQLSetConnectAttr** auf, wobei das **StringLength** -Argument auf 0 festgelegt ist.  
  
 Bei einem ODBC 3 *. x* -Treiber prüft der Treiber-Manager nicht mehr, ob *fOption* zwischen SQL_CONN_OPT_MIN und SQL_CONN_OPT_MAX liegt, oder ist größer als SQL_CONNECT_OPT_DRVR_START.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Festlegen von Anweisungs Optionen auf der Verbindungs Ebene  
 In ODBC 2. *x*, eine Anwendung könnte **SQLSetConnectOption** aufrufen, um eine Anweisungs Option festzulegen. Wenn dies der Fall ist, legt der Treiber die Anweisungs Option als Standard für alle Anweisungen fest, die später für diese Verbindung zugewiesen werden. Es ist Treiber definiert, ob der Treiber die Anweisungs Option für alle vorhandenen Anweisungen festlegt, die der angegebenen Verbindung zugeordnet sind.  
  
 Diese Fähigkeit wurde in ODBC 3 *. x*als veraltet markiert. ODBC 3 *. x* -Treiber müssen nur das Festlegen von ODBC 2 unterstützen. *x* -Anweisungs Attribute auf Verbindungs Ebene, wenn Sie mit ODBC 2 arbeiten möchten. *x* -Anwendungen, die dies tun. ODBC 3 *. x* -Anwendungen sollten nie Anweisungs Attribute auf Verbindungs Ebene festlegen. ODBC 3 *. x* -Anweisungs Attribute können nicht auf Verbindungs Ebene festgelegt werden, mit Ausnahme der Attribute "SQL_ATTR_METADATA_ID" und "SQL_ATTR_ASYNC_ENABLE", bei denen es sich um Verbindungs Attribute und Anweisungs Attribute handelt und die entweder auf der Verbindungs Ebene oder auf der Anweisungs Ebene festgelegt werden können.
