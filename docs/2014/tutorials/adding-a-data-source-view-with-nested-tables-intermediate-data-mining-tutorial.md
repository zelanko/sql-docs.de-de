---
title: Hinzufügen einer Datenquellensicht mit geschachtelten Tabellen (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 70db9a9ff6ed8aa5c9a960ae40009369341b99b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068040"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a>Hinzufügen einer Datenquellensicht mit geschachtelten Tabellen (Data Mining-Lernprogramm für Fortgeschrittene)
  Zum Erstellen eines Warenkorbmodells müssen Sie eine Datenquellensicht verwenden, die assoziative Daten unterstützt. Diese Datenquellensicht wird auch für das Sequenzclusterszenario verwendet.  
  
 Diese Datenquellensicht unterscheidet sich von anderen Benutzern, die Sie mit gearbeitet haben können, da er enthält eine *geschachtelte Tabelle*. Ein *geschachtelte Tabelle* ist eine Tabelle, die mehrere Zeilen mit Informationen über eine einzelne Zeile in der Falltabelle enthält. Wenn das Modell beispielsweise das Kaufverhalten von Kunden analysiert, würden Sie als Falltabelle in der Regel eine Tabelle verwenden, die eine eindeutige Zeile für jeden Kunden enthält. Es kann jedoch vorkommen, dass ein Kunde mehrere Käufe tätigt und Sie die Sequenz der Käufe oder Produkte analysieren möchten, die häufig zusammen gekauft werden. Um diese Käufe im Modell logisch darzustellen, fügen Sie der Datenquellensicht, in der die Käufe jedes Kunden aufgeführt werden, eine weitere Tabelle hinzu.  
  
 Diese geschachtelte Tabelle ist über eine n:1-Beziehung mit der Kundentabelle verknüpft. Die geschachtelte Tabelle kann mehrere Zeilen für jeden Kunden enthalten, wobei jede Zeile ein einzelnes Produkt enthält, das gekauft wurde, ggf. mit weiteren Informationen zur Reihenfolge der Einkäufe, zum Verkaufspreis oder zu gewährten Rabatten. Sie können die Informationen in der geschachtelten Tabelle als Eingaben für das Modell oder als vorhersagbares Attribut verwenden.  
  
 In dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Sie fügen eine Datenquellensicht an, die [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] -Datenquelle.  
  
-   Sie fügen dieser Sicht die Falltabelle und die geschachtelte Tabelle hinzu.  
  
-   Sie geben die n:1-Beziehung zwischen der Falltabelle und der geschachtelten Tabelle an.  
  
    > [!NOTE]  
    >  . Es ist wichtig, dass Sie die beschriebene Prozedur genau befolgen, um die Beziehung zwischen der Falltabelle und der geschachtelten Tabelle korrekt zu definieren und Fehler bei der Verarbeitung des Modells zu vermeiden.  
  
-   Sie definieren, wie die Datenspalten im Modell verwendet werden.  
  
 Weitere Informationen zum Arbeiten mit Groß-/Kleinschreibung und geschachtelten Tabellen und einen Schlüssel der geschachtelten Tabelle auswählen, finden Sie unter [geschachtelte Tabellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
### <a name="to-add-a-data-source-view"></a>So fügen Sie eine Datenquellensicht hinzu  
  
1.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Datenquellensichten**, und wählen Sie dann **neue Datenquellensicht**.  
  
     Der Datenquellensicht-Assistent wird geöffnet.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**.  
  
3.  Auf der **Vybrat Zdroj DAT** Seite **relationale Datenquellen**, wählen die [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] -Datenquelle, die Sie in der Basic Data Mining-Tutorial erstellt haben. Klicken Sie auf **Weiter**.  
  
4.  Auf der **Tabellen und Sichten auswählen** Seite, wählen Sie die folgenden Tabellen, und klicken Sie dann auf den Pfeil nach rechts, um diese in die neue Datenquellensicht aufzunehmen:  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **Abschließen des Assistenten** Seite standardmäßig den Namen die Datenquellensicht [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Ändern Sie den Namen in `Orders`, und klicken Sie dann auf **Fertig stellen**.  
  
     Datenquellensicht-Designer wird geöffnet und die `Orders` Datenquellensicht angezeigt wird.  
  
### <a name="to-create-a-relationship-between-tables"></a>So erstellen Sie eine Beziehung zwischen Tabellen  
  
1.  Positionieren Sie die beiden Tabellen im Datenquellensicht-Designer horizontal nebeneinander, sodass sich die Tabelle vAssocSeqLineItems links und die Tabelle vAssocSeqOrders rechts befindet.  
  
2.  Wählen Sie die **OrderNumber** Spalte in der Tabelle "vassocseqlineitems".  
  
3.  Ziehen Sie die Spalte in die Tabelle vAssocSeqOrders, und legen Sie es in der **OrderNumber** Spalte.  
  
    > [!IMPORTANT]  
    >  Achten Sie darauf, ziehen die **OrderNumber** Spalte der geschachtelten Tabelle "vassocseqlineitems", die die n-Seite des Joins darstellt, auf die Groß-/Kleinschreibung vAssocSeqOrders-Tabelle, die die eine Seite des Joins darstellt.  
  
     Ein neues *viele-zu-eins-Beziehung* besteht jetzt zwischen den Tabellen vAssocSeqLineItems und vAssocSeqOrders. Wenn Sie die Tabellen ordnungsgemäß verknüpft haben, sollte die Datenquellensicht wie folgt angezeigt werden:  
  
     ![erwartete n: 1 Join für geschachtelte Tabelle und Falltabelle](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "erwarteten n: 1 Join für geschachtelte Tabelle und Falltabelle")  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen einer Warenkorbstruktur und eines Modells &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Lernprogramm für fortgeschrittene &#40;Analysis Services – Datamining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Miningstrukturen &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Miningmodelle &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
