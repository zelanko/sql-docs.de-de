---
title: Beginnen der Kreisdiagrammwerte an der Kreisoberseite (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2610534159be781e2719034b41276be5f0d7d473
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104815"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>Beginnen der Kreisdiagrammwerte an der Kreisoberseite (Berichts-Generator und SSRS)
  Standardmäßig beginnt bei Kreisdiagrammen der erste Wert im Dataset bei 90 Grad zur Oberseite des Kreises versetzt. Möglicherweise ziehen Sie es vor, dass der erste Wert oben beginnt.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>So beginnen Sie das Kreisdiagramm an der Kreisoberseite  
  
1.  Klicken Sie auf den Kreis selbst.  
  
2.  Zum Anzeigen des Bereichs **Eigenschaften** klicken Sie auf der Registerkarte **Ansicht** auf **Eigenschaften**.  
  
3.  Ändern Sie im Bereich **Eigenschaften** unter **benutzerdefinierte Attribute**den Wert für **PieStartAngle** von **0** in **270**.  
  
4.  Klicken Sie auf **Ausführen** , um den Bericht in der Vorschau anzuzeigen.  
  
 Der erste Wert beginnt jetzt an der Kreisdiagrammoberseite.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Kreisdiagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
