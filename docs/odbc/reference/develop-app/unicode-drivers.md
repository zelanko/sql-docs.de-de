---
title: Unicode-Treiber | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], drivers
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: 3b4742d5-74fb-4aff-aa21-d83a0064d73d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aabdd899d78c1141716725d57e343dc002dc96ad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284352"
---
# <a name="unicode-drivers"></a>Unicode-Treiber
Ob ein Treiber ein Unicode-Treiber oder ein ANSI-Treiber sein soll, hängt vollständig von der Art der Datenquelle ab. Wenn die Datenquelle Unicode-Daten unterstützt, sollte der Treiber ein Unicode-Treiber sein. Wenn die Datenquelle nur ANSI-Daten unterstützt, sollte der Treiber ein ANSI-Treiber bleiben.  
  
 Ein Unicode-Treiber muss **SQLConnectW** exportieren, um vom Treiber-Manager als Unicode-Treiber erkannt zu werden.  
  
 Ein Unicode-Treiber muss Unicode-Funktionen (mit dem Suffix *W*) akzeptieren und Unicode-Daten speichern. Es kann auch ANSI-Funktionen akzeptieren, ist aber nicht erforderlich. (Der Treiber-Manager gibt keinen ANSI-Funktionsaufruf mit dem *Suffix A* an den Treiber weiter, sondern konvertiert ihn in einen ANSI-Funktionsaufruf ohne suffix und übergibt ihn dann an den Treiber.)  
  
 Ein Unicode-Treiber muss in der Lage sein, Ergebnismengen in Unicode oder ANSI zurückzugeben, abhängig von der Bindung der Anwendung. Wenn eine Anwendung an SQL_C_CHAR bindet, muss der Unicode-Treiber SQL_WCHAR Daten in SQL_CHAR konvertieren. Der Treiber-Manager ordnet SQL_C_WCHAR SQL_C_CHAR für ANSI-Treiber zu, führt jedoch keine Zuordnung für Unicode-Treiber aus.  
  
> [!NOTE]  
>  Beim Bestimmen des Treibertyps ruft der Treiber-Manager **SQLSetConnectAttr** auf und legt das attribut SQL_ATTR_ANSI_APP zur Verbindungszeit fest. Wenn die Anwendung ANSI-APIs verwendet, wird SQL_ATTR_ANSI_APP auf SQL_AA_TRUE festgelegt, und wenn sie Unicode verwendet, wird sie auf den Wert SQL_AA_FALSE festgelegt. Dieses Attribut wird verwendet, damit der Treiber je nach Anwendungstyp ein anderes Verhalten aufweisen kann. Das Attribut kann nicht direkt von der Anwendung festgelegt werden und wird von **SQLGetConnectAttr**nicht unterstützt. Wenn ein Treiber das gleiche Verhalten sowohl für ANSI- als auch für Unicode-Anwendungen aufweist, sollte er SQL_ERROR für dieses Attribut zurückgeben. Wenn der Treiber SQL_SUCCESS zurückgibt, trennt der Treiber-Manager ANSI- und Unicode-Verbindungen, wenn Verbindungspooling verwendet wird.
