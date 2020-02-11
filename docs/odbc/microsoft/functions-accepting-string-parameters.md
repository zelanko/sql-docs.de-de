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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4165dd51437f143351835bc1739ffb8279bd04ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67952487"
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
