---
title: Erstellen von durchsuchten Anweisungen | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284740"
---
# <a name="constructing-searched-statements"></a>Erstellen von searched-Anweisungen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Um positionierte UPDATE-und DELETE-Anweisungen zu unterstützen, erstellt die Cursor Bibliothek eine gesuchte **Update** -oder **Delete** -Anweisung aus der positionierten Anweisung. Zur Unterstützung von Aufrufen von **SQLGetData** in einem Datenblock erstellt die Cursor Bibliothek eine gesuchte **Select** -Anweisung, um ein Resultset zu erstellen, das die aktuelle Daten Zeile enthält. In jeder dieser Anweisungen listet die **Where** -Klausel die im Cache gespeicherten Werte für jede gebundene Spalte auf, die SQL_PRED_SEARCHABLE oder SQL_PRED_BASIC für den SQL_DESC_SEARCHABLE Feld Bezeichner in **SQLColAttribute**zurückgibt.  
  
> [!CAUTION]  
>  Die **Where** -Klausel, die von der Cursor Bibliothek zum Identifizieren der aktuellen Zeile erstellt wurde, kann keine Zeilen identifizieren, eine andere Zeile identifizieren oder mehr als eine Zeile identifizieren.  
  
 Wenn eine positionierte UPDATE-oder DELETE-Anweisung mehr als eine Zeile betrifft, aktualisiert die Cursor Bibliothek das Zeilen Status Array nur für die Zeile, in der der Cursor positioniert ist, und gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01001 (Cursor Vorgangs Konflikt) zurück. Wenn die Anweisung keine Zeilen identifiziert, aktualisiert die Cursor Bibliothek das Zeilen Status Array nicht und gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01001 (Cursor Vorgangs Konflikt) zurück. Eine Anwendung kann **SQLRowCount** aufzurufen, um die Anzahl der Zeilen zu bestimmen, die aktualisiert oder gelöscht wurden.  
  
 Wenn die **Select** -Klausel, die zum Positionieren des Cursors für einen **SQLGetData** -Befehl verwendet wird, mehr als eine Zeile identifiziert, kann **SQLGetData** nicht sicherstellen, dass die richtigen Daten zurückgegeben werden. Wenn keine Zeilen identifiziert werden, gibt **SQLGetData** SQL_NO_DATA zurück.  
  
 Wenn eine Anwendung den folgenden Richtlinien entspricht, sollte die von der Cursor Bibliothek erstellte **Where** -Klausel die aktuelle Zeile eindeutig identifizieren, außer wenn dies nicht möglich ist, z. b. wenn die Datenquelle doppelte Zeilen enthält.  
  
-   **Binden Sie Spalten, die die Zeile eindeutig identifizieren.** Wenn die Zeilen durch die gebundenen Spalten nicht eindeutig identifiziert werden, kann die von der Cursor Bibliothek erstellte **Where** -Klausel mehr als eine Zeile identifizieren. In einer positionierten Update-oder DELETE-Anweisung kann eine solche Klausel dazu führen, dass mehr als eine Zeile aktualisiert oder gelöscht wird. Beim Aufrufen von **SQLGetData**kann eine solche Klausel bewirken, dass der Treiber Daten für die falsche Zeile zurückgibt. Wenn alle Spalten in einem eindeutigen Schlüssel gebunden werden, wird sichergestellt, dass jede Zeile eindeutig identifiziert wird.  
  
-   **Weisen Sie Datenpuffer groß genug zu, sodass keine Kürzung stattfindet.** Der Cache der Cursor Bibliothek ist eine Kopie der Werte in den rowsetpuffern, die an das Resultset mit **SQLBindCol**gebunden sind. Wenn Daten abgeschnitten werden, wenn Sie in diese Puffer eingefügt werden, werden Sie auch im Cache abgeschnitten. Eine **Where** -Klausel, die aus abschneidewerten erstellt wurde, identifiziert die zugrunde liegende Zeile in der Datenquelle möglicherweise nicht korrekt.  
  
-   **Geben Sie Puffer mit einer Länge ungleich NULL für binäre C-Daten an.** Die Cursor Bibliothek weist den Cache Längenpuffer nur dann zu, wenn das *StrLen_or_IndPtr* -Argument in **SQLBindCol** nicht NULL ist. Wenn das *TargetType* -Argument SQL_C_BINARY ist, erfordert die Cursor Bibliothek die Länge der Binärdaten, um eine **Where** -Klausel aus den Daten zu erstellen. Wenn für eine SQL_C_BINARY Spalte kein Längenpuffer vorhanden ist und die Anwendung **SQLGetData** aufruft oder versucht, eine positionierte UPDATE-oder DELETE-Anweisung auszuführen, gibt die Cursor Bibliothek SQL_ERROR und SQLSTATE SL014 (eine positionierte Anforderung wurde ausgegeben und nicht alle Spalten Anzahl Felder wurden gepuffert) zurück.  
  
-   **Geben Sie für Spalten, die NULL-Werte zulassen, keine Längenpuffer an.** Die Cursor Bibliothek weist den Cache Längenpuffer nur dann zu, wenn das *StrLen_or_IndPtr* -Argument in **SQLBindCol** nicht NULL ist. Da SQL_NULL_DATA im Längenpuffer gespeichert ist, geht die Cursor Bibliothek davon aus, dass jede Spalte, für die kein Längenpuffer angegeben ist, keine NULL-Werte zulässt. Wenn für eine Spalte, die NULL-Werte zulässt, keine Längen Spalte angegeben ist, erstellt die Cursor Bibliothek eine **Where** -Klausel, die den Datenwert für die Spalte verwendet. Diese Klausel identifiziert die Zeile nicht ordnungsgemäß.
