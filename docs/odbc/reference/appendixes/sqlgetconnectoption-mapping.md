---
title: SQLGetConnectOption Zuordnung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8d2905bd6793d032e485183c8f553cef2cdefda3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302001"
---
# <a name="sqlgetconnectoption-mapping"></a>SQLGetConnectOption-Zuordnung
Wenn eine Anwendung **SQLGetConnectOption** über einen ODBC *3.x-Treiber* aufruft,  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 wird wie folgt abgebildet:  
  
-   Wenn *fOption* eine ODBC-definierte Verbindungsoption angibt, die eine Zeichenfolge zurückgibt, ruft der Treiber-Manager  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Wenn *fOption* eine ODBC-definierte Verbindungsoption angibt, die einen 32-Bit-Ganzzahlwert zurückgibt, ruft der Treiber-Manager  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Wenn *fOption* eine treiberdefinierte Anweisungsoption angibt, ruft der Treiber-Manager  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 In den ersten drei Fällen wird das *ConnectionHandle-Argument* auf den Wert in *hdbc*festgelegt, das *Attributargument* wird auf den Wert in *fOption*und das *ValuePtr-Argument* auf den gleichen Wert wie *pvParam*festgelegt.  
  
 Bei ODBC-definierten Zeichenfolgenverbindungsoptionen legt der Treiber-Manager das *Argument BufferLength* im Aufruf von **SQLGetConnectAttr** auf die vordefinierte maximale Länge (SQL_MAX_OPTION_STRING_LENGTH) fest. für eine Nicht-Zeichenfolgenverbindungsoption ist *BufferLength* auf 0 festgelegt.  
  
 Bei einem ODBC *3.x-Treiber* überprüft der Treiber-Manager nicht mehr, ob sich *die Option* zwischen SQL_CONN_OPT_MIN und SQL_CONN_OPT_MAX befindet oder größer als SQL_CONNECT_OPT_DRVR_START ist. Der Treiber muss die Gültigkeit der Optionswerte überprüfen.
