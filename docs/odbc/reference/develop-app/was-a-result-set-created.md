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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db287e729678f54aaf637950c89c724724678f08
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208394"
---
# <a name="was-a-result-set-created"></a>Wurde ein Resultset erstellt?
In den meisten Fällen kennen Anwendungsprogrammierer an, ob die Anweisungen aus, wenn, die Ihre Anwendung ausgeführt wird, ein Resultset erstellt werden. Dies ist der Fall, wenn die Anwendung auf hartcodierte SQL-Anweisungen, die durch den Programmierer verwendet. Es ist normalerweise der Fall, wenn die Anwendung SQL-Anweisungen zur Laufzeit erstellt: Der Programmierer kann problemlos enthalten Code, der kennzeichnet, ob eine **wählen** Anweisung oder ein **einfügen** -Anweisung erstellt wird. In einigen Fällen kann nicht der Programmierer wissen, ob eine Anweisung ein Resultset erstellt. Dies gilt, wenn die Anwendung bietet eine Möglichkeit für den Benutzer zum eingeben und Ausführen einer SQL-Anweisung. Es ist auch "true", wenn die Anwendung eine Anweisung zur Laufzeit zum Ausführen einer Prozedur erstellt wird.  
  
 In solchen Fällen die Anwendung ruft **SQLNumResultCols** um die Anzahl der Spalten im Resultset zu ermitteln. Wenn dies 0 ist, die Anweisung ein Resultset; nicht erstellt werden Wenn sie jede andere Zahl ist, hat die Anweisung ein Resultset erstellt.  
  
 Die Anwendung kann Aufrufen **SQLNumResultCols** zu einem beliebigen Zeitpunkt nach dem die Anweisung vorbereitet oder ausgeführt wurde. Aber da es sich bei einigen Datenquellen ganz einfach die Resultsets nicht beschreiben, die von vorbereiteten Anweisungen erstellt werden, Leistung wird beeinträchtigt werden, wenn **SQLNumResultCols** wird aufgerufen, nachdem eine Anweisung vorbereitet wurde, aber bevor er ausgeführt wird.  
  
 Einige Datenquellen unterstützen auch das Bestimmen der Anzahl der Zeilen, die eine SQL-Anweisung in einem Resultset zurückgibt. Ruft die Anwendung dazu **SQLRowCount**. Genau wie die Anzahl der Zeilen darstellt wird von der Einstellung der Option "SQL_DYNAMIC_CURSOR_ATTRIBUTES2 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 oder SQL_STATIC_CURSOR_ATTRIBUTES2" (je nach Art des Cursors) angegeben werden. durch einen Aufruf zurückgegebenen **SQLGetInfo**. Bitmaske für jeden Cursortyp gibt an, ob die Anzahl der Zeilen zurückgegeben, genau, ungefähren wird, oder es ist gar nicht verfügbar. Ob die Zeilenanzahl für statische oder keysetgesteuerte Cursor auf Änderungen, die über unterliegen **SQLBulkOperations** oder **SQLSetPos**, oder durch positioniertes Update oder Delete-Anweisungen, hängt vom restlichen Bits durch die gleichen Optionsargumente, die zuvor aufgeführten zurückgegeben. Weitere Informationen finden Sie unter den [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung.
