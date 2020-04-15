---
title: SQLSetConnectOption Zuordnung | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287470"
---
# <a name="sqlsetconnectoption-mapping"></a>SQLSetConnectOption-Zuordnung
Wenn ein ODBC 2. *x* Anwendung ruft **SQLSetConnectOption** über einen ODBC 3 *.x* Treiber auf,  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 wird wie folgt führen:  
  
-   Wenn *fOption* ein ODBC-definiertes Verbindungsattribut angibt, das eine Zeichenfolge erfordert, ruft der Treiber-Manager  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Wenn *fOption* ein ODBC-definiertes Verbindungsattribut angibt, das einen 32-Bit-Ganzzahlwert zurückgibt, ruft der Treiber-Manager  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Wenn *fOption* ein treiberdefiniertes Verbindungsattribut angibt, ruft der Treiber-Manager  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 In den ersten drei Fällen wird das *ConnectionHandle-Argument* auf den Wert in *hdbc*festgelegt, das *Attributargument* wird auf den Wert in *fOption*und das *ValuePtr-Argument* auf den gleichen Wert wie *vParam*festgelegt.  
  
 Da der Treiber-Manager nicht weiß, ob das treiberdefinierte Verbindungsattribut einen Zeichenfolgen- oder 32-Bit-Ganzzahlwert benötigt, muss er einen gültigen Wert für das *BufferLength-Argument* von **SQLSetConnectAttr**übergeben. Wenn der Treiber eine spezielle Semantik für treiberdefinierte Verbindungsattribute definiert hat und mit **SQLSetConnectOption**aufgerufen werden muss, muss er **SQLSetConnectOption**unterstützen.  
  
 Wenn ein ODBC 2. *x-Anwendung* ruft **SQLSetConnectOption auf,** um eine treiberspezifische Anweisungsoption in einem ODBC 3 *.x-Treiber* festzulegen, und die Option wurde in einem ODBC 2 definiert. *x* Version des Treibers sollte eine neue Manifestkonstante für die Option im ODBC 3 *.x-Treiber* definiert werden. Wenn die alte Manifestkonstante beim Aufruf von **SQLSetConnectOption**verwendet wird, ruft der Treiber-Manager **SQLSetConnectAttr** auf, wobei das **StringLength-Argument** auf 0 festgelegt ist.  
  
 Bei einem ODBC 3 *.x-Treiber* überprüft der Treiber-Manager nicht mehr, ob *sich fOption* zwischen SQL_CONN_OPT_MIN und SQL_CONN_OPT_MAX befindet oder größer als SQL_CONNECT_OPT_DRVR_START ist.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Festlegen von Anweisungsoptionen auf Verbindungsebene  
 In ODBC 2. *x*, eine Anwendung könnte **SQLSetConnectOption** aufrufen, um eine Anweisungsoption festzulegen. Wenn dies geschehen ist, legt der Treiber die Anweisungsoption als Standard für alle Anweisungen fest, die später für diese Verbindung zugewiesen wurden. Es ist treiberdefiniert, ob der Treiber die Anweisungsoption für alle vorhandenen Anweisungen festlegt, die der angegebenen Verbindung zugeordnet sind.  
  
 Diese Fähigkeit wurde in ODBC 3 *.x*veraltet. ODBC 3 *.x* Treiber müssen nur die Einstellung ODBC 2 unterstützen. *x* x-Anweisungsattribute auf Verbindungsebene, wenn sie mit ODBC 2 arbeiten möchten. *x* Anwendungen, die dies tun. ODBC 3 *.x-Anwendungen* sollten niemals Anweisungsattribute auf Verbindungsebene festlegen. ODBC *.x* 3 .x-Anweisungsattribute können nicht auf Verbindungsebene festgelegt werden, mit Ausnahme der SQL_ATTR_METADATA_ID- und SQL_ATTR_ASYNC_ENABLE-Attribute, die sowohl Verbindungsattribute als auch Anweisungsattribute sind und entweder auf Verbindungsebene oder auf Anweisungsebene festgelegt werden können.
