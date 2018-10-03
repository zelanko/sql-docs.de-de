---
title: Anzahl der abgerufenen Zeilen und Status | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab4830ddd56335959dd7049a1dabdcc3a0354213
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47808768"
---
# <a name="number-of-rows-fetched-and-status"></a>Anzahl von abgerufenen Zeilen und Status
Wenn das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut festgelegt wurde, gibt es einen Puffer, der die Anzahl der durch den Aufruf von abgerufenen Zeilen zurückgegeben **SQLFetch** oder **SQLFetchScroll**, und Zeilen. (Diese Zahl ist die Anzahl aller Zeilen, die nicht den Status SQL_ROW_NO_ROWS verfügen.) Nach einem Aufruf von **SQLBulkOperations** oder **SQLSetPos**, enthält der Puffer die Anzahl der Zeilen, die durch einen Massenvorgang ausgeführt, die von der Funktion betroffen waren. Wenn das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut festgelegt wurde, **SQLFetch** oder **SQLFetchScroll** gibt die *zeilenstatusarray,* dem bietet es sich um des Status der einzelnen zurückgegebene Zeile. Sowohl von den Puffern, verweist diese Felder sind von der Anwendung belegt und vom Treiber aufgefüllt. Eine Anwendung muss sicherstellen, dass diese Zeiger gültig bleiben, bis der Cursor geschlossen wird.  
  
 Einträge in der Zeile (Zustand) Status-Array, ob jede Zeile erfolgreich abgerufen wurde, ob sie aktualisiert wurde, hinzugefügt oder gelöscht, seit dem letzten Abruf wurde und ob Fehler beim Abrufen der Zeile. Wenn **SQLFetch** oder **SQLFetchScroll** tritt ein Fehler beim Abrufen einer Zeile eines mehrzeiligen Rowsets, oder wenn **SQLBulkOperations** mit einer *Vorgang*  Argument SQL_FETCH_BY_BOOKMARK es tritt ein Fehler beim Ausführen von Massenladen Fetch, wird der entsprechenden Wert in der zeilenstatusarray, SQL_ROW_ERROR, weiterhin das Abrufen von Zeilen und gibt SQL_SUCCESS_WITH_INFO zurück. Weitere Informationen zur Fehlerbehandlung und die zeilenstatusarray finden Sie unter den [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) und [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) Beschreibungen funktionieren.
