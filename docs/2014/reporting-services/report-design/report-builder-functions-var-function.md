---
title: Var-Funktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7b2018ce-c5f9-4f8b-bd44-4201379a584b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a10d92d8492f9f07f18d2edccd7f3074b7c584c5
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66105089"
---
# <a name="var-function-report-builder-and-ssrs"></a>Var-Funktion (Berichts-Generator und SSRS)
  Gibt die Varianz aller numerischen Werte ungleich NULL aus dem angegebenen Ausdruck im Kontext des festgelegten Bereichs ausgewertet zurück.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Var(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Parameter  
 *expression*  
 (`Integer` oder `Float`) Der Ausdruck, für den die Aggregation ausgeführt werden soll.  
  
 *Bereich*  
 (`String`) optional. Eine Konstante, die dem Namen eines Datasets, einer Gruppe oder eines Datenbereichs mit den Berichtselementen entspricht, auf die die Aggregatfunktion anzuwenden ist. Wenn *scope* nicht angegeben ist, wird der aktuelle Bereich verwendet.  
  
 *Rekursiv*  
 (**Enumerationstyp**) Optional. `Simple` (Standardwert) oder `RdlRecursive`. Gibt an, ob die Aggregation rekursiv auszuführen ist.  
  
## <a name="return-type"></a>Rückgabetyp  
 Gibt für Dezimalausdrücke einen Wert vom Typ `Decimal` und für alle anderen Ausdrücke einen Wert vom Typ `Double` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Die im Ausdruck angegebene Gruppe von Daten muss über den gleichen Datentyp verfügen. Um Daten mit mehreren numerischen Datentypen in den gleichen Datentyp zu konvertieren, verwenden Sie Konvertierungsfunktionen wie `CInt`, `CDbl` oder `CDec`. Weitere Informationen finden Sie unter [Funktionen für die Typkonvertierung](https://go.microsoft.com/fwlink/?LinkId=96142).  
  
 Der Wert des *scope* -Objekts muss eine Zeichenfolgenkonstante sein und darf kein Ausdruck sein. Für äußere Aggregate oder Aggregate, die keine anderen Aggregate angeben, muss das *scope* -Objekt auf den aktuellen Bereich oder einen enthaltenen Bereich verweisen. Bei Aggregaten von Aggregaten können geschachtelte Aggregate einen untergeordneten Bereich angeben.  
  
 Das*Expression* -Objekt kann Aufrufe von geschachtelten Aggregatfunktionen enthalten. Dabei gelten folgende Ausnahmen und Bedingungen:  
  
-   Das*Scope* -Objekt für geschachtelte Aggregate muss dem Bereich des äußeren Aggregats entsprechen oder darin enthalten sein. In allen eindeutigen Bereichen des Ausdrucks muss ein Bereich eine untergeordnete Beziehung zu allen anderen Bereichen haben.  
  
-   Das*Scope* -Objekt für geschachtelte Aggregate darf nicht der Name eines Datasets sein.  
  
-   *Ausdruck* darf keinen `First`, `Last`, `Previous`, oder `RunningValue` Funktionen.  
  
-   Das*Expression* -Objekt darf keine geschachtelten Aggregate enthalten, die ein *recursive*-Objekt angeben.  
  
 Weitere Informationen finden Sie in der [Aggregatfunktionsreferenz (Berichts-Generator und SSRS)](report-builder-functions-aggregate-functions-reference.md) und unter [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen (Berichts-Generator und SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Weitere Informationen zu rekursiven Aggregaten finden Sie unter [Creating Recursive Hierarchy Groups (Report Builder and SSRS) (Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS))](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel berechnet die Varianz von Einzelpostensummen in der Gruppe bzw. im Datenbereich `Order` :  
  
```  
=Var(Fields!LineTotal.Value, "Order")  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
