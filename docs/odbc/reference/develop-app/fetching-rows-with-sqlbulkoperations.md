---
title: Abrufen von Zeilen mit SQLBulkOperations | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], fetching rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: 0efee2d6-ce94-411e-9976-97ba28b8da37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a99592210ff315db026d60b8743d4a3bca13c969
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47791538"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Abrufen von Zeilen mit SQLBulkOperations
Daten können in ein Rowset mithilfe von Lesezeichen erneut abgerufen werden, durch einen Aufruf von **SQLBulkOperations.** Die Zeilen abgerufen werden, werden durch die Lesezeichen in einer Lesezeichenspalte gebundene identifiziert. Spalten mit einem Wert von SQL_COLUMN_IGNORE werden nicht abgerufen.  
  
 Zum Ausführen von Massenladen Abrufvorgänge mit **SQLBulkOperations**, die Anwendung führt Folgendes:  
  
1.  Ruft ab und speichert die Lesezeichen aller Zeilen aktualisiert werden. Wenn mehrere Lesezeichen vorhanden ist, und spaltenbezogene Bindungen verwendet wird, werden die Lesezeichen in einem Array gespeichert. Wenn mehrere Lesezeichen vorhanden ist, und die zeilenweise Bindung wird verwendet, werden die Lesezeichen in ein Array von Zeilenstrukturen gespeichert.  
  
2.  Legt das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf die Anzahl der abzurufenden Zeilen aus, und bindet den Puffer mit der Lesezeichenwert, oder das Array von Lesezeichen, an die Spalte 0.  
  
3.  Legt den Wert in den Längen-/Indikatorpuffer für jede Spalte, nach Bedarf. Dies ist die Bytelänge der Daten oder SQL_NTS für Spalten gebunden auf Zeichenfolgepuffer,-die Bytelänge der Daten für Spalten gebunden, binärer Puffer und SQL_NULL_DATA für alle Spalten auf NULL festgelegt werden. Die Anwendung legt den Wert in den Längen-/Indikatorpuffer diese Spalten, die die Standardwerte festgelegt werden (falls vorhanden) oder NULL (falls es sich bei einer nicht der Fall ist), um die SQL_COLUMN_IGNORE.  
  
4.  Aufrufe **SQLBulkOperations** mit der *Vorgang* -Argument auf SQL_FETCH_BY_BOOKMARK festgelegt.  
  
 Besteht keine Notwendigkeit für die Anwendung auf die Zeile Operation-Array zu verwenden, um zu verhindern, dass den Vorgang für bestimmte Spalten ausgeführt werden soll. Die Anwendung wählt die Zeilen, die abgerufen werden nur die Lesezeichen für die Zeilen in die gebundene Lesezeichen-Array kopiert werden sollen.
