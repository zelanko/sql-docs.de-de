---
title: Bestimmen von Cursor Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], capabilities
- cursors [ODBC], scrollable
ms.assetid: 35be486c-8f2d-4cec-beb8-df14151abfef
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 14715e40cd99f3f1a03c2ae19e825705a8376e30
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68040003"
---
# <a name="determining-cursor-capabilities"></a>Festlegen der Cursorfähigkeiten
Die folgenden vier Optionen in **SQLGetInfo** beschreiben, welche Typen von Cursorn unterstützt werden und welche Funktionen Sie haben:  
  
-   SQL_CURSOR_SENSITIVITY. Gibt an, ob ein Cursor von Änderungen abhängig ist, die von einem anderen Cursor vorgenommen wurden.  
  
-   SQL_SCROLL_OPTIONS. Listet die unterstützten Cursor Typen auf (vorwärts, statisch, keysetgesteuert, dynamisch oder gemischt). Alle Datenquellen müssen Vorwärts Cursor unterstützen.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 (abhängig vom Typ des Cursors). Listet die von scrollfähigen Cursorn unterstützten Abruf Typen auf. Die Bits im Rückgabewert entsprechen den FETCH-Typen in **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 oder SQL_STATIC_CURSOR_ATTRIBUTES2 (abhängig vom Typ des Cursors). Listet auf, ob statische und keysetgesteuerte Cursor ihre eigenen Aktualisierungen, Löschungen und Einfügungen erkennen können.  
  
 Eine Anwendung kann die Cursor Funktionen zur Laufzeit ermitteln, indem **SQLGetInfo** mit diesen Optionen aufgerufen wird. Dies erfolgt in der Regel durch generische Anwendungen. Cursor Funktionen können auch während der Anwendungsentwicklung und deren Verwendung in der Anwendung fest programmiert werden. Dies erfolgt in der Regel durch vertikale und benutzerdefinierte Anwendungen, kann aber auch von generischen Anwendungen ausgeführt werden, die eine Client seitige Cursor Implementierung wie die ODBC-Cursor Bibliothek verwenden.
