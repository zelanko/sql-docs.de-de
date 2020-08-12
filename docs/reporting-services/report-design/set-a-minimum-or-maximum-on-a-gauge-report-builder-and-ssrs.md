---
title: Festlegen eines Mindestwerts oder eines Höchstwerts auf einem Messgerät (Berichts-Generator) | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie sich das Messgerät von Diagrammen in einem paginierten Bericht unterscheidet. Im Berichts-Generator geben Sie den Mindest- und den Höchstwert auf einer Skala an.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: b4c260c0-5a88-4f30-8977-eb5cc78fc146
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2277867a1709ddaa735c00934468800c23841548
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84886582"
---
# <a name="set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs"></a>Festlegen eines Mindestwerts oder eines Höchstwerts auf einem Messgerät (Berichts-Generator und SSRS)
  Im Gegensatz zu Diagrammen in einem paginierten [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] -Bericht, in dem mehrere Gruppen definiert sind, zeigen Messgeräte nur einen Wert an. Da Berichts-Generator und Berichts-Designer nicht in der Lage sind, den Kontext oder die relative Bedeutung des einen Werts, der auf dem Messgerät angezeigt werden soll, zu ermitteln, müssen Sie den niedrigsten und den höchsten Wert der Skala festlegen.   
    
  Wenn die Datenwerte zum Beispiel zwischen 0 und 10 liegen, sollten Sie den Mindestwert 0 und den Höchstwert 10 festlegen. Die Intervalle werden automatisch basierend auf dem festgelegten Mindest- und Höchstwert berechnet. Standardmäßig wird der Mindestwert 0 und der Höchstwert 100 festgelegt. Dies sind jedoch willkürliche Werte, die geändert werden können. Der Wert wird nicht als Prozentwert berechnet.  
  
 Falls Sie mit einem großen Wertebereich arbeiten, wie etwa von 0 bis 10000, können Sie ggf. einen Multiplikator verwenden, um die Anzahl der Nullen auf dem Messgerät zu reduzieren. Der Multiplikator reduziert lediglich die Skalierung der Zahlen auf dem Messgerät, nicht den Wert selbst.  
  
 Sie können die Werte der Optionen **Minimum** und **Maximum** mithilfe von Ausdrücken festlegen. Weitere Informationen finden Sie unter [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
## <a name="to-set-the-minimum-and-maximum-on-the-gauge"></a>So legen Sie den Mindestwert und den Höchstwert auf dem Messgerät fest  
  
1.  Klicken Sie mit der rechten Maustaste auf die Skalierung, und wählen Sie **Skalierungseigenschaften**aus. Das Dialogfeld **Skalierungseigenschaften** wird angezeigt.  
  
2.  Geben Sie im Abschnitt **Allgemein**einen Wert für **Minimum**an. Dieser Wert ist standardmäßig 0. Klicken Sie optional auf die **Ausdrucksschaltfläche** (*fx*), um den Ausdruck zu bearbeiten, der den Wert der Option festlegt.  
  
3.  Geben Sie einen Wert für **Maximum**an. Der Standardwert ist 100. Klicken Sie optional auf die **Ausdrucksschaltfläche** (*fx*), um den Ausdruck zu bearbeiten, der den Wert der Option festlegt.  
  
4.  (Optional) Falls die angegebenen Werte sehr groß sind, legen Sie einen Wert für **Skalabezeichnungen multiplizieren mit** fest. Um einen Multiplikator festzulegen, durch den die Skalierung reduziert wird, verwenden Sie eine Dezimalzahl. Wenn Sie zum Beispiel eine Skalierung von 0 bis 1000 verwenden, können Sie den Multiplikatorwert 0,01 festlegen, sodass die Skalierung als 0 bis 10 angezeigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Skalen auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Formatieren von Zeigern auf einem Messgerät (Berichts-Generator und SSRS)](../../reporting-services/report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Messgeräte &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)  
  
  
