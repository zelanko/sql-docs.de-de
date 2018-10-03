---
title: MSMQ-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a1501af4a26c0e039df3113a719a61e1e2c3f40a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135040"
---
# <a name="msmq-connection-manager"></a>MSMQ-Verbindungs-Manager
  Mit einem MSMQ-Verbindungs-Manager kann ein Paket eine Verbindung mit einer Nachrichtenwarteschlange herstellen, die Message Queuing (MSMQ) verwendet. Der Task Nachrichtenwarteschlange von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet einen MSMQ-Verbindungs-Manager.  
  
 Wenn Sie einem Paket einen MSMQ-Verbindungs-Manager hinzufügen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, die in eine MSMQ-Verbindung zur Laufzeit aufgelöst wird, die Verbindungs-Manager-Eigenschaften festlegt und fügt den Verbindungs-Manager erstellt die `Connections` Auflistung auf der das Paket. Die `ConnectionManagerType` Eigenschaft des Verbindungs-Managers nastaven NA hodnotu `MSMQ`.  
  
 Es gibt folgende Möglichkeiten, um einen MSMQ-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie eine Verbindungszeichenfolge an.  
  
-   Stellen Sie den Pfad der Nachrichtenwarteschlange bereit, mit der eine Verbindung hergestellt werden soll.  
  
 Das Format des Pfads richtet sich nach dem Typ der Warteschlange, wie in der folgenden Tabelle dargestellt.  
  
|Warteschlangentyp|Beispielpfad|  
|----------------|-----------------|  
|Öffentlich|\<Computername>\\<Name der Warteschlange\>|  
|Privat|\<Computername>\Private$\\<Name der Warteschlange\>|  
  
 Sie können einen Punkt (.) verwenden, um den lokalen Computer darzustellen.  
  
## <a name="configuration-of-the-msmq-connection-manager"></a>Konfiguration des MSMQ-Verbindungs-Managers  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [MSMQ-Verbindungs-Manager-Editor](../msmq-connection-manager-editor.md).  
  
 Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Nachrichtenwarteschlange (Task)](../control-flow/message-queue-task.md)   
 [Integrationsdienste &#40;SSIS&#41; Verbindungen](integration-services-ssis-connections.md)  
  
  
