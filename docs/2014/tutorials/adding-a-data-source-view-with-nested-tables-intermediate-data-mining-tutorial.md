---
title: Hinzufügen einer Datenquellen Sicht mit einer Liste von Tabellen (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 648b9d561ae340b67ed5e2d1aa878969e5a3bc47
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62822777"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a>Hinzufügen einer Datenquellensicht mit geschachtelten Tabellen (Data Mining-Lernprogramm für Fortgeschrittene)
  Zum Erstellen eines Warenkorbmodells müssen Sie eine Datenquellensicht verwenden, die assoziative Daten unterstützt. Diese Datenquellensicht wird auch für das Sequenzclusterszenario verwendet.  
  
 Diese Datenquellen Sicht unterscheidet sich von anderen, mit denen Sie möglicherweise gearbeitet haben, da Sie eine *Tabelle*enthält. Eine Tabellen *Tabelle* ist eine Tabelle, die mehrere Zeilen mit Informationen zu einer einzelnen Zeile in der Fall Tabelle enthält. Wenn das Modell beispielsweise das Kaufverhalten von Kunden analysiert, würden Sie als Falltabelle in der Regel eine Tabelle verwenden, die eine eindeutige Zeile für jeden Kunden enthält. Es kann jedoch vorkommen, dass ein Kunde mehrere Käufe tätigt und Sie die Sequenz der Käufe oder Produkte analysieren möchten, die häufig zusammen gekauft werden. Um diese Käufe im Modell logisch darzustellen, fügen Sie der Datenquellensicht, in der die Käufe jedes Kunden aufgeführt werden, eine weitere Tabelle hinzu.  
  
 Diese geschachtelte Tabelle ist über eine n:1-Beziehung mit der Kundentabelle verknüpft. Die geschachtelte Tabelle kann mehrere Zeilen für jeden Kunden enthalten, wobei jede Zeile ein einzelnes Produkt enthält, das gekauft wurde, ggf. mit weiteren Informationen zur Reihenfolge der Einkäufe, zum Verkaufspreis oder zu gewährten Rabatten. Sie können die Informationen in der geschachtelten Tabelle als Eingaben für das Modell oder als vorhersagbares Attribut verwenden.  
  
 In dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Sie fügen der [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] Datenquelle eine Datenquellen Sicht hinzu.  
  
-   Sie fügen dieser Sicht die Falltabelle und die geschachtelte Tabelle hinzu.  
  
-   Sie geben die n:1-Beziehung zwischen der Falltabelle und der geschachtelten Tabelle an.  
  
    > [!NOTE]  
    >  . Es ist wichtig, dass Sie die beschriebene Prozedur genau befolgen, um die Beziehung zwischen der Falltabelle und der geschachtelten Tabelle korrekt zu definieren und Fehler bei der Verarbeitung des Modells zu vermeiden.  
  
-   Sie definieren, wie die Datenspalten im Modell verwendet werden.  
  
 Weitere Informationen zum Arbeiten mit Case-und netsted-Tabellen und zum Auswählen einer Schlüssel Tabelle für eine Schlüssel Tabelle finden Sie unter [&#40;von Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
### <a name="to-add-a-data-source-view"></a>So fügen Sie eine Datenquellensicht hinzu  
  
1.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **Datenquellen Sichten**, und wählen Sie dann **neue Datenquellen Sicht**aus.  
  
     Der Datenquellensicht-Assistent wird geöffnet.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**.  
  
3.  Wählen Sie auf der Seite **Datenquelle auswählen** unter **relationale Datenquellen**die [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] Datenquelle aus, die Sie im Lernprogramm zu Data Mining-Grundlagen erstellt haben. Klicken Sie auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Tabellen und Sichten auswählen** die folgenden Tabellen aus, und klicken Sie dann auf den Pfeil nach rechts, um Sie in die neue Datenquellen Sicht einzuschließen:  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der Seite **Assistenten abschließen** wird die Datenquellen Sicht standardmäßig benannt [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Ändern Sie den Namen `Orders`in, und klicken Sie dann auf **Fertig**stellen.  
  
     Der Datenquellen Sicht-Designer wird `Orders` geöffnet, und die Datenquellen Sicht wird angezeigt.  
  
### <a name="to-create-a-relationship-between-tables"></a>So erstellen Sie eine Beziehung zwischen Tabellen  
  
1.  Positionieren Sie die beiden Tabellen im Datenquellensicht-Designer horizontal nebeneinander, sodass sich die Tabelle vAssocSeqLineItems links und die Tabelle vAssocSeqOrders rechts befindet.  
  
2.  Wählen Sie die Spalte **OrderNumber** in der Tabelle vassocsetqlineitems aus.  
  
3.  Ziehen Sie die Spalte in die Tabelle vassocsetqorders, und legen Sie Sie in der Spalte **OrderNumber** ab.  
  
    > [!IMPORTANT]  
    >  Stellen Sie sicher, dass Sie die Spalte **OrderNumber** aus der in der Tabelle vassocsetqlineitems dargestellten Tabelle, die die n-Seite des Joins darstellt, in die Fall Tabelle vassocsetqorders ziehen, die die 1-Seite des Joins darstellt.  
  
     Zwischen den ** Tabellen vassoccot qlineitems und vassocssqorders besteht jetzt eine neue m:1-Beziehung. Wenn Sie die Tabellen ordnungsgemäß verknüpft haben, sollte die Datenquellensicht wie folgt angezeigt werden:  
  
     ![Erwarteter m:1-Join für geschachtelte Tabelle und Falltabelle](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "Erwarteter m:1-Join für geschachtelte Tabelle und Falltabelle")  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erstellen einer Market Basket-Struktur und eines Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Lernprogramm für fortgeschrittene &#40;Analysis Services-Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Mining Strukturen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Mining Modelle &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
