---
title: Aktualisieren von Zeilen durch Lesezeichen mit SQLBulkOperations | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283198"
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>Aktualisieren von Zeilen durch Textmarken mit SQLBulkOperations
Beim Aktualisieren einer Zeile anhand eines Lesezeichens führt **SQLBulkOperations** zum Aktualisieren der Datenquelle eine oder mehrere Zeilen der Tabelle. Die Zeilen werden durch das Lesezeichen in einer gebundenen Lesezeichen Spalte identifiziert. Die Zeile wird mit Daten in den Anwendungs Puffern für jede gebundene Spalte aktualisiert (es sei denn, der Wert im Längen-/Indikatorpuffer für eine Spalte ist SQL_COLUMN_IGNORE). Ungebundene Spalten werden nicht aktualisiert.  
  
 Zum Aktualisieren von Zeilen mithilfe von Lesezeichen mit **SQLBulkOperations**ist die Anwendung:  
  
1.  Ruft die Lesezeichen aller zu aktualisierenden Zeilen ab und speichert Sie zwischen. Wenn mehr als ein Lesezeichen und eine spaltenweise Bindung verwendet werden, werden die Lesezeichen in einem Array gespeichert. Wenn mehr als ein Lesezeichen vorhanden ist und die zeilenweise Bindung verwendet wird, werden die Lesezeichen in einem Array von Zeilen Strukturen gespeichert.  
  
2.  Legt das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungs Attribut auf die Anzahl von Lesezeichen fest und bindet den Puffer mit dem Lesezeichen Wert oder das Array von Lesezeichen an die Spalte 0.  
  
3.  Platziert die neuen Datenwerte in den rowsetpuffern. Weitere Informationen zum Senden von Long-Daten mit **SQLBulkOperations**finden Sie unter [Long Data und SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
4.  Legt den Wert im Längen-/Indikatorpuffer jeder Spalte nach Bedarf fest. Dies ist die Byte Länge der Daten oder SQL_NTS für Spalten, die an Zeichen folgen Puffer gebunden sind, die Byte Länge der Daten für Spalten, die an binäre Puffer gebunden sind, und SQL_NULL_DATA für alle Spalten, die auf NULL festgelegt werden sollen.  
  
5.  Legt den Wert im Längen-/Indikatorpuffer der Spalten fest, die nicht auf SQL_COLUMN_IGNORE aktualisiert werden sollen. Obwohl die Anwendung diesen Schritt überspringen und vorhandene Daten erneut senden kann, ist dies ineffizient, und es besteht das Risiko, dass Werte an die Datenquelle gesendet werden, die beim Lesen abgeschnitten wurden.  
  
6.  Ruft **SQLBulkOperations** auf, wobei das *Vorgangs* Argument auf SQL_UPDATE_BY_BOOKMARK festgelegt ist.  
  
 Für jede Zeile, die als Update an die Datenquelle gesendet wird, sollten die Anwendungs Puffer gültige Zeilendaten aufweisen. Wenn die Anwendungs Puffer durch Abrufen ausgefüllt wurden und ein Zeilen Status Array beibehalten wurde und der Statuswert für eine Zeile SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW ist, könnten ungültige Daten an die Datenquelle gesendet werden.
