---
title: SQLFetchScroll (Cursor Bibliothek) | Microsoft-Dokumentation
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
ms.openlocfilehash: 16e7e4d133fdfafd7a005c19b0a2943b2ea9ef6d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086452"
---
# <a name="sqlfetchscroll-cursor-library"></a>SQLFetchScroll (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLFetchScroll** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLFetchScroll**finden Sie unter [SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 Die Cursor Bibliothek implementiert **SQLFetchScroll** durch wiederholtes Aufrufen von **SQLFetch** im Treiber. Die Daten, die Sie aus dem Treiber abruft, werden auf die von der Anwendung bereitgestellten rowsetpuffer übertragen. Außerdem werden die Daten im Arbeitsspeicher und in den Datenträger Dateien zwischengespeichert. Wenn eine Anwendung ein neues Rowset anfordert, ruft die Cursor Bibliothek Sie nach Bedarf vom Treiber ab (wenn Sie noch nicht abgerufen wurde) oder den Cache (wenn Sie zuvor abgerufen wurde). Schließlich behält die Cursor Bibliothek den Status der zwischengespeicherten Daten bei und gibt diese Informationen an die Anwendung im Zeilen Status Array zurück.  
  
 Wenn die Cursor Bibliothek verwendet wird, können Aufrufe von **SQLFetchScroll** nicht mit Aufrufen von **SQLFetch** oder **SQLExtendedFetch**gemischt werden.  
  
 Wenn die Cursor Bibliothek verwendet wird, werden Aufrufe von **SQLFetchScroll** sowohl für ODBC 2 unterstützt. *x* und für ODBC 3. *x* -Treiber.  
  
## <a name="rowset-buffers"></a>Rowsetpuffer  
 Die Cursor Bibliothek optimiert die Übertragung von Daten vom Treiber zum Rowset-Puffer, der von der Anwendung bereitgestellt wird, wenn:  
  
-   Die Anwendung verwendet die zeilenweise Bindung.  
  
-   Es gibt keine nicht verwendeten Bytes zwischen den Feldern in der Struktur, die von der Anwendung deklariert werden, um eine Daten Zeile zu speichern.  
  
-   Die Felder, in denen **SQLFetch** oder **SQLFetchScroll** die Länge/den Indikator für eine Spalte zurückgibt, folgen dem Puffer für diese Spalte und liegen vor dem Puffer für die nächste Spalte. Diese Felder sind optional.  
  
 Wenn die Anwendung ein neues Rowset anfordert, ruft die Cursor Bibliothek die Daten aus dem Cache und ggf. aus dem Treiber ab. Wenn sich die neuen und alten Rowsets überlappen, kann die Cursor Bibliothek die Leistung optimieren, indem die Daten aus den überlappenden Abschnitten der rowsetpuffer wieder verwendet werden. Daher gehen nicht gespeicherte Änderungen an den rowsetpuffern verloren, es sei denn, die neuen und alten Rowsets überlappen sich, und die Änderungen befinden sich in den überlappenden Abschnitten der rowsetpuffer. Um die Änderungen zu speichern, sendet eine Anwendung eine positionierte UPDATE-Anweisung.  
  
 Beachten Sie, dass die Cursor Bibliothek immer die rowsetpuffer mit Daten aus dem Cache aktualisiert, wenn eine Anwendung **SQLFetchScroll** aufruft, wobei das *FetchOrientation* -Argument auf SQL_FETCH_RELATIVE festgelegt und das *FetchOffset* -Argument auf 0 festgelegt ist.  
  
 Die Cursor Bibliothek unterstützt das Aufrufen von **SQLSetStmtAttr** mit einem *Attribut* von SQL_ATTR_ROW_ARRAY_SIZE, um die Rowsetgröße zu ändern, während ein Cursor geöffnet ist. Die neue Rowsetgröße wird beim nächsten Aufruf von **SQLFetchScroll** wirksam.  
  
## <a name="result-set-membership"></a>Resultsetmitgliedschaft  
 Die Cursor Bibliothek ruft Daten nur dann vom Treiber ab, wenn Sie von der Anwendung angefordert werden. Abhängig von der Datenquelle und der Einstellung des Attributs der SQL_CONCURRENCY Anweisung hat dies folgende Konsequenzen:  
  
-   Die von der Cursor Bibliothek abgerufenen Daten können sich von den Daten unterscheiden, die zum Zeitpunkt der Ausführung der Anweisung verfügbar waren. Nach dem Öffnen des Cursors können z. b. Zeilen, die an einem Punkt außerhalb der aktuellen Cursorposition eingefügt wurden, von einigen Treibern abgerufen werden.  
  
-   Die Daten im Resultset werden möglicherweise von der Datenquelle für die Cursor Bibliothek gesperrt und sind daher für andere Benutzer nicht verfügbar.  
  
 Nachdem die Cursor Bibliothek eine Zeile mit Daten zwischengespeichert hat, kann Sie keine Änderungen an dieser Zeile in der zugrunde liegenden Datenquelle erkennen (mit Ausnahme von positionierten Updates und Lösch Vorgängen, die für den Cache des gleichen Cursors ausgeführt werden). Dies liegt daran, dass die Cursor Bibliothek bei Aufrufen von **SQLFetchScroll**niemals Daten aus der Datenquelle wiederholt. Stattdessen werden Daten aus dem Cache wiederholt.  
  
