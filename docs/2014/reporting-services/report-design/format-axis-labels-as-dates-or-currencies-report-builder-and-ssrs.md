---
title: Formatieren von Achsenbezeichnungen als Datumsangabe oder Währung (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9a01a74-2f51-4b35-be3a-a6138568f6cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d328f58da2be026046fc2688a4959b37f5ff7d65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105883"
---
# <a name="format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs"></a>Formatieren von Achsenbezeichnungen als Datumsangabe oder Währung (Berichts-Generator und SSRS)
  Wenn Sie ordnungsgemäß formatierte DateTime-Werte auf einer Achse anzeigen, zeigt ein Diagramm diese Werte automatisch als Tage an. Zum Festlegen eines Datums- oder Zeitintervalls für die x-Achse (z. B. ein Monats- oder Stundenintervall) müssen Sie die Achsenbezeichnungen formatieren und den Achsentyp auf ein gültiges Datums- oder Zeitintervall festlegen.  
  
> [!NOTE]  
>  In Säulen- und Punktdiagrammen ist die horizontale Achse bzw. x-Achse die Kategorieachse. In Balkendiagrammen ist die vertikale Achse bzw. y-Achse die Kategorieachse.  
  
 Für die korrekte Formatierung von Zeitintervallen müssen die auf der x-Achse angezeigten Werte einen <xref:System.DateTime> -Datentyp ergeben. Wenn das Feld den Datentyp <xref:System.String>aufweist, berechnet das Diagramm Intervalle nicht als Datumsangaben oder Zeiten. Weitere Informationen finden Sie unter [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
 Wenn der y-Achse ein numerischer Wert hinzugefügt wird, wird die Zahl im Diagramm erst formatiert, wenn sie angezeigt wird. Wenn das numerische Feld eine Verkaufszahl enthält, sollten Sie die Zahlen als Währungseinheiten formatieren, um so die Lesbarkeit des Diagramms zu verbessern.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-format-x-axis-labels-as-monthly-intervals"></a>So formatieren Sie x-Achsenbezeichnungen als monatliche Intervalle  
  
1.  Klicken Sie mit der rechten Maustaste auf die horizontale Achse bzw. x-Achse des Diagramms, und wählen Sie **Eigenschaften für horizontale Achsen**aus.  
  
2.  Wählen Sie im Dialogfeld **Eigenschaften für horizontale Achsen** die Option **Zahl**aus.  
  
3.  Wählen Sie in der Liste **Kategorie** die Option **Datum**aus. Wählen Sie in der Liste **Typ** das Datumsformat aus, das auf die X-Achsenbezeichnungen angewendet werden soll.  
  
4.  Wählen Sie **Achsenoptionen**aus.  
  
5.  Geben Sie in **Intervall**den Wert **1**ein. Wählen Sie unter **Intervalltyp** die Eigenschaft **Monate**aus.  
  
    > [!NOTE]  
    >  Wenn Sie keinen Intervalltyp angeben, berechnet das Diagramm Intervalle in Tagen.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-format-y-axis-labels-using-a-currency-format"></a>So formatieren Sie y-Achsenbezeichnungen mit einem Währungsformat  
  
1.  Klicken Sie mit der rechten Maustaste auf die vertikale Achse bzw. y-Achse des Diagramms, und wählen Sie **Eigenschaften für vertikale Achsen**aus.  
  
2.  Wählen Sie im Dialogfeld **Eigenschaften für vertikale Achsen** die Option **Zahl**aus.  
  
3.  Wählen Sie in der Liste **Kategorie** die Option **Währung**aus. Wählen Sie in der Liste **Symbol** das Währungsformat aus, das auf die Y-Achsenbezeichnungen angewendet werden soll.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Angeben einer logarithmischen Skalierung (Berichts-Generator und SSRS)](specify-a-logarithmic-scale-report-builder-and-ssrs.md)   
 [Angeben eines Achsenintervalls &#40;Berichts-Generator und SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
