---
title: Dimensionsfunktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35526e8928a98ccca2e2e61e88fb9361a6d00d6c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105237"
---
# <a name="level-function-report-builder-and-ssrs"></a>Level-Funktion (Berichts-Generator und SSRS)
  Gibt die aktuelle Ebene in einer rekursiven Hierarchie zurück.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Parameter  
 *scope*  
 (`String`) (optional). Der Name eines Datasets, einer Gruppe oder eines Datenbereichs mit den Berichtselementen, auf die die Aggregatfunktion anzuwenden ist. Wenn *scope* nicht angegeben ist, wird der aktuelle Bereich verwendet.  
  
## <a name="return-type"></a>Rückgabetyp  
 Gibt einen Wert vom Typ `Integer` zurück. Wenn *Scope* ein DataSet oder einen Datenbereich angibt oder eine nicht rekursive Gruppierung (d. h. eine Gruppierung ohne `Parent` -Element) `Level` angibt, wird 0 zurückgegeben. Wenn *scope* weggelassen wird, wird die Ebene des aktuellen Bereichs zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der von der `Level`-Funktion zurückgegebene Wert ist nullbasiert, d. h., die erste Ebene in einer Hierarchie hat den Wert 0.  
  
 Die `Level`-Funktion kann verwendet werden, um den Einzug in einer rekursiven Hierarchie, z. B. einer Mitarbeiterliste, bereitzustellen.  
  
 Weitere Informationen zu rekursiven Hierarchien finden Sie unter [Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS)](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Beispiel  
 Mit dem folgenden Codebeispiel wird die Zeilenebene in der Employees-Gruppe bereitgestellt:  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
