---
title: Ändern der Eigenschaften einer Miningstruktur | Microsoft-Dokumentation
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8064fcc088c7ae9e7dd96c5c132b1246fe0ae2db
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62670170"
---
# <a name="change-the-properties-of-a-mining-structure"></a>Ändern der Eigenschaften einer Miningstruktur
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Es gibt zwei Arten von Eigenschaften in einer Miningstruktur, die jeweils geändert werden können:  
  
-   Eigenschaften der Miningstruktur, die die gesamte Struktur betreffen.  
  
-   Eigenschaften in einzelnen Spalten in der Struktur  
  
 Einige Eigenschaften sind von anderen Eigenschafteneinstellungen abhängig. Sie können beispielsweise keine Eigenschaften festlegen, die das Diskretisierungsverhalten steuern (wie <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> oder <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>), solange Sie den Datentyp der Spalte auf **Diskretisiert**festgelegt haben.  
  
 Weitere Informationen zu Miningstruktureigenschaften finden Sie unter [Miningstrukturspalten](../../analysis-services/data-mining/mining-structure-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>So ändern Sie die Eigenschaften einer Miningstruktur  
  
1.  Klicken Sie auf der Registerkarte **Miningstruktur** im Data Mining-Designer mit der rechten Maustaste entweder auf die Miningstruktur oder auf eine Spalte innerhalb der Miningstruktur, und klicken Sie anschließend auf **Eigenschaften**.  
  
     Im rechten Bildschirmbereich wird das **Eigenschaften** -Fenster geöffnet, wenn es nicht bereits sichtbar war.  
  
2.  Wählen Sie im **Eigenschaften** -Fenster den Wert aus, der der Eigenschaft entspricht, die Sie ändern möchten, und geben Sie dann den neuen Wert ein.  
  
     Der neue Wert wird wirksam, wenn Sie ein anderes Element im Designer auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningstrukturen](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
