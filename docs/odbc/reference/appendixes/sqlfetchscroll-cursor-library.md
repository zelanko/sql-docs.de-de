---
title: SQLFetchScroll (Cursorbibliothek) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e5573b8afc49afec8b7afa4fc52590e7a6a9e2fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302051"
---
# <a name="sqlfetchscroll-cursor-library"></a>SQLFetchScroll (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLFetchScroll-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLFetchScroll**finden Sie unter [SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 Die Cursorbibliothek implementiert **SQLFetchScroll,** indem **SQLFetch** wiederholt im Treiber aufgerufen wird. Es überträgt die Daten, die er vom Treiber abruft, an die von der Anwendung bereitgestellten Rowsetpuffer. Es speichert auch die Daten in Speicher- und Festplattendateien. Wenn eine Anwendung ein neues Rowset anfordert, ruft die Cursorbibliothek sie bei Bedarf vom Treiber (sofern es zuvor nicht abgerufen wurde) oder aus dem Cache (wenn es zuvor abgerufen wurde) ab. Schließlich behält die Cursorbibliothek den Status der zwischengespeicherten Daten bei und gibt diese Informationen an die Anwendung im Zeilenstatusarray zurück.  
  
 Wenn die Cursorbibliothek verwendet wird, können Aufrufe von **SQLFetchScroll** nicht mit Aufrufen von **SQLFetch** oder **SQLExtendedFetch**gemischt werden.  
  
 Wenn die Cursorbibliothek verwendet wird, werden Aufrufe von **SQLFetchScroll** sowohl für ODBC 2 unterstützt. *x* und für ODBC 3. *x-Treiber.*  
  
## <a name="rowset-buffers"></a>Rowset-Puffer  
 Die Cursorbibliothek optimiert die Übertragung von Daten vom Treiber in den rowset-Puffer, der von der Anwendung bereitgestellt wird, wenn:  
  
-   Die Anwendung verwendet zeilenweise Bindung.  
  
-   Es gibt keine nicht verwendeten Bytes zwischen Feldern in der Struktur, die von der Anwendung deklariert wird, um eine Datenzeile zu enthalten.  
  
-   Die Felder, in denen **SQLFetch** oder **SQLFetchScroll** die Länge/den Indikator für eine Spalte zurückgibt, folgen dem Puffer für diese Spalte und leiten den Puffer für die nächste Spalte voraus. Diese Felder sind optional.  
  
 Wenn die Anwendung ein neues Rowset anfordert, ruft die Cursorbibliothek bei Bedarf Daten aus ihrem Cache und vom Treiber ab. Wenn sich die neuen und die alten Rowsets überlappen, kann die Cursorbibliothek ihre Leistung optimieren, indem sie die Daten aus den überlappenden Abschnitten der Rowsetpuffer wiederverwendet. Daher gehen nicht gespeicherte Änderungen an den Rowsetpuffern verloren, es sei denn, die neuen und alten Rowsets überlappen sich, und die Änderungen befinden sich in den überlappenden Abschnitten der Rowsetpuffer. Um die Änderungen zu speichern, sendet eine Anwendung eine positionierte Aktualisierungsanweisung.  
  
 Beachten Sie, dass die Cursorbibliothek die Rowsetpuffer immer mit Daten aus dem Cache aktualisiert, wenn eine Anwendung **SQLFetchScroll** aufruft, wobei das *Argument FetchOrientation* auf SQL_FETCH_RELATIVE und das *FetchOffset-Argument* auf 0 festgelegt ist.  
  
 Die Cursorbibliothek unterstützt das Aufrufen von **SQLSetStmtAttr** mit einem *Attribut* von SQL_ATTR_ROW_ARRAY_SIZE, um die Rowsetgröße zu ändern, während ein Cursor geöffnet ist. Die neue Rowsetgröße wird beim nächsten Aufruf von **SQLFetchScroll** wirksam.  
  
## <a name="result-set-membership"></a>Ergebnis-Set-Mitgliedschaft  
 Die Cursorbibliothek ruft Daten vom Treiber nur ab, wenn die Anwendung sie anfordert. Abhängig von der Datenquelle und der Einstellung des SQL_CONCURRENCY-Anweisungsattributs hat dies folgende Folgen:  
  
-   Die von der Cursorbibliothek abgerufenen Daten können von den Daten abweichen, die zum Zeitpunkt der Ausführung der Anweisung verfügbar waren. Beispielsweise können Zeilen, die an einem Punkt außerhalb der aktuellen Cursorposition eingefügt wurden, nach dem Öffnen des Cursors von einigen Treibern abgerufen werden.  
  
