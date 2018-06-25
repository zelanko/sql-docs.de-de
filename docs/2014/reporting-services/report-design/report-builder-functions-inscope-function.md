---
title: InScope-Funktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e677c9e02f452a486b9168f15c662362640ea86e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151053"
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
 (`String`) Den Namen des Datasets, eines Datenbereichs oder einer Gruppe, der einen Bereich angibt.  
  
## <a name="return-type"></a>Rückgabetyp  
 Gibt eine `Boolean`.  
  
## <a name="remarks"></a>Hinweise  
 Die `InScope` Funktion testet den Bereich für die Mitgliedschaft der aktuellen Instanz eines Berichtselements innerhalb des Bereichs, die gemäß der *Bereich*Parameter.  
  
 *Scope* darf kein Ausdruck sein.  
  
 Eine typische Verwendung für die `InScope` Funktion ist in Datenbereichen mit dynamischer Bereichsdefinierung. Beispielsweise `InScope` kann in einem Drillthroughlink in einer datenbereichszelle verwendet werden, um einen anderen Bericht bereitzustellen und unterschiedliche Sätze von Parametern abhängig, welche Zelle geklickt wird. Dies wird im folgenden Beispiel verdeutlicht:  
  
-   Mit dem folgenden Ausdruck, der in einem Drillthroughlink als Berichtsname verwendet wird, wird der `ProductDetail` -Bericht geöffnet, wenn sich die angeklickte Zelle in der `Month` -Gruppierung befindet; andernfalls wird der `ProductSummary` -Bericht geöffnet.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   Der folgende Ausdruck, der verwendet wird, der `Omit` -Eigenschaft eines Drillthroughberichts-Parameters, wird der Parameter an den Zielbericht übergeben, nur, wenn die angeklickte Zelle in ist die `Product` Gruppe.  
  
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
 [Ausdruck verwendet wird, in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  