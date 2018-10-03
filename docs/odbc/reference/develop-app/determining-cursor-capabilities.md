---
title: Der cursorfähigkeiten | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 716471786400c030febb62ebf41c8422770a8c09
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47598369"
---
# <a name="determining-cursor-capabilities"></a>Festlegen der Cursorfähigkeiten
Die folgenden vier Optionen im **SQLGetInfo** wird beschrieben, welche Arten von Cursorn unterstützt werden und was ihre Funktionen sind:  
  
-   SQL_CURSOR_SENSITIVITY FEST. Gibt an, ob ein Cursor empfindlich gegenüber Änderungen, die von einem anderen Cursor vorgenommen wird.  
  
-   SQL_SCROLL_OPTIONS. Listet die unterstützten Cursortypen (Vorwärtscursor, statische, keysetgesteuerte, dynamische oder gemischten). Alle Datenquellen müssen Vorwärtscursor unterstützen.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 (je nach Art des Cursors). Listet die Fetch-Typen, die von scrollfähige Cursor unterstützt. Die Bits im Rückgabewert entsprechen den Fetch-Typen in **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 oder SQL_STATIC_CURSOR_ATTRIBUTES2 (je nach Art des Cursors). Listet, ob die statische und keysetgesteuerte Cursor eigene Updates, löschungen und einfügungen erkennen können.  
  
 Eine Anwendung kann zur Laufzeit cursorfähigkeiten bestimmen, durch den Aufruf **SQLGetInfo** mit diesen Optionen. Dies erfolgt häufig von generischen Anwendungen. Cursor-Funktionen können auch bei der Anwendung während der Entwicklung von Anwendungen und deren Verwendung, die hartcodierte ermittelt werden. Dies erfolgt häufig durch vertikale und benutzerdefinierten Anwendungen, jedoch kann auch von generischen Anwendungen, die eine Implementierung der clientseitigen Cursor, z. B. die ODBC-Cursorbibliothek verwenden ausgeführt werden.
