---
title: MSMQ-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a057c6678e27f51aba438b6dd57129777867e759
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728209"
---
# <a name="msmq-connection-manager"></a>MSMQ-Verbindungs-Manager

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Mit einem MSMQ-Verbindungs-Manager kann ein Paket eine Verbindung mit einer Nachrichtenwarteschlange herstellen, die Message Queuing (MSMQ) verwendet. Der Task Nachrichtenwarteschlange von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet einen MSMQ-Verbindungs-Manager.  
  
 Wenn Sie einem Paket einen MSMQ-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit in eine MSMQ-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der **Connections** -Sammlung im Paket den Verbindungs-Manager hinzufügt. Die **ConnectionManagerType** -Eigenschaft des Verbindungs-Managers ist auf **MSMQ**festgelegt.  
  
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
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [MSMQ-Verbindungs-Manager-Editor](../../integration-services/connection-manager/msmq-connection-manager-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="msmq-connection-manager-editor"></a>MSMQ-Verbindungs-Manager-Editor
  Mithilfe des Dialogfelds **MSMQ-Verbindungs-Manager** geben Sie den Pfad zu einer Message Queuing-Meldungswarteschlange (auch bekannt als MSMQ) an.  
  
 Weitere Informationen zum MSMQ-Verbindungs-Manager finden Sie unter [MSMQ Connection Manager](../../integration-services/connection-manager/msmq-connection-manager.md).  
  
> [!NOTE]  
>  Der MSMQ-Verbindungs-Manager unterstützt lokale öffentliche und private Warteschlangen sowie öffentliche Remotewarteschlangen. Er unterstützt keine privaten Remotewarteschlangen. Eine Problemumgehung mithilfe des Skripttasks finden Sie unter [Senden mit dem Skripttask an eine private Remotemeldungswarteschlange](../../integration-services/extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md).  
  
### <a name="options"></a>Optionen  
 **Name**  
 Geben Sie einen eindeutigen Namen für den Verbindungs-Manager im Workflow an. Der angegebene Name wird im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer angezeigt.  
  
 **Beschreibung**  
 Beschreiben Sie den Verbindungs-Manager. Die bewährte Methode ist hierbei, den Verbindungs-Manager zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und leichter zu verwalten sind.  
  
 **Pfad**  
 Geben Sie den vollständigen Pfad der Meldungswarteschlange ein. Das Format des Pfades ist vom Typ der Warteschlange abhängig.  
  
|Warteschlangentyp|Beispielpfad|  
|----------------|-----------------|  
|Öffentlich|\<Computername>\\<Name der Warteschlange\>|  
|Privat|\<Computername>\Private$\\<Name der Warteschlange\>|  
  
 Sie können "." verwenden, um den lokalen Computer darzustellen.  
  
 **Test**  
 Nachdem die Konfiguration des MSMQ-Verbindungs-Managers abgeschlossen ist, überprüfen Sie die Gültigkeit der Verbindung, indem Sie auf **Testen**klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nachrichtenwarteschlange (Task)](../../integration-services/control-flow/message-queue-task.md)   
 [Integration Services-Verbindungen &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
