---
title: Verbinden Sie Tasks und Containern mithilfe einer Standardrangfolgeneinschränkung | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- default precedence constraints
- containers [Integration Services], precedence constraints
ms.assetid: 8f31f15f-98ff-4c35-b41f-8b8cfd148d75
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cf278d02e1c2eb523964ee07b039b46942c7e9de
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048094"
---
# <a name="connect-tasks-and-containers-by-using-a-default-precedence-constraint"></a>Verbinden von Tasks und Containern mithilfe einer Standardrangfolgeneinschränkung
  Mit Rangfolgeneinschränkungen werden zwei ausführbare Dateien miteinander verbunden. Bei einer ausführbaren Datei kann es sich um einen Task oder einen For-Schleifencontainer, einen Foreach-Schleifencontainer oder einen Sequenzcontainer handeln. In diesem Verfahren wird beschrieben, wie Sie das Standardverhalten für Rangfolgeneinschränkungen festlegen, und wie Sie ausführbare Dateien mithilfe der Standardrangfolgeneinschränkungen verbinden.  
  
## <a name="creating-default-precedence-constraints"></a>Erstellen von Standardrangfolgeneinschränkungen  
 Bei der ersten Verwendung [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer, der Standardwert einer rangfolgeneinschränkung ist `Success`. Führen Sie die folgenden Schritte aus, um für den [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer einen anderen Standardwert für Rangfolgeneinschränkungen zu konfigurieren.  
  
#### <a name="to-set-the-default-value-for-precedence-constraints"></a>So legen Sie den Standardwert für Rangfolgeneinschränkungen fest  
  
1.  Öffnen Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
3.  Erweitern Sie im Dialogfeld **Optionen** den Ordner **Business Intelligence-Designer** , und erweitern Sie dann **Integration Services-Designer**.  
  
4.  Klicken Sie auf **Automatische Ablaufsteuerungsverbindung** , und aktivieren Sie das Kontrollkästchen **Neue Form standardmäßig mit der ausgewählten Form verbinden**.  
  
5.  Wählen Sie in der Dropdownliste **Failure-Einschränkung für die neue Form verwenden** oder **Completion-Einschränkung für die neue Form verwenden**aus.  
  
6.  Klicken Sie auf **OK**.  
  
#### <a name="to-create-a-default-precedence-constraint"></a>So erstellen Sie eine Standardrangfolgeneinschränkung  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Klicken Sie in der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** auf den Task oder Container, und ziehen Sie dessen Konnektor auf die ausführbare Datei, auf die Sie die Rangfolgeneinschränkung anwenden möchten.  
  
5.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md)   
 [Legen Sie den Wert einer rangfolgeneinschränkung mithilfe der Kontextmenüs](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Legen Sie die Eigenschaften von Rangfolgeneinschränkungen](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)   
 [Verwenden eines Ausdrucks in einer Rangfolgeneinschränkung](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  