---
title: Trennen der Verbindung zu einer Datenquelle oder einem Treiber | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- disconnecting from driver [ODBC]
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
- connecting to data source [ODBC], disconnecting
- connecting to driver [ODBC], disconnecting
- ODBC drivers [ODBC], disconnecting
ms.assetid: 83dbf0bf-b400-41fb-8537-9b016050dc3c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 154a571bce3a337d539216ce89c32420ab981bd8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300460"
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Trennen der Verbindung mit einer Datenquelle oder einem Treiber
Wenn eine Anwendung mit der Verwendung einer Datenquelle fertig ist, ruft sie **SQLDisconnect**auf. **SQLDisconnect** gibt alle Anweisungen frei, die der Verbindung zugewiesen sind, und trennt den Treiber von der Datenquelle. Es wird ein Fehler zurückgegeben, wenn eine Transaktion ausgeführt wird.  
  
 Nach dem Trennen kann die Anwendung **SQLFreeHandle** aufrufen, um die Verbindung freizugeben. Nach dem Freilassen der Verbindung ist es ein Anwendungsprogrammierfehler, das Handle der Verbindung in einem Aufruf einer ODBC-Funktion zu verwenden. dies hat undefinierte, aber wahrscheinlich fatale Folgen. Wenn **SQLFreeHandle** aufgerufen wird, gibt der Treiber die Struktur frei, die zum Speichern von Informationen über die Verbindung verwendet wird.  
  
 Die Anwendung kann die Verbindung auch wiederverwenden, entweder um eine Verbindung mit einer anderen Datenquelle herzustellen oder eine erneute Verbindung mit derselben Datenquelle herzustellen. Die Entscheidung, eine Verbindung zu bleiben, anstatt die Verbindung später zu trennen und erneut herzustellen, erfordert, dass der Anwendungsschreiber die relativen Kosten jeder Option berücksichtigt. Sowohl das Herstellen einer Verbindung mit einer Datenquelle als auch die verbleibende Verbindung können je nach Verbindungsmedium relativ kostspielig sein. Bei einem korrekten Kompromiss muss die Anwendung auch Annahmen über die Wahrscheinlichkeit und den Zeitpunkt weiterer Vorgänge auf derselben Datenquelle treffen.
