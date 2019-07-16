---
title: Verbindungszeichenfolgen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f68a87db729df2f4a27e2766a9de60e8c75a71a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036423"
---
# <a name="connection-strings"></a>Verbindungszeichenfolgen
Eine Verbindungszeichenfolge enthält Informationen, die zum Herstellen einer Verbindung verwendet. Eine vollständige Verbindungszeichenfolge enthält alle Informationen, die zum Herstellen einer Verbindung erforderlich sind. Die Verbindungszeichenfolge ist eine Reihe von Schlüsselwort-Wert-Paaren, die durch Semikolons getrennt ein. (Die vollständige Syntax der Verbindungszeichenfolge finden Sie unter den [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) funktionsbeschreibung.) Die Verbindungszeichenfolge wird von verwendet:  
  
-   **SQLDriverConnect**, die die Verbindungszeichenfolge führt Sie durch Interaktion mit dem Benutzer.  
  
-   **SQLBrowseConnect**, die die Verbindungszeichenfolge iterativ mit der Datenquelle abgeschlossen.  
  
 **SQLConnect** verwendet eine Verbindungszeichenfolge nicht; verwenden von **SQLConnect** ist analog zum Herstellen einer Verbindung mit einer Verbindungszeichenfolge mit genau drei Schlüsselwort-Wert-Paaren (für ODBC-Datenquellenname und, optional, Benutzer-ID und Kennwort) .
