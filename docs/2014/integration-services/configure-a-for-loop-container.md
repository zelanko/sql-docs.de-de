---
title: Konfigurieren eines for-Schleifen Containers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 24e2fe71b958395a5be35afad32804d2a748348d
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84921981"
---
# <a name="configure-a-for-loop-container"></a>Konfigurieren eines For-Schleifencontainers
  In diesem Verfahren wird beschrieben, wie Sie einen For-Schleifencontainer mithilfe des Dialogfelds **For-Schleifen-Editor** konfigurieren.  
  
### <a name="to-configure-the-for-loop-container"></a>So konfigurieren Sie den For-Schleifencontainer  
  
1.  Doppelklicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf den For-Schleifencontainer, um den **For-Schleifen-Editor**zu öffnen.  
  
2.  Ändern Sie optional den Namen und die Beschreibung des For-Schleifencontainers.  
  
3.  Geben Sie optional einen Initialisierungsausdruck in das Textfeld **InitExpression** ein.  
  
4.  Geben Sie einen Auswertungsausdruck in das Textfeld **EvalExpression** ein.  
  
    > [!NOTE]  
    >  Der Ausdruck muss zu einem booleschen Wert ausgewertet werden. Wenn der Ausdruck zu `false` ausgewertet wird, wird die Ausführung der Schleife beendet.  
  
5.  Geben Sie optional einen Zuweisungsausdruck in das Textfeld **AssignExpression** ein.  
  
6.  Klicken Sie optional auf **Ausdrücke** , und erstellen Sie auf der Seite **Ausdrücke** Eigenschaftsausdrücke für die Eigenschaften des For-Schleifencontainers. Weitere Informationen finden Sie unter [Hinzufügen oder Ändern eines Eigenschaftsausdrucks](expressions/add-or-change-a-property-expression.md).  
  
7.  Klicken Sie auf **OK** , um den **For-Schleifen-Editor**zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [For-Schleifen Container](control-flow/for-loop-container.md)   
 [Integration Services &#40;SSIS-&#41; Ausdrücke](expressions/integration-services-ssis-expressions.md)   
 [Verwenden von Eigenschaftsausdrücken in Paketen](expressions/use-property-expressions-in-packages.md)  
  
  
