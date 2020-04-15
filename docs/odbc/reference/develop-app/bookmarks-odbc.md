---
title: Lesezeichen (ODBC) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8273c82b918024417e613ea44a2d26bafaf7d76
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306321"
---
# <a name="bookmarks-odbc"></a>Textmarken (ODBC)
Ein Lesezeichen ist ein Wert, der verwendet wird, um eine Zeile mit Daten zu identifizieren. Die Bedeutung des Lesezeichenwerts ist nur dem Treiber oder der Datenquelle bekannt. Der Wert kann so einfach wie eine Zeilennummer oder so komplex wie eine Datenträgeradresse sein. Lesezeichen in ODBC unterscheiden sich ein wenig von Lesezeichen in echten Büchern. In einem echten Buch platziert der Leser ein Lesezeichen auf einer bestimmten Seite und sucht dann nach diesem Lesezeichen, um zur Seite zurückzukehren. In ODBC fordert die Anwendung ein Lesezeichen für bestimmte Zeilen an, speichert es und gibt es an den Cursor für die Rückgabe an die Zeile zurück. Daher ähneln Lesezeichen in ODBC einem Leser, der eine Seitenzahl aufschreibt, sich daran erinnert und dann die Seite erneut nachoben.  
  
 Um die Unterstützung von Lesezeichen durch einen Treiber zu ermitteln, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_BOOKMARK_PERSISTENCE auf. Die Bits in diesem Wert beschreiben, welche Betriebs-Lesezeichen überleben, z. B. ob Lesezeichen nach dem Schließen des Cursors noch gültig sind.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Textmarkentypen](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Abrufen von Textmarken](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Scrollen durch Textmarken](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Aktualisieren, Löschen oder Abrufen durch Textmarke](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Vergleichen von Textmarken](../../../odbc/reference/develop-app/comparing-bookmarks.md)
