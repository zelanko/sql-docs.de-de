---
title: Einfügen von Zeilen mit SQLBulkOperations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a6fa384292f02026b8390aa92525144dce6f549b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300110"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Einfügen von Zeilen mit SQLBulkOperations
Das Einfügen von Daten mit **SQLBulkOperations** ähnelt dem Aktualisieren von Daten mit **SQLBulkOperations,** da Daten aus den gebundenen Anwendungspuffern verwendet werden.  
  
 Damit jede Spalte in der neuen Zeile einen Wert hat, müssen alle gebundenen Spalten mit dem Längen-/Indikatorwert SQL_COLUMN_IGNORE und alle ungebundenen Spalten entweder NULL-Werte akzeptieren oder einen Standardwert aufweisen.  
  
 Um Zeilen mit **SQLBulkOperations**einzufügen, führt die Anwendung die folgenden Schritte aus:  
  
1.  Legt das Attribut SQL_ATTR_ROW_ARRAY_SIZE Anweisung auf die Anzahl der einzufügenden Zeilen fest und platziert die neuen Datenwerte in den gebundenen Anwendungspuffern. Informationen zum Senden langer Daten mit **SQLBulkOperations**finden Sie unter [Long Data und SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Legt den Wert im Längen-/Indikatorpuffer jeder Spalte nach Bedarf fest. Dies ist die Bytelänge der Daten oder SQL_NTS für Spalten, die an Zeichenfolgenpuffer gebunden sind, die Bytelänge der Daten für Spalten, die an Binärpuffer gebunden sind, und SQL_NULL_DATA für alle Spalten, die auf NULL festgelegt werden sollen. Die Anwendung legt den Wert im Längen-/Indikatorpuffer der Spalten, die auf den Standardwert (falls vorhanden) oder NULL (falls nicht vorhanden) auf SQL_COLUMN_IGNORE festgelegt werden.  
  
3.  Ruft **SQLBulkOperations** auf, wobei das *Argument Operation* auf SQL_ADD festgelegt ist.  
  
 Nachdem **SQLBulkOperations** zurückgegeben wurde, bleibt die aktuelle Zeile unverändert. Wenn die Lesezeichenspalte (Spalte 0) gebunden ist, gibt **SQLBulkOperations** die Lesezeichen der eingefügten Zeilen im Rowsetpuffer zurück, der an diese Spalte gebunden ist.
