---
title: Herstellen einer Verbindung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7ef6f3d50382d810dd9df246c4d857d9467674f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "76941024"
---
# <a name="establishing-a-connection"></a>Herstellen einer Verbindung
Nachdem Sie Umgebungs-und Verbindungs Handles zugeordnet und Verbindungs Attribute festgelegt haben, ist die Anwendung bereit, eine Verbindung mit der Datenquelle oder dem Treiber herzustellen. Es gibt drei verschiedene Funktionen, die von der Anwendung verwendet werden können: **SQLCONNECT** (Kompatibilität der Kern Schnittstellen Konformität), **SQLDriverConnect** (Core) und **SQLBrowseConnect** (Stufe 1). Jede der drei ist für die Verwendung in einem anderen Szenario konzipiert. Vor dem Herstellen der Verbindung kann die Anwendung bestimmen, welche dieser Funktionen mit dem von **SQLDrivers**zurückgegebenen **connectfunctions** -Schlüsselwort unterstützt wird.  
  
> [!NOTE]  
>  Einige Treiber schränken die Anzahl aktiver Verbindungen ein, die Sie unterstützen. Eine Anwendung ruft **SQLGetInfo** mit der SQL_MAX_DRIVER_CONNECTIONS-Option auf, um zu bestimmen, wie viele aktive Verbindungen von einem bestimmten Treiber unterstützt werden.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Standarddatenquelle](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Herstellen einer Verbindung mit SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Verbindungszeichenfolgen](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Herstellen einer Verbindung mit SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Herstellen einer Verbindung mit SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
