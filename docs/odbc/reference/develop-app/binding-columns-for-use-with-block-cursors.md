---
title: Binden von Spalten für die Verwendung mit Blockcursorn | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0ed819643e7ea818fc17c0fa317473afc8f5ca3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007865"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>Binden von Spalten für die Verwendung mit Blockcursorn
Da Blockcursor mehrere Zeilen zurückgeben, müssen Anwendungen, die sie verwenden ein Array von Variablen für die einzelnen Spalten anstelle einer einzelnen Variable binden. Diese Arrays werden zusammen als bezeichnet die *Rowset Puffer*. Es folgen die beiden Formate Bindung:  
  
-   Binden Sie ein Array für jede Spalte ein. Dies wird als bezeichnet *spaltenbezogene Bindungen* , da jede Data-Struktur (Array) Daten für eine einzelne Spalte enthält.  
  
-   Definieren Sie eine Struktur zum Speichern der Daten für eine gesamte Zeile und ein Array dieser Strukturen binden. Dies wird als bezeichnet *zeilenbezogene Bindungen* da jede Data-Struktur, die Daten für eine einzelne Zeile enthält.  
  
 Als wenn die Anwendung die einzelne Variablen an Spalten bindet, er ruft **SQLBindCol** Arrays an Spalten gebunden. Der einzige Unterschied ist, dass die Adressen übergeben des Arrays liegenden Adressen, nicht einzelne Variable Adressen. Die Anwendung legt fest, das SQL_BIND_BY_COLUMN-Anweisungsattribut, um anzugeben, ob es spaltenweise oder zeilenweise Binden verwendet wird. Angibt, ob verwendet die spaltenweise oder zeilenweise binden ist hauptsächlich eine Frage der anwendungseinstellung. Zeilenweise Bindung entspricht möglicherweise genauer der Anwendung Layout der Daten, die in diesem Fall würden sie eine bessere Leistung bereitstellen.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Spaltenweises Binden](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [Zeilenweises Binden](../../../odbc/reference/develop-app/row-wise-binding.md)
