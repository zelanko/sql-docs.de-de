---
title: Herstellen einer Verbindung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establishing a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establishing a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f71190a8a2ca1dd8af0d28adb5531540fb1b57e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298700"
---
# <a name="establishing-a-connection"></a>Herstellen einer Verbindung
Nach dem Zuweisen von Umgebungs- und Verbindungshandles und dem Festlegen von Verbindungsattributen kann die Anwendung eine Verbindung mit der Datenquelle oder dem Treiber herstellen. Es gibt drei verschiedene Funktionen, die die Anwendung dazu verwenden kann: **SQLConnect** (Core Interface Conformance Level), **SQLDriverConnect** (Core) und **SQLBrowseConnect** (Level 1). Jeder der drei ist für die Verwendung in einem anderen Szenario konzipiert. Vor dem Herstellen einer Verbindung kann die Anwendung bestimmen, welche dieser Funktionen mit dem Von **SQLDrivers**zurückgegebenen **Schlüsselwort ConnectFunctions** unterstützt wird.  
  
> [!NOTE]  
>  Einige Treiber begrenzen die Anzahl der aktiven Verbindungen, die sie unterstützen. Eine Anwendung ruft **SQLGetInfo** mit der Option SQL_MAX_DRIVER_CONNECTIONS auf, um zu bestimmen, wie viele aktive Verbindungen ein bestimmter Treiber unterstützt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Standarddatenquelle](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Herstellen einer Verbindung mit SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Verbindungszeichenfolgen](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Herstellen einer Verbindung mit SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Herstellen einer Verbindung mit SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
