---
title: Erstellen einer Sequence Clustering-Miningmodellstruktur (mittleres Datamining-Lernprogramm) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 09aaac50873d6c4c63b46fdf37dd7ee854000886
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312698"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a>Erstellen einer Sequence Clustering-Miningmodellstruktur (Mittleres Data Mining Tutorial)
  Der erste Schritt zum Erstellen eines Sequenzcluster-Miningmodells besteht im Erstellen einer neuen Miningstruktur sowie eines neuen Miningmodells auf der Basis des [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus mittels des Data Mining-Assistenten.  
  
 Dazu verwenden Sie die gleiche Datenquellensicht wie für die Market Basket-Analyse, fügen jedoch eine Spalte mit dem `sequence`-Bezeichner hinzu. In diesem Szenario bezeichnet "Sequenz" die Reihenfolge, in der die Elemente vom Kunden im Warenkorb abgelegt werden.  
  
 Darüber hinaus fügen Sie einige Spalten hinzu, die in einem der Modelle zum Gruppieren von Kunden anhand demografischer Daten verwendet werden.  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a>So erstellen Sie eine Sequenzclusterstruktur und ein Sequenzclustermodell  
  
1.  Im Projektmappen-Explorer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], mit der rechten Maustaste **Miningstrukturen** , und wählen Sie **neue Miningstruktur**.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Auf der **Definitionsmethode auswählen** Seite, überprüfen Sie, ob **aus vorhandener relationaler Datenbank oder vorhandenem Data Warehouse** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Data Mining-Struktur erstellen** Seite, überprüfen Sie, ob die Option **Miningstruktur ein Miningmodell erstellen** ausgewählt ist. Klicken Sie als Nächstes auf die Dropdownliste für die Option **welche Datamining-Technik möchten Sie verwenden?**, und wählen Sie **Microsoft Sequence Clustering**. Klicken Sie auf **Weiter**.  
  
     Die **Datenquellensicht auswählen** Seite wird angezeigt. Klicken Sie unter **verfügbare Datenquellensichten**Option `Orders`.  
  
     Orders ist die gleiche Datenquellensicht, die Sie auch für das Market Basket-Szenario verwendet haben. Wenn Sie nicht diese Datenquellensicht erstellt haben, finden Sie unter [Hinzufügen einer Datenquellensicht mit geschachtelten Tabellen &#40;Mining-Lernprogramm für fortgeschrittene Data&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **Tabellentypen angeben** Seite der **Fall** das Kontrollkästchen neben der **vAssocSeqOrders** Tabelle, und wählen Sie die **geschachtelte** Kontrollkästchen neben den **"vassocseqlineitems"** Tabelle. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn ein Fehler auftritt, bei der Auswahl der **Fall** oder **geschachtelte** Kontrollkästchen, kann es sein, dass der Join in der Datenquellensicht nicht korrekt ist. Die geschachtelte Tabelle **"vassocseqlineitems"**, muss eine Verbindung mit der Falltabelle **vAssocSeqOrders** durch einen Join viele-zu-eins. Sie können die Beziehung bearbeiten, indem Sie mit der rechten Maustaste auf die Joinlinie klicken und dann die Richtung des Joins umkehren. Weitere Informationen finden Sie unter [erstellen oder Bearbeiten von Beziehung Dialogfeld &#40;Analysis Services – mehrdimensionale Daten&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).  
  
7.  Auf der **Trainingsdaten angeben** Seite, wählen Sie die Spalten für die Verwendung im Modell durch ein Kontrollkästchen wie folgt auswählen:  
  
    -   **IncomeGroup** wählen Sie die **Eingabe** Kontrollkästchen.  
  
         Diese Spalte enthält interessante Informationen über die Kunden, die Sie für das Clustering verwenden können. Eine Verwendung findet nur im ersten Modell, nicht jedoch im zweiten Modell statt.  
  
    -   **OrderNumber** wählen Sie die `Key` Kontrollkästchen.  
  
         Dieses Feld wird als Bezeichner oder `Key` für die Falltabelle verwendet. Das Schlüsselfeld der Falltabelle sollte nicht als Eingabe verwendet werden, da der Schlüssel eindeutige Werte enthält, die nicht nützlich für das Clustering sind.  
  
    -   **Region** wählen Sie die **Eingabe** Kontrollkästchen.  
  
         Diese Spalte enthält interessante Informationen über die Kunden, die Sie für das Clustering verwenden können. Eine Verwendung findet nur im ersten Modell, nicht jedoch im zweiten Modell statt.  
  
    -   **LineNumber** wählen Sie die `Key` und **Eingabe** Kontrollkästchen.  
  
         Die **LineNumber** Feld wird als Bezeichner verwendet werden, für die geschachtelte Tabelle oder `Sequence Key`. Der Schlüssel für eine geschachtelte Tabelle muss immer für die Eingabe verwendet werden.  
  
    -   **Modell** wählen Sie die **Eingabe** und **vorhersagbar** Kontrollkästchen.  
  
     Stellen Sie sicher, dass die Auswahl richtig sind, und klicken Sie dann auf **Weiter**.  
  
8.  Auf der **Inhalt und Datentyp der Spalten angeben** Seite stellen Sie sicher, dass das Raster enthält, Spalten, Inhaltstypen und Datentypen, die in der folgenden Tabelle dargestellt, und klicken Sie dann auf **Weiter**.  
  
    |Tabellen/Spalten|Inhaltstyp|Datentyp|  
    |---------------------|------------------|---------------|  
    |IncomeGroup|Discrete|Textmodus|  
    |OrderNumber|Key|Textmodus|  
    |Region|Discrete|Textmodus|  
    |vAssocSeqLineItems|||  
    |Zeilennummer|Key Sequence|Long|  
    |Model|Discrete|Textmodus|  
  
9. Auf der **Testsatz erstellen** Seite, ändern Sie die **Prozentsatz der Testdaten** in 20, und klicken Sie dann auf **Weiter**.  
  
10. Auf der **Abschließen des Assistenten** Seite für die **Miningstrukturname**, Typ `Sequence Clustering with Region`.  
  
11. Für die **Miningmodellname**, Typ `Sequence Clustering with Region`.  
  
12. Überprüfen Sie die **Drillthrough zulassen** Feld, und klicken Sie dann auf **Fertig stellen**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Verarbeiten des Sequenzclustermodells](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Designer](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft Sequence Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  