---
title: Wurde ein Resultset erstellt? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], determining if created
ms.assetid: 4a83b8cb-2d57-4e64-b497-80bd587ee1f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c171a154dd16a291c5dbe1dcade8c01ea95fb084
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294548"
---
# <a name="was-a-result-set-created"></a>Wurde ein Resultset erstellt?
In den meisten Fällen wissen Anwendungsprogrammierer, ob die Anweisungen, die ihre Anwendung ausführt, eine Ergebnismenge erstellen. Dies ist der Fall, wenn die Anwendung hartcodierte SQL-Anweisungen verwendet, die vom Programmierer geschrieben wurden. Dies ist in der Regel der Fall, wenn die Anwendung SQL-Anweisungen zur Laufzeit erstellt: Der Programmierer kann problemlos Code einschließen, der kennzeichnet, ob eine **SELECT-Anweisung** oder eine **INSERT-Anweisung** erstellt wird. In einigen Situationen kann der Programmierer unmöglich wissen, ob eine Anweisung eine Ergebnismenge erstellt. Dies gilt, wenn die Anwendung dem Benutzer die Möglichkeit bietet, eine SQL-Anweisung einzugeben und auszuführen. Dies gilt auch, wenn die Anwendung zur Laufzeit eine Anweisung erstellt, um eine Prozedur auszuführen.  
  
 In solchen Fällen ruft die Anwendung **SQLNumResultCols auf,** um die Anzahl der Spalten im Resultset zu bestimmen. Wenn dies 0 ist, hat die Anweisung kein Resultset erstellt. Wenn es sich um eine andere Zahl handelt, hat die Anweisung ein Resultset erstellt.  
  
 Die Anwendung kann **SQLNumResultCols** jederzeit aufrufen, nachdem die Anweisung vorbereitet oder ausgeführt wurde. Da jedoch einige Datenquellen die Resultsets, die durch vorbereitete Anweisungen erstellt werden, nicht einfach beschreiben können, leidet die Leistung, wenn **SQLNumResultCols** aufgerufen wird, nachdem eine Anweisung vorbereitet, aber ausgeführt wird.  
  
 Einige Datenquellen unterstützen auch das Bestimmen der Anzahl der Zeilen, die eine SQL-Anweisung in einem Resultset zurückgibt. Dazu ruft die Anwendung **SQLRowCount**auf. Genau das, was die Zeilenanzahl darstellt, wird durch die Einstellung der Option SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 oder SQL_STATIC_CURSOR_ATTRIBUTES2 (je nach Typ des Cursors) angezeigt, die von einem Aufruf von **SQLGetInfo**zurückgegeben wird. Diese Bitmaske gibt für jeden Cursortyp an, ob die zurückgegebene Zeilenanzahl genau, ungefähr oder gar nicht verfügbar ist. Ob die Zeilenanzahl für statische oder keysetgesteuerte Cursor von Änderungen beeinflusst wird, die über **SQLBulkOperations** oder **SQLSetPos**oder durch positionierte Aktualisierungs- oder Löschanweisungen vorgenommen wurden, hängt von anderen Bits ab, die von denselben zuvor aufgeführten Optionsargumenten zurückgegeben werden. Weitere Informationen finden Sie in der [SQLGetInfo-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetinfo-function.md)
