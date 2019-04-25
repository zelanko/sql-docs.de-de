---
title: Scrollbare Cursortypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6290d18ec26fcfa6e2960c3a2c1c408938d9e0e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468577"
---
# <a name="scrollable-cursor-types"></a>Scrollbare Cursortypen
Die vier Typen von bildlauffähigen Cursor werden statische, dynamische, keysetgesteuerte und gemischte. Statische Cursor erkennen wenige oder gar keine Änderungen jedoch relativ günstig zu implementieren sind. Dynamische Cursor erkennen alle Änderungen jedoch aufwendig zu implementieren. Keysetgesteuerte und gemischte Cursor liegen zwischen, die meisten Änderungen erkennen, aber auf weniger Kosten als dynamische Cursor.  
  
 Die folgenden Begriffe werden verwendet, um die Eigenschaften für jede Art von bildlauffähigen Cursor zu definieren:  
  
-   **Besitzen Sie Updates, löschungen und einfügungen.** Updates, löschungen und einfügungen, die über den Cursor, entweder durch einen Aufruf von **SQLBulkOperations** oder **SQLSetPos** oder mit ein positioniertes update oder delete-Anweisung.  
  
-   **Andere aktualisiert, gelöscht und fügt ein.** Updates, löschungen und nicht von den Cursor, einschließlich derjenigen, die von anderen Vorgängen in der gleichen Transaktion vorgenommenen einfügungen, die durch andere Transaktionen und die von anderen Anwendungen.  
  
-   **Mitgliedschaft.** Der Satz von Zeilen im Resultset.  
  
-   **Die Reihenfolge.** Die Reihenfolge, in der Zeilen vom Cursor zurückgegeben werden.  
  
-   **Werte.** Die Werte in jeder Zeile im Resultset.  
  
 Informationen zum Aktualisieren, löschen und Einfügen von Daten zu erhalten, finden Sie unter [Übersicht über die Daten Aktualisierung](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Statische ODBC-Cursor](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [Dynamische Cursor von ODBC](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [Keysetgesteuerte Cursor](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [Gemischte Cursor](../../../odbc/reference/develop-app/mixed-cursors.md)
