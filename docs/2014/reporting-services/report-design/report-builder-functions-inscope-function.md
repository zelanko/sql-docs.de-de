---
title: InScope-Funktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84f9b681ee632e922f5ab349bf1a72fbea63f911
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105251"
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
 *scope*  
 (`String`) Der Name eines Datasets, eines Datenbereichs oder einer Gruppe, die einen Bereich angibt.  
  
## <a name="return-type"></a>Rückgabetyp  
 Gibt einen `Boolean` zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Die `InScope` -Funktion testet den Bereich der aktuellen Instanz eines Berichts Elements auf die Mitgliedschaft in dem durch den *Scope*-Parameter angegebenen Bereich.  
  
 *Scope* darf kein Ausdruck sein.  
  
 Die `InScope`-Funktion wird üblicherweise in Datenbereichen mit dynamischer Bereichsdefinierung eingesetzt. So kann `InScope` beispielsweise in einem Drillthroughlink in einer Datenbereichszelle verwendet werden, um unterschiedliche Berichtsnamen und unterschiedliche Parametersätze bereitzustellen, je nach Zelle, auf die Sie klicken. Dies wird im folgenden Beispiel verdeutlicht:  
  
-   Mit dem folgenden Ausdruck, der in einem Drillthroughlink als Berichtsname verwendet wird, wird der `ProductDetail` -Bericht geöffnet, wenn sich die angeklickte Zelle in der `Month` -Gruppierung befindet; andernfalls wird der `ProductSummary` -Bericht geöffnet.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   Mit dem folgenden Ausdruck, der in der `Omit`-Eigenschaft eines Drillthroughberichts-Parameters verwendet wird, wird der Parameter nur dann an den Zielbericht übergeben, wenn sich die angeklickte Zelle in der `Product`-Gruppierung befindet.  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 Weitere Informationen finden Sie in der [Aggregatfunktionsreferenz (Berichts-Generator und SSRS)](report-builder-functions-aggregate-functions-reference.md) und unter [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen (Berichts-Generator und SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird angezeigt, ob sich die aktuelle Instanz des Elements innerhalb des `Product` -Datasets, -Datenbereichs oder -Gruppenbereichs befindet.  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
