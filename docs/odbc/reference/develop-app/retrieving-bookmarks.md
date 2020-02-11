---
title: Abrufen von Lesezeichen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f18b87adf31f19d2a93bb3af3e14c265ae3940af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020575"
---
# <a name="retrieving-bookmarks"></a>Abrufen von Textmarken
Wenn die Anwendung Lesezeichen verwendet, muss Sie das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut auf SQL_UB_VARIABLE festlegen, bevor die Anweisung vorbereitet oder ausgeführt wird. Dies ist erforderlich, da das Erstellen und Verwalten von Lesezeichen ein kostspieliger Vorgang sein kann. Daher sollten Lesezeichen nur aktiviert werden, wenn Sie von einer Anwendung genutzt werden können.  
  
 Lesezeichen werden als Spalte 0 des Resultsets zurückgegeben. Es gibt drei Möglichkeiten, wie eine Anwendung Sie abrufen kann:  
  
-   Binden Sie die Spalte 0 des Resultsets. **SQLFetch** oder **SQLFetchScroll** gibt die Lesezeichen für jede Zeile im Rowset zusammen mit den Daten für andere gebundene Spalten zurück.  
  
-   Aufrufen von **SQLSetPos** , um zu einer Zeile im Rowset zu positionieren, und anschließendes Aufrufen von **SQLGetData** für Spalte 0. Wenn ein Treiber Lesezeichen unterstützt, muss er immer die Möglichkeit unterstützen, **SQLGetData** für Spalte 0 aufzurufen, auch wenn er nicht zulässt, dass Anwendungen **SQLGetData** für andere Spalten vor der letzten gebundenen Spalte aufruft.  
  
-   Nennen Sie **SQLBulkOperations** , wobei das *Vorgangs* Argument auf SQL_ADD und die Spalte 0 (null) festgelegt ist. Der Cursor fügt die Zeile ein und gibt das Lesezeichen für die Zeile im gebundenen Puffer zurück.
