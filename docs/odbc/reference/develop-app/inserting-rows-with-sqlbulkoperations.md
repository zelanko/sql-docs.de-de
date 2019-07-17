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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 05b8f71d6f4c885c7dc64887dd92b1f600005ca7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138920"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Einfügen von Zeilen mit SQLBulkOperations
Einfügen von Daten mit **SQLBulkOperations** ähnelt dem Aktualisieren von Daten mit **SQLBulkOperations** weil Daten aus den Puffern für gebundene Anwendung verwendet.  
  
 Jede Spalte in der neuen Zeile einen Wert hat, alle Spalten mit dem Wert Längenindikator/SQL_COLUMN_IGNORE gebunden und alle ungebundene Spalten NULL-Werte annehmen müssen oder einen Standardwert aufweisen.  
  
 Zum Einfügen von Zeilen mit **SQLBulkOperations**, die Anwendung führt Folgendes:  
  
1.  Legt das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf die Anzahl der einzufügenden Zeilen und die neuen Datenwerte in den Puffern mit gebundenen Anwendung platziert. Informationen zum Senden von long-Daten mit **SQLBulkOperations**, finden Sie unter [Long-Daten, SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Legt den Wert in den Längen-/Indikatorpuffer für jede Spalte, nach Bedarf. Dies ist die Bytelänge der Daten oder SQL_NTS für Spalten gebunden auf Zeichenfolgepuffer,-die Bytelänge der Daten für Spalten gebunden, binärer Puffer und SQL_NULL_DATA für alle Spalten auf NULL festgelegt werden. Die Anwendung legt den Wert in den Längen-/Indikatorpuffer diese Spalten, die die Standardwerte festgelegt werden (falls vorhanden) oder NULL (falls es sich bei einer nicht der Fall ist), um die SQL_COLUMN_IGNORE.  
  
3.  Aufrufe **SQLBulkOperations** mit der *Vorgang* -Argument auf SQL_ADD festgelegt.  
  
 Nach dem **SQLBulkOperations** zurückgegeben wird, die aktuelle Zeile unverändert ist. Wenn die (0) Lesezeichenspalte gebunden ist, **SQLBulkOperations** gibt die eingefügten Zeilen im Puffer Rowset Lesezeichen an diese Spalte gebunden.
