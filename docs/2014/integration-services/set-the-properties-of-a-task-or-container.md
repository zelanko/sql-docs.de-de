---
title: Festlegen der Eigenschaften eines Tasks oder Containers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], properties
ms.assetid: 52d47ca4-fb8c-493d-8b2b-48bb269f859b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 05e98e0a735cc54e129b82c65841c6db688953de
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66055669"
---
# <a name="set-the-properties-of-a-task-or-container"></a>Festlegen der Eigenschaften eines Tasks oder Containers
  Sie können die meisten Eigenschaften von Tasks und Containern im Fenster **Eigenschaften** festlegen. Eine Ausnahme sind Eigenschaften von Taskauflistungen und Eigenschaften, die zu komplex sind, als dass sie im Fenster **Eigenschaften** festgelegt werden könnten. Beispielsweise können Sie nicht den Enumerator konfigurieren, der vom Foreach-Schleifencontainer im Fenster **Eigenschaften** verwendet wird. Sie müssen einen Task- oder Container-Editor verwenden, um diese komplexen Eigenschaften festzulegen. Die meisten Task- und Container-Editoren weisen mehrere Knoten auf, und jeder Knoten enthält zugehörige Eigenschaften. Der Name des Knotens weist auf die Art der Eigenschaften hin, die der Knoten enthält.  
  
 Im Folgenden wird beschrieben, wie die Eigenschaften eines Tasks oder Containers entweder mit dem Fenster **Eigenschaften** oder dem entsprechenden Task- oder Container-Editor festgelegt werden.  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-the-properties-window"></a>So legen Sie die Eigenschaften eines Tasks oder Containers mithilfe des Eigenschaftenfensters fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Klicken Sie in der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** mit der rechten Maustaste auf den Task oder Container, und klicken Sie auf **Eigenschaften**.  
  
5.  Aktualisieren Sie im Fenster **Eigenschaften** den Eigenschaftswert.  
  
    > [!NOTE]  
    >  Die meisten Eigenschaften können durch direktes Eingeben der gewünschten Werte in die jeweiligen Textfelder bzw. Auswählen der Werte aus einer Liste festgelegt werden. Einige Eigenschaften sind jedoch komplexer und verfügen über einen Editor für benutzerdefinierte Eigenschaften. Klicken Sie zum Festlegen der Eigenschaft in das Textfeld und anschließend auf die Schaltfläche zum Erstellen **(...)**. Der benutzerdefinierte Editor wird geöffnet.  
  
6.  Erstellen Sie optional Eigenschaftsausdrücke, um die Eigenschaften des Tasks oder Containers dynamisch zu aktualisieren. Weitere Informationen finden Sie unter [Hinzufügen oder Ändern eines Eigenschaftsausdrucks](expressions/add-or-change-a-property-expression.md).  
  
7.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-a-task-or-container-editor"></a>So legen Sie die Eigenschaften eines Tasks oder Containers mithilfe eines Task- oder Container-Editors fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Klicken Sie auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** mit der rechten Maustaste auf den Task oder Container, und klicken Sie auf **Bearbeiten** , um den entsprechenden Task- bzw. Container-Editor zu öffnen.  
  
     Informationen zum Konfigurieren eines For-Schleifencontainers finden Sie unter [Konfigurieren eines For-Schleifencontainers](control-flow/for-loop-container.md).  
  
     Informationen zum Konfigurieren eines Foreach-Schleifencontainers finden Sie unter [Konfigurieren eines Foreach-Schleifencontainers](control-flow/foreach-loop-container.md).  
  
    > [!NOTE]  
    >  Der Sequenzcontainer weist keinen benutzerdefinierten Editor auf.  
  
5.  Falls der Task- oder Container-Editor mehrere Knoten aufweist, klicken Sie auf den Knoten mit der Eigenschaft, die Sie festlegen möchten.  
  
6.  Klicken Sie optional auf **Ausdrücke** , und erstellen Sie auf der Seite **Ausdrücke** Eigenschaftsausdrücke, um die Eigenschaften des Tasks oder Containers dynamisch zu aktualisieren. Weitere Informationen finden Sie unter [Hinzufügen oder Ändern eines Eigenschaftsausdrucks](expressions/add-or-change-a-property-expression.md).  
  
7.  Aktualisieren Sie den Eigenschaftswert.  
  
8.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Tasks](control-flow/integration-services-tasks.md)   
 [SQL Server Integration Services-Container](control-flow/integration-services-containers.md)  
  
  
