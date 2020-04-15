---
title: Verbindungszeichenfolgen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbbb5b4672a8ea393380063887cfd77b3e910238
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299030"
---
# <a name="connection-strings"></a>Verbindungszeichenfolgen
Eine Verbindungszeichenfolge enthält Informationen, die zum Herstellen einer Verbindung verwendet werden. Eine vollständige Verbindungszeichenfolge enthält alle Informationen, die zum Herstellen einer Verbindung erforderlich sind. Die Verbindungszeichenfolge ist eine Reihe von Schlüsselwort-Wert-Paaren, die durch Semikolons getrennt sind. (Die vollständige Syntax einer Verbindungszeichenfolge finden Sie in der [SQLDriverConnect-Funktionsbeschreibung.)](../../../odbc/reference/syntax/sqldriverconnect-function.md) Die Verbindungszeichenfolge wird verwendet von:  
  
-   **SQLDriverConnect**, die die Verbindungszeichenfolge durch Interaktion mit dem Benutzer abschließt.  
  
-   **SQLBrowseConnect**, die die Verbindungszeichenfolge iterativ mit der Datenquelle abschließt.  
  
 **SQLConnect** verwendet keine Verbindungszeichenfolge. Die Verwendung von **SQLConnect** ist analog zum Herstellen einer Verbindung über eine Verbindungszeichenfolge mit genau drei Schlüsselwort-Wert-Paaren (für Datenquellenname und optional Benutzer-ID und Kennwort).
