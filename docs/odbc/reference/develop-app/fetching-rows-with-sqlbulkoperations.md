---
title: Abrufen von Zeilen mit SQLBulkOperations | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae0b4c2114059cecaaf8f8825169300f131bd473
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305649"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Abrufen von Zeilen mit SQLBulkOperations
Daten können mithilfe von Lesezeichen durch einen Aufruf von **SQLBulkOperations** in ein Rowset neu abgerufen werden. Die zu holenden Zeilen werden durch die Lesezeichen in einer gebundenen Lesezeichenspalte identifiziert. Spalten mit dem Wert SQL_COLUMN_IGNORE werden nicht abgerufen.  
  
 Um Massenabrufe mit **SQLBulkOperations**durchzuführen, führt die Anwendung die folgenden Schritte aus:  
  
1.  Ruft die Lesezeichen aller zu aktualisierenden Zeilen ab und speichert sie zwischen. Wenn mehr als ein Lesezeichen vorhanden ist und eine spaltenweise Bindung verwendet wird, werden die Lesezeichen in einem Array gespeichert. Wenn mehr als eine Textmarke vorhanden ist und eine zeilenweise Bindung verwendet wird, werden die Lesezeichen in einem Array von Zeilenstrukturen gespeichert.  
  
2.  Legt das Attribut SQL_ATTR_ROW_ARRAY_SIZE Anweisung auf die Anzahl der abzurufenden Zeilen fest und bindet den Puffer, der den Lesezeichenwert oder das Array von Lesezeichen enthält, an Spalte 0.  
  
3.  Legt den Wert im Längen-/Indikatorpuffer jeder Spalte nach Bedarf fest. Dies ist die Bytelänge der Daten oder SQL_NTS für Spalten, die an Zeichenfolgenpuffer gebunden sind, die Bytelänge der Daten für Spalten, die an Binärpuffer gebunden sind, und SQL_NULL_DATA für alle Spalten, die auf NULL festgelegt werden sollen. Die Anwendung legt den Wert im Längen-/Indikatorpuffer der Spalten, die auf den Standardwert (falls vorhanden) oder NULL (falls nicht vorhanden) auf SQL_COLUMN_IGNORE festgelegt werden.  
  
4.  Ruft **SQLBulkOperations** auf, wobei das *Argument Operation* auf SQL_FETCH_BY_BOOKMARK festgelegt ist.  
  
 Die Anwendung muss das Zeilenoperationarray nicht verwenden, um zu verhindern, dass der Vorgang für bestimmte Spalten ausgeführt wird. Die Anwendung wählt die Zeilen aus, die sie abrufen möchte, indem sie nur die Lesezeichen für diese Zeilen in das gebundene Lesezeichenarray kopiert.
