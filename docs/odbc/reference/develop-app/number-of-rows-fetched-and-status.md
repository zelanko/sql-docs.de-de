---
title: Anzahl der abgerufenen Zeilen und Status | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- number of rows fetched [ODBC]
- result sets [ODBC], row status array
ms.assetid: a069b979-5108-4905-932f-8ae8e7905ff2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20e1632e8da765b0da2785bd846b67d13ebe01ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302361"
---
# <a name="number-of-rows-fetched-and-status"></a>Anzahl von abgerufenen Zeilen und Status
Wenn das SQL_ATTR_ROWS_FETCHED_PTR Anweisungsattribut festgelegt wurde, gibt es einen Puffer an, der die Anzahl der Zeilen zurückgibt, die vom Aufruf von **SQLFetch** oder **SQLFetchScroll**abgerufen wurden, sowie Fehlerzeilen. (Diese Zahl ist eine Anzahl aller Zeilen, die nicht den Status SQL_ROW_NO_ROWS haben.) Nach einem Aufruf von **SQLBulkOperations** oder **SQLSetPos**enthält der Puffer die Anzahl der Zeilen, die von einem Massenvorgang betroffen waren, der von der Funktion ausgeführt wurde. Wenn das SQL_ATTR_ROW_STATUS_PTR Anweisungsattribut festgelegt wurde, gibt **SQLFetch** oder **SQLFetchScroll** das *Zeilenstatusarray zurück,* das den Status jeder zurückgegebenen Zeile bereitstellt. Beide Puffer, auf die durch diese Felder verwiesen wird, werden von der Anwendung zugewiesen und vom Treiber aufgefüllt. Eine Anwendung muss sicherstellen, dass diese Zeiger gültig bleiben, bis der Cursor geschlossen wird.  
  
 Einträge im Zeilenstatusarray geben an, ob jede Zeile erfolgreich abgerufen wurde, ob sie seit dem letzten Abruf aktualisiert, hinzugefügt oder gelöscht wurde und ob beim Abrufen der Zeile ein Fehler aufgetreten ist. Wenn **SQLFetch** oder **SQLFetchScroll** beim Abrufen einer Zeile eines mehrreihigen Rowsets einen Fehler auffindet oder **SQLBulkOperations** mit einem *Operation-Argument* von SQL_FETCH_BY_BOOKMARK beim Ausführen eines Massenabrufs auf einen Fehler stößt, legt es den entsprechenden Wert im Zeilenstatusarray auf SQL_ROW_ERROR fest, setzt das Abrufen von Zeilen fort und gibt SQL_SUCCESS_WITH_INFO zurück. Weitere Informationen zur Fehlerbehandlung und zum Zeilenstatusarray finden Sie in den Funktionsbeschreibungen [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) und [SQLFetchScroll.](../../../odbc/reference/syntax/sqlfetchscroll-function.md)
