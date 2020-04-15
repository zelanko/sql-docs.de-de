---
title: Rowset Größe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rowset size [ODBC]
- cursors [ODBC], block
- result sets [ODBC], rowset size
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 60366ae8-175c-456a-ae5e-bdd860786911
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 11b95768934f96e1587b3c570b2510f3c2849239
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304241"
---
# <a name="rowset-size"></a>Rowsetgröße
Welche Rowsetgröße verwendet werden soll, hängt von der Anwendung ab. Bildschirmbasierte Anwendungen folgen in der Regel einer von zwei Strategien. Die erste besteht darin, die Rowsetgröße auf die Anzahl der auf dem Bildschirm angezeigten Zeilen festzulegen. Wenn der Benutzer die Größe des Bildschirms ändert, ändert die Anwendung die Rowsetgröße entsprechend. Die zweite besteht darin, die Rowsetgröße auf eine größere Anzahl festzulegen, z. B. 100, wodurch die Anzahl der Aufrufe an die Datenquelle reduziert wird. Die Anwendung scrollt nach Möglichkeit lokal innerhalb des Rowsets und ruft neue Zeilen nur ab, wenn sie außerhalb des Rowsets scrollt.  
  
 Andere Anwendungen, z. B. Berichte, neigen dazu, die Rowsetgröße auf die größte Anzahl von Zeilen festzulegen, die die Anwendung vernünftigerweise verarbeiten kann – bei einem größeren Rowset wird der Netzwerkaufwand pro Zeile manchmal reduziert. Wie groß ein Rowset genau sein kann, hängt von der Größe jeder Zeile und der verfügbaren Speichermenge ab.  
  
 Die Rowsetgröße wird durch einen Aufruf von **SQLSetStmtAttr** mit dem *Attributargument* SQL_ATTR_ROW_ARRAY_SIZE festgelegt. Die Anwendung kann die Rowsetgröße ändern, neue Rowsetpuffer binden (durch Aufrufen von **SQLBindCol** oder Angeben eines Bindungsoffsets) auch nach dem Abrufen von Zeilen oder beides. Die Auswirkungen der Änderung der Rowsetgröße hängen von der Funktion ab:  
  
-   **SQLFetch** und **SQLFetchScroll** verwenden die Rowsetgröße zum Zeitpunkt des Aufrufs, um zu bestimmen, wie viele Zeilen abgerufen werden sollen. **SQLFetchScroll** mit einer *FetchOrientation* von SQL_FETCH_NEXT erhöht den Cursor jedoch basierend auf dem Rowset des vorherigen Abrufs und ruft dann ein Rowset basierend auf der aktuellen Rowsetgröße ab.  
  
-   **SQLSetPos** verwendet die Rowsetgröße, die ab dem vorherigen Aufruf von **SQLFetch** oder **SQLFetchScroll**wirksam ist, da **SQLSetPos** für ein Rowset arbeitet, das bereits festgelegt wurde. **SQLSetPos** nimmt auch die neue Rowsetgröße auf, wenn **SQLBulkOperations** aufgerufen wurde, nachdem die Rowsetgröße geändert wurde.  
  
-   **SQLBulkOperations** verwendet die Rowsetgröße, die zum Zeitpunkt des Aufrufs wirksam war, da sie Vorgänge für eine Tabelle unabhängig von jedem abgerufenen Rowset ausführt.
