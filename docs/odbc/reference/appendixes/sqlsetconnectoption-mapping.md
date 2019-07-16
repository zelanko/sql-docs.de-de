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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b512a795c3b9e2d1c6aa1c7c9e92fbc42a8c7862
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125593"
---
# <a name="sqlsetconnectoption-mapping"></a>SQLSetConnectOption-Zuordnung
Wenn eine ODBC-2. *x* Anwendungsaufrufe **SQLSetConnectOption** über einen ODBC 3. *.x* Treiber, den Aufruf von  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 wird wie folgt ausgegeben:  
  
-   Wenn *fOption* gibt ein ODBC-definierten Verbindungsattribut, das eine Zeichenfolge, die Aufrufe des Treiber-Manager erfordert  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Wenn *fOption* kennzeichnet ein ODBC-definierten Verbindungsattribut, das einen 32-Bit-Ganzzahl-Wert, der Treiber-Manager ruft zurückgibt  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Wenn *fOption* gibt ein treiberdefinierten Verbindungsattribut die Treiber-Manager-Aufrufe  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 In den vorherigen drei Fällen die *ConnectionHandle* Argument festgelegt ist, mit dem Wert im *Hdbc*, *Attribut* Argument festgelegt ist, mit dem Wert im *fOption* , und die *ValuePtr* Argument festgelegt ist, auf den gleichen Wert wie *vParam*.  
  
 Da der Treiber-Manager nicht weiß, ob das treiberdefinierten Verbindungsattribut 32-Bit-Ganzzahl-Wert oder eine Zeichenfolge erforderlich, wurde es für die Übergabe in einen gültigen Wert für die *Pufferlänge* Argument **SQLSetConnectAttr**. Wenn spezielle Semantik für den treiberdefinierten treiberdefinierten verbinden, Attribute und muss aufgerufen werden, mithilfe von **SQLSetConnectOption**, sie unterstützen muss **SQLSetConnectOption**.  
  
 Wenn eine ODBC-2. *x* Anwendungsaufrufe **SQLSetConnectOption** festzulegende eine treiberspezifische-Anweisungsoption in einer ODBC 3. *.x* Treiber und die Option in einer ODBC 2. definiert wurde. *X* Version des Treibers, neue manifestkonstante sollte definiert werden, für die Option in die ODBC 3. *.x* Treiber. Wenn die alte manifestkonstante, in dem Aufruf von verwendet wird **SQLSetConnectOption**, ruft der Treiber-Manager **SQLSetConnectAttr** mit der **StringLength** Argument auf 0 festgelegt.  
  
 Eine ODBC 3. *.x* -Treiber verwenden, der Treiber-Manager nicht mehr überprüft, ob *fOption* zwischen SQL_CONN_OPT_MIN und SQL_CONN_OPT_MAX ist, oder ist größer als SQL_CONNECT_OPT_DRVR_START.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Festlegen von Optionen auf der Verbindungsebene-Anweisung  
 In ODBC 2. *x*, eine Anwendung aufrufen kann **SQLSetConnectOption** festlegen eine Option-Anweisung. Wenn Sie fertig sind, richtet der Treiber die Option-Anweisung als Standard für alle Anweisungen, die für diese Verbindung später zugeordnet. Es wird-Treiber-definiert, ob der Treiber die Anweisung Optionssätze, die für alle vorhandenen Anweisungen, die mit der angegebenen Verbindung verknüpft ist.  
  
 Diese Funktion ist veraltet in ODBC 3. *.x*. ODBC 3. *.x* Treiber müssen unterstützen nur ODBC 2. festlegen. *X* Anweisungsattribute auf Verbindungsebene, die mit ODBC 2. arbeiten sollen. *X* Anwendungen, die dazu. ODBC 3. *.x* Anwendungen sollten auf der Verbindungsebene Anweisungsattribute festlegen. ODBC 3. *.x* Anweisungsattribute können nicht auf Verbindungsebene, mit Ausnahme von den SQL_ATTR_METADATA_ID und SQL_ATTR_ASYNC_ENABLE-Attributen, die sowohl-Verbindungsattributen und Anweisungsattribute und kann nicht festgelegt werden Legen Sie auf der Verbindungsebene oder Anweisungsebene.
