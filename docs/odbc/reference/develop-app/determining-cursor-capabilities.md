---
title: Bestimmen der Cursorfunktionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 984ad8302f2e1695c8df84a64a18042f4cc9e364
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305881"
---
# <a name="determining-cursor-capabilities"></a>Festlegen der Cursorfähigkeiten
Die folgenden vier Optionen in **SQLGetInfo** beschreiben, welche Cursortypen unterstützt werden und welche Funktionen sie haben:  
  
-   SQL_CURSOR_SENSITIVITY. Gibt an, ob ein Cursor auf Änderungen reagiert, die von einem anderen Cursor vorgenommen werden.  
  
-   SQL_SCROLL_OPTIONS. Listet die unterstützten Cursortypen auf (vorwärts, statisch, Keyset-gesteuert, dynamisch oder gemischt). Alle Datenquellen müssen vorwärtsgerichtete Cursor unterstützen.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 (je nach Cursortyp). Listet die Abruftypen auf, die von scrollbaren Cursorn unterstützt werden. Die Bits im Rückgabewert entsprechen den Abruftypen in **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 oder SQL_STATIC_CURSOR_ATTRIBUTES2 (je nach Typ des Cursors). Listet auf, ob statische und Keyset-gesteuerte Cursor ihre eigenen Aktualisierungen, Löschungen und Einfügungen erkennen können.  
  
 Eine Anwendung kann Cursorfunktionen zur Laufzeit bestimmen, indem **sie SQLGetInfo** mit diesen Optionen aufruft. Dies wird häufig von generischen Anwendungen durchgeführt. Cursorfunktionen können auch während der Anwendungsentwicklung bestimmt und ihre Verwendung in der Anwendung hartcodiert werden. Dies geschieht häufig durch vertikale und benutzerdefinierte Anwendungen, kann aber auch von generischen Anwendungen durchgeführt werden, die eine clientseitige Cursorimplementierung wie die ODBC-Cursorbibliothek verwenden.
