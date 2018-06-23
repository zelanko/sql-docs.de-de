---
title: Max-Funktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61c4d6ff-6435-456a-9cbd-5113d2113e8a
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 45e019d423486968ab47dabcb7ba24822dc551fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160575"
---
# <a name="max-function-report-builder-and-ssrs"></a>Max-Funktion (Berichts-Generator und SSRS)
  Gibt den Maximalwert aller numerischen Werte ungleich NULL aus dem angegebenen Ausdruck im Kontext des angegebenen Bereichs zurück.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Max(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Parameter  
 *expression*  
 (`Variant`) Der Ausdruck für den die Aggregation auszuführen.  
  
 *Bereich*  
 (`String`) Dies ist optional. Der Name eines Datasets, einer Gruppe oder eines Datenbereichs mit den Berichtselementen, auf die die Aggregatfunktion anzuwenden ist. Wenn *scope* nicht angegeben ist, wird der aktuelle Bereich verwendet.  
  
 *Rekursiv*  
 (**Enumerationstyp**) Optional. `Simple` (Standard) oder `RdlRecursive`. Gibt an, ob die Aggregation rekursiv auszuführen ist.  
  
## <a name="return-type"></a>Rückgabetyp  
 Wird durch den Typ des Ausdrucks bestimmt.  
  
## <a name="remarks"></a>Hinweise  
 Die im Ausdruck angegebene Gruppe von Daten muss über den gleichen Datentyp verfügen. Zum Konvertieren von Daten, die mehreren numerischen Datentypen in den gleichen Datentyp aufweist, verwenden Sie Konvertierungsfunktionen wie `CInt`, `CDbl` oder `CDec`. Weitere Informationen finden Sie unter [Funktionen für die Typkonvertierung](http://go.microsoft.com/fwlink/?LinkId=96142).  
  
 Der Wert des *scope* -Objekts muss eine Zeichenfolgenkonstante sein und darf kein Ausdruck sein. Für äußere Aggregate oder Aggregate, die keine anderen Aggregate angeben, muss das *scope* -Objekt auf den aktuellen Bereich oder einen enthaltenen Bereich verweisen. Bei Aggregaten von Aggregaten können geschachtelte Aggregate einen untergeordneten Bereich angeben.  
  
 Das*Expression* -Objekt kann Aufrufe von geschachtelten Aggregatfunktionen enthalten. Dabei gelten folgende Ausnahmen und Bedingungen:  
  
-   Das*Scope* -Objekt für geschachtelte Aggregate muss dem Bereich des äußeren Aggregats entsprechen oder darin enthalten sein. In allen eindeutigen Bereichen des Ausdrucks muss ein Bereich eine untergeordnete Beziehung zu allen anderen Bereichen haben.  
  
-   Das*Scope* -Objekt für geschachtelte Aggregate darf nicht der Name eines Datasets sein.  
  
-   *Ausdruck* darf keinen `First`, `Last`, `Previous`, oder `RunningValue` Funktionen.  
  
-   Das*Expression* -Objekt darf keine geschachtelten Aggregate enthalten, die ein *recursive*-Objekt angeben.  
  
 Weitere Informationen finden Sie in der [Aggregatfunktionsreferenz (Berichts-Generator und SSRS)](report-builder-functions-aggregate-functions-reference.md) und unter [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen (Berichts-Generator und SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Weitere Informationen zu rekursiven Aggregaten finden Sie unter [Creating Recursive Hierarchy Groups (Report Builder and SSRS) (Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS))](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Beispiel  
 Mit dem folgenden Codebeispiel wird der höchste Gesamtwert in der Gruppierung bzw. dem Datenbereich `Year` bereitgestellt.  
  
```  
=Max(Fields!OrderTotal.Value, "Year")  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck verwendet wird, in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  