---
title: Einfügen von Zeilen mit SQLBulkOperations | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300110"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Einfügen von Zeilen mit SQLBulkOperations
Das Einfügen von Daten mit **SQLBulkOperations** ähnelt dem Aktualisieren von Daten mit **SQLBulkOperations** , da Daten aus den gebundenen Anwendungs Puffern verwendet werden.  
  
 Damit jede Spalte in der neuen Zeile über einen Wert verfügt, müssen alle gebundenen Spalten mit dem Längen-/Indikatorwert SQL_COLUMN_IGNORE und alle ungebundenen Spalten entweder NULL-Werte akzeptieren oder einen Standardwert aufweisen.  
  
 Zum Einfügen von Zeilen mit **SQLBulkOperations**führt die Anwendung Folgendes aus:  
  
1.  Legt das SQL_ATTR_ROW_ARRAY_SIZE Statement-Attribut auf die Anzahl der einzufügenden Zeilen fest und platziert die neuen Datenwerte in den gebundenen Anwendungs Puffern. Weitere Informationen zum Senden von Long-Daten mit **SQLBulkOperations**finden Sie unter [Long Data und SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Legt den Wert im Längen-/Indikatorpuffer jeder Spalte nach Bedarf fest. Dies ist die Byte Länge der Daten oder SQL_NTS für Spalten, die an Zeichen folgen Puffer gebunden sind, die Byte Länge der Daten für Spalten, die an binäre Puffer gebunden sind, und SQL_NULL_DATA für alle Spalten, die auf NULL festgelegt werden sollen. Die Anwendung legt den Wert im Längen-/Indikatorpuffer der Spalten fest, die auf ihren Standardwert festgelegt werden sollen (sofern vorhanden), oder NULL (falls nicht), um SQL_COLUMN_IGNORE.  
  
3.  Ruft **SQLBulkOperations** auf, wobei das *Vorgangs* Argument auf SQL_ADD festgelegt ist.  
  
 Nachdem **SQLBulkOperations** zurückgegeben wurde, ist die aktuelle Zeile unverändert. Wenn die Lesezeichen Spalte (Spalte 0) gebunden ist, gibt **SQLBulkOperations** die Lesezeichen der eingefügten Zeilen im Rowset-Puffer zurück, der an diese Spalte gebunden ist.
