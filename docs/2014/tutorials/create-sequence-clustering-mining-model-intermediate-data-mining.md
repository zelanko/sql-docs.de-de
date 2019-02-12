---
title: Erstellen einer Sequence Clustering-Miningmodellstruktur (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b7f4f543952fd86cf6c3c66f9f4b2c51019b1869
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56039352"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a>Erstellen einer Sequence Clustering-Miningmodellstruktur (Mittleres Data Mining Tutorial)
  Der erste Schritt zum Erstellen eines Sequenzcluster-Miningmodells besteht im Erstellen einer neuen Miningstruktur sowie eines neuen Miningmodells auf der Basis des [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus mittels des Data Mining-Assistenten.  
  
 Dazu verwenden Sie die gleiche Datenquellensicht wie für die Market Basket-Analyse, fügen jedoch eine Spalte mit dem `sequence`-Bezeichner hinzu. In diesem Szenario bezeichnet "Sequenz" die Reihenfolge, in der die Elemente vom Kunden im Warenkorb abgelegt werden.  
  
 Darüber hinaus fügen Sie einige Spalten hinzu, die in einem der Modelle zum Gruppieren von Kunden anhand demografischer Daten verwendet werden.  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a>So erstellen Sie eine Sequenzclusterstruktur und ein Sequenzclustermodell  
  
1.  Im Projektmappen-Explorer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], mit der rechten Maustaste **Miningstrukturen** , und wählen Sie **neue Miningstruktur**.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Auf der **Definitionsmethode auswählen** überprüfen Sie, ob Seite **aus vorhandener relationaler Datenbank oder Data Warehouse** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Erstellen von Data Mining-Struktur** Seite, überprüfen Sie, ob die Option **Miningstruktur mit Miningmodell erstellen** ausgewählt ist. Klicken Sie anschließend auf die Dropdownliste für die Option **welche Datamining-Technik möchten Sie verwenden?**, und wählen Sie **Microsoft Sequence Clustering**. Klicken Sie auf **Weiter**.  
  
     Die **Datenquellensicht auswählen** Seite wird angezeigt. Klicken Sie unter **verfügbare Datenquellensichten**Option `Orders`.  
  
     Orders ist die gleiche Datenquellensicht, die Sie auch für das Market Basket-Szenario verwendet haben. Wenn Sie diese Datenquellensicht noch nicht erstellt haben, finden Sie unter [Hinzufügen einer Datenquellensicht mit geschachtelten Tabellen &#40;Data Mining Tutorial für fortgeschrittene&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **Tabellentypen angeben** Seite die **Fall** das Kontrollkästchen neben der **vAssocSeqOrders** Tabelle, und wählen Sie die **geschachtelte** Kontrollkästchen neben der **vAssocSeqLineItems** Tabelle. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn ein Fehler auftritt, bei der Auswahl der **Fall** oder **geschachtelte** Kontrollkästchen kann es sein, dass der Join in der Datenquellensicht nicht korrekt ist. Die geschachtelte Tabelle **vAssocSeqLineItems**, muss eine Verbindung mit der Falltabelle **vAssocSeqOrders** durch einen n: 1 Join. Sie können die Beziehung bearbeiten, indem Sie mit der rechten Maustaste auf die Joinlinie klicken und dann die Richtung des Joins umkehren. Weitere Informationen finden Sie unter [erstellen oder Bearbeiten von Beziehung Dialogfeld &#40;Analysis Services – mehrdimensionale Daten&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).  
  
7.  Auf der **Trainingsdaten** Seite, wählen Sie die Spalten für die Verwendung im Modell durch Auswählen eines Kontrollkästchens wie folgt:  
  
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
  
8.  Auf der **Inhalt und Datentyp der Spalten angeben** Seite stellen Sie sicher, dass das Raster enthält, die Spalten, Inhaltstypen und Datentypen, die in der folgenden Tabelle dargestellt, und klicken Sie dann auf **Weiter**.  
  
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
  
12. Überprüfen Sie die **Drillthrough zulassen** ein, und klicken Sie dann auf **Fertig stellen**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Verarbeiten des Sequenzclustermodells](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Designer](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft Sequence Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  
