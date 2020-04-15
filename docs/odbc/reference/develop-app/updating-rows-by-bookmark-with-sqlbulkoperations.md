---
title: Aktualisieren von Zeilen nach Lesezeichen mit SQLBulkOperations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], updating rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: c9ad82b7-8dba-45b0-bdb9-f4668b37c0d6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9c755297e8beadad92b5be81d78ca534bb96ecae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283198"
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>Aktualisieren von Zeilen durch Textmarken mit SQLBulkOperations
Beim Aktualisieren einer Zeile nach Lesezeichen macht **SQLBulkOperations** die Datenquelle eine oder mehrere Zeilen der Tabelle aktualisieren. Die Zeilen werden durch die Textmarke in einer gebundenen Lesezeichenspalte identifiziert. Die Zeile wird mithilfe von Daten in den Anwendungspuffern für jede gebundene Spalte aktualisiert (außer wenn der Wert im Längen-/Indikatorpuffer für eine Spalte SQL_COLUMN_IGNORE ist). Ungebundene Spalten werden nicht aktualisiert.  
  
 So aktualisieren Sie Zeilen nach Lesezeichen mit **SQLBulkOperations**, der Anwendung:  
  
1.  Ruft die Lesezeichen aller zu aktualisierenden Zeilen ab und speichert sie zwischen. Wenn mehr als ein Lesezeichen vorhanden ist und eine spaltenweise Bindung verwendet wird, werden die Lesezeichen in einem Array gespeichert. Wenn mehr als eine Textmarke vorhanden ist und eine zeilenweise Bindung verwendet wird, werden die Lesezeichen in einem Array von Zeilenstrukturen gespeichert.  
  
2.  Legt das SQL_ATTR_ROW_ARRAY_SIZE Anweisungsattribut auf die Anzahl der Lesezeichen fest und bindet den Puffer, der den Lesezeichenwert oder das Array von Lesezeichen enthält, an Spalte 0.  
  
3.  Platziert die neuen Datenwerte in den Rowsetpuffern. Informationen zum Senden langer Daten mit **SQLBulkOperations**finden Sie unter [Long Data und SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
4.  Legt den Wert im Längen-/Indikatorpuffer jeder Spalte nach Bedarf fest. Dies ist die Bytelänge der Daten oder SQL_NTS für Spalten, die an Zeichenfolgenpuffer gebunden sind, die Bytelänge der Daten für Spalten, die an Binärpuffer gebunden sind, und SQL_NULL_DATA für alle Spalten, die auf NULL festgelegt werden sollen.  
  
5.  Legt den Wert im Längen-/Indikatorpuffer der Spalten fest, die nicht auf SQL_COLUMN_IGNORE aktualisiert werden sollen. Obwohl die Anwendung diesen Schritt überspringen und vorhandene Daten erneut senden kann, ist dies ineffizient und besteht die Gefahr, dass Werte an die Datenquelle gesendet werden, die beim Lesen abgeschnitten wurden.  
  
6.  Ruft **SQLBulkOperations** auf, wobei das *Argument Operation* auf SQL_UPDATE_BY_BOOKMARK festgelegt ist.  
  
 Für jede Zeile, die als Aktualisierung an die Datenquelle gesendet wird, sollten die Anwendungspuffer über gültige Zeilendaten verfügen. Wenn die Anwendungspuffer durch Abrufen gefüllt wurden, wenn ein Zeilenstatusarray beibehalten wurde und der Statuswert für eine Zeile SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW ist, können ungültige Daten versehentlich an die Datenquelle gesendet werden.
