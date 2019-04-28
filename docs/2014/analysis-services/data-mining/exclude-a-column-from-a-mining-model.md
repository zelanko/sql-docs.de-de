---
title: Ausschließen einer Spalte aus einem Miningmodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 418fdb56792c9d8e3ca15128ad8f93fed2ae9c47
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62722402"
---
# <a name="exclude-a-column-from-a-mining-model"></a>Ausschließen einer Spalte aus einem Miningmodell
  Wenn Sie ein neues Miningmodell erstellen, möchten Sie möglicherweise nicht alle Spalten verwenden, die in der Miningstruktur vorhanden sind, auf der das Modell basiert. Beispielsweise wird möglicherweise eine Kundennamenspalte für den Drillthrough hinzugefügt, aber nicht für modellierungen verwenden möchten. Unter Umständen möchten Sie auch mehrere Kopien einer Spalte mit verschiedenen Diskretisierungen erstellen und in jedem Modell nur eine Kopie verwenden und die restlichen Objekte ignorieren. Sie könnten auch Eingabespalten in mehreren verschiedenen Modellen selektiv hinzufügen, um zu erkennen, wie die hinzugefügte Variable die Ausgabespalte beeinflusst.  
  
 Sie müssen keine neue Miningstruktur für jede Kombination von Spalten erstellen, sondern es genügt, wenn Sie eine Spalte so kennzeichnen, dass sie nicht in einem bestimmten Modell verwendet wird.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>So schließen Sie eine Spalte aus einem Miningmodell aus  
  
1.  Wählen Sie in der Registerkarte **Miningmodelle** des Data Mining-Designers in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]unter dem entsprechenden Miningmodell die Zelle aus, die der Spalte entspricht, die ausgeschlossen werden soll.  
  
2.  Wählen Sie im Dropdown-Listenfeld **Ignorieren** aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodelltasks und -anweisungen](mining-model-tasks-and-how-tos.md)  
  
  
