---
title: SQLEndTran (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c2277a67cd5410ea3c2a5d5b03b16d4533ed6ee1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304770"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLEndTran-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLEndTran**finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
 Die Cursorbibliothek unterstützt keine Transaktionen und übergibt Aufrufe von **SQLEndTran** direkt an den Treiber. Die Cursorbibliothek unterstützt jedoch das Cursorcommit- und Rollbackverhalten, das von der Datenquelle mit den SQL_CURSOR_ROLLBACK_BEHAVIOR- und SQL_CURSOR_COMMIT_BEHAVIOR-Informationstypen zurückgegeben wird:  
  
-   Bei Datenquellen, die Cursor über Transaktionen hinweg beibehalten, werden Änderungen, die in der Datenquelle zurückgesetzt werden, nicht im Cache der Cursorbibliothek zurückgesetzt. Damit der Cache mit den Daten in der Datenquelle übereinstimmt, muss die Anwendung den Cursor schließen und erneut öffnen.  
  
-   Bei Datenquellen, die Cursor an Transaktionsgrenzen schließen, schließt die Cursorbibliothek die Cursor und löscht die Caches für alle Anweisungen auf der Verbindung.  
  
-   Bei Datenquellen, die vorbereitete Anweisungen an Transaktionsgrenzen löschen, muss die Anwendung alle vorbereiteten Anweisungen für die Verbindung neu vorbereiten, bevor sie erneut ausgeführt werden.
