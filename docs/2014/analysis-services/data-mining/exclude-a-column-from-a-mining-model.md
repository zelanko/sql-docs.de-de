---
title: Ausschließen einer Spalte aus einem Miningmodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d68a1251074d3815b852b1b43f63b36df744d0dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269816"
---
# <a name="exclude-a-column-from-a-mining-model"></a>Ausschließen einer Spalte aus einem Miningmodell
  Wenn Sie ein neues Miningmodell erstellen, möchten Sie möglicherweise nicht alle Spalten verwenden, die in der Miningstruktur vorhanden sind, auf der das Modell basiert. Beispiel: Sie haben möglicherweise eine Kundennamenspalte für einen Drillthroughvorgang hinzugefügt, möchten sie jedoch nicht für Modellierungen verwenden. Unter Umständen möchten Sie auch mehrere Kopien einer Spalte mit verschiedenen Diskretisierungen erstellen und in jedem Modell nur eine Kopie verwenden und die restlichen Objekte ignorieren. Sie könnten auch Eingabespalten in mehreren verschiedenen Modellen selektiv hinzufügen, um zu erkennen, wie die hinzugefügte Variable die Ausgabespalte beeinflusst.  
  
 Sie müssen keine neue Miningstruktur für jede Kombination von Spalten erstellen, sondern es genügt, wenn Sie eine Spalte so kennzeichnen, dass sie nicht in einem bestimmten Modell verwendet wird.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>So schließen Sie eine Spalte aus einem Miningmodell aus  
  
1.  Wählen Sie in der Registerkarte **Miningmodelle** des Data Mining-Designers in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]unter dem entsprechenden Miningmodell die Zelle aus, die der Spalte entspricht, die ausgeschlossen werden soll.  
  
2.  Wählen Sie im Dropdown-Listenfeld **Ignorieren** aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodelltasks und -anweisungen](mining-model-tasks-and-how-tos.md)  
  
  
