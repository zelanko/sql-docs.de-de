---
title: Hinzufügen einer Drillthroughaktion für einen Bericht (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 153729c4-d01e-4629-b78f-0cfd5a7f83da
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 3d0cc02fa47d4c3ba17f8140298a124f61ab070d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046020"
---
# <a name="add-a-drillthrough-action-on-a-report-report-builder-and-ssrs"></a>Hinzufügen einer Drillthroughaktion für einen Bericht (Berichts-Generator und SSRS)
  Der Bericht, der geöffnet wird, wenn Sie auf den Link im Hauptbericht klicken, wird als *Drillthroughbericht*bezeichnet. Der Drillthrough-Link ermöglicht einen Drillthrough-Vorgang.  
  
 Drillthroughberichte müssen auf demselben Berichtsserver wie der Hauptbericht veröffentlicht werden, können aber in anderen Ordnern abgelegt sein. Sie können jedem Element einen Drillthroughlink hinzufügen, das über eine Eigenschaft **Aktion** verfügt, z. B. ein Textfeld, ein Bild oder Datenpunkte in einem Diagramm.  
  
 Sie müssen zuerst den Drillthroughbericht erstellen, mit dem der Hauptbericht verknüpft wird, um einem Bericht einen Drillthroughlink hinzuzufügen. Ein Drillthroughbericht enthält im Allgemeinen Details zu einem im ursprünglichen Zusammenfassungsbericht enthaltenen Element und enthält oft Parameter, mit denen der Drillthroughbericht basierend auf Parametern, die vom Hauptbericht übergeben werden, gefiltert wird. Weitere Informationen zum Erstellen des Drillthroughberichts finden Sie unter [Drillthroughberichte (Berichts-Generator und SSRS)](drillthrough-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-drillthrough-action"></a>So fügen Sie eine Drillthroughaktion hinzu  
  
1.  Klicken Sie in der Entwurfsansicht mit der rechten Maustaste auf das Textfeld, Bild oder Diagramm, dem Sie einen Link hinzufügen möchten, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld **Eigenschaften** des Elements auf **Aktion**.  
  
3.  Wählen Sie **Gehe zu Bericht**. Im Dialogfeld für diese Option werden zusätzliche Abschnitte angezeigt.  
  
4.  Klicken Sie unter **Bericht angeben**auf **Durchsuchen** , um nach dem Namen des gewünschten Berichts zu suchen, oder geben Sie den Namen ein. Alternativ können Sie auf die Ausdrucksschaltfläche (**fx**) klicken, um einen Ausdruck für den Berichtsnamen zu erstellen.  
  
     Das Format des Pfads zum Drillthroughbericht unterscheidet sich beim einheitlichen und integrierten SharePoint-Modus. Wenn Sie den Bericht über "Durchsuchen" auswählen, wird der Pfad im richtigen Format angegeben. Weitere Informationen finden Sie unter [Angeben von Pfaden zu externen Elementen &#40;Berichts-Generator und SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
     Wenn Sie Parameter für den Drillthroughbericht angeben müssen, führen Sie den nächsten Schritt aus.  
  
5.  Klicken Sie in **Diese Parameter zum Ausführen des Berichts verwenden**auf **Hinzufügen**. Dem Parameterraster wird eine neue Zeile hinzugefügt.  
  
    -   Klicken Sie im Textfeld **Name** auf die Dropdownliste, oder geben Sie den Namen des Berichtsparameters im Drillthroughbericht ein.  
  
        > [!NOTE]  
        >  Die Namen in der Parameterliste müssen mit den erwarteten Parametern im Zielbericht genau übereinstimmen. Beispiel: Die Schreibweise von Parameternamen muss übereinstimmen. Falls die Namen nicht übereinstimmen oder ein erwarteter Parameter nicht aufgeführt ist, ergibt der Drillthroughbericht einen Fehler.  
  
    -   Geben Sie den Wert, der an den Parameter im Drillthroughbericht übergeben werden soll, in das Feld **Wert**ein bzw. wählen Sie ihn aus.  
  
        > [!NOTE]  
        >  Werte können einen Ausdruck enthalten, der zu einem an den Berichtsparameter zu übergebenden Wert ausgewertet werden kann. Die Ausdrücke in der Werteliste beinhalten die Feldliste für den aktuellen Bericht.  
  
     Informationen zum Ausblenden von Parametern in Berichten finden Sie unter [Hinzufügen, Ändern oder Löschen von Berichtsparametern (Berichts-Generator und SSRS)](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md).  
  
6.  (Optional) Bei Textfeldern ist es hilfreich, die Farbe und den Effekt des Texts zu ändern, um zu verdeutlichen, dass es sich um einen Link handelt. Verwenden Sie dazu die Registerkarte **Home** auf dem Menüband.  
  
7.  Führen Sie den Bericht aus, und klicken Sie auf das Berichtselement, für das Sie den Link festgelegt haben, um den Link zu testen.  
  
## <a name="see-also"></a>Siehe auch  
 [Im Dialogfeld "Eigenschaften" Aktion &#40;Berichts-Generator und SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md)   
 [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Anzeigen von QuickInfos für eine Reihe &#40;Berichts-Generator und SSRS&#41;](show-tooltips-on-a-series-report-builder-and-ssrs.md)  
  
  