---
title: Funktionen, die Zeichenfolgenparameter akzeptieren | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], string parameters
- ODBC desktop database drivers [ODBC], string parameters
- Jet-based ODBC drivers [ODBC], string parameters
- functions [ODBC], string parameters
- string parameters [ODBC]
ms.assetid: 869b8421-f71e-4dfd-adce-691bd3012b16
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01d0f143c72f57e946f7fe2bf52a50910d4e56aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286300"
---
# <a name="functions-accepting-string-parameters"></a>Funktionen, die Zeichenfolgenparameter akzeptieren
Alle Funktionen, die Zeichenfolgenparameter annehmen, werden in Unicode konvertiert. (Die Form "W" der Funktion wird exportiert.) Die Anzahl der Bytes wird in die Anzahl der Zeichen für die entsprechenden ODBC-APIs konvertiert. Dies gilt für folgende Funktionen:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLColAttributes**  
  
-   **SQLDescribeCol**  
  
-   **SQLError** (ersetzt durch **SQLGetDiagField**)  
  
-   **SQLExecDirect**  
  
-   **SQLGetCursorName**  
  
-   **SQLSetCursorName**  
  
-   **'SQLGetStmtAttr'**  
  
-   **SQLGetInfo**  
  
-   **SQLGetStmtOption** (wird **SQLGetStmtAttr**)  
  
-   **SQLSetStmtOption** (wird **SQLSetStmtAttr**)  
  
-   **SQLGetConnectOption**  
  
-   **SQLSetConnectOption**  
  
-   **SQLGetTypeInfo**  
  
-   **'SQLStatistics'**  
  
-   **SQLTables**  
  
-   **SQLNativeSQL**  
  
-   **'SQLSpecialColumns'**  
  
-   **ConfigDSNEx**  
  
-   **ConfigDSN**
