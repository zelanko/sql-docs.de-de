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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036505"
---
# <a name="connecting-with-sqldriverconnect"></a>Herstellen einer Verbindung mit SQLDriverConnect
**SQLDriverConnect** wird zum Herstellen einer Verbindung mit einer Datenquelle mithilfe einer Verbindungs Zeichenfolge verwendet. **SQLDriverConnect** wird aus den folgenden Gründen anstelle von **SQLCONNECT** verwendet:  
  
-   , Damit die Anwendung Treiber spezifische Verbindungsinformationen verwenden können.  
  
-   Um anzugeben, dass der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordert.  
  
-   , Um eine Verbindung herzustellen, ohne eine Datenquelle anzugeben.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Treiberspezifische Verbindungsinformationen](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [Aufforderung an Benutzer zur Eingabe von Verbindungsinformationen](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [Herstellen einer Verbindung mithilfe von Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [Herstellen einer Verbindung direkt mit Treibern](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
