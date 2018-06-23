---
title: Erstellen einer Warenkorbstruktur und eines Modells (mittleres Datamining-Lernprogramm) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
caps.latest.revision: 48
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 957a55114e5a4fb756c63b63779eed3fbfb5f95b
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312598"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a>Erstellen einer Warenkorbstruktur und eines Warenkorbmodells (Data Mining-Lernprogramm für Fortgeschrittene)
  Sie haben nun eine Datenquellensicht erstellt und erstellen mithilfe des Data Mining-Assistenten eine neue Miningstruktur. In dieser Aufgabe legen Sie eine Miningstruktur und ein Miningmodell an, die auf dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus basieren.  
  
> [!NOTE]  
>  Wenn Sie eine Fehlermeldung erhalten, nach der "vAssocSeqLineItems" nicht in einer geschachtelten Tabelle verwendet werden kann, kehren Sie zur vorherigen Aufgabe in dieser Lektion zurück, und erstellen Sie den n:1-Join, indem Sie ihn aus der Tabelle "vAssocSeqLineItems" (die n-Seite) in die Tabelle "vAssocSeqOrders" (die 1-Seite) ziehen. Sie können die Beziehung zwischen den Tabellen auch bearbeiten, indem Sie mit der rechten Maustaste auf die Joinlinie klicken.  
  
### <a name="to-create-an-association-mining-structure"></a>So legen Sie die Miningstruktur Association an  
  
1.  Im Projektmappen-Explorer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], mit der rechten Maustaste **Miningstrukturen** , und wählen Sie **neue Miningstruktur** zu Data Mining-Assistenten zu öffnen.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Auf der **Definitionsmethode auswählen** Seite, überprüfen Sie, ob **aus vorhandener relationaler Datenbank oder vorhandenem Data Warehouse** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Data Mining-Struktur erstellen** Seite **welche Datamining-Technik möchten Sie verwenden?** Option **Microsoft Association Rules** aus der Liste aus, und klicken Sie dann auf **Weiter**. Die **Datenquellensicht auswählen** Seite wird angezeigt.  
  
5.  Wählen Sie **Aufträge**unter **verfügbare Datenquellensichten**, und klicken Sie dann auf **Weiter**.  
  
6.  Auf der **Tabellentypen angeben** wählen Sie die Seite in der Zeile für die Tabelle "vassocseqlineitems" die **geschachtelte** Kontrollkästchen, und wählen Sie in der Zeile für die geschachtelte Tabelle vAssocSeqOrders der **Fall** Kontrollkästchen. Klicken Sie auf **Weiter**.  
  
7.  Auf der **Trainingsdaten angeben** Seite, deaktivieren Sie alle Kontrollkästchen, die möglicherweise aktiviert sind. Legen Sie den Schlüssel für die Falltabelle vAssocSeqOrders durch Aktivieren der **Schlüssel** das Kontrollkästchen neben OrderNumber fest.  
  
     Da die Warenkorbanalyse zum Bestimmen dient, welche Produkte in einer einzelnen Transaktion eingefügt werden, müssen Sie nicht verwenden, die **CustomerKey** Feld.  
  
8.  Legen Sie den Schlüssel für die geschachtelte Tabelle vAssocSeqLineItems durch Aktivieren der **Schlüssel** das Kontrollkästchen neben dem Modell. Die **Eingabe** Kontrollkästchen wird auch automatisch ausgewählt, wenn Sie dies tun. Wählen Sie die **vorhersagbar** für das Kontrollkästchen `Model` ebenfalls.  
  
     In einem Market Basket-Modell können Sie nicht von Bedeutung ist die Reihenfolge der Produkte im Einkaufswagen und aus diesem Grund sollten Sie nicht einschließen **LineNumber** als Schlüssel für die geschachtelte Tabelle. Verwenden Sie **LineNumber** als Schlüssel nur in einem Modell, in dem die Sequenz wichtig ist. In Lektion 4 erstellen Sie ein Modell, das den [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus verwendet.  
  
9. Aktivieren Sie das Kontrollkästchen links neben IncomeGroup und Region, aber nehmen Sie keine anderen Angaben. Durch Aktivieren der äußerst linken Spalte fügen Sie der Struktur die Spalten zur späteren Bezugnahme hinzu. Die Spalten werden jedoch nicht im Modell verwendet. Ihre Auswahl sollte wie folgt aussehen:  
  
     ![wie im Dialogfeld aussehen soll](../../2014/tutorials/media/tutorial-configassocmodel.gif "aussehen (Dialogfeld)")  
  
10. Klicken Sie auf **Weiter**.  
  
11. Auf der **Inhalt und Datentyp der Spalten angeben**überprüfen Sie die Auswahl sollte wie in der folgenden Tabelle dargestellt werden, und klicken Sie dann auf **Weiter**.  
  
    |Spalte|Inhaltstyp|Datentyp|  
    |-------------|------------------|---------------|  
    |IncomeGroup|Discrete|Textmodus|  
    |Order Number|Key|Textmodus|  
    |Region|Discrete|Textmodus|  
    |vAssocSeqLineItems|||  
    |Model|Key|Textmodus|  
  
12. Auf der **legen erstellen Tests** Seite, den Standardwert für die Option **Prozentsatz der Testdaten** liegt bei 30 Prozent. Ändern Sie diese Option, um **0**. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt andere Diagramme zum Messen der Modellgenauigkeit bereit. Einige Genauigkeitsdiagrammtypen, z. B. das Prognosegütediagramm und der Kreuzvalidierungsbericht, dienen jedoch der Klassifizierung und Schätzung. Eine Unterstützung für assoziative Vorhersagen ist nicht vorgesehen.  
  
13. Auf der **Abschließen des Assistenten** Seite **Miningstrukturname**, Typ `Association`.  
  
14. In **Miningmodellname**, Typ `Association`.  
  
15. Wählen Sie die Option **Drillthrough zulassen**, und klicken Sie dann auf **Fertig stellen**.  
  
     Data Mining-Designer wird geöffnet und zeigt die `Association` Miningstruktur, die Sie gerade erstellt haben.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Ändern und Verarbeiten des Market Basket-Modells &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Association-Algorithmus](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)   
 [Inhaltstypen &#40;Datamining&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  