---
title: Parameterdatentypen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.openlocfilehash: 5140c69184332b1760859421b7e802a5163a0f09
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100604"
---
# <a name="parameter-data-types"></a>Parameterdatentypen
Obwohl jedes Parameters angegeben **SQLBindParameter** wird definiert, mit einer SQL-Datentyp, die Parameter in einer SQL-Anweisung keine systeminternen Datentyp haben. Parametermarkierungen können daher in einer SQL­Anweisung enthalten sein, nur dann, wenn ihre Datentypen, die von einem anderen Operanden in der Anweisung abgeleitet werden können. Z. B. in einem arithmetischen Ausdruck wie z. B.? + COLUMN1, den Datentyp des Parameters kann von den Datentyp der benannten Spalte COLUMN1 verhältnisschwellenwert abgeleitet werden. Eine Anwendung kann nicht auf eine parametermarkierung verwenden, wenn der Datentyp kann nicht bestimmt werden.  
  
 In der folgende Tabelle wird beschrieben, wie ein Datentyp für mehrere Typen von Parametern, die in Übereinstimmung mit der SQL-92 bestimmt wird. Eine umfassendere Spezifikation für das Ableiten von der Parametertyp, wenn andere SQL-Klauseln verwendet werden, finden Sie in der SQL-92-Spezifikation.  
  
|Speicherort des Parameters|Davon ausgegangen, dass-Datentyp|  
|---------------------------|-----------------------|  
|Einer der Operanden des binären Operators arithmetischen oder Vergleichsoperationen|Identisch mit der andere operand|  
|Der erste Operand in einem **BETWEEN** Klausel|Identisch mit dem zweiten operand|  
|Der zweite oder dritte Operand in einem **BETWEEN** Klausel|Identisch mit den ersten Operanden|  
|Ein Ausdruck für die **IN**|Identisch mit den ersten Wert oder der Ergebnisspalte der Unterabfrage|  
|Ein Wert, der Verwendung **IN**|Identisch mit dem Ausdruck oder der erste Wert, wenn eine parametermarkierung im Ausdruck vorliegt.|  
|Einen Musterwert mit verwendet **wie**|VARCHAR|  
|Ein Updatewert, der Verwendung **aktualisieren**|Der Update-Spalte|
