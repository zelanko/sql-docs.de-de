---
title: Aktualisieren von Daten mit SQLSetPos | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating data
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16476a1e1007905f34ec2e70ce6032eb8d81fe7a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286160"
---
# <a name="updating-data-with-sqlsetpos"></a>Aktualisieren von Daten mit SQLSetPos
Anwendungen können jede Zeile im Rowset mit **SQLSetPos**aktualisieren oder löschen. Das Aufrufen von **SQLSetPos** ist eine bequeme Alternative zum Erstellen und Ausführen einer SQL-Anweisung. Ein ODBC-Treiber kann positionierte Updates auch dann unterstützen, wenn die Datenquelle keine positionierten SQL-Anweisungen unterstützt. Es ist Teil des Paradigmas, mithilfe von Funktionsaufrufen den gesamten Datenbankzugriff zu erreichen.  
  
 **SQLSetPos** funktioniert auf dem aktuellen Rowset und kann nur nach einem **SQLFetchScroll**-Aufrufvorgang verwendet werden. Die Anwendung gibt die Nummer der Zeile an, die aktualisiert, gelöscht oder eingefügt werden soll, und der Treiber ruft die neuen Daten für diese Zeile aus den rowsetpuffern ab. **SQLSetPos** können auch verwendet werden, um eine angegebene Zeile als aktuelle Zeile oder eine bestimmte Zeile im Rowset aus der Datenquelle zu aktualisieren.  
  
 Die Rowsetgröße wird durch einen Aufrufen von **SQLSetStmtAttr** mit dem *Attribut* Argument SQL_ATTR_ROW_ARRAY_SIZE festgelegt. **SQLSetPos** verwendet jedoch nur nach einem **SQLFetch** -oder **SQLFetchScroll**-Befehl eine neue Rowsetgröße. Wenn z. b. die Rowsetgröße geändert wird, wird **SQLSetPos** aufgerufen und dann **SQLFetch** oder **SQLFetchScroll** aufgerufen, und der Aufruf von **SQLSetPos** verwendet die alte Rowsetgröße, während **SQLFetch** oder **SQLFetchScroll** die neue Rowsetgröße verwendet.  
  
 Die erste Zeile im Rowset ist die Zeile 1. Das *RowNumber* -Argument in **SQLSetPos** muss eine Zeile im Rowset identifizieren. Das heißt, der Wert muss im Bereich zwischen 1 und der Anzahl von Zeilen liegen, die zuletzt abgerufen wurden (was möglicherweise kleiner als die Rowsetgröße ist). Wenn *RowNumber* 0 ist, gilt der Vorgang für jede Zeile im Rowset.  
  
 Da die meisten Interaktionen mit relationalen Datenbanken mit SQL durchgeführt werden, wird **SQLSetPos** nicht häufig unterstützt. Ein Treiber kann ihn jedoch problemlos emulieren, indem er eine **Update** -oder **Delete** -Anweisung erstellt und ausführt.  
  
 Um zu ermitteln, welche Vorgänge von **SQLSetPos** unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 Information (abhängig vom Cursortyp) auf.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Löschen von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