## <a name="scrolling"></a>Bildlauf  
 Die Cursor Bibliothek unterstützt die folgenden Abruf Typen in **SQLFetchScroll**.  
  
|Cursortyp|FETCH-Typen|  
|-----------------|-----------------|  
|Vorwärtscursor|SQL_FETCH_NEXT|  
|statischen|SQL_FETCH_NEXT<br /><br /> SQL_FETCH_PRIOR<br /><br /> SQL_FETCH_FIRST<br /><br /> SQL_FETCH_LAST<br /><br /> SQL_FETCH_RELATIVE<br /><br /> SQL_FETCH_ABSOLUTE<br /><br /> SQL_FETCH_BOOKMARK|  
  
## <a name="errors"></a>Errors  
 Wenn **SQLFetchScroll** aufgerufen wird und einer der Aufrufe von **SQLFetch** SQL_ERROR zurückgibt, geht die Cursor Bibliothek wie folgt vor. Nachdem Sie diese Schritte abgeschlossen haben, wird die Verarbeitung der Cursor Bibliothek fortgesetzt.  
  
1.  Hiermit wird **SQLGetDiagRec** zum Abrufen von Fehlerinformationen vom Treiber aufgerufen und als Diagnosedaten Satz im Treiber-Manager veröffentlicht.  
  
2.  Legt das SQL_DIAG_ROW_NUMBER Feld im Diagnosedaten Satz auf den entsprechenden Wert fest.  
  
3.  Legt das SQL_DIAG_COLUMN_NUMBER Feld im Diagnosedaten Satz auf den entsprechenden Wert fest, falls zutreffend. Andernfalls wird der Wert auf 0 festgelegt.  
  
4.  Legt den Wert für die Fehler Zeile im Zeilen Status Array auf SQL_ROW_ERROR fest.  
  
 Nachdem die Cursor Bibliothek in der Implementierung von **SQLFetchScroll**mehrmals **SQLFetch** aufgerufen hat, werden alle Fehler oder Warnungen, die von einem der Aufrufe an **SQLFetch** zurückgegeben werden, in einem Diagnosedaten Satz gespeichert und können durch einen Aufruf von **SQLGetDiagRec**abgerufen werden. Wenn die Daten abgeschnitten wurden, als Sie abgerufen wurden, befinden sich die abgeschnittene Daten jetzt im Cache der Cursor Bibliothek. Nachfolgende Aufrufe von **SQLFetchScroll** , um zu einer Zeile mit abschneidenden Daten zu scrollen, geben die abgeschnittene Daten zurück, und es wird keine Warnung ausgelöst, da die Daten aus dem Cache der Cursor Bibliothek abgerufen werden. Um die Länge der zurückgegebenen Daten nachzuverfolgen, damit festgestellt werden kann, ob die in einem Puffer zurückgegebenen Daten abgeschnitten wurden, sollte eine Anwendung den Längen-/indikatorenpuffer binden.  
  
## <a name="bookmark-operations"></a>Lesezeichen Vorgänge  
 Die Cursor Bibliothek unterstützt das Aufrufen von **SQLFetchScroll** mit der *FetchOrientation* -SQL_FETCH_BOOKMARK. Es unterstützt auch das Angeben eines Offsets im *FetchOffset* -Argument, das im Lesezeichen Vorgang verwendet werden kann. Dies ist der einzige Lesezeichen Vorgang, den die Cursor Bibliothek unterstützt. Das Aufrufen von **SQLBulkOperations**wird von der Cursor Bibliothek nicht unterstützt.  
  
 Wenn die Anwendung das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut festgelegt und an die Lesezeichen Spalte gebunden hat, generiert die Cursor Bibliothek ein Lesezeichen mit fester Länge und gibt Sie an die Anwendung zurück. Die Cursor Bibliothek erstellt und verwaltet die verwendeten Lesezeichen. Lesezeichen, die in der Datenquelle beibehalten werden, werden nicht verwendet. Wenn **SQLFetchScroll** aufgerufen wird, um einen Datenblock abzurufen, der bereits aus der Datenquelle abgerufen wurde, werden die Daten aus dem Cursor-Bibliotheks Cache abgerufen. Folglich muss das Lesezeichen, das in einem-Befehl von **SQLFetchScroll** mit der *FetchOrientation* -SQL_FETCH_BOOKMARK verwendet wird, von der Cursor Bibliothek erstellt und verwaltet werden.  
  
## <a name="interaction-with-other-functions"></a>Interaktion mit anderen Funktionen  
 Eine Anwendung muss **SQLFetch** oder **SQLFetchScroll** aufzurufen, bevor Sie positionierte UPDATE-oder DELETE-Anweisungen vorbereitet oder ausführt.
