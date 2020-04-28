---
title: Löschen von Zeilen durch Lesezeichen mit SQLBulkOperations | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b6a4c1b24ee276c86175392eb45ac5ce0aa45e5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305961"
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Löschen von Zeilen durch Textmarken mit SQLBulkOperations
Beim Löschen einer Zeile anhand eines Lesezeichens bewirkt **SQLBulkOperations** , dass die Datenquelle eine oder mehrere ausgewählte Zeilen der Tabelle löscht. Die Zeilen werden durch das Lesezeichen in einer gebundenen Lesezeichen Spalte identifiziert.  
  
 Zum Löschen von Zeilen durch Lesezeichen mit **SQLBulkOperations**führt die Anwendung Folgendes aus:  
  
1.  Ruft die Lesezeichen aller zu löschenden Zeilen ab und speichert Sie zwischen. Wenn mehr als ein Lesezeichen und eine spaltenweise Bindung verwendet werden, werden die Lesezeichen in einem Array gespeichert. Wenn mehr als ein Lesezeichen vorhanden ist und die zeilenweise Bindung verwendet wird, werden die Lesezeichen in einem Array von Zeilen Strukturen gespeichert.  
  
2.  Legt das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungs Attribut auf die Anzahl von Lesezeichen fest und bindet den Puffer mit dem Lesezeichen Wert oder das Array von Lesezeichen an die Spalte 0.  
  
3.  Ruft **SQLBulkOperations** auf, wobei der *Vorgang* auf SQL_DELETE_BY_BOOKMARK festgelegt ist.
