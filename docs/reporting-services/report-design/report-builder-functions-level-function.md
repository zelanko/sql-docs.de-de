---
title: Level-Funktion (Berichts-Generator) | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Level-Funktion im Berichts-Generator. Diese Funktion gibt die aktuelle Ebene in einer rekursiven Hierarchie zurück.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b582a1c62f92fc001b4c6047319b9100b4e27ac9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048239"
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
 *scope*  
 (**String**) Optional. Der Name eines Datasets, einer Gruppe oder eines Datenbereichs mit den Berichtselementen, auf die die Aggregatfunktion anzuwenden ist. Wenn *scope* nicht angegeben ist, wird der aktuelle Bereich verwendet.  
  
## <a name="return-type"></a>Rückgabetyp  
 Gibt einen Wert vom Typ **Integer**zurück. Wenn *scope* ein Dataset, einen Datenbereich oder eine nicht rekursive Gruppierung angibt (d.h. eine Gruppierung ohne **Parent** -Element), gibt **Level** den Wert 0 zurück. Wenn *scope* weggelassen wird, wird die Ebene des aktuellen Bereichs zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der von der **Level** -Funktion zurückgegebene Wert ist nullbasiert, d. h., die erste Ebene in einer Hierarchie hat den Wert 0.  
  
 Die **Level** -Funktion kann verwendet werden, um den Einzug in einer rekursiven Hierarchie, z. B. einer Mitarbeiterliste, bereitzustellen.  
  
 Weitere Informationen zu rekursiven Hierarchien finden Sie unter [Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS)](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Beispiel  
 Mit dem folgenden Codebeispiel wird die Zeilenebene in der Employees-Gruppe bereitgestellt:  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
