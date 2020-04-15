---
title: IntervallDatentyplänge | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68bb4daa47cb58d5a0ff7b680a2d2154fb14b345
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284320"
---
# <a name="interval-data-type-length"></a>Länge des Datentyps „Intervall“
Die folgenden Regeln werden verwendet, um die Länge eines Intervalldatentyps in Zeichen zu bestimmen. Die Länge wird in der Anzahl der Zeichen ausgedrückt. Die Anzahl der Bytes hängt vom Zeichensatz ab. Die Länge enthält die folgenden Werte, die addiert werden:  
  
-   Zwei Zeichen für jedes Feld im Intervall, das nicht das führende Feld ist.  
  
-   Für das führende Feld die Anzahl der Zeichen, die die ausausdrücklichte oder implizite führende Genauigkeit ist. Wenn die führende Genauigkeit nicht angegeben ist, ist der Standardwert 2.  
  
-   Ein Zeichen für das Trennzeichen zwischen den Feldern.  
  
-   Eine plus die ausdrückliche oder implizierte Sekunden Präzision. Wenn die Sekundengenauigkeit nicht angegeben ist, ist der Standardwert 6.  
  
 Spezifische Spaltenlängenwerte für jeden Intervalldatentyp sind in [Spaltengröße](../../../odbc/reference/appendixes/column-size.md)enthalten.
