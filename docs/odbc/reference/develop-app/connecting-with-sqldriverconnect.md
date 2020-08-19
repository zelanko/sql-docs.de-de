---
description: Herstellen einer Verbindung mit SQLDriverConnect
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 298461f5a1cb4758b3dc3d7bbddb1bb9f04ac577
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424812"
---
# <a name="connecting-with-sqldriverconnect"></a>Herstellen einer Verbindung mit SQLDriverConnect
**SQLDriverConnect** wird zum Herstellen einer Verbindung mit einer Datenquelle mithilfe einer Verbindungs Zeichenfolge verwendet. **SQLDriverConnect** wird aus den folgenden Gründen anstelle von **SQLCONNECT** verwendet:  
  
-   , Damit die Anwendung Treiber spezifische Verbindungsinformationen verwenden können.  
  
-   Um anzugeben, dass der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordert.  
  
-   , Um eine Verbindung herzustellen, ohne eine Datenquelle anzugeben.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Treiberspezifische Verbindungsinformationen](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [Aufforderung an Benutzer zur Eingabe von Verbindungsinformationen](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [Herstellen einer Verbindung mithilfe von Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [Herstellen einer Verbindung direkt mit Treibern](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
