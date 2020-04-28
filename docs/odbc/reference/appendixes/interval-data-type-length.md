---
title: Länge des Intervall Datentyps | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284320"
---
# <a name="interval-data-type-length"></a>Länge des Datentyps „Intervall“
Die folgenden Regeln werden verwendet, um die Länge eines Intervall Datentyps in Zeichen zu bestimmen. Die Länge wird als Anzahl von Zeichen ausgedrückt. Die Anzahl der Bytes ist abhängig vom Zeichensatz. Die Länge schließt die folgenden hinzugefügten Werte ein:  
  
-   Zwei Zeichen für jedes Feld in dem Intervall, das nicht das führende Feld ist.  
  
-   Für das führende Feld die Anzahl von Zeichen, die die schnelle oder implizite führende Genauigkeit ist. Wenn die führende Genauigkeit nicht angegeben wird, ist der Standardwert 2.  
  
-   Ein Zeichen für das Trennzeichen zwischen den Feldern.  
  
-   Ein Plus der ausdrücklichen oder impliziten Sekunden Genauigkeit. Wenn die Genauigkeit der Sekunden nicht angegeben wird, ist der Standardwert 6.  
  
 Bestimmte Spalten Längenwerte für die einzelnen interval-Datentypen sind in der [Spaltengröße](../../../odbc/reference/appendixes/column-size.md)enthalten.
