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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d1c31ef622281b4f52f62ca3867c5afa7dcae8ca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680788"
---
# <a name="updating-data-with-sqlsetpos"></a>Aktualisieren von Daten mit SQLSetPos
Anwendungen können aktualisieren oder löschen Sie eine beliebige Zeile im Rowset mit **SQLSetPos**. Aufrufen von **SQLSetPos** ist eine praktische Alternative zum Erstellen und Ausführen einer SQL-Anweisung. Sie können einen ODBC-Treiber positionierte Updates zu unterstützen, auch wenn die Datenquelle positionierte SQL-Anweisungen nicht unterstützt. Es ist Teil des Paradigmas Zugriff auf die vollständige Datenbank mithilfe von Funktionsaufrufen zu erreichen.  
  
 **SQLSetPos** greift auf das aktuelle Rowset und kann verwendet werden, nur nach einem Aufruf von **SQLFetchScroll**. Die Anwendung gibt die Nummer der Zeile zu aktualisieren, löschen oder einfügen, und ruft der Treiber die neuen Daten für diese Zeile aus dem Rowset-Puffer. **SQLSetPos** kann auch verwendet werden, um eine bestimmte Zeile als die aktuelle Zeile festzulegen oder eine bestimmte Zeile im Rowset aus der Datenquelle zu aktualisieren.  
  
 Rowsetgröße wird durch einen Aufruf von **SQLSetStmtAttr** mit einer *Attribut* SQL_ATTR_ROW_ARRAY_SIZE Argument. **SQLSetPos** verwendet eine neue Rowsetgröße, jedoch nur nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**. Wenn die Rowsetgröße geändert wird, z. B. **SQLSetPos** wird aufgerufen, und klicken Sie dann **SQLFetch** oder **SQLFetchScroll** aufgerufen wird, und der Aufruf von **SQLSetPos** wird verwendet, während die alte Rowsetgröße **SQLFetch** oder **SQLFetchScroll** die neue Rowsetgröße verwendet.  
  
 Die erste Zeile im Rowset ist die Zeile 1. Die *RowNumber* -Argument in **SQLSetPos** muss eine Zeile im Rowset identifizieren, also muss sein Wert im Bereich zwischen 1 und die Anzahl der Zeilen, die zuletzt abgerufen wurden (die möglicherweise kleiner als der Größe des Rowsets). Wenn *RowNumber* gleich 0 ist, der Vorgang gilt für jede Zeile im Rowset.  
  
 Da die meisten Interaktion mit relationalen Datenbanken über SQL und erfolgt **SQLSetPos** wird allgemein nicht unterstützt. Treiber kann jedoch problemlos emulieren, sie durch Erstellen und Ausführen einer **UPDATE** oder **löschen** Anweisung.  
  
 Um zu bestimmen, welche Vorgänge **SQLSetPos** unterstützt werden, um eine Anwendung ruft **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 Informationsoption (je nach Art des Cursors).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Löschen von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
