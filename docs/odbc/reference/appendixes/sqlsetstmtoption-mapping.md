---
title: SQLSetStmtOption-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad53ba3fa02107d4902c43084beadda7a420e586
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811278"
---
# <a name="sqlsetstmtoption-mapping"></a>SQLSetStmtOption-Zuordnung
Wenn eine Anwendung ruft **SQLSetStmtOption** über einen ODBC 3.*.x* Treiber, den Aufruf von  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 wird wie folgt ausgegeben:  
  
-   Wenn *fOption* kennzeichnet ein ODBC-definierten Anweisungsattribut, das eine Zeichenfolge, die Treiber-Manager-Aufrufe  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   Wenn *fOption* kennzeichnet ein ODBC-definierten-Anweisungsattribut, das einen 32-Bit-Ganzzahl-Wert, der Treiber-Manager ruft zurückgibt  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   Wenn *fOption* gibt eine treiberdefinierten-Anweisungsattribut, die Treiber-Manager-Aufrufe  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 In den vorherigen drei Fällen die **StatementHandle** Argument festgelegt ist, mit dem Wert im *Befehls beschäftigt*, *Attribut* Argument festgelegt ist, mit dem Wert im *fOption* , und die *ValuePtr* Argument festgelegt ist, auf den Wert als *vParam*.  
  
 Da der Treiber-Manager nicht weiß, ob das treiberdefinierten Anweisungsattribut 32-Bit-Ganzzahl-Wert oder eine Zeichenfolge erforderlich, wurde es für die Übergabe in einen gültigen Wert für die *StringLength* Argument **SQLSetStmtAttr**. Wenn der Treiber verfügt über spezielle Semantik für treiberdefinierten Anweisungsattribute definiert und mithilfe von aufgerufen werden muss, **SQLSetStmtOption**, es muss unterstützen **SQLSetStmtOption**.  
  
 Wenn eine Anwendung ruft **SQLSetStmtOption** festzulegende eine treiberspezifische-Anweisungsoption in einer ODBC 3.*.x* Treiber und die Option in einer ODBC 2. definiert wurde. *X* Version des Treibers, neue manifestkonstante sollte definiert werden, für die Option in die ODBC 3.*.x* Treiber. Wenn die alte manifestkonstante, in dem Aufruf von verwendet wird **SQLSetStmtOption**, ruft der Treiber-Manager **SQLSetStmtAttr** mit der *StringLength* Argument auf 0 festgelegt.  
  
 Wenn eine Anwendung ruft **SQLSetStmtAttr** SQL_ATTR_USE_BOOKMARKS SQL_UB_ON in einer ODBC 3. festzulegende *.x* -Treiber verwenden, das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_FIXED festgelegt ist. SQL_UB_ON ist die gleiche Konstante als SQL_UB_FIXED. Der Treiber-Manager übergibt SQL_UB_FIXED über an den Treiber. SQL_UB_FIXED veraltet in ODBC 3.*.x*, aber eine ODBC 3.*.x* Treiber muss diese für das Arbeiten mit ODBC 2. implementieren. *X* Anwendungen, die Lesezeichen mit fester Länge verwenden.  
  
 Eine ODBC 3.*.x* -Treiber verwenden, der Treiber-Manager nicht mehr überprüft, ob *Option* zwischen SQL_STMT_OPT_MIN und SQL_STMT_OPT_MAX ist, oder ist größer als SQL_CONNECT_OPT_DRVR_START.
