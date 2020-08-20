---
description: DATEDIFF (SSIS-Ausdruck)
title: DATEDIFF (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e7133fffcea2afe188e00f2c80aa51d6825386c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484420"
---
# <a name="datediff-ssis-expression"></a>DATEDIFF (SSIS-Ausdruck)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Gibt die Anzahl von Datums- und Zeiteinheiten zurück, die zwischen zwei angegebenen Daten überschritten wurden. Der *datepart* -Parameter identifiziert, welche Datums- und Zeiteinheiten verglichen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a>Argumente  
 *datepart*  
 Der Parameter, der angibt, welche Datumseinheit verglichen und für welche Datumseinheit ein Wert zurückgegeben werden soll.  
  
 *startdate*  
 Das Startdatum des Intervalls.  
  
 *endate*  
 Das Enddatum des Intervalls.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_I4  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle sind die datepart-Werte und Abkürzungen aufgeführt, die von der Ausdrucksauswertung erkannt werden.  
  
|datepart|Abkürzungen|  
|--------------|-------------------|  
|Jahr|yy, yyyy|  
|Quarter|qq, q|  
|Month (Monat)|mm, m|  
|Dayofyear|dy, y|  
|Tag|dd, d|  
|Woche|wk, ww|  
|Wochentag|dw, w|  
|Stunde|Hh|  
|Minute|mi, n|  
|Second|ss, s|  
|Millisekunde|Ms|  
  
 DATEDIFF gibt ein NULL-Ergebnis zurück, wenn eines der Argumente NULL ist.  
  
 Ein Datumsliteral muss explizit in einen der date-Datentypen umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Ein Fehler tritt auf, wenn ein Datum ungültig ist, die Datums- oder Zeiteinheit keine Zeichenfolge ist, das Startdatum kein Datum ist oder das Enddatum kein Datum ist.  
  
 Wenn das Enddatum vor dem Startdatum liegt, gibt die Funktion eine negative Zahl zurück. Wenn das Startdatum und das Enddatum identisch sind oder im gleichen Zeitraum liegen, gibt die Funktion Null zurück.  
  
## <a name="ssis-expression-examples"></a>Beispiele für SSIS-Ausdrücke  
 In diesem Beispiel wird die Anzahl von Tagen zwischen zwei Datumsliteralen berechnet. Falls das Datum das Format "mm/dd/yyyy" aufweist, wird 7 zurückgegeben.  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 In diesem Beispiel wird die Anzahl von Monaten zwischen einem Datumsliteral und dem aktuellen Datum zurückgegeben.  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 In diesem Beispiel wird die Anzahl von Wochen zwischen dem Datum in der **ModifiedDate** -Spalte und der **YearEndDate** -Variablen zurückgegeben. Falls **YearEndDate** einen **date** -Datentyp aufweist, ist keine explizite Umwandlung erforderlich.  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DATEADD &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEPART &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
