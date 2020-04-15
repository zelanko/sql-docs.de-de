---
title: Erstellen von durchsuchten Anweisungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- searched statements [ODBC]
- ODBC cursor library [ODBC], statement processing
- ODBC cursor library [ODBC], searched statements
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- cursor library [ODBC], searched statements
- SQL statements [ODBC], searched statements
ms.assetid: e429254c-c43f-4fbf-98b2-5f1ed53501ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8b9a27aa9fc84aadc6659993de3e12e269631d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284740"
---
# <a name="constructing-searched-statements"></a>Erstellen von searched-Anweisungen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Um positionierte Aktualisierungs- und Löschanweisungen zu unterstützen, erstellt die Cursorbibliothek eine durchsuchte **UPDATE-** oder **DELETE-Anweisung** aus der positioned-Anweisung. Um Aufrufe von **SQLGetData** in einem Datenblock zu unterstützen, erstellt die Cursorbibliothek eine durchsuchte **SELECT-Anweisung,** um ein Resultset zu erstellen, das die aktuelle Datenzeile enthält. In jeder dieser Anweisungen zählt die **WHERE-Klausel** die im Cache gespeicherten Werte für jede gebundene Spalte auf, die SQL_PRED_SEARCHABLE oder SQL_PRED_BASIC für den Feldbezeichner SQL_DESC_SEARCHABLE in **SQLColAttribute**zurückgibt.  
  
> [!CAUTION]  
>  Die **WHERE** WHERE-Klausel, die von der Cursorbibliothek erstellt wurde, um die aktuelle Zeile zu identifizieren, kann keine Zeilen identifizieren, eine andere Zeile identifizieren oder mehr als eine Zeile identifizieren.  
  
 Wenn eine positionierte Aktualisierungs- oder Löschanweisung mehr als eine Zeile betrifft, aktualisiert die Cursorbibliothek das Zeilenstatusarray nur für die Zeile, in der der Cursor positioniert ist, und gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01001 (Cursor-Vorgangskonflikt) zurück. Wenn die Anweisung keine Zeilen identifiziert, aktualisiert die Cursorbibliothek das Zeilenstatusarray nicht und gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01001 (Cursor-Vorgangskonflikt) zurück. Eine Anwendung kann **SQLRowCount** aufrufen, um die Anzahl der Zeilen zu bestimmen, die aktualisiert oder gelöscht wurden.  
  
 Wenn **SELECT** die SELECT-Klausel, die zum Positionieren des Cursors für einen Aufruf von **SQLGetData** verwendet wird, mehr als eine Zeile identifiziert, ist es nicht garantiert, dass **SQLGetData** die richtigen Daten zurückgibt. Wenn keine Zeilen identifiziert werden, gibt **SQLGetData** SQL_NO_DATA zurück.  
  
 Wenn eine Anwendung den folgenden Richtlinien entspricht, sollte die von der Cursorbibliothek erstellte **WHERE-Klausel** die aktuelle Zeile eindeutig identifizieren, es sei denn, dies ist nicht möglich, z. B. wenn die Datenquelle doppelte Zeilen enthält.  
  
-   **Binden Sie Spalten, die die Zeile eindeutig identifizieren.** Wenn die gebundenen Spalten die Zeile nicht eindeutig identifizieren, kann die von der Cursorbibliothek erstellte **WHERE-Klausel** mehr als eine Zeile identifizieren. In einer positionierten Aktualisierungs- oder Löschanweisung kann eine solche Klausel dazu führen, dass mehr als eine Zeile aktualisiert oder gelöscht wird. Bei einem Aufruf von **SQLGetData**kann eine solche Klausel dazu führen, dass der Treiber Daten für die falsche Zeile zurückgibt. Das Binden aller Spalten in einem eindeutigen Schlüssel garantiert, dass jede Zeile eindeutig identifiziert wird.  
  
-   **Zuweisen von Datenpuffern, die so groß sind, dass keine Abschneidung erfolgt.** Der Cache der Cursorbibliothek ist eine Kopie der Werte in den Rowset-Puffern, die mit **SQLBindCol**an das Resultset gebunden sind. Wenn Daten abgeschnitten werden, wenn sie in diesen Puffern platziert werden, werden sie auch im Cache abgeschnitten. Eine **WHERE** WHERE-Klausel, die aus abgeschnittenen Werten erstellt wurde, identifiziert die zugrunde liegende Zeile in der Datenquelle möglicherweise nicht korrekt.  
  
-   **Geben Sie Puffer für Binär-C-Daten für keine Null-Länge an.** Die Cursorbibliothek weist Längenpuffer in ihrem Cache nur zu, wenn das *StrLen_or_IndPtr* Argument in **SQLBindCol** ungleich NULL ist. Wenn das *TargetType-Argument* SQL_C_BINARY ist, benötigt die Cursorbibliothek die Länge der Binärdaten, um eine **WHERE-Klausel** aus den Daten zu erstellen. Wenn kein Längenpuffer für eine SQL_C_BINARY Spalte vorhanden ist und die Anwendung **SQLGetData** aufruft oder versucht, eine positionierte Aktualisierungs- oder Löschanweisung auszuführen, gibt die Cursorbibliothek SQL_ERROR und SQLSTATE SL014 zurück (Eine positionierte Anforderung wurde ausgegeben, und nicht alle Spaltenanzahlfelder wurden gepuffert).  
  
-   **Geben Sie Puffer für Nulllängen für NULL-Längenpuffer für NULL-Spalten an.** Die Cursorbibliothek weist Längenpuffer in ihrem Cache nur zu, wenn das *StrLen_or_IndPtr* Argument in **SQLBindCol** ungleich NULL ist. Da SQL_NULL_DATA im Längenpuffer gespeichert ist, geht die Cursorbibliothek davon aus, dass jede Spalte, für die kein Längenpuffer angegeben ist, nicht NULL ist. Wenn für eine null-fähige Spalte keine Längenspalte angegeben **WHERE** ist, erstellt die Cursorbibliothek eine WHERE-Klausel, die den Datenwert für die Spalte verwendet. Diese Klausel identifiziert die Zeile nicht korrekt.
