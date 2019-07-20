---
title: SQLSetScrollOptions-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 77a85caefadb54c3db2716c4db18b504e02da996
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342938"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions-Funktion
**Konformitäts**  
 Eingeführte Version: Konformität der ODBC 1,0-Standards: Als veraltet markiert  
  
 **Zusammenfassung**  
 In ODBC *3. x*wurde die ODBC 2,0-Funktion **SQLSetScrollOptions** durch Aufrufe von **SQLGetInfo** und **SQLSetStmtAttr**ersetzt.  
  
> [!NOTE]
>  Weitere Informationen dazu, wie der Treiber-Manager diese Funktion zuordnet, wenn eine ODBC *2. x* -Anwendung mit einem ODBC *3. x* -Treiber arbeitet, finden Sie unter [Mapping Deprecated Functions](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Anhang G: Treiber Richtlinien für die Abwärtskompatibilität.  
> 
> [!NOTE]
>  Wenn der Treiber-Manager **SQLSetScrollOptions** für eine Anwendung zuordnet, die mit einem ODBC *3. x* -Treiber arbeitet, der **SQLSetScrollOptions**nicht unterstützt, legt der Treiber-Manager die SQL_ROWSET_SIZE-Anweisungs Option fest, nicht die SQL_ATTR_ROW_ ARRAY_SIZE-Anweisungs Attribut, zum *rowsetsize* -Argument in **sqlsetscrolloption**. Daher kann **SQLSetScrollOptions** nicht von einer Anwendung verwendet werden, wenn mehrere Zeilen durch einen-Befehl von **SQLFetch** oder **SQLFetchScroll**abgerufen werden. Diese Option kann nur verwendet werden, wenn mehrere Zeilen durch einen **sqlextendebug**-Befehl abgerufen werden.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Ihre Anwendung unter einem 64-Bit-Betriebssystem ausgeführt wird, finden Sie weitere [Informationen unter ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
