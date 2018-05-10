---
title: Dimensionsfunktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e092b79a5ddd1e43a740520fc2505cc0dede5b4d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="report-builder-functions---level-function"></a>Funktionen des Berichts-Generators: Dimensionsfunktion
  Gibt die aktuelle Ebene in einer rekursiven Hierarchie zurück.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Bereich*  
 (**String**) Optional. Der Name eines Datasets, einer Gruppe oder eines Datenbereichs mit den Berichtselementen, auf die die Aggregatfunktion anzuwenden ist. Wenn *scope* nicht angegeben ist, wird der aktuelle Bereich verwendet.  
  
## <a name="return-type"></a>Rückgabetyp  
 Gibt einen Wert vom Typ **Integer**zurück. Wenn *scope* ein Dataset, einen Datenbereich oder eine nicht rekursive Gruppierung angibt (d.h. eine Gruppierung ohne **Parent** -Element), gibt **Level** den Wert 0 zurück. Wenn *scope* weggelassen wird, wird die Ebene des aktuellen Bereichs zurückgegeben.  
  
## <a name="remarks"></a>Remarks  
 Der von der **Level** -Funktion zurückgegebene Wert ist nullbasiert, d. h., die erste Ebene in einer Hierarchie hat den Wert 0.  
  
 Die **Level** -Funktion kann verwendet werden, um den Einzug in einer rekursiven Hierarchie, z. B. einer Mitarbeiterliste, bereitzustellen.  
  
 Weitere Informationen zu rekursiven Hierarchien finden Sie unter [Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS)](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Beispiel  
 Mit dem folgenden Codebeispiel wird die Zeilenebene in der Employees-Gruppe bereitgestellt:  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
