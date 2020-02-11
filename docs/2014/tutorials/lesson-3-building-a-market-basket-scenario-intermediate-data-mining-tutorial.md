---
title: 'Lektion 3: aufbauen eines Market Basket-Szenarios (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- association algorithms [Analysis Services]
- nested tables
- tutorials [Data Mining]
ms.assetid: 651eef38-772e-4d97-af51-075b1b27fc5a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c2f1c5a8ae897284f07c3fd6c65d9735099a41fa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63042786"
---
# <a name="lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial"></a>Lektion 3: Erstellen eines Warenkorbszenarios (Data Mining-Lernprogramm für Fortgeschrittene)
  Die Marketingabteilung von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] möchte die Unternehmenswebsite in Hinblick auf Cross-Selling-Möglichkeiten optimieren. Als Teil des Websiteupdates soll die Möglichkeit bestehen, anhand von Produkten, die sich bereits im Onlinewarenkorb eines Kunden befinden, Produkte vorherzusagen, die der Kunde möglicherweise noch kaufen möchte. Die Marketingabteilung möchte außerdem das Kaufverhalten von Kunden besser verstehen, um die Website so zu gestalten, dass Artikel, die tendenziell zusammen gekauft werden, auch zusammen angezeigt werden. Die Marketingabteilung hat erfahren, dass Data Mining besonders nützlich für diese Art von *Warenkorbanalyse* ist, und bittet Sie, ein Data Mining-Modell zu entwickeln.  
  
 Nach Abschluss der Aufgaben in dieser Lektion verfügen Sie über ein Miningmodell, das Gruppen von Artikeln aus vergangenen Kundentransaktionen anzeigt. Außerdem können Sie das Miningmodell verwenden, um weitere Artikel vorherzusagen, die ein Kunde möglicherweise kaufen möchte.  
  
 Zum Ausführen der Aufgaben in dieser Lektion verwenden Sie die Projekt Mappe und die Datenquelle, die Sie in der ersten Lektion des Data Mining-Lernprogramms für fortgeschrittene erstellt haben, [&#40;Analysis Services Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md). Sie ändern diese Lösung, indem Sie eine Datenquellensicht hinzufügen, die Tabellen über den Kunden enthält, einschließlich einer geschachtelten Tabelle von Kundenbestellungen.  Anschließend erstellen Sie ein Miningmodell, dass den Microsoft Association Rules-Algorithmus verwendet, der für Warenkorbszenarien geeignet ist.  
  
 Diese Lektion enthält die folgenden Themen:  
  
-   [Hinzufügen einer Datenquellen Sicht mit einer Reihe von Tabellen &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
-   [Erstellen einer Market Basket-Struktur und eines Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Ändern und Verarbeiten des Market Basket-Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
-   [Erkunden des Market Basket-Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
-   [Filtern einer geclusterte Tabelle in einem Mining Modell &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
-   [Vorhersagen von Zuordnungen &#40;Data&#41;Mining-Lernprogramms](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Hinzufügen einer Datenquellen Sicht mit einer Reihe von Tabellen &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>Alle Lektionen  
 [Lektion 1: Erstellen der Data Mining-Lösung für fortgeschrittene &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Lektion 2: Erstellung eines Vorhersage Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 Lektion 3: Warenkorbszenario (Data Mining-Tutorial für Fortgeschrittene)  
  
 [Lektion 4: Entwickeln eines Sequence Clustering-Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Lektion 5: aufbauen von neuronalen Netzwerk-und logistischen Regressionsmodellen &#40;Data&#41;Mining-Lernprogramms](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Lektion 2: Erstellung eines Vorhersage Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)   
 [Lektion 4: Entwickeln eines Sequence Clustering-Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
  
