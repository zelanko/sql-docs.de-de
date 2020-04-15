---
title: Herstellen einer Verbindung mit SQLDriverConnect | Microsoft Docs
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
ms.openlocfilehash: 6cd95364d8a5316a50d9f55616236a8677bf99e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299070"
---
# <a name="connecting-with-sqldriverconnect"></a>Herstellen einer Verbindung mit SQLDriverConnect
**SQLDriverConnect** wird verwendet, um mithilfe einer Verbindungszeichenfolge eine Verbindung mit einer Datenquelle herzustellen. **SQLDriverConnect** wird aus den folgenden Gründen anstelle von **SQLConnect** verwendet:  
  
-   Damit die Anwendung treiberspezifische Verbindungsinformationen verwendet.  
  
-   Um anzugeben, dass der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordert.  
  
-   So stellen Sie eine Verbindung her, ohne eine Datenquelle anzugeben.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Treiberspezifische Verbindungsinformationen](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [Aufforderung an Benutzer zur Eingabe von Verbindungsinformationen](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [Herstellen einer Verbindung mithilfe von Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [Herstellen einer Verbindung direkt mit Treibern](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
