---
description: Scrollbare Cursortypen
title: Scrollbare Cursor Typen | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c27ccd54bfe0ba099d78c002fce4c901e4bf8c1c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476512"
---
# <a name="scrollable-cursor-types"></a>Scrollbare Cursortypen
Die vier Typen von scrollfähigen Cursorn sind statisch, dynamisch, keysetgesteuert und gemischt. Statische Cursor erkennen wenige oder keine Änderungen, sind aber relativ kostengünstig zu implementieren. Dynamische Cursor erkennen alle Änderungen, sind aber aufwendig zu implementieren. Keysetgesteuerte und gemischte Cursor befinden sich dazwischen und erkennen die meisten Änderungen, aber weniger Kosten als dynamische Cursor.  
  
 Die folgenden Begriffe werden verwendet, um die Merkmale der einzelnen scrollfähigen Cursor Typen zu definieren:  
  
-   **Eigene Updates, Löschungen und Einfügungen.** Aktualisierungen, Löschungen und Einfügungen, die über den Cursor durchgeführt werden, entweder durch einen **SQLBulkOperations** -oder **SQLSetPos** -Befehl oder eine positionierte UPDATE-oder DELETE-Anweisung.  
  
-   **Andere Updates, Löschungen und Einfügungen.** Updates, Löschungen und Einfügungen, die nicht vom Cursor vorgenommen werden, einschließlich derjenigen, die von anderen Vorgängen in derselben Transaktion, von anderen Transaktionen und von anderen Anwendungen vorgenommenen Vorgängen durchgeführt wurden.  
  
-   **Mitglied.** Der Satz von Zeilen im Resultset.  
  
-   **Reihenfolge.** Die Reihenfolge, in der Zeilen vom Cursor zurückgegeben werden.  
  
-   **Werte.** Die Werte in den einzelnen Zeilen im Resultset.  
  
 Informationen zum Aktualisieren, löschen und Einfügen von Daten finden Sie unter Übersicht über das Aktualisieren von [Daten](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Statische ODBC-Cursor](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [Dynamische ODBC-Cursor](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [Keysetgesteuerte Cursor](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [Gemischte Cursor](../../../odbc/reference/develop-app/mixed-cursors.md)
