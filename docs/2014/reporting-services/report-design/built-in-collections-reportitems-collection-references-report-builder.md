---
title: Verweise auf Parameterauflistungen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: edc0c75f-0530-4e6d-85aa-3385301bfd00
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 92872f29600bc380025e76933ef8a1aab2879e51
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56285878"
---
# <a name="reportitems-collection-references-report-builder-and-ssrs"></a>Verweise auf ReportItems-Auflistungen (Berichts-Generator und SSRS)
  Die integrierte `ReportItems`-Auflistung besteht aus einem Satz von Textfeldern aus Berichtselementen, wie Zeilen eines Datenbereichs oder Textfelder auf der Berichtsentwurfsoberfläche. Die `ReportItems`-Auflistung umfasst Textfelder, die sich im aktuellen Bereich einer Seitenkopfzeile, einer Seitenfußzeile oder eines Berichtshauptteils befinden. Diese Auflistung wird vom Berichtsprozessor und vom Berichtsrenderer zur Laufzeit bestimmt. Der aktuelle Bereich wird geändert, wenn der Berichtsprozessor Berichtsdaten und die Layoutelemente des Berichtselements erfolgreich kombiniert, während der Benutzer Seiten eines Berichts anzeigt. Sie können die integrierte `ReportItems`-Auflistung verwenden, um Seitenkopfzeilen im Wörterbuchformat zu erstellen, die das erste und das letzte Element auf jeder Seite anzeigen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-reportitems-value-property"></a>Verwenden der ReportItems-Werteigenschaft  
 Elemente in der `ReportItems` -Auflistung verfügen über nur eine Eigenschaft: Wert. Mit dem Wert für ein `ReportItems`-Element können Daten aus einem anderen Feld im Bericht angezeigt oder berechnet werden. Der Zugriff auf den Wert des aktuellen Textfelds kann über den in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] integrierten globalen Me.Value oder einfach über Value erfolgen. In Berichtsfunktionen wie "Erster" und in Aggregatfunktionen müssen Sie jedoch die vollqualifizierte Syntax verwenden.  
  
 Zum Beispiel:  
  
-   Dieser Ausdruck wird in einem Textfeld platziert und zeigt den Wert eines `ReportItem`-Textfelds mit dem Namen `Textbox1` an:  
  
     `=ReportItems!Textbox1.Value`  
  
-   Dieser Ausdruck platziert einem `ReportItem` Textfeld Color-Eigenschaft, die Text in Schwarz angezeigt, wenn der Wert > 0 ist; andernfalls wird der Wert in Rot angezeigt:  
  
     `=IIF(Me.Value > 0,"Black","Red")`  
  
-   Dieser Ausdruck wird in einem Textfeld des Seitenkopfes oder Seitenfußes platziert und zeigt den ersten Wert pro Seite des gerenderten Berichts für ein Textfeld mit dem Namen `LastName`an:  
  
     `=First(ReportItems("LastName").Value)`  
  
## <a name="dictionary-style-page-header-expressions"></a>Seitenkopfausdrücke im Wörterbuchformat  
 Sie können einen Seitenkopf erstellen, der den ersten Kunden auf der Seite und den letzten Kunden auf der Seite anzeigt. Da ein Textfeld im Seitenkopf nur einmal auf die integrierte `ReportItems`-Auflistung verweisen kann, müssen Sie dem Seitenkopf zwei Textfelder hinzufügen: ein Feld für den Namen des ersten Kunden (`=First(ReportItems!textboxLastName.Value`) und ein Feld für den Namen des letzten Kunden (`=Last(ReportItems!textboxLastName.Value`).  
  
 In einem Seitenkopf- oder Seitenfußabschnitt sind nur Textfelder auf der aktuellen Seite als Elemente der `ReportItems`-Auflistung verfügbar. Wenn `ReportItems!textboxLastName.Value` beispielsweise auf ein Textfeld verweist, das nur auf der ersten Seite eines mehrseitigen Datenbereichs angezeigt wird, wird ein Wert für die erste Seite angezeigt. Alle anderen Seiten enthalten jedoch die Meldung **#Error** , die angibt, dass der Ausdruck nicht als geschrieben ausgewertet werden konnte.  
  
## <a name="scope-for-the-reportitems-collection"></a>Bereich der ReportItems-Auflistung  
 Während der Bericht verarbeitet wird, wird jedes Textfeld im Berichtshauptteil oder in einem Datenbereich im Kontext des entsprechenden Datasets, des Datenbereichs und der Gruppenzuordnungen ausgewertet. Der Bereich für einen Verweis auf die `ReportItems`-Auflistung ist der aktuelle Bereich oder jeder Punkt, der höher liegt als der aktuelle Bereich.  
  
 Ein Textfeld in einer Zeile, die sich in einer übergeordneten Gruppe befindet, darf beispielsweise keinen Ausdruck enthalten, der auf den Namen eines Textfelds in einer Zeile einer untergeordneten Gruppe verweist. Ein solcher Ausdruck wird nicht in einen Wert des Berichts aufgelöst, da sich das Textfeld in der untergeordneten Zeile außerhalb des Bereichs befindet. Weitere Informationen finden Sie unter [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Integrierte Sammlungen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](built-in-collections-in-expressions-report-builder.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
