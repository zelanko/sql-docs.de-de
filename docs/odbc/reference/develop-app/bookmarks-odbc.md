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
ms.openlocfilehash: bab3571ba880658d9f1a2629b899484008428083
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68118789"
---
# <a name="bookmarks-odbc"></a>Textmarken (ODBC)
Ein Lesezeichen ist ein Wert, der verwendet wird, um eine Zeile mit Daten zu identifizieren. Die Bedeutung des Lesezeichenwerts ist nur dem Treiber oder der Datenquelle bekannt. Der Wert kann so einfach wie eine Zeilennummer oder so komplex wie eine Datenträgeradresse sein. Lesezeichen in ODBC unterscheiden sich etwas von Lesezeichen in echten Büchern. In einem echten Buch platziert der Reader ein Lesezeichen auf einer bestimmten Seite und sucht dann nach diesem Lesezeichen, um zur Seite zurückzukehren. In ODBC fordert die Anwendung ein Lesezeichen für bestimmte Zeilen an, speichert es und gibt es an den Cursor für die Rückgabe an die Zeile zurück. Daher ähneln Lesezeichen in ODBC den Lesern, die eine Seitenzahl schreiben, Sie zu speichern und die Seite dann erneut zu suchen.  
  
 Um die Unterstützung von Lesezeichen eines Treibers zu ermitteln, ruft eine Anwendung **SQLGetInfo** mit der SQL_BOOKMARK_PERSISTENCE-Option auf. Die Bits in diesem Wert beschreiben, welche Vorgangs Lesezeichen überleben, wie z. b. ob Lesezeichen nach dem Schließen des Cursors noch gültig sind.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Textmarkentypen](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Abrufen von Textmarken](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Scrollen durch Textmarken](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Aktualisieren, Löschen oder Abrufen durch Textmarke](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Vergleichen von Textmarken](../../../odbc/reference/develop-app/comparing-bookmarks.md)
