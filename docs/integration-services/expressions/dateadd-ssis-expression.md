---
title: DATEADD (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
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
ms.openlocfilehash: 146d9be6b10acf2fbe27db2ef540ebd0dae3beea
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58279334"
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
  
## <a name="remarks"></a>Remarks  
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
  
 Ein Datumsliteral muss explizit in einen der date-Datentypen umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
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
 [DATEDIFF &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