-   Die Daten im Resultset werden möglicherweise von der Datenquelle für die Cursorbibliothek gesperrt und sind daher für andere Benutzer nicht verfügbar.  
  
 Nachdem die Cursorbibliothek eine Datenzeile zwischengespeichert hat, können sie keine Änderungen an dieser Zeile in der zugrunde liegenden Datenquelle erkennen (mit Ausnahme von positionierten Aktualisierungen und Löschungen, die im Cache desselben Cursors ausgeführt werden). Dies liegt daran, dass die Cursorbibliothek bei Aufrufen von **SQLFetchScroll**niemals Daten aus der Datenquelle erneut abruft. Stattdessen werden Daten aus dem Cache erneut abgerufen.  
  
## <a name="scrolling"></a>Scrollen  
 Die Cursorbibliothek unterstützt die folgenden Abruftypen in **SQLFetchScroll**.  
  
|Cursortyp|Abruftypen|  
|-----------------|-----------------|  
|Vorwärtscursor|SQL_FETCH_NEXT|  
|statischen|SQL_FETCH_NEXT<br /><br /> SQL_FETCH_PRIOR<br /><br /> SQL_FETCH_FIRST<br /><br /> SQL_FETCH_LAST<br /><br /> SQL_FETCH_RELATIVE<br /><br /> SQL_FETCH_ABSOLUTE<br /><br /> SQL_FETCH_BOOKMARK|  
  
## <a name="errors"></a>Errors  
 Wenn **SQLFetchScroll** aufgerufen wird und einer der Aufrufe von **SQLFetch** SQL_ERROR zurückgibt, verläuft die Cursorbibliothek wie folgt. Nachdem diese Schritte abgeschlossen wurden, wird die Cursorbibliothek weiterverarbeitet.  
  
1.  Ruft **SQLGetDiagRec** auf, um Fehlerinformationen vom Treiber abzuholen, und veröffentlicht diese als Diagnosedatensatz im Treiber-Manager.  
  
2.  Legt das Feld SQL_DIAG_ROW_NUMBER im Diagnosedatensatz auf den entsprechenden Wert fest.  
  
3.  Legt das SQL_DIAG_COLUMN_NUMBER Feld im Diagnosedatensatz ggf. auf den entsprechenden Wert fest. Andernfalls wird es auf 0 festgelegt.  
  
4.  Legt den Wert für die fehlerhafte Zeile im Zeilenstatusarray auf SQL_ROW_ERROR fest.  
  
 Nachdem die Cursorbibliothek **SQLFetch** mehrmals in der Implementierung von **SQLFetchScroll**aufgerufen hat, befinden sich alle Fehler oder Warnungen, die von einem der Aufrufe von **SQLFetch** zurückgegeben werden, in einem Diagnosedatensatz und können durch einen Aufruf von **SQLGetDiagRec**abgerufen werden. Wenn die Daten beim Abrufen abgeschnitten wurden, befinden sich die abgeschnittenen Daten nun im Cache der Cursorbibliothek. Nachfolgende Aufrufe von **SQLFetchScroll** zum Scrollen zu einer Zeile mit abgeschnittenen Daten geben die abgeschnittenen Daten zurück, und es wird keine Warnung ausgelöst, da die Daten aus dem Cache der Cursorbibliothek abgerufen werden. Um die Länge der zurückgegebenen Daten nachzuverfolgen, damit sie bestimmen kann, ob die in einem Puffer zurückgegebenen Daten abgeschnitten wurden, sollte eine Anwendung den Längen-/Indikatorpuffer binden.  
  
## <a name="bookmark-operations"></a>Lesezeichen-Operationen  
 Die Cursorbibliothek unterstützt das Aufrufen von **SQLFetchScroll** mit einem *FetchOrientation* von SQL_FETCH_BOOKMARK. Es unterstützt auch die Angabe eines Offsets im *FetchOffset-Argument,* das im Lesezeichenvorgang verwendet werden kann. Dies ist der einzige Lesezeichenvorgang, den die Cursorbibliothek unterstützt. Die Cursorbibliothek unterstützt den Aufruf von **SQLBulkOperations**nicht .  
  
 Wenn die Anwendung das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut festgelegt hat und an die Lesezeichenspalte gebunden ist, generiert die Cursorbibliothek eine Textmarke mit fester Länge und gibt sie an die Anwendung zurück. Die Cursorbibliothek erstellt und verwaltet die von ihr verwendeten Lesezeichen. Es werden keine Lesezeichen verwendet, die an der Datenquelle verwaltet werden. Wenn **SQLFetchScroll** aufgerufen wird, um einen Datenblock abzurufen, der bereits aus der Datenquelle abgerufen wurde, werden die Daten aus dem Cursorbibliothekscache abgerufen. Daher muss die Inschrift, die in einem Aufruf von **SQLFetchScroll** mit einem *FetchOrientation* von SQL_FETCH_BOOKMARK verwendet wird, von der Cursorbibliothek erstellt und verwaltet werden.  
  
## <a name="interaction-with-other-functions"></a>Interaktion mit anderen Funktionen  
 Eine Anwendung muss **SQLFetch** oder **SQLFetchScroll** aufrufen, bevor sie positionierte Aktualisierungs- oder Löschanweisungen vorbereitet oder ausführt.
