---
description: Anzahl von abgerufenen Zeilen und Status
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc328aab77d6e59db258c463a7dae1554f7d4c11
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429212"
---
# <a name="number-of-rows-fetched-and-status"></a>Anzahl von abgerufenen Zeilen und Status
Wenn das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungs Attribut festgelegt wurde, gibt es einen Puffer an, der die Anzahl der Zeilen zurückgibt, die durch den-Befehl von **SQLFetch** oder **SQLFetchScroll**abgerufen wurden, sowie Fehler Zeilen. (Diese Zahl ist eine Anzahl von Zeilen, die nicht den Status SQL_ROW_NO_ROWS haben.) Nach einem Aufrufen von **SQLBulkOperations** oder **SQLSetPos**enthält der Puffer die Anzahl der Zeilen, die von einem Massen Vorgang betroffen sind, der von der Funktion ausgeführt wurde. Wenn das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut festgelegt wurde, gibt **SQLFetch** oder **SQLFetchScroll** das *Zeilen Status Array zurück,* das den Status der einzelnen zurückgegebenen Zeilen bereitstellt. Beide Puffer, auf die von diesen Feldern verwiesen wird, werden von der Anwendung zugeordnet und vom Treiber aufgefüllt. Eine Anwendung muss sicherstellen, dass diese Zeiger gültig bleiben, bis der Cursor geschlossen wird.  
  
 Einträge im Zeilen Status Array geben an, ob die einzelnen Zeilen erfolgreich abgerufen wurden, ob Sie seit dem letzten Abruf aktualisiert, hinzugefügt oder gelöscht wurden und ob beim Abrufen der Zeile ein Fehler aufgetreten ist. Wenn **SQLFetch** oder **SQLFetchScroll** beim Abrufen einer Zeile eines mehrzeilige-Rowsets einen Fehler feststellt oder wenn **SQLBulkOperations** mit einem Vorgangs Argument von SQL_FETCH_BY_BOOKMARK beim Ausführen eines Massen Abruf *Vorgangs* einen Fehler feststellt, wird der entsprechende Wert im Zeilen Status Array auf SQL_ROW_ERROR festgelegt, das Abrufen von Zeilen wird fortgesetzt und SQL_SUCCESS_WITH_INFO zurückgegeben. Weitere Informationen zur Fehlerbehandlung und zum Zeilen Status Array finden Sie in den Beschreibungen der Funktionen [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) und [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) .
