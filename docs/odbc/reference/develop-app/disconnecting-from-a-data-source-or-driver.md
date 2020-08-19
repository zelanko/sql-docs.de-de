---
description: Trennen der Verbindung mit einer Datenquelle oder einem Treiber
title: Trennen der Verbindung mit einer Datenquelle oder einem Treiber | Microsoft-Dokumentation
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
ms.openlocfilehash: fc14ca0ebf29a2ab203a4408db4b5681ad667497
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476692"
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Trennen der Verbindung mit einer Datenquelle oder einem Treiber
Wenn eine Anwendung mit der Verwendung einer Datenquelle fertig ist, wird **SQLDisconnect**aufgerufen. **SQLDisconnect** gibt alle-Anweisungen frei, die der Verbindung zugeordnet sind, und trennt den Treiber von der Datenquelle. Wenn eine Transaktion gerade verarbeitet wird, wird ein Fehler zurückgegeben.  
  
 Nach dem Trennen der Verbindung kann die Anwendung **SQLFreeHandle** aufzurufen, um die Verbindung freizugeben. Nachdem die Verbindung freigegeben wurde, handelt es sich um einen Anwendungs Programmierfehler, der das Handle der Verbindung in einem Rückruf einer ODBC-Funktion verwendet. Dies hat nicht definierte, aber wahrscheinlich schwerwiegende Konsequenzen. Wenn **SQLFreeHandle** aufgerufen wird, gibt der Treiber die Struktur frei, die zum Speichern von Informationen über die Verbindung verwendet wird.  
  
 Die Anwendung kann die Verbindung auch wieder verwenden, um eine Verbindung mit einer anderen Datenquelle herzustellen oder eine erneute Verbindung mit derselben Datenquelle herzustellen. Die Entscheidung, mit der Verbindung zu bleiben, im Gegensatz zum Trennen und erneuten Herstellen der Verbindung, erfordert, dass der anwendungswriter die relativen Kosten der einzelnen Optionen berücksichtigt. das Herstellen einer Verbindung mit einer Datenquelle und die verbleibende Verbindung kann je nach Verbindungs Medium relativ kostspielig sein. Wenn Sie einen richtigen Kompromiss treffen, muss die Anwendung auch Annahmen über die Wahrscheinlichkeit und zeitliche Steuerung von weiteren Vorgängen in derselben Datenquelle treffen.
