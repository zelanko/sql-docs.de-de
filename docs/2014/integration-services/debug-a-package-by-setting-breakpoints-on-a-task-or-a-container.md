---
title: Debuggen eines Pakets durch Festlegen von Breakpoints auf einem Task oder Container | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3c78fb92078c604d881f18ea3472e23619771b49
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898888"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a>Debuggen eines Pakets durch Festlegen von Breakpoints auf einem Task oder Container
  In diesem Verfahren wird beschrieben, wie in einem Paket, Task, For-Schleifencontainer, Foreach-Schleifencontainer oder einem Sequenzcontainer Breakpoints festgelegt werden.  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a>So legen Sie Breakpoints in einem Paket, einem Task oder einem Container fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie auf das Paket, in dem Sie Breakpoints festlegen möchten.  
  
3.  Gehen Sie im SSIS-Designer wie folgt vor:  
  
    -   Um Breakpoints im Paketobjekt festzulegen, klicken Sie auf die Registerkarte **Ablaufsteuerung,** setzen den Cursor an eine beliebige Stelle im Hintergrund der Entwurfsoberfläche, klicken mit der rechten Maustaste und wählen dann **Breakpoints bearbeiten**aus.  
  
    -   Um Breakpoints in einer Paketablaufsteuerung festzulegen, klicken Sie auf die Registerkarte **Ablaufsteuerung** , klicken mit der rechten Maustaste auf einen Task, einen For-Schleifencontainer, einen Foreach-Schleifencontainer oder einen Sequenzcontainer und dann auf **Breakpoints bearbeiten**.  
  
    -   Um Breakpoints in einem Ereignishandler festzulegen, klicken Sie auf die Registerkarte **Ereignishandler** , klicken mit der rechten Maustaste auf einen Task, einen For-Schleifencontainer, einen Foreach-Schleifencontainer oder einen Sequenzcontainer und dann auf **Breakpoints bearbeiten**.  
  
4.  Wählen Sie im Dialogfeld **Breakpoints festlegen \<Containername>** die zu aktivierenden Breakpoints aus.  
  
5.  Ändern Sie wahlweise den Typ der Trefferanzahl und die Trefferanzahl für jeden Breakpoint.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Tools zur Problembehandlung für die Paketentwicklung](troubleshooting/troubleshooting-tools-for-package-development.md)   
 [Debuggen eines Skripts durch Festlegen von Breakpoints in einem Skripttask und einer Skriptkomponente](data-flow/transformations/script-component.md)   
 [Codieren und Debuggen des Skripttasks](control-flow/script-task.md)   
 [Codieren und Debuggen der Skriptkomponente](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
