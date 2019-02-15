---
title: Ändern der Reihenfolge von Berichtsparametern (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 41280d4021dae3c52ebd0e2d888108104ca7b01c
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56289168"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Ändern der Reihenfolge von Berichtsparametern (Berichts-Generator und SSRS)
  Ändern Sie die Reihenfolge der Berichtsparameter, wenn ein abhängiger Parameter vor dem Parameter angeordnet ist, von dem er abhängt. Die Reihenfolge der Parameter spielt eine wichtige Rolle, wenn Sie mit kaskadierenden Parametern arbeiten, oder wenn Sie möchten, dass der Standardwert für einen Parameter angezeigt wird, bevor die Benutzer Werte für andere Parameter auswählen. Ein abhängiger Berichtsparameter enthält entweder in der Abfrage der Standardwerte oder in der Abfrage der gültigen Werte einen Verweis auf einen Abfrageparameter, der auf einen Berichtsparameter verweist, der in der Parameterliste im Berichtsdatenbereich nach ihm angeordnet ist.  
  
 Die Reihenfolge der Parameter auf der Symbolleiste des Berichts-Viewers hängt von der Reihenfolge der Parameter im Berichtsdatenbereich ab.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a>So ändern Sie die Reihenfolge von Berichtsparametern  
  
1.  Erweitern Sie im Berichtsdatenbereich den Knoten Parameter.  
  
2.  Klicken Sie auf einen Parameter, und verschieben Sie ihn mit den Pfeilschaltflächen im Berichtsdatenbereich in der Liste nach oben oder nach unten. In der folgenden Grafik wird der Berichtsdatenbereich im Berichts-Generator dargestellt.  
  
     ![Berichtsdatenbereich](../media/reportdatapane.png "Berichtsdatenbereich")  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Hinzufügen von kaskadierenden Parametern zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Tutorial: Hinzufügen eines Parameters zum Bericht &#40;Berichts-Generator&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Hinzufügen von Datasetfiltern, Datenbereichsfiltern und Gruppenfiltern &#40;Berichts-Generator und SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Verweise auf Parameters-Sammlungen &#40;Berichts-Generator und SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
