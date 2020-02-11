---
title: Angeben eines Achsenintervalls (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46712d-a5bf-44c0-9929-e30ccc1e7e33
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d862ac509af3936a9f09cadd01667cbe81a679c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104847"
---
# <a name="specify-an-axis-interval-report-builder-and-ssrs"></a>Angeben eines Achsenintervalls (Berichts-Generator und SSRS)
  Das Achsenintervall definiert die Anzahl von Bezeichnungen und zugehörigen Teilstrichen auf einer Achse. Auf der Wertachse stellen die Achsenintervalle ein konsistentes Maß für die Datenpunkte im Diagramm bereit. Auf der Kategorieachse kann diese Funktion jedoch bewirken, dass Kategorien ohne Achsenbezeichnungen angezeigt werden. Sie können die Anzahl der Intervalle in der Interval-Eigenschaft der Achse festlegen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] berechnet die Anzahl der Intervalle zur Laufzeit basierend auf den Daten im Resultset. Weitere Informationen zum Berechnen von Achsenintervallen finden Sie unter [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  
  
 Dieses Thema gilt nicht für Datums- oder Zeitwerte auf der Kategorieachse. Standardmäßig werden `DateTime`-Werte als Tage angezeigt. Wenn Sie ein anderes Datums- oder Zeitintervall angeben möchten, z. B. ein Monats- oder Zeitintervall, müssen Sie die Achsenbezeichnungen formatieren und die Achse auf die Anzeige von Instanzen von `DateTime`-Typen statt von `String`-Typen festlegen. Darüber hinaus müssen Sie die Interval-Eigenschaft festlegen. Weitere Informationen finden Sie unter [Formatieren von Achsenbezeichnungen als Datumsangabe oder Währung &#40;Berichts-Generator und SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md).  
  
 Dieses Thema gilt nicht für Kreis-, Ring-, Trichter- oder Pyramidendiagramme, die keine Achsen haben.  
  
> [!NOTE]  
>  Die Kategorieachse ist normalerweise die horizontale Achse oder x-Achse. Bei Balkendiagrammen ist die Kategorieachse jedoch die vertikale Achse oder y-Achse.  
  
 Ein Beispiel für ein Diagramm, in dem andere Achsenintervalle angegeben werden, ist als Beispielbericht verfügbar. Weitere Informationen zum Herunterladen dieses Beispiel Berichts und anderer Informationen finden [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]Sie unter [Berichts-Generator und Berichts-Designer Beispiel Berichte](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-show-all-category-labels-on-the-x-axis"></a>So zeigen Sie alle Kategoriebezeichnungen auf der X-Achse an  
  
1.  Klicken Sie mit der rechten Maustaste auf die Kategorieachse, und klicken Sie auf **Achseneigenschaften**. Das Dialogfeld **Achseneigenschaften** wird angezeigt.  
  
2.  Legen Sie unter **Achsen Optionen** `Interval` auf **1**fest. Jede Kategoriegruppenbezeichnung wird angezeigt. Wenn Sie jede zweite Kategoriegruppenbezeichnung auf der X-Achse anzeigen möchten, geben Sie **2**ein.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  Wenn ein Achsenintervall festgelegt wird, wird die automatische Kennzeichnung deaktiviert. Wenn Sie einen Wert für das Achsenintervall angeben, kann es je nach Anzahl der Kategorien auf der Kategorieachse zu unerwartetem Kennzeichnungsverhalten kommen.  
  
### <a name="to-enable-a-variable-interval-calculation-on-an-axis"></a>So aktivieren Sie eine variable Intervallberechnung auf einer Achse  
  
1.  Klicken Sie mit der rechten Maustaste auf die Diagrammachse, die Sie ändern möchten, und klicken Sie dann auf **Achseneigenschaften**. Das Dialogfeld **Achseneigenschaften** wird angezeigt.  
  
2.  Legen Sie unter **Achsen Optionen die Option**auf `Interval` **automatisch**fest. Im Diagramm wird die optimale Anzahl von Kategoriebezeichnungen angezeigt, die auf die Achse passen.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Sortieren von Daten in einem Datenbereich &#40;Berichts-Generator und SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)   
 [Achseneigenschaften (Dialogfeld), Achsenoptionen (Berichts-Generator und SSRS)](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)   
 [Angeben einer logarithmischen Skalierung (Berichts-Generator und SSRS)](specify-a-logarithmic-scale-report-builder-and-ssrs.md)   
 [Zeichnen von Daten auf einer sekundären Achse &#40;Berichts-Generator und SSRS&#41;](plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)  
  
  
