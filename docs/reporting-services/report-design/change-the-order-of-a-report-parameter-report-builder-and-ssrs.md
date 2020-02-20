---
title: Ändern der Reihenfolge von Berichtsparametern (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 48da3d62e18a77bc8629d43ef170ca2b0622fe16
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "65581703"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Ändern der Reihenfolge von Berichtsparametern (Berichts-Generator und SSRS)
  Ändern Sie die Reihenfolge der Berichtsparameter, wenn ein abhängiger Parameter vor dem Parameter angeordnet ist, von dem er abhängt. Die Reihenfolge der Parameter spielt eine wichtige Rolle, wenn Sie mit kaskadierenden Parametern arbeiten, oder wenn Sie möchten, dass der Standardwert für einen Parameter angezeigt wird, bevor die Benutzer Werte für andere Parameter auswählen. Ein abhängiger Berichtsparameter enthält entweder in der Abfrage der Standardwerte oder in der Abfrage der gültigen Werte einen Verweis auf einen Abfrageparameter, der auf einen Berichtsparameter verweist, der in der Parameterliste im Bereich **Berichtsdaten** nach ihm angeordnet ist.  
  
 Die Reihenfolge der Parameter auf der Symbolleiste des Berichts-Viewers beim Ausführen des Berichts hängt von der Reihenfolge der Parameter im Bereich **Berichtsdaten** sowie der Position der Parameter im Bereich der benutzerdefinierten Parameter ab. Weitere Informationen finden Sie unter [Benutzerdefiniertes Anpassen des Parameterbereichs (Berichts-Generator)](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md) erstellen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-order-of-report-parameters"></a>So ändern Sie die Reihenfolge von Berichtsparametern  
  
Wählen Sie eine der folgenden Vorgehensweisen aus, um die Reihenfolge von Berichtsparametern zu ändern:  
  
-   Klicken Sie im Bereich **Berichtsdaten** auf einen Parameter, und verschieben Sie ihn mit den Pfeilschaltflächen in der Liste nach oben oder nach unten (siehe Abbildung unten).  Wenn Sie die Reihenfolge der Parameter im Bereich **Berichtsdaten** ändern, wird die Position des Parameters im Parameterbereich geändert.  
  
     ![Ändern der Reihenfolge der Parameter im Berichtsdatenbereich](../../reporting-services/report-design/media/ssrs-changeorderofparameters-reportdata.png "Ändern der Reihenfolge der Parameter im Berichtsdatenbereich")  
  
-   Ziehen Sie den Parameter im Parameterbereich in eine neue Spalte oder Zeile des Bereichs. Wenn Sie die Position des Parameters in diesem Bereich ändern, wird die Parameterreihenfolge im Bereich **Berichtsdaten** geändert. Weitere Informationen zum Verschieben der Parameter in diesem Bereich finden Sie unter [Benutzerdefiniertes Anpassen des Parameterbereichs (Berichts-Generator)](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Hinzufügen von kaskadierenden Parametern zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Tutorial: Hinzufügen eines Parameters zu einem Bericht (Berichts-Generator)](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Hinzufügen von Datasetfiltern, Datenbereichsfiltern und Gruppenfiltern &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Verweise auf Parameters-Sammlungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
