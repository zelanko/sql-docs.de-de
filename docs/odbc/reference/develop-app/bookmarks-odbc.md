---
description: Textmarken (ODBC)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f162fc317f2651549a1a2e80af03c9942dc64bb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461612"
---
# <a name="bookmarks-odbc"></a>Textmarken (ODBC)
Ein Lesezeichen ist ein Wert, der verwendet wird, um eine Zeile mit Daten zu identifizieren. Die Bedeutung des Lesezeichenwerts ist nur dem Treiber oder der Datenquelle bekannt. Der Wert kann so einfach wie eine Zeilennummer oder so komplex wie eine Datenträgeradresse sein. Lesezeichen in ODBC unterscheiden sich etwas von Lesezeichen in echten Büchern. In einem echten Buch platziert der Reader ein Lesezeichen auf einer bestimmten Seite und sucht dann nach diesem Lesezeichen, um zur Seite zurückzukehren. In ODBC fordert die Anwendung ein Lesezeichen für bestimmte Zeilen an, speichert es und gibt es an den Cursor für die Rückgabe an die Zeile zurück. Daher ähneln Lesezeichen in ODBC den Lesern, die eine Seitenzahl schreiben, Sie zu speichern und die Seite dann erneut zu suchen.  
  
 Um die Unterstützung von Lesezeichen eines Treibers zu ermitteln, ruft eine Anwendung **SQLGetInfo** mit der SQL_BOOKMARK_PERSISTENCE-Option auf. Die Bits in diesem Wert beschreiben, welche Vorgangs Lesezeichen überleben, wie z. b. ob Lesezeichen nach dem Schließen des Cursors noch gültig sind.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Textmarkentypen](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Abrufen von Textmarken](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Scrollen durch Textmarken](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Aktualisieren, Löschen oder Abrufen durch Textmarke](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Vergleichen von Textmarken](../../../odbc/reference/develop-app/comparing-bookmarks.md)
