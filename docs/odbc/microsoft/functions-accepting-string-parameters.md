---
title: Funktionen, die Zeichen folgen Parameter akzeptieren | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286300"
---
# <a name="functions-accepting-string-parameters"></a>Funktionen, die Zeichenfolgenparameter akzeptieren
Alle Funktionen, die Zeichen folgen Parameter annehmen, werden in Unicode konvertiert. (Die "W"-Form der Funktion wird exportiert.) Die Anzahl von Bytes wird in die Anzahl der Zeichen für die entsprechenden ODBC-APIs konvertiert. Dies gilt für die folgenden Funktionen:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLColAttributes**  
  
-   **SQLDescribeCol**  
  
-   **SQLError** (durch **SQLGetDiagField**ersetzt)  
  
-   **SQLExecDirect**  
  
-   **SQLGetCursorName**  
  
-   **SQLSetCursorName**  
  
-   **'SQLGetStmtAttr'**  
  
-   **SQLGetInfo**  
  
-   **SQLGetStmtOption** (wird zu **SQLGetStmtAttr**)  
  
-   **SQLSetStmtOption** (wird zu **SQLSetStmtAttr**)  
  
-   **SQLGetConnectOption**  
  
-   **SQLSetConnectOption**  
  
-   **SQLGetTypeInfo**  
  
-   **'SQLStatistics'**  
  
-   **SQLTables**  
  
-   **SQLNativeSQL**  
  
-   **'SQLSpecialColumns'**  
  
-   **Configdsnex**  
  
-   **ConfigDSN ausgeführt werden**
