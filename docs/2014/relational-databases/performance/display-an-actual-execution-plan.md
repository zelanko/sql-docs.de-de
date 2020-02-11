---
title: Anzeigen eines tatsächlichen Ausführungsplans | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9403e6e2cf1c341780a06bbdff1c5f38685dd34a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63150972"
---
# <a name="display-an-actual-execution-plan"></a>Anzeigen eines tatsächlichen Ausführungsplans
  In diesem Thema wird das Generieren tatsächlicher grafischer Ausführungspläne mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]beschrieben. Beim Generieren tatsächlicher Ausführungspläne werden die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen oder -Batches ausgeführt. Der generierte Ausführungsplan zeigt den tatsächlichen Abfrageausführungsplan an, der von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] zur Ausführung der Abfragen verwendet wird.  
  
 Benutzer müssen zum Verwenden dieser Funktion die entsprechenden Berechtigungen zum Ausführen der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen besitzen, für die ein grafischer Ausführungsplan generiert wird. Darüber hinaus muss ihnen die SHOWPLAN-Berechtigung für alle Datenbanken erteilt werden, auf die die Abfrage verweist.  
  
### <a name="to-include-an-execution-plan-for-a-query-during-execution"></a>So schließen Sie einen Ausführungsplan für eine Abfrage bei der Ausführung ein  
  
1.  Klicken Sie auf der Symbolleiste von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf **Datenbank-Engine-Abfrage**. Sie können auch eine vorhandene Abfrage öffnen und den geschätzten Ausführungsplan anzeigen, indem Sie auf die Symbolleisten-Schaltfläche **Datei öffnen** klicken und die vorhandene Abfrage suchen.  
  
2.  Geben Sie die Abfrage ein, für die Sie den tatsächlichen Ausführungsplan anzeigen möchten.  
  
3.  Klicken Sie im Menü **Abfrage** auf **tatsächlichen Ausführungsplan einschließen** , oder klicken Sie auf die Symbolleisten Schaltfläche **tatsächlichen Ausführungsplan einschließen** .  
  
4.  Führen Sie die Abfrage aus, indem Sie auf die Symbolleistenschaltfläche **Ausführen** klicken. Der vom Abfrageoptimierer verwendete Plan wird im Ergebnisbereich auf der Registerkarte **Ausführungsplan** angezeigt. Positionieren Sie die Maus über die logischen und physischen Operatoren, um deren Beschreibung und Eigenschaften in der QuickInfo anzuzeigen.  
  
     Sie können die Operatoreigenschaften auch im Eigenschaftenfenster anzeigen. Falls die Eigenschaften nicht sichtbar sind, klicken Sie mit der rechten Maustaste auf einen Operator, und wählen Sie **Eigenschaften**aus. Wählen Sie einen Operator aus, um seine Eigenschaften anzuzeigen.  
  
5.  Sie können die Anzeige des Ausführungsplans ändern, indem Sie mit der rechten Maustaste auf den Ausführungsplan klicken und **Vergrößern**, **Verkleinern**, **Vergrößern/Verkleinern**oder **Zoom anpassen**auswählen. Durch **vergrößern** und verkleinern können Sie den Ausführungsplan vergrößern oder verkleinern, während Sie mit dem **benutzerdefinierten Zoom** -Wert einen eigenen Zoomfaktor definieren können, z. b. die Vergrößerung um 80 Prozent. **** **Mit Zoom anpassen** können Sie den Ausführungsplan so vergrößern, dass er dem Ergebnisbereich entspricht.  
  
  
