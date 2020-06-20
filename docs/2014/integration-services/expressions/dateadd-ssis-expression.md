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
ms.openlocfilehash: 8eb32407c6e8fdd79593e7710a2bf1e332f5e4a9
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966670"
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
  
 *Zahl*  
 Der Wert, um den *datepart*inkrementiert wird. Dieser Wert muss ein ganzzahliger Wert sein, der beim Analysieren des Ausdrucks bekannt ist.  
  
 *date*  
 Ein Ausdruck, der ein gültiges Datum oder eine Zeichenfolge im Datumsformat zurückgibt.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_DBTIMESTAMP  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Tabelle sind die datepart-Werte und Abkürzungen aufgeführt, die von der Ausdrucksauswertung erkannt werden. Bei datepart-Namen wird die Groß-/Kleinschreibung nicht berücksichtigt.  
  
|datepart|Abkürzungen|  
|--------------|-------------------|  
|Jahr|yy, yyyy|  
|Quarter|qq, q|  
|Month (Monat)|mm, m|  
|Dayofyear|dy, y|  
|Day (Tag)|dd, d|  
|Week|wk, ww|  
|Wochentag|dw, w|  
|Hour|Hh|  
|Minute|mi, n|  
|Sekunde|ss, s|  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [DATEDIFF &#40;SSIS-Ausdruck&#41;](datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS-Ausdruck&#41;](datepart-ssis-expression.md)   
 [DAY &#40;SSIS-Ausdruck&#41;](day-ssis-expression.md)   
 [MONTH &#40;SSIS-Ausdruck&#41;](month-ssis-expression.md)   
 [YEAR &#40;SSIS-Ausdruck&#41;](year-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
