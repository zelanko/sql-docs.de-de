---
title: Hinzufügen einer Enumeration zu einer Ablaufsteuerung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding enumerations
- Foreach Loop containers
- control flow [Integration Services], enumerations
- repeating workflows
- enumerations [Integration Services]
ms.assetid: f212b5fb-3cc4-422e-9b7c-89eb769a812a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7e203b75918cad416d97ab7a226f360c1203d69d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383958"
---
# <a name="add-enumeration-to-a-control-flow"></a>Hinzufügen einer Enumeration zu einer Ablaufsteuerung
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] schließt den Foreach-Schleifencontainer ein. Dabei handelt es sich um ein Ablaufsteuerungselement, mit dem Sie auf einfache Weise eine Schleifenkonstruktion einschließen können, mit der Dateien und Objekte in der Ablaufsteuerung eines Pakets aufgezählt werden. Weitere Informationen finden Sie unter [Foreach-Schleifencontainer](control-flow/foreach-loop-container.md).  
  
 Der Foreach-Schleifencontainer stellt keine Funktionalität bereit. Er stellt lediglich die Struktur bereit, in der Sie die wiederholbare Ablaufsteuerung erstellen, einen Enumeratortyp angeben und den Enumerator konfigurieren. Sie müssen mindestens einen Task in den Foreach-Schleifencontainer einschließen, um Containerfunktionalität bereitzustellen. Weitere Informationen finden Sie unter [Integration Services Tasks](control-flow/integration-services-tasks.md).  
  
 Der Foreach-Schleifencontainer kann eine Ablaufsteuerung mit mehreren Tasks und anderen Containern einschließen. Das Hinzufügen von Tasks und Containern zu einem Foreach-Schleifencontainer ist mit dem Hinzufügen von Tasks und Containern zu einem Paket vergleichbar, außer dass Sie die Tasks und Container nicht in das Paket, sondern in den Foreach-Schleifencontainer ziehen. Falls der Foreach-Schleifencontainer mehrere Tasks oder Container einschließt, können Sie diese wie bei einem Paket mithilfe von Rangfolgeneinschränkungen verbinden. Weitere Informationen finden Sie unter [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md).  
  
### <a name="to-implement-a-foreach-loop-container-in-a-control-flow"></a>So implementieren Sie einen Foreach-Schleifencontainer in einer Ablaufsteuerung  
  
1.  Fügen Sie dem Paket den Foreach-Schleifencontainer hinzu. Weitere Informationen finden Sie unter [hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
2.  Fügen Sie dem Foreach-Schleifencontainer Tasks und Container hinzu. Weitere Informationen finden Sie unter [hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
3.  Verbinden Sie Tasks und Container im Foreach-Schleifencontainer mithilfe von Rangfolgeneinschränkungen. Weitere Informationen finden Sie unter [Verbinden von Tasks und Containern mithilfe einer Standardrangfolgeneinschränkung](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).  
  
4.  Konfigurieren Sie den Foreach-Schleifencontainer. Weitere Informationen finden Sie unter [Konfigurieren eines Foreach-Schleifencontainers](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Gruppe oder Aufheben der Gruppierung von Komponenten](group-or-ungroup-components.md)   
 [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md)   
 [Hinzufügen einer Iteration zu einer Ablaufsteuerung](add-iteration-to-a-control-flow.md)   
 [Ablaufsteuerung](control-flow/control-flow.md)  
  
  
