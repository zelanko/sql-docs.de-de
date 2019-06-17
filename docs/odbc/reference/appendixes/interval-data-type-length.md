---
title: Länge des Datentyps Interval | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16d0590d3297b52891bf399822ce984674022583
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188918"
---
# <a name="interval-data-type-length"></a>Länge des Datentyps „Intervall“
Die folgenden Regeln werden verwendet, um zu bestimmen, die Länge eines Intervall-Datentyps in Zeichen. Länge wird als Anzahl der Zeichen angegeben. Die Anzahl der Bytes, hängt von den Zeichensatz ab. Die Länge der umfasst die folgenden Werte addiert:  
  
-   Zwei Zeichen für jedes Feld in das Intervall, das nicht das Feld "führende" ist.  
  
-   Der führende Feld muss die Anzahl der Zeichen, die die ausdrückliche oder implizite führende Genauigkeit ist. Wenn die führende Genauigkeit nicht angegeben wird, ist der Standardwert 2 auf.  
  
-   Ein Zeichen für das Trennzeichen zwischen den Feldern.  
  
-   1 plus die Genauigkeit Sie ausdrücklich oder konkludent. Wenn die Genauigkeit nicht angegeben wird, ist der Standardwert 6.  
  
 Bestimmte Länge Spaltenwerte für jeden Datentyp Interval befinden sich [Spaltengröße](../../../odbc/reference/appendixes/column-size.md).
