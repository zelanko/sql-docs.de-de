---
title: InScope-Funktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: e37a25432e6e701ffd97bf95799b1a567748e1df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183785"
---
# <a name="inscope-function-report-builder-and-ssrs"></a>InScope-Funktion (Berichts-Generator und SSRS)
  Gibt an, ob sich die aktuelle Instanz eines Elements innerhalb des angegebenen Bereichs befindet.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntax  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Bereich*  
 (`String`) Den Namen der ein Dataset, Datenbereich oder Gruppe, die einen Bereich angibt.  
  
## <a name="return-type"></a>Rückgabetyp  
 Gibt eine `Boolean`.  
  
## <a name="remarks"></a>Hinweise  
 Die `InScope` Funktion testet den Bereich für die Mitgliedschaft der aktuellen Instanz eines Berichtselements im Bereich gemäß der *Bereich*Parameter.  
  
 *Scope* darf kein Ausdruck sein.  
  
 Eine typische Verwendung für die `InScope` Funktion ist in Datenbereichen mit dynamischer Bereichsdefinierung. Z. B. `InScope` kann in einem Drillthroughlink in einer datenbereichszelle verwendet werden, um unterschiedliche Berichtsnamen und unterschiedliche Parametersätze bereitzustellen abhängig, welche Zelle geklickt wird. Dies wird im folgenden Beispiel verdeutlicht:  
  
-   Mit dem folgenden Ausdruck, der in einem Drillthroughlink als Berichtsname verwendet wird, wird der `ProductDetail` -Bericht geöffnet, wenn sich die angeklickte Zelle in der `Month` -Gruppierung befindet; andernfalls wird der `ProductSummary` -Bericht geöffnet.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   Der folgende Ausdruck in verwendet die `Omit` -Eigenschaft eines Drillthroughberichts-Parameters, wird der Parameter an den Zielbericht übergeben, nur, wenn die angeklickte Zelle in ist die `Product` Gruppe.  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 Weitere Informationen finden Sie in der [Aggregatfunktionsreferenz (Berichts-Generator und SSRS)](report-builder-functions-aggregate-functions-reference.md) und unter [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen (Berichts-Generator und SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird angezeigt, ob sich die aktuelle Instanz des Elements innerhalb des `Product` -Datasets, -Datenbereichs oder -Gruppenbereichs befindet.  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
