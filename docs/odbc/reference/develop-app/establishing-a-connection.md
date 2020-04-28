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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f71190a8a2ca1dd8af0d28adb5531540fb1b57e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298700"
---
# <a name="establishing-a-connection"></a>Herstellen einer Verbindung
Nachdem Sie Umgebungs-und Verbindungs Handles zugeordnet und Verbindungs Attribute festgelegt haben, ist die Anwendung bereit, eine Verbindung mit der Datenquelle oder dem Treiber herzustellen. Es gibt drei verschiedene Funktionen, die von der Anwendung verwendet werden können: **SQLCONNECT** (Kompatibilität der Kern Schnittstellen Konformität), **SQLDriverConnect** (Core) und **SQLBrowseConnect** (Stufe 1). Jede der drei ist für die Verwendung in einem anderen Szenario konzipiert. Vor dem Herstellen der Verbindung kann die Anwendung bestimmen, welche dieser Funktionen mit dem von **SQLDrivers**zurückgegebenen **connectfunctions** -Schlüsselwort unterstützt wird.  
  
> [!NOTE]  
>  Einige Treiber schränken die Anzahl aktiver Verbindungen ein, die Sie unterstützen. Eine Anwendung ruft **SQLGetInfo** mit der SQL_MAX_DRIVER_CONNECTIONS-Option auf, um zu bestimmen, wie viele aktive Verbindungen von einem bestimmten Treiber unterstützt werden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Standarddaten Quelle](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Herstellen einer Verbindung mit SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Verbindungs Zeichenfolgen](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Herstellen einer Verbindung mit SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Herstellen einer Verbindung mit SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
