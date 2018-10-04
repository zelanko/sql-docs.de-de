---
title: Lesezeichen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9eecd202a17a0a08e8607ebec0caaa31b7b3ca9c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854468"
---
# <a name="bookmarks-odbc"></a>Textmarken (ODBC)
Ein Lesezeichen ist ein Wert, der verwendet wird, um eine Zeile mit Daten zu identifizieren. Die Bedeutung des Lesezeichenwerts ist nur dem Treiber oder der Datenquelle bekannt. Der Wert kann so einfach wie eine Zeilennummer oder so komplex wie eine Datenträgeradresse sein. Lesezeichen in ODBC unterscheiden sich etwas von Lesezeichen im real-Onlinedokumentation. In einer echten Buch wird der Reader wird ein Lesezeichen, an einer bestimmten Seite und sucht dann nach diesem Lesezeichen aus, um zur Seite zurückzukehren. In ODBC fordert die Anwendung ein Lesezeichen für bestimmte Zeilen an, speichert es und gibt es an den Cursor für die Rückgabe an die Zeile zurück. Daher sind Lesezeichen in ODBC ähnelt einem Reader schreiben Sie eine Seitenzahl, speichern es aus, und klicken Sie dann die Seite erneut nachschlagen.  
  
 Um einen Treiber für die Unterstützung von Lesezeichen zu bestimmen, die eine Anwendung ruft **SQLGetInfo** mit der Option SQL_BOOKMARK_PERSISTENCE. Die Bits in diesem Wert wird beschrieben, welche Vorgänge Lesezeichen überleben, wie z. B., ob Lesezeichen noch gültig sind, nachdem der Cursor geschlossen ist.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Lesezeichentypen](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Abrufen von Lesezeichen](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Scrollen durch Lesezeichen](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Aktualisieren, Löschen oder Abrufen nach Lesezeichen](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Vergleichen von Lesezeichen](../../../odbc/reference/develop-app/comparing-bookmarks.md)
