---
title: Bindungsspalten für die Verwendung mit Blockcursorn | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc7e527658a7d6945921510de898c648075c41fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284900"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>Binden von Spalten für die Verwendung mit Blockcursorn
Da Blockcursor mehrere Zeilen zurückgeben, müssen Anwendungen, die sie verwenden, ein Array von Variablen an jede Spalte anstelle einer einzelnen Variablen binden. Diese Arrays werden zusammen als *Rowsetpuffer*bezeichnet. Im Folgenden sind die beiden Bindungsstile zu finden:  
  
-   Binden Sie ein Array an jede Spalte. Dies wird als *spaltenweise Bindung* bezeichnet, da jede Datenstruktur (Array) Daten für eine einzelne Spalte enthält.  
  
-   Definieren Sie eine Struktur, um die Daten für eine ganze Zeile zu halten und ein Array dieser Strukturen zu binden. Dies wird als *zeilenweise Bindung* bezeichnet, da jede Datenstruktur die Daten für eine einzelne Zeile enthält.  
  
 Wie wenn die Anwendung einzelne Variablen an Spalten bindet, ruft sie **SQLBindCol auf,** um Arrays an Spalten zu binden. Der einzige Unterschied besteht darin, dass es sich bei den übergebenen Adressen um Arrayadressen und nicht um einzelne Variablenadressen handelt. Die Anwendung legt das SQL_BIND_BY_COLUMN-Anweisungsattribut fest, um anzugeben, ob eine spalten- oder zeilenweise Bindung verwendet wird. Ob spalten- oder zeilenweise Bindung verwendet werden soll, ist weitgehend eine Frage der Anwendungspräferenz. Die Zeilenweise Bindung könnte dem Datenlayout der Anwendung besser entsprechen, und in diesem Fall würde sie eine bessere Leistung bieten.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Spaltenweise Bindung](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [Zeilenbezogenes Binden](../../../odbc/reference/develop-app/row-wise-binding.md)
