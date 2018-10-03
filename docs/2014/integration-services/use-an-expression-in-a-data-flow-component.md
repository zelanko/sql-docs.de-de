---
title: Verwenden eines Ausdrucks in einer Datenflusskomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], data flow
- expressions [Integration Services], data flow components
ms.assetid: 9181b998-d24a-41fb-bb3c-14eee34f910d
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8a6510294daf15eac25c335ee84a73f136a57f5e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083461"
---
# <a name="use-an-expression-in-a-data-flow-component"></a>Verwenden eines Ausdrucks in einer Datenflusskomponente
  In diesem Verfahren wird beschrieben, wie ein Ausdruck der Transformation für bedingtes Teilen oder der Transformation für abgeleitete Spalten hinzugefügt wird. Die Transformation für bedingtes Teilen verwendet Ausdrücke zum Definieren der Bedingungen, die Datenzeilen in eine Transformationsausgabe leiten, und die Transformation für abgeleitete Spalten verwendet Ausdrücke zum Definieren von Werten, die Spalten zugewiesen sind.  
  
 Um einen Ausdruck in einer Transformation zu implementieren, muss das Paket bereits mindestens einen Datenflusstask und eine Quelle einschließen. Weitere Informationen zum Hinzufügen von Elementen zu Paketen finden Sie in den folgenden Themen:  
  
-   [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
    
  
-   [Hinzufügen oder Löschen einer Komponente im Datenfluss](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
-   [Verbinden von Komponenten in einem Datenfluss](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-create-an-expression"></a>So erstellen Sie einen Ausdruck  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer auf die Registerkarte **Ablaufsteuerung** , und klicken Sie dann auf den Datenflusstask mit dem Datenfluss, den Sie in einem Ausdruck implementieren möchten.  
  
4.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus der **Toolbox** die Transformation für bedingtes Teilen oder die Transformation für abgeleitete Spalten auf die Entwurfsoberfläche.  
  
5.  Ziehen Sie den grünen Konnektor von der Quelle oder einer Transformation auf die Transformation für bedingtes Teilen oder abgeleitete Spalten.  
  
6.  Doppelklicken Sie auf die Transformation, um ihr Dialogfeld zu öffnen.  
  
7.  Erweitern Sie im linken Fenster die Option **Variablen** , um system- und benutzerdefinierte Variablen anzuzeigen, und erweitern Sie **Spalten** , um die Transformationseingabespalten anzuzeigen.  
  
8.  Erweitern Sie im rechten Fenster die Option **Mathematische Funktionen**, **Zeichenfolgenfunktionen**, **Datums-/Uhrzeitfunktionen**, **NULL-Funktionen**, **Typumwandlungen**und **Operatoren** , um auf die Funktionen, die Umwandlungen und die Operatoren zuzugreifen, die von der Ausdrucksgrammatik bereitgestellt werden.  
  
9. Gehen Sie je nach Transformation zum Erstellen eines Ausdrucks wie folgt vor  
  
    -   Ziehen Sie im Dialogfeld **Transformations-Editor für bedingtes Teilen** die Variablen, Spalten, Funktionen, Operatoren und Umwandlungen in die Spalte **Bedingung** . Sie können den Ausdruck aber auch direkt in die Spalte **Bedingung** eingeben.  
  
    -   Ziehen Sie im Dialogfeld **Transformations-Editor für abgeleitete Spalten** die Variablen, Spalten, Funktionen, Operatoren und Umwandlungen in die Spalte **Ausdruck** . Sie können den Ausdruck aber auch direkt in die Spalte **Ausdruck** eingeben.  
  
        > [!NOTE]  
        >  Wenn Sie den Fokus von der Spalte **Bedingung** oder **Ausdruck** entfernen, kann der Ausdruckstext hervorgehoben dargestellt werden, was auf eine falsche Ausdruckssyntax hinweist.  
  
10. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
    > [!NOTE]  
    >  Wenn der Ausdruck ungültig ist, wird eine Warnung angezeigt, die die Syntaxfehler im Ausdruck beschreibt.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)   
 [Transformation für bedingtes Teilen](data-flow/transformations/conditional-split-transformation.md)   
 [Transformation für abgeleitete Spalten](data-flow/transformations/derived-column-transformation.md)   
 [Datenflusstask](control-flow/data-flow-task.md)   
 [Datenfluss](data-flow/data-flow.md)  
  
  
