---
title: Konfigurieren Sie eine For-Schleifencontainer | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: fe51deb631f0c3d794bdce3f05af61b5e030d5e3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66060832"
---
# <a name="configure-a-for-loop-container"></a>Konfigurieren eines For-Schleifencontainers
  In diesem Verfahren wird beschrieben, wie Sie einen For-Schleifencontainer mithilfe des Dialogfelds **For-Schleifen-Editor** konfigurieren.  
  
 Ein Beispiel für den For-Schleifencontainer finden Sie unter [Nicht fehleranfällige SSIS-Schleifen](https://go.microsoft.com/fwlink/?LinkId=240295) auf bimonkey.com.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [For-Schleifencontainer](control-flow/for-loop-container.md)   
 [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)   
 [Verwenden von Eigenschaftsausdrücken in Paketen](expressions/use-property-expressions-in-packages.md)  
  
  
