---
title: DATEPART (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 460cc962ec8ce871438a74ee914ba60ba406d583
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428827"
---
# <a name="datepart-ssis-expression"></a>DATEPART (SSIS-Ausdruck)
  Gibt eine ganze Zahl zurück, die einen datepart-Wert eines Datums darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a>Argumente  
 *datepart*  
 Der Parameter, der angibt, für welche Datumseinheit ein neuer Wert zurückgegeben werden soll.  
  
 *date*  
 Ein Ausdruck, der ein gültiges Datum oder eine Zeichenfolge im Datumsformat zurückgibt.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_I4  
  
## <a name="remarks"></a>Bemerkungen  
 DATEPART gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 Ein Datumsliteral muss explizit in einen der date-Datentypen umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
 In der folgenden Tabelle sind die datepart-Werte und Abkürzungen aufgeführt, die von der Ausdrucksauswertung erkannt werden. Bei datepart-Namen wird die Groß-/Kleinschreibung nicht berücksichtigt.  
  
|datepart|Abkürzungen|  
|--------------|-------------------|  
|Jahr|yy, yyyy|  
|Quarter|qq, q|  
|Month (Monat)|mm, m|  
|Dayofyear|dy, y|  
|Day (Tag)|dd, d|  
|Week|wk, ww|  
|Wochentag|dw|  
|Hour|Hh|  
|Minute|mi, n|  
|Sekunde|ss, s|  
|Millisekunde|Ms|  
  
## <a name="ssis-expression-examples"></a>Beispiele für SSIS-Ausdrücke  
 In diesem Beispiel wird die ganze Zahl zurückgegeben, die den Monat in einem Datumsliteral darstellt. Falls das Datum das Format „MM/TT/JJJJ“ aufweist, gibt dieses Beispiel „11“ zurück.  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 In diesem Beispiel wird die ganze Zahl zurückgegeben, die den Tag in der **ModifiedDate** -Spalte darstellt.  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 In diesem Beispiel wird die ganze Zahl zurückgegeben, die das Jahr des aktuellen Datums darstellt.  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DATEADD &#40;SSIS-Ausdruck&#41;](dateadd-ssis-expression.md)   
 [DATEDIFF &#40;SSIS-Ausdruck&#41;](datediff-ssis-expression.md)   
 [DAY &#40;SSIS-Ausdruck&#41;](day-ssis-expression.md)   
 [MONTH &#40;SSIS-Ausdruck&#41;](month-ssis-expression.md)   
 [YEAR &#40;SSIS-Ausdruck&#41;](year-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
