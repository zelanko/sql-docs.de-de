---
title: SQLSetStmtOption Zuordnung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91264cee0dfceeb7195e2bad40d1638a88e1e01a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304901"
---
# <a name="sqlsetstmtoption-mapping"></a>SQLSetStmtOption-Zuordnung
Wenn eine Anwendung **SQLSetStmtOption** über einen ODBC *3.x-Treiber* aufruft,  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 wird wie folgt führen:  
  
-   Wenn *fOption* ein ODBC-defined statement-Attribut angibt, das eine Zeichenfolge ist, ruft der Treiber-Manager  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   Wenn *fOption* ein ODBC-defined statement-Attribut angibt, das einen 32-Bit-Ganzzahlwert zurückgibt, ruft der Treiber-Manager  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   Wenn *fOption* ein treiberdefiniertes Anweisungsattribut angibt, ruft der Treiber-Manager  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 In den ersten drei Fällen wird das **StatementHandle-Argument** auf den Wert in *hstmt*festgelegt, das *Attributargument* wird auf den Wert in *fOption*und das *ValuePtr-Argument* auf den Wert als *vParam*festgelegt.  
  
 Da der Treiber-Manager nicht weiß, ob das treiberdefinierte Anweisungsattribut einen Zeichenfolgen- oder 32-Bit-Ganzzahlwert benötigt, muss er einen gültigen Wert für das *StringLength-Argument* von **SQLSetStmtAttr**übergeben. Wenn der Treiber eine spezielle Semantik für treiberdefinierte Anweisungsattribute definiert hat und mit **SQLSetStmtOption**aufgerufen werden muss, muss er **SQLSetStmtOption**unterstützen.  
  
 Wenn eine Anwendung **SQLSetStmtOption** aufruft, um eine treiberspezifische Anweisungsoption in einem ODBC *3.x-Treiber* festzulegen, und die Option in einer ODBC *2.x-Version* des Treibers definiert wurde, sollte eine neue Manifestkonstante für die Option im ODBC *3.x-Treiber* definiert werden. Wenn die alte Manifestkonstante beim Aufruf von **SQLSetStmtOption**verwendet wird, ruft der Treiber-Manager **SQLSetStmtAttr** auf, wobei das *StringLength-Argument* auf 0 festgelegt ist.  
  
 Wenn eine Anwendung **SQLSetStmtAttr** aufruft, um SQL_ATTR_USE_BOOKMARKS in einem ODBC *3.x-Treiber* auf SQL_UB_ON festzulegen, wird das Attribut SQL_ATTR_USE_BOOKMARKS-Anweisung auf SQL_UB_FIXED festgelegt. SQL_UB_ON ist die gleiche Konstante wie SQL_UB_FIXED. Der Treiber-Manager leitet SQL_UB_FIXED an den Fahrer weiter. SQL_UB_FIXED ist in ODBC *3.x*veraltet, aber ein ODBC *3.x-Treiber* muss ihn implementieren, um mit ODBC *2.x-Anwendungen* zu arbeiten, die Lesezeichen mit fester Länge verwenden.  
  
 Bei einem ODBC *3.x-Treiber* überprüft der Treiber-Manager nicht mehr, ob sich *die Option* zwischen SQL_STMT_OPT_MIN und SQL_STMT_OPT_MAX befindet oder größer als SQL_CONNECT_OPT_DRVR_START ist.
