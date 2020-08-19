---
description: Wurde ein Resultset erstellt?
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
ms.openlocfilehash: 57b65c254f48d9c3f5078c3b2c1f576ae54d4740
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421384"
---
# <a name="was-a-result-set-created"></a>Wurde ein Resultset erstellt?
In den meisten Fällen wissen die Anwendungsprogrammierer, ob die von Ihrer Anwendung ausgeführten Anweisungen ein Resultset erstellen werden. Dies ist der Fall, wenn die Anwendung hart codierte SQL-Anweisungen verwendet, die vom Programmierer geschrieben wurden. Dies ist normalerweise der Fall, wenn die Anwendung SQL-Anweisungen zur Laufzeit erstellt: der Programmierer kann problemlos Code einschließen, der Flags, ob eine **Select** -Anweisung oder eine **Insert** -Anweisung erstellt wird. In einigen Situationen kann der Programmierer möglicherweise nicht wissen, ob eine-Anweisung ein Resultset erstellt. Dies trifft zu, wenn die Anwendung eine Möglichkeit für den Benutzer bietet, eine SQL-Anweisung einzugeben und auszuführen. Dies trifft auch zu, wenn die Anwendung zur Laufzeit eine-Anweisung erstellt, um eine Prozedur auszuführen.  
  
 In solchen Fällen wird von der Anwendung **SQLNumResultCols** aufgerufen, um die Anzahl der Spalten im Resultset zu ermitteln. Wenn dieser Wert 0 ist, hat die Anweisung kein Resultset erstellt. Wenn es sich um eine beliebige andere Zahl handelt, hat die Anweisung ein Resultset erstellt.  
  
 Die Anwendung kann **SQLNumResultCols** jederzeit nach der Vorbereitung oder Ausführung der Anweisung abrufen. Da jedoch einige Datenquellen die Resultsets, die von vorbereiteten-Anweisungen erstellt werden, nicht leicht beschreiben können, wird die Leistung beeinträchtigt, wenn **SQLNumResultCols** aufgerufen wird, nachdem eine Anweisung vorbereitet wurde, aber bevor Sie ausgeführt wird.  
  
 Einige Datenquellen unterstützen auch die Ermittlung der Anzahl von Zeilen, die von einer SQL-Anweisung in einem Resultset zurückgegeben werden. Zu diesem Zweck wird von der Anwendung **SQLRowCount**aufgerufen. Welche Zeilen Anzahl dargestellt wird, wird durch die Einstellung der Option SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 oder SQL_STATIC_CURSOR_ATTRIBUTES2 (abhängig vom Typ des Cursors) angezeigt, die durch einen **SQLGetInfo**-Befehl zurückgegeben wird. Diese Bitmaske gibt für jeden Cursortyp an, ob die zurückgegebene Zeilen Anzahl genau, ungefähre Werte oder überhaupt nicht verfügbar ist. Ob die Zeilen Anzahl für statische oder keysetgesteuerte Cursor von Änderungen betroffen ist, die über **SQLBulkOperations** oder **SQLSetPos**durchgeführt werden, oder durch positionierte UPDATE-oder DELETE-Anweisungen, hängt von anderen Bits ab, die von den oben aufgeführten Options Argumenten zurückgegeben werden. Weitere Informationen finden Sie in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion.
