---
title: Löschen von Zeilen nach Lesezeichen mit SQLBulkOperations | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305961"
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Löschen von Zeilen durch Textmarken mit SQLBulkOperations
Beim Löschen einer Zeile nach Lesezeichen führt **SQLBulkOperations** dazu, dass die Datenquelle eine oder mehrere ausgewählte Zeilen der Tabelle löscht. Die Zeilen werden durch die Textmarke in einer gebundenen Lesezeichenspalte identifiziert.  
  
 Um Zeilen nach Lesezeichen mit **SQLBulkOperations**zu löschen, führt die Anwendung die folgenden Schritte aus:  
  
1.  Ruft die Lesezeichen aller zu löschenden Zeilen ab und speichert sie zwischen. Wenn mehr als ein Lesezeichen vorhanden ist und eine spaltenweise Bindung verwendet wird, werden die Lesezeichen in einem Array gespeichert. Wenn mehr als eine Textmarke vorhanden ist und eine zeilenweise Bindung verwendet wird, werden die Lesezeichen in einem Array von Zeilenstrukturen gespeichert.  
  
2.  Legt das SQL_ATTR_ROW_ARRAY_SIZE Anweisungsattribut auf die Anzahl der Lesezeichen fest und bindet den Puffer, der den Lesezeichenwert oder das Array von Lesezeichen enthält, an Spalte 0.  
  
3.  Ruft **SQLBulkOperations** auf, wobei *der Vorgang* auf SQL_DELETE_BY_BOOKMARK festgelegt ist.
