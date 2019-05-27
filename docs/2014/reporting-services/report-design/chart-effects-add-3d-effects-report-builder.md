---
title: Hinzufügen von 3D-Effekten zu einem Diagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab9625d8-6557-4a4d-8123-eefa7c066ff5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07934e74138f17317eb0258e2b3ad0fa6d26254a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66106322"
---
# <a name="add-3d-effects-to-a-chart-report-builder-and-ssrs"></a>Hinzufügen von 3D-Effekten zu einem Diagramm (Berichts-Generator und SSRS)
  Dreidimensionale (3D-)Effekte können verwendet werden, um Tiefe zu vermitteln und dem Diagramm eine optische Wirkung zu verleihen. Wenn Sie beispielsweise in einem explodierten Kreisdiagramm ein bestimmtes Segment des Kreises hervorheben möchten, können Sie die Perspektive des Diagramms so drehen und ändern, dass den Benutzern dieses Segment zuerst ins Auge fällt. Wenn 3D-Effekte auf das Diagramm angewendet werden, werden der Farbverlauf und alle Schraffurstile deaktiviert.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-3d-effects-to-a-range-area-line-scatter-or-polar-chart"></a>So übernehmen Sie 3D-Effekte für ein Bereichs-, Flächen-, Linien-, Punkt- oder Polardiagramm  
  
1.  Klicken Sie mit der rechten Maustaste in die Diagrammfläche, und wählen Sie **3D-Effekte**aus. Das Dialogfeld **Diagrammflächeneigenschaften** wird angezeigt.  
  
2.  Wählen Sie unter **3D-Optionen**die Option **3D aktivieren** aus.  
  
3.  (Optional) Unter **3D-Optionen**können Sie eine Vielzahl von Eigenschaften festlegen, die sich auf 3D-Winkel- und Szenenoptionen beziehen. Weitere Informationen zu diesen Eigenschaften finden Sie unter [3D, Abschrägungen und andere Effekte in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md)aus.  
  
4.  Klicken Sie auf **OK**.  
  
### <a name="to-apply-3d-effects-to-a-funnel-chart"></a>So wenden Sie 3D-Effekte auf ein Trichterdiagramm an  
  
1.  Klicken Sie mit der rechten Maustaste in die Diagrammfläche, und wählen Sie **3D-Effekte**aus. Das Dialogfeld **Diagrammflächeneigenschaften** wird angezeigt.  
  
2.  Wählen Sie unter **3D-Optionen**die Option **3D aktivieren** aus. Klicken Sie auf **OK**.  
  
3.  (Optional) Um die visuelle Darstellung des Trichterdiagramms anzupassen, wechseln Sie in den Bereich Eigenschaften, und ändern Sie die für das Trichterdiagramm spezifischen Eigenschaften.  
  
    1.  Öffnen Sie den Bereich Eigenschaften.  
  
    2.  Klicken Sie auf der Entwurfsoberfläche auf das Trichterdiagramm. Die Eigenschaften für die Reihen des Trichterdiagramms werden im Bereich Eigenschaften angezeigt.  
  
    3.  Erweitern Sie im Abschnitt **Allgemein** den Knoten **CustomAttributes** .  
  
    4.  Wählen Sie für die **Funnel3DDrawingStyle** -Eigenschaft aus, ob der Trichter rund oder quadratisch angezeigt wird.  
  
    5.  Legen Sie für die **Funnel3DRotationAngle** -Eigenschaft einen Wert zwischen -10 und 10 fest. Mit diesem Wert wird der Neigungswinkel bestimmt, der für das 3D-Trichterdiagramm verwendet wird.  
  
### <a name="to-apply-3d-effects-to-a-pie-chart"></a>So wenden Sie 3D-Effekte auf ein Kreisdiagramm an  
  
1.  Klicken Sie mit der rechten Maustaste in die Diagrammfläche, und wählen Sie 3D-Effekte aus. Das Dialogfeld **Diagrammflächeneigenschaften** wird angezeigt.  
  
2.  Wählen Sie unter **3D-Optionen**die Option **3D aktivieren** aus. Klicken Sie auf **OK**.  
  
3.  (Optional) Geben Sie unter **Drehung**einen ganzzahligen Wert ein, der die horizontale Drehung des Kreisdiagramms darstellt.  
  
4.  (Optional) Geben Sie unter **Neigung**einen ganzzahligen Wert ein, der die vertikale Drehung des Kreisdiagramms darstellt.  
  
5.  Klicken Sie auf **OK**.  
  
### <a name="to-apply-3d-effects-to-a-bar-or-column-chart"></a>So wenden Sie 3D-Effekte auf ein Balken- oder Säulendiagramm an  
  
1.  Klicken Sie mit der rechten Maustaste in die Diagrammfläche, und wählen Sie **3D-Effekte**aus. Das Dialogfeld **Diagrammflächeneigenschaften** wird angezeigt.  
  
2.  Wählen Sie die Option **3D aktivieren** aus. Klicken Sie auf **OK**.  
  
3.  (Optional) Wählen Sie die Option **Reihengruppierung aktivieren** aus. Wenn das Diagramm mehrere Balken- oder Säulendiagrammreihen enthält, werden die Reihen mit dieser Option gruppiert angezeigt. Standardmäßig werden mehrere Balken- oder Säulenreihen nebeneinander angezeigt.  
  
4.  Klicken Sie auf **OK**.  
  
5.  (Optional) Um Zylindereffekte einem Balken- oder Säulendiagramm hinzuzufügen, führen Sie folgende Schritte aus:  
  
    1.  Öffnen Sie den Bereich Eigenschaften.  
  
    2.  Klicken Sie auf der Entwurfsoberfläche auf einen beliebigen Balken der Reihe. Die Eigenschaften für die Reihe werden im Bereich "Eigenschaften" angezeigt.  
  
    3.  Erweitern Sie im Abschnitt **Allgemein** den Knoten **CustomAttributes** .  
  
    4.  Geben Sie für die **DrawingStyle** -Eigenschaft den Wert **Zylinder** ein.  
  
## <a name="see-also"></a>Siehe auch  
 [3D, Abschrägungen und andere Effekte in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md)   
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
