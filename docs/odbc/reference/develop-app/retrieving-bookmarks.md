---
title: Abrufen von Lesezeichen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d146b2fb9bfc0e7294709e971f1b6752dc99ab3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300070"
---
# <a name="retrieving-bookmarks"></a>Abrufen von Textmarken
Wenn die Anwendung Lesezeichen verwendet, muss sie das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung auf SQL_UB_VARIABLE festlegen, bevor die Anweisung vorbereitet oder ausgeführt wird. Dies ist notwendig, da das Erstellen und Verwalten von Lesezeichen ein kostspieliger Vorgang sein kann, daher sollten Lesezeichen nur aktiviert werden, wenn eine Anwendung sie sinnvoll nutzen kann.  
  
 Lesezeichen werden als Spalte 0 des Resultsets zurückgegeben. Es gibt drei Möglichkeiten, wie eine Anwendung sie abrufen kann:  
  
-   Binden Sie Spalte 0 des Resultsets. **SQLFetch** oder **SQLFetchScroll** gibt die Lesezeichen für jede Zeile im Rowset zusammen mit den Daten für andere gebundene Spalten zurück.  
  
-   Rufen Sie **SQLSetPos** auf, um es in einer Zeile im Rowset zu positionieren, und rufen Sie dann **SQLGetData** für Spalte 0 auf. Wenn ein Treiber Lesezeichen unterstützt, muss er immer die Möglichkeit unterstützen, **SQLGetData** für Spalte 0 aufzurufen, auch wenn es Anwendungen nicht erlaubt, **SQLGetData** für andere Spalten vor der letzten gebundenen Spalte aufzurufen.  
  
-   Rufen Sie **SQLBulkOperations** auf, wobei das *Argument Operation* auf SQL_ADD festgelegt ist und Spalte 0 gebunden ist. Der Cursor fügt die Zeile ein und gibt die Textmarke für die Zeile im gebundenen Puffer zurück.
