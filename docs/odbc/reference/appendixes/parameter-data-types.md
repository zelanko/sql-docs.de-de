---
title: Parameterdatentypen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: f29bb70937df32e03480c13c7ef739eb273f15eb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303581"
---
# <a name="parameter-data-types"></a>Parameterdatentypen
Obwohl jeder mit **SQLBindParameter** angegebene Parameter mit einem SQL-Datentyp definiert wird, haben die Parameter in einer SQL-Anweisung keinen intrinsischen Datentyp. Daher können Parametermarkierungen nur dann in eine SQL-Anweisung eingeschlossen werden, wenn ihre Datentypen aus einem anderen Operanden in der Anweisung abgeleitet werden können. Zum Beispiel in einem arithmetischen Ausdruck wie ? + COLUMN1 kann der Datentyp des Parameters aus dem Datentyp der benannten Spalte abgeleitet werden, die durch COLUMN1 dargestellt wird. Eine Anwendung kann keine Parametermarkierung verwenden, wenn der Datentyp nicht bestimmt werden kann.  
  
 In der folgenden Tabelle wird beschrieben, wie ein Datentyp für verschiedene Parametertypen gemäß SQL-92 bestimmt wird. Eine umfassendere Spezifikation zum Ableiten des Parametertyps bei Verwendung anderer SQL-Klauseln finden Sie in der SQL-92-Spezifikation.  
  
|Position des Parameters|Angenommener Datentyp|  
|---------------------------|-----------------------|  
|Ein Operand eines binären Arithmetik- oder Vergleichsoperators|Wie der andere Operand|  
|Der erste Operand in einer **BETWEEN-Klausel**|Wie der zweite Operand|  
|Der zweite oder dritte Operand in einer **BETWEEN-Klausel**|Wie der erste Operand|  
|Ein Ausdruck, der mit **IN** verwendet wird|Genauso wie der erste Wert oder die Ergebnisspalte der Unterabfrage|  
|Ein Wert, der mit **IN** verwendet wird|Genauso wie der Ausdruck oder der erste Wert, wenn sich eine Parametermarkierung im Ausdruck befindet|  
|Ein Musterwert, der mit **LIKE** verwendet wird|VARCHAR|  
|Ein Aktualisierungswert, der mit **UPDATE** verwendet wird|Genauso wie die Aktualisierungsspalte|
