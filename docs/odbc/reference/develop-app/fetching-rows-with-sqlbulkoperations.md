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
ms.openlocfilehash: 60b6673c4a6d618e52c78b48fe7307c20c8628f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069843"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Abrufen von Zeilen mit SQLBulkOperations
Daten können mithilfe von Lesezeichen durch einen **SQLBulkOperations** -Befehl wieder in ein Rowset abgerufen werden. Die Zeilen, die abgerufen werden sollen, werden durch die Lesezeichen in einer gebundenen Lesezeichen Spalte identifiziert. Spalten mit dem Wert SQL_COLUMN_IGNORE werden nicht abgerufen.  
  
 Um Massen Abruf **Vorgänge mit SQLBulkOperations**auszuführen, führt die Anwendung die folgenden Schritte aus:  
  
1.  Ruft die Lesezeichen aller zu aktualisierenden Zeilen ab und speichert Sie zwischen. Wenn mehr als ein Lesezeichen und eine spaltenweise Bindung verwendet werden, werden die Lesezeichen in einem Array gespeichert. Wenn mehr als ein Lesezeichen vorhanden ist und die zeilenweise Bindung verwendet wird, werden die Lesezeichen in einem Array von Zeilen Strukturen gespeichert.  
  
2.  Legt das Attribut der SQL_ATTR_ROW_ARRAY_SIZE Anweisung auf die Anzahl der abzurufenden Zeilen fest und bindet den Puffer mit dem Lesezeichen Wert oder das Array von Lesezeichen an die Spalte 0.  
  
3.  Legt den Wert im Längen-/Indikatorpuffer jeder Spalte nach Bedarf fest. Dies ist die Byte Länge der Daten oder SQL_NTS für Spalten, die an Zeichen folgen Puffer gebunden sind, die Byte Länge der Daten für Spalten, die an binäre Puffer gebunden sind, und SQL_NULL_DATA für alle Spalten, die auf NULL festgelegt werden sollen. Die Anwendung legt den Wert im Längen-/Indikatorpuffer der Spalten fest, die auf ihren Standardwert festgelegt werden sollen (sofern vorhanden), oder NULL (falls nicht), um SQL_COLUMN_IGNORE.  
  
4.  Ruft **SQLBulkOperations** auf, wobei das *Vorgangs* Argument auf SQL_FETCH_BY_BOOKMARK festgelegt ist.  
  
 Es ist nicht erforderlich, dass die Anwendung das Zeilen Vorgangs Array verwendet, um zu verhindern, dass der Vorgang für bestimmte Spalten ausgeführt wird. Die Anwendung wählt die Zeilen aus, die Sie abrufen möchten, indem Sie nur die Lesezeichen für diese Zeilen in das gebundene Lesezeichen Array kopiert.
