---
title: Herstellen einer Verbindung mit SQLDriverConnect | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- SQLDriverConnect function [ODBC], connecting
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: e46e959f-d3c5-4ddb-810a-107bfcb83fd2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b8285ca9fddf0e1b77ca171414e4c00b0029d110
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036505"
---
# <a name="connecting-with-sqldriverconnect"></a>Herstellen einer Verbindung mit SQLDriverConnect
**SQLDriverConnect** wird verwendet, um die Verbindung mit einer Datenquelle mithilfe einer Verbindungszeichenfolge. **SQLDriverConnect** anstelle **SQLConnect** aus den folgenden Gründen:  
  
-   Um die Anwendung, die treiberspezifische Verbindungsinformationen verwenden zu können.  
  
-   Um anzugeben, dass der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordert.  
  
-   Um eine Verbindung herstellen, ohne eine Datenquelle angeben.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Treiberspezifische Verbindungsinformationen](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [Auffordern des Benutzers zur Eingabe der Verbindungsinformationen](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [Herstellen einer Verbindung mithilfe von Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [Herstellen einer Verbindung direkt mit dem Treiber](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
