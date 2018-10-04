---
title: RowNumber-Funktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: abf8cdd0eb4ffceb21061ea0101a42e4b84f3773
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105710"
---
# <a name="rownumber-function-report-builder-and-ssrs"></a>RowNumber-Funktion (Berichts-Generator und SSRS)
  Gibt eine laufende Zählung der Zeilenanzahl für den angegebenen Bereich zurück.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Bereich*  
 (`String`) Den Namen des eine Datasets, eines Datenbereichs oder einer Gruppe oder Null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), den Kontext, in dem die Anzahl von Zeilen ausgewertet angibt. `Nothing` Gibt an, der äußerste Kontext angegeben, normalerweise das Berichtsdataset.  
  
## <a name="remarks"></a>Hinweise  
 `RowNumber` Gibt einen wirksamer Wert der Anzahl der Zeilen im angegebenen Bereich, ebenso wie [RunningValue](report-builder-functions-runningvalue-function.md) der wirksame Wert einer Aggregatfunktion zurückgegeben. Wenn Sie einen Bereich angeben, geben Sie an, wann die Zeilenanzahl auf 1 zurückzusetzen ist.  
  
 *scope* darf kein Ausdruck sein. *scope* muss ein Gültigkeitsbereich sein. Typische Bereiche, von der äußersten bis zur innersten Einkapselung, sind Berichtsdataset, Datenbereich, Zeilengruppen oder Spaltengruppen.  
  
 Um Werte über Spalten hinweg zu inkrementieren, geben Sie einen Bereich an, der dem Namen einer Spaltengruppe enspricht. Um Zahlen über Zeilen hinweg zu inkrementieren, geben Sie einen Bereich an, der dem Namen einer Zeilengruppe enspricht.  
  
> [!NOTE]  
>  Das Einschließen von Aggregaten, die sowohl eine Zeilengruppe als auch eine Spaltengruppe in einem einzelnen Ausdruck angeben, wird nicht unterstützt.  
  
 Weitere Informationen finden Sie in der [Aggregatfunktionsreferenz (Berichts-Generator und SSRS)](report-builder-functions-aggregate-functions-reference.md) und unter [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen (Berichts-Generator und SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden finden Sie einen Ausdruck, mit denen Sie für die `BackgroundColor` Eigenschaft einer Detailzeile Tablix Data Region um die Farbe der Detailzeilen für jede Gruppe abzuwechseln, wobei stets mit Weiß begonnen.  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
