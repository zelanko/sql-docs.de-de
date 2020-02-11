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
ms.openlocfilehash: fda38811fa876c9a0fad55e7f2ee7566ad3026d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67943760"
---
# <a name="rowset-size"></a>Rowsetgröße
Welche Rowsetgröße verwendet werden soll, hängt von der Anwendung ab. Bildschirmbasierte Anwendungen folgen in der Regel einer der beiden Strategien. Der erste besteht darin, die Rowsetgröße auf die Anzahl der auf dem Bildschirm angezeigten Zeilen festzulegen. Wenn der Benutzer die Größe des Bildschirms ändert, ändert die Anwendung die Rowsetgröße entsprechend. Die zweite besteht darin, die Rowsetgröße auf eine größere Zahl, z. b. 100, festzulegen, wodurch die Anzahl der Aufrufe an die Datenquelle reduziert wird. Die Anwendung scrollt nach Möglichkeit lokal innerhalb des Rowsets und ruft neue Zeilen nur dann ab, wenn ein Bildlauf außerhalb des Rowsets durchgeführt wird.  
  
 Andere Anwendungen, wie z. b. Berichte, legen tendenziell die Rowsetgröße auf die größte Anzahl von Zeilen fest, die von der Anwendung angemessen verarbeitet werden können. bei einem größeren Rowset wird der Netzwerk Aufwand pro Zeile manchmal reduziert. Wie groß ein Rowset sein kann, hängt von der Größe der einzelnen Zeilen und der Menge des verfügbaren Arbeitsspeichers ab.  
  
 Die Rowsetgröße wird durch einen Aufrufen von **SQLSetStmtAttr** mit dem *Attribut* Argument SQL_ATTR_ROW_ARRAY_SIZE festgelegt. Die Anwendung kann die Rowsetgröße ändern, neue rowsetpuffer binden (durch Aufrufen von **SQLBindCol** oder durch Angeben eines Bindungs Offsets), auch nachdem Zeilen abgerufen wurden, oder beides. Die Auswirkungen der Änderung der Rowsetgröße hängen von der Funktion ab:  
  
-   **SQLFetch** und **SQLFetchScroll** verwenden die Rowsetgröße zum Zeitpunkt des Aufrufs, um zu bestimmen, wie viele Zeilen abgerufen werden sollen. Allerdings erhöht **SQLFetchScroll** mit der *FetchOrientation* -SQL_FETCH_NEXT den Cursor basierend auf dem Rowset des vorherigen Abruf Vorgangs und ruft dann ein Rowset basierend auf der aktuellen Rowsetgröße ab.  
  
-   **SQLSetPos** verwendet die Rowsetgröße, die ab dem vorhergehenden-Befehl von **SQLFetch** oder **SQLFetchScroll**wirksam ist, da **SQLSetPos** auf ein Rowset angewendet wird, das bereits festgelegt wurde. **SQLSetPos** übernimmt außerdem die neue Rowsetgröße, wenn **SQLBulkOperations** aufgerufen wurde, nachdem die Rowsetgröße geändert wurde.  
  
-   **SQLBulkOperations** verwendet die Rowsetgröße, die zum Zeitpunkt des Aufrufes verwendet wird, da Sie Vorgänge für eine Tabelle unabhängig von einem abgerufenen Rowset ausführt.
