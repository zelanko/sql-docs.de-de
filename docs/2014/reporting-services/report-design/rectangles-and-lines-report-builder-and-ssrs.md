---
title: Rechtecke und Linien (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d6226b0c-0398-4185-8565-96099876fc21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f447d05501949df0fd0860ed7799fca2932714fa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66105386"
---
# <a name="rectangles-and-lines-report-builder-and-ssrs"></a>Rechtecke und Linien (Berichts-Generator und SSRS)
  Mit Rechtecken und Linien können visuelle Effekte in einem Bericht erzeugt werden. Sie können Anzeigeeigenschaften für diese Berichtselemente im Abschnitt "Rahmen" der Registerkarte "Home" festlegen, und im Bereich "Eigenschaften" können weitere Eigenschaften festgelegt werden. Sie können einem Rechteck Funktionen wie eine Hintergrundfarbe oder ein Bild, eine QuickInfo oder ein Lesezeichen hinzufügen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="RectanglesLinesReportParts"></a> Rechtecke und Linien als Berichtsteile  
 Sie können Rechtecke mit den darin enthaltenen Elementen getrennt von den Berichten als Berichtsteile veröffentlichen. [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 Die Berichtselemente innerhalb des Rechtecks können nicht als Berichtsteile veröffentlicht werden. Wenn Benutzer das Rechteck einem Bericht hinzufügen, erhalten sie das Rechteck und die darin enthaltenen Elemente.  
  

  
##  <a name="RectangleAsContainer"></a> Verwenden eines Rechtecks als Container  
 Ein Rechteck kann als Container für andere Elemente verwendet werden. Wenn Sie das Rechteck verschieben, werden gleichzeitig die darin enthaltenen Elemente verschoben. Ein Element innerhalb des Rechtecks zeigt den Namen des Rechtecks in seiner **Parent** -Eigenschaft an. Weitere Informationen zum Verwenden eines Rechtecks als Container finden Sie unter [Hinzufügen eines Rechtecks oder Containers (Berichts-Generator und SSRS)](add-a-rectangle-or-container-report-builder-and-ssrs.md) und [Anzeigen derselben Daten in einer Matrix und einem Diagramm (Berichts-Generator)](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).  
  
> [!NOTE]  
>  Ein Rechteck ist lediglich ein Container für Elemente, die Sie im Rechteck erstellen oder in das Rechteck ziehen. Wenn Sie ein Rechteck um ein Element zeichnen, das bereits auf der Entwurfsoberfläche vorhanden ist, fungiert das Rechteck nicht als Container. Das Rechteck wird nicht in der Parent-Eigenschaft des Elements aufgelistet.  
  
 Wenn Rechtecke als Container für Berichtselemente verwendet werden, sollten Sie berücksichtigen, wie die Elemente als Ganzes beim Rendern des Berichts beeinflusst werden. Berichtselemente, die wiederholte Zeilen von Daten enthalten (z. B. Tabellen), werden erweitert, um die Daten aufzunehmen, die von einer Abfrage zurückgegeben werden, was die Positionierung anderer Elemente im Rechteck beeinflusst. Elemente werden von einer Tabelle nach unten verschoben, wenn sich diese Elemente unterhalb des Datenbereichs befinden. Um ein Element an einem bestimmten Platz zu verankern, können Sie das Berichtselement innerhalb eines Rechtecks platzieren, dessen oberer Rand oberhalb des unteren Randes der Tabelle liegt. Weitere Informationen finden Sie unter [Renderingverhalten &#40;Berichts-Generator und SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).  
  

  
##  <a name="ReportBorder"></a> Hinzufügen von Berichtsrahmen  
 Sie können einem Bericht ohne Hinzufügen von Linien oder Rechtecken einen Rahmen hinzufügen, indem Sie Kopfzeilen, Fußzeilen und dem Berichtshauptteil selbst Rahmen hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen eines Rahmens zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).  
  

  
##  <a name="HowTo"></a> Themen zur Vorgehensweise  
 [Hinzufügen eines Rahmens zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md)  
  
 [Hinzufügen eines Rechtecks oder Containers &#40;Berichts-Generator und SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
 [Hinzufügen und Ändern einer Linie &#40;Berichts-Generator und SSRS&#41;](add-and-modify-a-line-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen eines Rechtecks oder Containers &#40;Berichts-Generator und SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
  
