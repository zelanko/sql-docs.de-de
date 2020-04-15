---
title: SQLGetData (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07200d48f439c97003da7062fc218cd2f3081d1b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307841"
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLGetData-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLGetData**finden Sie unter [SQLGetData Function](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
 Die Cursorbibliothek implementiert **SQLGetData,** indem sie zunächst eine **SELECT-Anweisung** mit einer **WHERE-Klausel** erstellt, die die im Cache gespeicherten Werte für jede gebundene Spalte in der aktuellen Zeile aufzählt. Anschließend wird die **SELECT-Anweisung** ausgeführt, um die Zeile erneut auszuwählen, und **SQLGetData** im Treiber aufruft, um die Daten aus der Datenquelle abzurufen (im Gegensatz zum Cache).  
  
> [!CAUTION]  
>  Die **WHERE** WHERE-Klausel, die von der Cursorbibliothek erstellt wurde, um die aktuelle Zeile zu identifizieren, kann keine Zeilen identifizieren, eine andere Zeile identifizieren oder mehr als eine Zeile identifizieren. Weitere Informationen finden Sie unter [Erstellen von durchsuchten Anweisungen](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Wenn das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung auf SQL_UB_VARIABLE festgelegt ist, kann **SQLGetData** in Spalte 0 aufgerufen werden, um Lesezeichendaten zurückzugeben.  
  
 Aufrufe von **SQLGetData** unterliegen den folgenden Einschränkungen:  
  
-   **SQLGetData** kann nicht für Vorwärtscursor aufgerufen werden.  
  
-   **SQLGetData** kann nur aufgerufen werden, wenn die folgenden Bedingungen erfüllt sind: Eine **SELECT-Anweisung** generierte das Resultset; die **SELECT-Anweisung** enthielt keine Join-, **union-Klausel** oder **GROUP BY-Klausel;** und alle Spalten, die einen Alias oder Ausdruck in der Auswahlliste verwendet haben, waren nicht mit **SQLBindCol**gebunden.  
  
-   Wenn der Treiber nur eine aktive Anweisung unterstützt, ruft die Cursorbibliothek den Rest des Resultsets ab, bevor die **SELECT-Anweisung** ausgeführt und **SQLGetData**aufgerufen wird.
