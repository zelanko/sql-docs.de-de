---
description: Funktionen, die Zeichenfolgenparameter akzeptieren
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
ms.openlocfilehash: f634e65260332851d02d2fe67302f03529a6ff7b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421854"
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
