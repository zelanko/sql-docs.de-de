---
title: Trennen von einer Datenquelle oder einem Treiber | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2189c0fcc65fd4192e94da140e2d55ac86826137
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706418"
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Trennen der Verbindung mit einer Datenquelle oder einem Treiber
Wenn eine Anwendung mithilfe einer Datenquelle abgeschlossen ist, ruft er **SQLDisconnect**. **SQLDisconnect** gibt alle Anweisungen, die bei der Verbindung zugeordnet sind frei und trennt den Treiber aus der Datenquelle. Es gibt einen Fehler zurück, wenn eine Transaktion ausgeführt wird.  
  
 Nach dem Trennen der Verbindung kann die Anwendung aufrufen kann **SQLFreeHandle** , die Verbindung freizugeben. Nach der Freigabe der der Verbindungs, ist es ein anwendungsprogrammierungsfehler Fehler Handle für die Verbindung in einem Aufruf von einer ODBC-Funktion zu verwenden. Dies ist also nicht definierte, aber wahrscheinlich schwerwiegende Folgen. Wenn **SQLFreeHandle** aufgerufen wird, wird der Treiberversionen, die die Struktur, die zum Speichern von Informationen über die Verbindung verwendet.  
  
 Die Anwendung kann auch wiederverwenden, die Verbindung entweder um eine Verbindung mit einer anderen Datenquelle herstellen oder die Verbindung mit der gleichen Datenquelle wiederherstellen. Die Entscheidung, im Gegensatz zu trennen und erneut eine Verbindung herzustellen höher verbunden bleiben erfordert, dass der Autor der Anwendung die relativen Kosten der einzelnen Optionen berücksichtigen. Herstellen einer Verbindung mit einer Datenquelle, sowohl Bestehens der Verbindung können je nach Verbindungsmedium relativ kostspielig sein. Bei der Erstellung einer Nachteile, muss die Anwendung auch Annahmen über die Wahrscheinlichkeit und die zeitliche Steuerung von weiteren Vorgänge in der gleichen Datenquelle vornehmen.
