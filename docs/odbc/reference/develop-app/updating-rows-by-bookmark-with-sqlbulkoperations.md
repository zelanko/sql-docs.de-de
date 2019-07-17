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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e9b10037883ef9cfa4051195270e6477c5cc04ee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091626"
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>Aktualisieren von Zeilen durch Textmarken mit SQLBulkOperations
Beim Aktualisieren einer Zeile durch Lesezeichen, **SQLBulkOperations** macht die Datenquelle, die eine oder mehrere Zeilen der Tabelle zu aktualisieren. Die Zeilen werden durch das Lesezeichen in einer Lesezeichenspalte gebundene identifiziert. Die Zeile mit Daten in den Puffern der Anwendung für jede gebundene Spalte (es sei denn, der Wert in den Längen-/Indikatorpuffer für eine Spalte SQL_COLUMN_IGNORE) aktualisiert. Ungebundene Spalten werden nicht aktualisiert werden.  
  
 Zum Aktualisieren von Zeilen durch Lesezeichen mit **SQLBulkOperations**, die Anwendung:  
  
1.  Ruft ab und speichert die Lesezeichen aller Zeilen aktualisiert werden. Wenn mehrere Lesezeichen vorhanden ist, und spaltenbezogene Bindungen verwendet wird, werden die Lesezeichen in einem Array gespeichert. Wenn mehrere Lesezeichen vorhanden ist, und die zeilenweise Bindung wird verwendet, werden die Lesezeichen in ein Array von Zeilenstrukturen gespeichert.  
  
2.  Legt das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf die Anzahl von Lesezeichen und bindet den Puffer mit der Lesezeichenwert, oder das Array von Lesezeichen, an die Spalte 0.  
  
3.  Stellen Sie die neuen Datenwerte in den Puffern Rowset. Informationen zum Senden von long-Daten mit **SQLBulkOperations**, finden Sie unter [Long-Daten, SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
4.  Legt den Wert in den Längen-/Indikatorpuffer für jede Spalte, nach Bedarf. Dies ist die Bytelänge der Daten oder SQL_NTS für Spalten gebunden auf Zeichenfolgepuffer,-die Bytelänge der Daten für Spalten gebunden, binärer Puffer und SQL_NULL_DATA für alle Spalten auf NULL festgelegt werden.  
  
5.  Legt den Wert in den Längen-/Indikatorpuffer dieser Spalten, die nicht auf SQL_COLUMN_IGNORE aktualisiert werden. Obwohl die Anwendung kann diesen Schritt überspringen und vorhandene Daten erneut zu senden, wird dies ist ineffizient und birgt das Risiko senden die Werte an die Datenquelle, die abgeschnitten wurden, beim Lesen.  
  
6.  Aufrufe **SQLBulkOperations** mit der *Vorgang* -Argument auf SQL_UPDATE_BY_BOOKMARK festgelegt.  
  
 Für jede Zeile, die mit der Datenquelle als Update gesendet wird, sollte die Anwendungspuffer gültigen Zeilendaten haben. Wenn die Anwendungspuffer mit einem Fetchvorgang, gefüllt wurden, wenn ein zeilenstatusarray gewahrt wurde und der Statuswert für eine Zeile SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW ist, konnte die ungültige Daten versehentlich an die Datenquelle gesendet werden.
