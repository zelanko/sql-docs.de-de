---
title: SQLFetchScroll (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetchScroll function [ODBC], Cursor Library
ms.assetid: 4417e57c-31dd-475e-8fe9-eab00a459c80
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db7dc5482347ad9b7f194b3c9c8c6cd7fc3f9f6a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199597"
---
# <a name="sqlfetchscroll-cursor-library"></a>SQLFetchScroll (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLFetchScroll** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLFetchScroll**, finden Sie unter [SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 Die Cursorbibliothek implementiert **SQLFetchScroll** durch wiederholtes Aufrufen **SQLFetch** im Treiber. Sie überträgt die Daten, die sie aus dem Treiber Ruft ab, der Rowset-Puffern, die von der Anwendung bereitgestellt. Es werden auch die Daten im Arbeitsspeicher und Festplattenspeicher Dateien zwischengespeichert. Wenn eine Anwendung ein neues Rowset anfordert, die Cursorbibliothek wird abgerufen nach Bedarf aus der Treiber (sofern sie nicht bereits abgerufen wurden) oder dem Cache (sofern sie zuvor abgerufen wurden). Abschließend wird die Cursorbibliothek verwaltet den Status der zwischengespeicherten Daten und gibt diese Informationen in den zeilenstatusarray an die Anwendung zurück.  
  
 Wenn die Cursorbibliothek verwendet wird, Aufrufe von **SQLFetchScroll** können nicht kombiniert werden, mit Aufrufen von entweder **SQLFetch** oder **SQLExtendedFetch**.  
  
 Wenn die Cursorbibliothek verwendet wird, Aufrufe von **SQLFetchScroll** sind unterstützt ODBC 2. *X* und für ODBC 3. *X* Treiber.  
  
## <a name="rowset-buffers"></a>Rowset-Puffer  
 Die Cursorbibliothek optimiert die Übertragung von Daten aus dem Treiber in den Rowset-Puffer, die von der Anwendung bereitgestellt wird, wenn:  
  
-   Die Anwendung verwendet die zeilenweise Bindung.  
  
-   Es gibt keine nicht verwendeten Bytes zwischen Feldern in der Struktur, die die Anwendung deklariert werden, um eine Zeile mit Daten zu speichern.  
  
-   Die Felder in der **SQLFetch** oder **SQLFetchScroll** gibt den Längenindikator, für den eine Spalte folgt den Puffer für diese Spalte und den Puffer für die nächste Spalte steht. Diese Felder sind optional.  
  
 Wenn die Anwendung ein neues Rowset anfordert, ruft die Cursorbibliothek Daten ab, aus dem Cache und aus dem Treiber nach Bedarf. Wenn überlappen ist die alten und neuen Rowsets, kann die Cursorbibliothek die Leistung optimieren, durch die Wiederverwendung von Daten aus die überlappenden Teile die Rowset-Puffer. Daher sind nicht gespeicherte Änderungen an die Rowset-Puffer verloren gehen, es sei denn, die den alten und neuen Rowsets überlappen und die Änderungen in die überlappenden Teile die Rowset-Puffer. Um die Änderungen zu speichern, wird eine Anwendung eine positionierte Update-Anweisung übermittelt.  
  
 Beachten Sie, dass die Cursorbibliothek immer die Rowset-Puffer mit Daten aus dem Cache aktualisiert, wenn eine Anwendung ruft **SQLFetchScroll** mit der *FetchOrientation* -Argument auf SQL_FETCH_RELATIVE festgelegt und die *FetchOffset* Argument auf 0 festgelegt.  
  
 Die Cursorbibliothek unterstützt Aufrufen **SQLSetStmtAttr** mit einer *Attribut* von SQL_ATTR_ROW_ARRAY_SIZE, um die Größe des Rowsets zu ändern, während ein Cursor geöffnet ist. Die neue Rowsetgröße werden wirksam, das nächste Mal **SQLFetchScroll** aufgerufen wird.  
  
## <a name="result-set-membership"></a>Resultset  
 Die Cursorbibliothek Ruft Daten aus dem Treiber ab, nur, wie die Anwendung sie anfordert. Abhängig von der Datenquelle und die Einstellung des Attributs SQL_CONCURRENCY-Anweisung hat dies folgende Konsequenzen:  
  
-   Die von der Cursorbibliothek abgerufenen Daten können aus den Daten abweichen, die verfügbar zur Zeit war, die die Anweisung ausgeführt wurde. Nachdem der Cursor geöffnet wurde, können z. B. Zeilen, die zu einem Zeitpunkt nach der aktuellen Cursorposition eingefügt durch einige Treiber abgerufen werden.  
  
-   Die Daten im Resultset möglicherweise durch die Datenquelle für die Cursorbibliothek gesperrt und daher nicht für andere Benutzer verfügbar.  
  
 Nachdem die Cursorbibliothek eine Zeile mit Daten zwischengespeichert, kann er Änderungen an dieser Zeile in der zugrunde liegenden Datenquelle (mit Ausnahme von positionierte Update- und Löschvorgänge, die auf den gleichen Cursor Cache) nicht erkennen. Dies tritt auf, da für Aufrufe von **SQLFetchScroll**, die Cursorbibliothek refetches niemals Daten aus der Datenquelle. Stattdessen refetches sie Daten aus dem Cache.  
  
## <a name="scrolling"></a>Durchführen eines Bildlaufs  
 Die Cursorbibliothek unterstützt die folgenden Typen von Fetch in **SQLFetchScroll**.  
  
|Cursortyp|Abrufen von Typen|  
|-----------------|-----------------|  
|Vorwärtscursor|SQL_FETCH_NEXT|  
|Statisch|SQL_FETCH_NEXT<br /><br /> SQL_FETCH_PRIOR<br /><br /> SQL_FETCH_FIRST<br /><br /> SQL_FETCH_LAST<br /><br /> SQL_FETCH_RELATIVE<br /><br /> SQL_FETCH_ABSOLUTE<br /><br /> SQL_FETCH_BOOKMARK|  
  
## <a name="errors"></a>Fehler  
 Wenn **SQLFetchScroll** aufgerufen wird und einen der Aufrufe **SQLFetch** gibt SQL_ERROR zurück, das Cursor-Bibliothek durchgeführt wird, die wie folgt. Wenn sie diese Schritte abgeschlossen ist, wird die Cursorbibliothek die Verarbeitung fortgesetzt.  
  
1.  Aufrufe **SQLGetDiagRec** zum Abrufen von Fehlerinformationen aus dem Treiber und stellt Sie dies als ein Diagnosedatensatz im Treiber-Manager.  
  
2.  Legt das Feld "SQL_DIAG_ROW_NUMBER" in dem Diagnosedatensatz auf den entsprechenden Wert fest.  
  
3.  Das Feld "SQL_DIAG_COLUMN_NUMBER" festgelegt im dem Diagnosedatensatz auf den entsprechenden Wert, wenn anwendbar; Andernfalls wird es auf 0.  
  
4.  Legt den Wert für die Zeile im Fehler in der zeilenstatusarray, SQL_ROW_ERROR fest.  
  
 Nach dem Cursor Library nennt **SQLFetch** mehrere Male in seiner Implementierung von **SQLFetchScroll**, Fehler noch Warnungen, die von den Aufrufen zum zurückgegebenen **SQLFetch** wird ein Diagnosedatensatz und abgerufen werden kann, durch einen Aufruf von **SQLGetDiagRec**. Wenn die Daten abgeschnitten wurden, wenn sie abgerufen wurde, werden die abgeschnittenen Daten jetzt in der Cursorbibliothek-Cache befinden. Nachfolgende Aufrufe von **SQLFetchScroll** führen Sie einen Bildlauf um eine Zeile mit abgeschnittene Daten werden die abgeschnittenen Daten zurückgeben und keine Warnung wird ausgelöst, da die Daten aus der Cursorbibliothek-Cache abgerufen werden. Zum Nachverfolgen die Länge der Daten zurückgegeben, sodass sie bestimmen kann, ob die Daten in einem Puffer zurückgegeben abgeschnitten wurde, sollte eine Anwendung den Längen-/Indikatorpuffer binden.  
  
## <a name="bookmark-operations"></a>Lesezeichen-Vorgänge  
 Die Cursorbibliothek unterstützt Aufrufen **SQLFetchScroll** mit einem *FetchOrientation* von sql_fetch_bookmark auf. Es unterstützt auch die Angabe eines Offsets in die *FetchOffset* Argument, das in der Lesezeichen-Vorgang verwendet werden kann. Dies ist der einzige Lesezeichen-Vorgang, die, den die Cursor-Bibliothek unterstützt. Die Cursorbibliothek unterstützt keine Aufrufen **SQLBulkOperations**.  
  
 Wenn die Anwendung das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut festgelegt wurde und die Lesezeichenspalte gebunden wurde, wird die Cursorbibliothek ein Lesezeichen fester Länge generiert und an die Anwendung zurückgegeben. Die Cursorbibliothek erstellt und verwaltet die Lesezeichen, die verwendet wird; Es verwendet keine Lesezeichen in der Datenquelle verwaltet. Wenn **SQLFetchScroll** wird aufgerufen, um einen Block von Daten abzurufen, die bereits aus der Datenquelle abgerufen wurde, die Daten von der Cursorbibliothek-Cache abgerufen. Daher wird das Lesezeichen in einem Aufruf verwendet **SQLFetchScroll** mit einer *FetchOrientation* von SQL_FETCH_BOOKMARK erstellt und von der Cursorbibliothek verwaltet werden müssen.  
  
## <a name="interaction-with-other-functions"></a>Interaktion mit anderen Funktionen  
 Eine Anwendung aufrufen muss **SQLFetch** oder **SQLFetchScroll** , bevor es vorbereitet oder ausführt alle positioniert update oder delete-Anweisungen.
