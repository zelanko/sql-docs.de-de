---
title: Angeben der Größe eines Indikators mithilfe eines Ausdrucks (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: ab0b86f1-4882-4258-a2b6-c612faecfa4b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a77a96d57a1ea9489697a415e96fb52165b8270f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014811"
---
# <a name="specify-the-size-of-an-indicator-using-an-expression-report-builder-and-ssrs"></a>Angeben der Größe eines Indikators mithilfe eines Ausdrucks (Berichts-Generator und SSRS)
  Zusätzlich zu Farbe, Richtung und Form können Sie die Größe anpassen und damit die visuelle Wirkung von Indikatoren maximieren.  
  
 Ein Indikator verfügt über eine Auflistung von Indikatorstatus mit der Bezeichnung IndicatorStates. Die IndicatorStates-Auflistung verfügt in der Regel über mehrere Status. Jeder Status ist ein Element der Auflistung und wird durch ein Symbol dargestellt. Zusammen bilden die Status die IndicatorsStates-Auflistung.  
  
 Um die Größen von Symbolen dynamisch zu konfigurieren, legen Sie die Eigenschaften der Elemente der IndicatorsStates-Auflistung im Eigenschaftenbereich des Berichts-Generators fest. Zum Anzeigen des Bereichs **Eigenschaften** klicken Sie auf der Registerkarte **Ansicht** auf **Eigenschaften**.  
  
> [!NOTE]  
>  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]verwenden Sie das **Eigenschaftenfenster** , um die Elementeigenschaften festzulegen. Wenn das **Eigenschaftenfenster** nicht geöffnet ist, drücken Sie die F4-TASTE.  
  
 Der Bereich **Eigenschaften** bietet Zugriff auf die Eigenschaften der IndicatorStates-Auflistung eines Indikators. Sie konfigurieren die Größe der Symbole, indem Sie die ScaleFactor-Eigenschaft der IndicatorStates-Auflistungselemente mit einem Ausdruck festlegen. Weitere Informationen finden Sie unter [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
 Der in dieser Prozedur verwendete Ausdruck wurde ebenfalls verwendet, um den Bericht mit Indikatoren verschiedener Größe zu erstellen, wie in [Indikatoren &#40;Berichts-Generator und SSRS&#41;](indicators-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-the-indicator-icon-size-using-an-expression"></a>So geben Sie die Symbolgröße für Indikatoren mit einem Ausdruck an  
  
1.  Klicken Sie auf den Indikator, den Sie ändern möchten.  
  
2.  Suchen Sie im Eigenschaftenbereich die IndicatorStates-Eigenschaft.  
  
     Wenn der Eigenschaftenbereich nach Kategorie organisiert ist, finden Sie IndicatorStates unter der Kategorie **Status** .  
  
3.  Klicken Sie neben IndicatorStates auf die Schaltfläche mit den Auslassungszeichen **(...)** . Das Dialogfeld **IndicatorState-Auflistungs-Editor** wird geöffnet.  
  
     Wählen Sie alle Elemente der Auflistung aus.  
  
4.  Klicken Sie in der Liste mit den **Mehrfachauswahleigenschaften** auf den Abwärtspfeil neben ScaleFactor, und klicken Sie dann auf **Ausdruck**.  
  
5.  Schreiben Sie im Dialogfeld **Ausdruck** den Ausdruck.  
  
     Der folgende Beispielausdruck ändert die Größe des Symbols basierend auf dem Wert des **SalesYTD** -Felds.  
  
     `=IIF(Fields!SalesYTD.value = 0,0,Fields!SalesYTD.value/Max(Fields!SalesYTD.value,"Indicator"))`  
  
     Weitere Informationen finden Sie unter [Beispiele für Ausdrücke (Berichts-Generator und SSRS)](expression-examples-report-builder-and-ssrs.md).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Indikatoren &#40;Berichts-Generator und SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  
