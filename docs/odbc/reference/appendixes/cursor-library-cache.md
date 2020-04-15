---
title: Cursor-Bibliothekscache | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5686bf0c3e261b1df947c02e2edaa419da498ecb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284690"
---
# <a name="cursor-library-cache"></a>Cache der Cursorbibliothek
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Für jede Datenzeile im Resultset speichert die Cursorbibliothek die Daten für jede gebundene Spalte, die Länge der Daten in jeder gebundenen Spalte und den Status der Zeile zwischen. Die Cursorbibliothek verwendet die Werte im Cache, um sowohl **über SQLFetch** und **SQLFetchScroll** zurückzugeben als auch um gesuchte Anweisungen für positionierte Vorgänge zu erstellen. Weitere Informationen finden Sie unter [Erstellen von durchsuchten Anweisungen](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Spaltendaten](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Länge der Spaltendaten](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [Zeilenstatus](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Ort des Caches](../../../odbc/reference/appendixes/location-of-cache.md)
