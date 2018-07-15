---
title: Festlegen eines Ausrichtungsintervalls auf einem Messgerät (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0ece7297-6e2f-47fb-835d-b9e9cce53fe2
caps.latest.revision: 7
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 48dc33f7bf80aacb757e990987a58c86f932ccb4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296020"
---
# <a name="set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs"></a>Festlegen eines Ausrichtungsintervalls auf einem Messgerät (Berichts-Generator und SSRS)
  Durch das Ausrichtungsintervall wird das Vielfache festgelegt, auf das Werte gerundet werden. Standardmäßig zeigt das Messgerät auf den exakten Wert des Felds, das Sie im Datenbereich angegeben haben. Eventuell möchten Sie jedoch, dass der exakte Wert nach oben oder unten gerundet wird, sodass der Zeiger an einem vordefinierten Intervall ausgerichtet wird. Beispiel: Wenn der Wert auf dem Messgerät 34,2 beträgt und Sie ein Ausrichtungsintervall von 5 festlegen, zeigt der Messgerätzeiger auf 35. Wenn der Wert auf dem Messgerät 31,2 beträgt und Sie ein Ausrichtungsintervall von 5 festlegen, zeigt der Messgerätzeiger auf 30.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-snapping-interval-on-a-gauge"></a>So legen Sie ein Ausrichtungsintervall auf einem Messgerät fest  
  
1.  Klicken Sie auf eine der Nummern des Messgeräts, um die Skala auszuwählen.  
  
2.  Öffnen Sie den Bereich Eigenschaften.  
  
    > [!NOTE]  
    >  Wenn Sie den Bereich "Eigenschaften" nicht angezeigt werden, klicken Sie auf die **Ansicht** Registerkarte, und wählen Sie dann die **Eigenschaften** Kontrollkästchen.  
  
3.  In der **Zeiger** -Eigenschaft, klicken Sie auf die Schaltfläche (…). Der Zeigerauflistungs-Editor wird geöffnet.  
  
4.  Legen Sie die **SnappingEnabled** Eigenschaft `True`.  
  
5.  Legen Sie die **SnappingInterval** auf einen Wert, der das ausrichtungsintervall fest. Der Zeiger wird am nächsten Rundungsvielfachen des angegebenen Werts ausgerichtet.  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren von Skalen auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Formatieren von Zeigern auf einem Messgerät (Berichts-Generator und SSRS)](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Messgeräte &#40;Berichts-Generator und SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md)  
  
  
