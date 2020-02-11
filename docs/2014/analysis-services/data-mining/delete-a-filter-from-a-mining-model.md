---
title: Löschen eines Filters aus einem Mining Modell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filters [Analysis Services]
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a8b19c9c23857013796885eb8d2d3469607eae17
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66084730"
---
# <a name="delete-a-filter-from-a-mining-model"></a>Löschen eines Filters aus einem Miningmodell
  Wenn Sie auf einem Miningmodell einen Filter erstellen, können Sie Modelle auf einer Teilmenge der Daten in der Datenquellensicht erstellen. Filter sind auch für das Testen der Genauigkeit des Modells auf einer Teilmenge der ursprünglichen Daten nützlich.  
  
 Sie müssen den Filter jedoch löschen, wenn Sie wieder den vollständigen Satz von Fällen anzeigen möchten. Dieses Verfahren beschreibt, wie Sie Bedingungen in einem Filter entfernen oder den Filter vollständig löschen.  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a>So löschen Sie eine Bedingung aus einem Filter in einem Miningmodell  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Projektmappen-Explorer auf die Miningstruktur, die das Miningmodell enthält, auf das Sie einen Filter anwenden möchten.  
  
2.  Klicken Sie auf die Registerkarte **Miningmodelle** .  
  
3.  Wählen Sie das Modell aus, und klicken Sie mit der rechten Maustaste, um das Kontextmenü zu öffnen.  
  
     Oder  
  
     Wählen Sie das Modell aus. Wählen Sie im Menü **Miningmodell** die Option **Modellfilter festlegen**aus.  
  
4.  Klicken Sie im Dialogfeld **Modellfilter** mit der rechten Maustaste auf die Zeile im Raster, die die Bedingung enthält, die Sie löschen möchten.  
  
5.  Klicken Sie auf **Löschen**.  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a>So löschen Sie den Filter in einem Miningmodell im Dialogfeld 'Filter-Editor'  
  
-   Klicken Sie im Dialogfeld **Filter-Editor** mit der rechten Maustaste auf eine beliebige Zeile im Raster, und wählen Sie **Alle löschen**aus.  
  
## <a name="working-with-model-filters-using-the-properties-window"></a>Arbeiten mit Modellfiltern mit dem Eigenschaftenfenster  
 Wenn Sie den gesamten Filter löschen möchten, müssen Sie die Dialogfelder des Filter-Editors nicht öffnen. Die Filterbedingungen, die Sie erstellt haben, sind in der `Filter`-Eigenschaft des Miningmodells verfügbar.  
  
> [!NOTE]  
>  Sie können die Eigenschaften eines Miningmodells in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]anzeigen, aber nicht in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a>So löschen Sie den Filter in einem Miningmodell im Projektmappen-Explorer  
  
1.  Klicken Sie im Projektmappen-Explorer auf das Miningmodell, das den Filter enthält.  
  
2.  Klicken Sie im **Eigenschaften** Fenster mit der rechten Maustaste auf den Filter Text `Filter` in der-Eigenschaft, und wählen Sie **Alle auswählen**aus.  
  
3.  Drücken Sie die Rücktaste oder die Taste ENTF.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Drillthrough zu Falldaten aus einem Mining Modell](drill-through-to-case-data-from-a-mining-model.md)   
 [Mining Modell Tasks und Anleitungen](mining-model-tasks-and-how-tos.md)   
 [Filter für Mining Modelle &#40;Analysis Services Data Mining-&#41;](mining-models-analysis-services-data-mining.md)  
  
  
