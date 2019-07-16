---
title: Filtern eines Itemset in einem Zuordnungsmodell | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8cb507be05ae8f8ad3b25b386d55785c966f14f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68183233"
---
# <a name="filter-an-itemset-in-an-association-rules-model"></a>Filtern eines Itemset in einem Zuordnungsregelmodell
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]können Sie die Itemsets filtern, die auf der Registerkarte **Itemsets** des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules-Viewers angezeigt werden.  
  
### <a name="to-filter-an-itemset"></a>So filtern Sie ein Itemset  
  
1.  Klicken Sie auf der Registerkarte **Miningmodell-Viewer** des Data Mining-Designers in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]auf die Registerkarte **Itemsets** des **Zuordnungsregel-Viewers**.  
  
2.  Geben Sie in das Feld **Filteritemset** eine Regelbedingung ein. Eine Regelbedingung könnte z. B. "Touring-1000 = existing" sein.  
  
3.  Klicken Sie auf **Eingabe**.  
  
 Die Itemsets werden jetzt gefiltert und zeigen nur die Itemsets an, die die ausgewählten Elemente enthalten. In diesem Feld wird nicht nach Groß-/Kleinschreibung unterschieden. Filter werden im Arbeitsspeicher gespeichert. Sie können daher einen alten Filter aus der Liste auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für den Miningmodell-Viewer](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
