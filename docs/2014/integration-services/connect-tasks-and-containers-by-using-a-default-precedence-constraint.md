---
title: Verbinden von Tasks und Containern mithilfe einer Standard Rang folgen Einschränkung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- default precedence constraints
- containers [Integration Services], precedence constraints
ms.assetid: 8f31f15f-98ff-4c35-b41f-8b8cfd148d75
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4e5c0ad2405c0d62b703dcb7fa668837e7e47386
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060433"
---
# <a name="connect-tasks-and-containers-by-using-a-default-precedence-constraint"></a>Verbinden von Tasks und Containern mithilfe einer Standardrangfolgeneinschränkung
  Mit Rangfolgeneinschränkungen werden zwei ausführbare Dateien miteinander verbunden. Bei einer ausführbaren Datei kann es sich um einen Task oder einen For-Schleifencontainer, einen Foreach-Schleifencontainer oder einen Sequenzcontainer handeln. In diesem Verfahren wird beschrieben, wie Sie das Standardverhalten für Rangfolgeneinschränkungen festlegen, und wie Sie ausführbare Dateien mithilfe der Standardrangfolgeneinschränkungen verbinden.  
  
## <a name="creating-default-precedence-constraints"></a>Erstellen von Standardrangfolgeneinschränkungen  
 Wenn Sie den [!INCLUDE[ssIS](../includes/ssis-md.md)]-Designer zum ersten Mal verwenden, lautet der Standardwert einer Rangfolgeneinschränkung `Success`. Führen Sie die folgenden Schritte aus, um für den [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer einen anderen Standardwert für Rangfolgeneinschränkungen zu konfigurieren.  
  
#### <a name="to-set-the-default-value-for-precedence-constraints"></a>So legen Sie den Standardwert für Rangfolgeneinschränkungen fest  
  
1.  Öffnen Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
3.  Erweitern Sie im Dialogfeld **Optionen** den Ordner **Business Intelligence-Designer** , und erweitern Sie dann **Integration Services-Designer**.  
  
4.  Klicken Sie auf **Automatische Ablaufsteuerungsverbindung** , und aktivieren Sie das Kontrollkästchen **Neue Form standardmäßig mit der ausgewählten Form verbinden**.  
  
5.  Wählen Sie in der Dropdownliste **Failure-Einschränkung für die neue Form verwenden** oder **Completion-Einschränkung für die neue Form verwenden**aus.  
  
6.  Klicken Sie auf **OK**.  
  
#### <a name="to-create-a-default-precedence-constraint"></a>So erstellen Sie eine Standardrangfolgeneinschränkung  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Klicken Sie in der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** auf den Task oder Container, und ziehen Sie dessen Konnektor auf die ausführbare Datei, auf die Sie die Rangfolgeneinschränkung anwenden möchten.  
  
5.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rang folgen Einschränkungen](control-flow/precedence-constraints.md)   
 [Festlegen des Werts einer Rang folgen Einschränkung mithilfe des Kontextmenüs](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Festlegen der Eigenschaften einer Rang folgen Einschränkung](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)   
 [Verwenden eines Ausdrucks in einer Rangfolgeneinschränkung](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
