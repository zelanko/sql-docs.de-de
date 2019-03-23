---
title: DATEADD (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3c744d3f28bc27373f3dc9798ba591848d4b720e
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374538"
---
# <a name="dateadd-ssis-expression"></a>DATEADD (SSIS-Ausdruck)
  Gibt einen neuen DT_DBTIMESTAMP-Wert zurück, nachdem einem angegebenen datepart-Wert in einem Datum eine Zahl hinzugefügt wurde, die ein Datums- oder Zeitintervall darstellt. Der number-Parameter muss zu einer ganzen Zahl ausgewertet werden, und der date-Parameter muss zu einem gültigen Datum ausgewertet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a>Argumente  
 *datepart*  
 Der Parameter, der angibt, welcher Datumseinheit eine Zahl hinzugefügt werden soll.  
  
 *number*  
 Der Wert, um den *datepart*inkrementiert wird. Dieser Wert muss ein ganzzahliger Wert sein, der beim Analysieren des Ausdrucks bekannt ist.  
  
 *Datum*  
 Ein Ausdruck, der ein gültiges Datum oder eine Zeichenfolge im Datumsformat zurückgibt.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_DBTIMESTAMP  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle sind die datepart-Werte und Abkürzungen aufgeführt, die von der Ausdrucksauswertung erkannt werden. Bei datepart-Namen wird die Groß-/Kleinschreibung nicht berücksichtigt.  
  
|datepart|Abkürzungen|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Dayofyear|dy, y|  
|Day|dd, d|  
|Week|wk, ww|  
|Arbeitstag|dw, w|  
|Hour|Hh|  
|Minute|mi, n|  
|Zweimal|ss, s|  
|Millisekunde|Ms|  
  
 Das *number* -Argument muss beim Analysieren des Ausdrucks verfügbar sein. Bei diesem Argument kann es sich um eine Konstante oder eine Variable handeln. Spaltenwerte können nicht verwendet werden, weil diese Werte beim Analysieren des Ausdrucks nicht bekannt sind.  
  
 Das *datepart* -Argument muss in Anführungszeichen eingeschlossen werden.  
  
 Ein Datumsliteral muss explizit in einen der date-Datentypen umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
 DATEADD gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 Fehler treten auf, wenn ein Datum ungültig, die Datums- oder Zeiteinheit keine Zeichenfolge oder das Inkrement keine statische ganze Zahl ist.  
  
## <a name="ssis-expression-examples"></a>Beispiele für SSIS-Ausdrücke  
 In diesem Beispiel wird dem aktuellen Datum ein Monat hinzugefügt.  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 In diesem Beispiel werden den Datumsangaben in der **ModifiedDate** -Spalte 21 Tage hinzugefügt.  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 In diesem Beispiel werden einem Datumsliteral 2 Jahre hinzugefügt.  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DATEDIFF &#40;SSIS-Ausdruck&#41;](datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS-Ausdruck&#41;](datepart-ssis-expression.md)   
 [DAY &#40;SSIS-Ausdruck&#41;](day-ssis-expression.md)   
 [MONTH &#40;SSIS-Ausdruck&#41;](month-ssis-expression.md)   
 [YEAR &#40;SSIS-Ausdruck&#41;](year-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
