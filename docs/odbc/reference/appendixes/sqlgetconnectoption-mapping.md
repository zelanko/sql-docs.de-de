---
title: SQLGetConnectOption-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d0533a0ee616d4097793eca46c7d45a269142737
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086399"
---
# <a name="sqlgetconnectoption-mapping"></a>SQLGetConnectOption-Zuordnung
Wenn eine Anwendung **SQLGetConnectOption** über einen ODBC *3. x* -Treiber aufruft, wird der Aufruf von  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 wird wie folgt zugeordnet:  
  
-   Wenn " *f-Option* " eine ODBC-definierte Verbindungs Option angibt, die eine Zeichenfolge zurückgibt, ruft der Treiber-Manager  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Wenn " *f Option* " eine ODBC-definierte Verbindungs Option angibt, die einen ganzzahligen Wert von 32 Bit zurückgibt, ruft der Treiber-Manager  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Wenn " *f Option* " eine Treiber definierte Anweisungs Option angibt, ruft der Treiber-Manager  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 In den vorangegangenen drei Fällen wird das *connectionHandle* -Argument auf den Wert in *hdbc*festgelegt, das *Attribut* Argument wird auf den Wert in *fOption*festgelegt, und das *ValuePtr* -Argument wird auf denselben Wert wie *pvParam*festgelegt.  
  
 Für ODBC-definierte Zeichen folgen-Verbindungsoptionen legt der Treiber-Manager das *BufferLength* -Argument im-Befehl auf **SQLGetConnectAttr** auf die vordefinierte maximale Länge (SQL_MAX_OPTION_STRING_LENGTH) fest. für eine nicht-Zeichen folgen-Verbindungs Option wird *BufferLength* auf 0 festgelegt.  
  
 Bei einem ODBC *3. x* -Treiber prüft der Treiber-Manager nicht mehr, ob die *Option* zwischen SQL_CONN_OPT_MIN und SQL_CONN_OPT_MAX liegt oder größer als SQL_CONNECT_OPT_DRVR_START ist. Der Treiber muss die Gültigkeit der Optionswerte überprüfen.
