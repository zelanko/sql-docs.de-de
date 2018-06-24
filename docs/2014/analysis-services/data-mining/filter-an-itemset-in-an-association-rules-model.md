---
title: Filtern eines Itemset in einem Zuordnungsmodell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- itemsets [Analysis Services]
- filtering itemsets [Analysis Services]
- Mining Model Viewer [Analysis Services], itemsets
ms.assetid: 3ed919ea-8598-45d2-a4a0-b1b3357a4ab1
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c7bee45242d761b87d4cae3c112fe67a3b17509e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056817"
---
# <a name="filter-an-itemset-in-an-association-rules-model"></a>Filtern eines Itemset in einem Zuordnungsregelmodell
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]können Sie die Itemsets filtern, die auf der Registerkarte **Itemsets** des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules-Viewers angezeigt werden.  
  
### <a name="to-filter-an-itemset"></a>So filtern Sie ein Itemset  
  
1.  Klicken Sie auf der Registerkarte **Miningmodell-Viewer** des Data Mining-Designers in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]auf die Registerkarte **Itemsets** des **Zuordnungsregel-Viewers**.  
  
2.  Geben Sie in das Feld **Filteritemset** eine Regelbedingung ein. Eine Regelbedingung könnte z. B. "Touring-1000 = existing" sein.  
  
3.  Klicken Sie auf **Eingabe**.  
  
 Die Itemsets werden jetzt gefiltert und zeigen nur die Itemsets an, die die ausgewählten Elemente enthalten. In diesem Feld wird nicht nach Groß-/Kleinschreibung unterschieden. Filter werden im Arbeitsspeicher gespeichert. Sie können daher einen alten Filter aus der Liste auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für den Miningmodell-Viewer](mining-model-viewer-tasks-and-how-tos.md)  
  
  