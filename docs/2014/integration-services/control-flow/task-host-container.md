---
title: Taskhostcontainer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b2d8929b25a734073a5c93251c6fdc83aeecbe4c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37217960"
---
# <a name="task-host-container"></a>Taskhostcontainer
  Der Taskhostcontainer kapselt einen einzelnen Task. Im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer wird der Taskhost nicht separat konfiguriert. Er wird stattdessen konfiguriert, wenn Sie die Eigenschaften des gekapselten Tasks festlegen. Weitere Informationen zu den Tasks, die die Taskhostcontainer kapseln, finden Sie unter [Integration Services Tasks](integration-services-tasks.md).  
  
 Dieser Container erweitert die Verwendung von Variablen und Ereignishandlern auf die Taskebene. Weitere Informationen finden Sie unter [Integration Services-Ereignishandler &#40;SSIS&#41;](../integration-services-ssis-event-handlers.md) und [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
## <a name="configuration-of-the-task-host"></a>Konfiguration des Taskhosts  
 Eigenschaften können Sie im Fenster **Eigenschaften** von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oder programmgesteuert festlegen.  
  
 Informationen über die Festlegung dieser Eigenschaften in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]finden Sie unter [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md).  
  
 Weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Integration Services-Container](integration-services-containers.md)  
  
  
