---
description: SQLEndTran (Cursorbibliothek)
title: SQLEndTran (Cursor Bibliothek) | Microsoft-Dokumentation
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
ms.openlocfilehash: 25584f19a885580be24b2681ccd639de285fb4b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466032"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLEndTran** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLEndTran**finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
 Die Cursor Bibliothek unterstützt keine Transaktionen und übergibt Aufrufe an **SQLEndTran** direkt an den Treiber. Die Cursor Bibliothek unterstützt jedoch die von der Datenquelle zurückgegebenen Cursor-Commit-und Rollback-Verhaltensweisen mit den SQL_CURSOR_ROLLBACK_BEHAVIOR-und SQL_CURSOR_COMMIT_BEHAVIOR-Informationstypen:  
  
-   Bei Datenquellen, bei denen Cursor Transaktionen übergreifend beibehalten werden, wird für Änderungen, die in der Datenquelle zurückgesetzt werden, kein Rollback im Cache der Cursor Bibliothek ausgeführt. Damit der Cache den Daten in der Datenquelle entspricht, muss die Anwendung den Cursor schließen und erneut öffnen.  
  
-   Bei Datenquellen, die Cursor an Transaktionsgrenzen schließen, schließt die Cursor Bibliothek die Cursor und löscht die Caches für alle Anweisungen auf der Verbindung.  
  
-   Bei Datenquellen, die vorbereitete Anweisungen an Transaktionsgrenzen löschen, muss die Anwendung alle vorbereiteten Anweisungen für die Verbindung erneut vorbereiten, bevor Sie erneut ausgeführt werden.
