---
title: Verwenden Sie einen Ausdruck in einer Rangfolgeneinschränkung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- precedence constraints [Integration Services], adding expressions
- expressions [Integration Services], adding
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0b2491a03e0d0121f3aa3b31f354f71b36088e5d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62766123"
---
# <a name="use-an-expression-in-a-precedence-constraint"></a>Verwenden eines Ausdrucks in einer Rangfolgeneinschränkung
  In diesem Verfahren wird beschrieben, wie Sie einer Rangfolgeneinschränkung mithilfe des Dialogfelds **Rangfolgeneinschränkungs-Editor** einen Ausdruck hinzufügen. Wenn Sie einer Rangfolgeneinschränkung einen Ausdruck hinzufügen möchten, muss das Paket mindestens zwei ausführbare Dateien einschließen (Tasks oder Container), die mit einer Rangfolgeneinschränkung verbunden sein müssen.  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a>So fügen Sie einer Rangfolgeneinschränkung einen Ausdruck hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Doppelklicken Sie auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** auf die Rangfolgeneinschränkung. Das Dialogfeld **Rangfolgeneinschränkungs-Editor** wird geöffnet.  
  
5.  Wählen Sie **Ausdruck**, **Ausdruck und Einschränkung**oder **Ausdruck oder Einschränkung** in der Liste **Auswertungsvorgang** aus.  
  
6.  Geben Sie in das Textfeld **Ausdruck** einen Ausdruck ein, oder starten Sie den Ausdrucks-Generator, um einen Ausdruck zu erstellen.  
  
7.  Klicken Sie auf **Testen**, um die Ausdruckssyntax zu überprüfen.  
  
8.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md)   
 [Verbinden von Tasks und Containern mithilfe einer Standardrangfolgen-Einschränkung](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Legen Sie den Wert einer rangfolgeneinschränkung mithilfe der Kontextmenüs](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Legen Sie die Eigenschaften von Rangfolgeneinschränkungen](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)   
 [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)  
  
  
