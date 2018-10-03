---
title: Rowsetgröße | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 132ee99180595dca5e203a6821c5f87aa616530d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695218"
---
# <a name="rowset-size"></a>Rowsetgröße
Die Größe des Rowsets verwenden, hängt von der Anwendung ab. Bildschirmbasierte Anwendungen gehen häufig von zwei Strategien verfolgen. Die erste ist für die Rowsetgröße festzulegen, die Anzahl der Zeilen, die auf dem Bildschirm angezeigt. Wenn der Benutzer den Bildschirm angepasst wird, wird die Anwendung die Rowsetgröße entsprechend geändert. Die zweite besteht darin, die Rowsetgröße auf einen höheren Wert ein, z. B. 100 festzulegen, die reduziert die Anzahl der Aufrufe an die Datenquelle. Die Anwendung lokal innerhalb des Rowsets möglichst verschiebt und neue Zeilen abruft, nur, wenn es außerhalb des Rowsets verschiebt.  
  
 Andere Anwendungen, z. B. Berichte, in der Regel die Rowsetgröße auf der größten Anzahl von Zeilen der Anwendung angemessen verarbeitet werden kann – mit einer größeren Zeilengruppe, manchmal im Netzwerk Aufwand pro Zeile reduziert ist. Genau wie groß ein Rowset sein kann, hängt von der Größe des jede Zeile und die Menge des verfügbaren Arbeitsspeichers ab.  
  
 Rowsetgröße wird durch einen Aufruf von **SQLSetStmtAttr** mit einer *Attribut* SQL_ATTR_ROW_ARRAY_SIZE Argument. Die Anwendung die Größe des Rowsets zu ändern, neue Rowset-Puffer zu binden können (durch Aufrufen von **SQLBindCol** oder das Angeben eines Bindung Offsets) auch nach Zeilen abgerufen wurden, oder beides. Welche Konsequenzen eine Änderung der Größe des Rowsets, abhängig von der Funktion:  
  
-   **SQLFetch** und **SQLFetchScroll** die Rowsetgröße zum Zeitpunkt des Aufrufs zu verwenden, um zu bestimmen, wie viele Zeilen abgerufen werden. Allerdings **SQLFetchScroll** mit einem *FetchOrientation* der SQL_FETCH_NEXT inkrementiert der Cursor basierend auf das Rowset der vorhergehenden Abrufvorgang und klicken Sie dann Abrufvorgänge Rowset basierend auf der Größe des aktuellen Rowsets.  
  
-   **SQLSetPos** verwendet die Rowsetgröße, die seit dem vorherigen Aufruf von gilt **SQLFetch** oder **SQLFetchScroll**, da **SQLSetPos** verarbeitet ein Rowset wurde bereits festgelegt. **SQLSetPos** auch übernimmt die neue Rowsetgröße Wenn **SQLBulkOperations** wurde aufgerufen, nachdem die Rowsetgröße geändert wurde.  
  
-   **SQLBulkOperations** wird verwendet, die Größe des Rowsets in Kraft zum Zeitpunkt des Aufrufs, da sie Vorgänge in einer Tabelle, die unabhängig des abgerufenen Rowsets ausführt.
