---
title: Market Basket DMX-Lernprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- market basket analysis [Analysis Services]
- tutorials [Data Mining]
- tutorials [DMX]
ms.assetid: 6e262a1d-c89e-4033-8368-46cf25168ef5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0f29aff4341126665e184e12219aca014222cd82
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360792"
---
# <a name="market-basket-dmx-tutorial"></a>Market Basket DMX-Lernprogramm
  In diesem Lernprogramm erfahren Sie, wie Miningmodelle mithilfe der Abfragesprache Data Mining-Erweiterungen (Data Mining Extensions, DMX) erstellt, trainiert und analysiert werden. Anschließend verwenden Sie diese Miningmodelle zum Erstellen von Vorhersagen, die beschreiben, welche Produkte tendenziell als Kombinationskäufe erworben werden.  
  
 Die Miningmodelle werden aus Daten erstellt, die in der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]-Beispieldatenbank enthalten sind. In dieser Datenbank werden Daten für das fiktive Unternehmen [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] gespeichert. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ist ein großes, multinationales Produktionsunternehmen. Das Unternehmen fertigt und verkauft Fahrräder aus Metall und Verbundwerkstoffen auf dem nordamerikanischen, europäischen und asiatischen Markt. Der Hauptsitz befindet sich mit 290 Mitarbeitern in Bothell, Washington. Darüber hinaus sind mehrere regionale Vertriebsteams über die internationalen Zielmärkte des Unternehmens verteilt.  
  
## <a name="tutorial-scenario"></a>Lernprogrammszenario  
 Das Unternehmen [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] hat entschieden, eine benutzerdefinierte Anwendung zu erstellen, die mithilfe von Data Mining-Funktionen vorhersagt, welche Produkte die Kunden tendenziell als Kombinationskauf erwerben. Das Ziel für die benutzerdefinierte Anwendung besteht darin, eine Reihe von Produkten anzugeben und vorherzusagen, welche zusätzlichen Produkte mit den angegebenen Produkten gekauft werden. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] verwendet diese Informationen für eine Vorschlagsfunktion auf der entsprechenden Website sowie zur verbesserten Darstellung von Informationen für den Kunden.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet mehrere Tools, die zum Ausführen dieser Aufgabe verwendet werden können:  
  
-   Die DMX-Abfragesprache  
  
-   Die [Microsoft Association-Algorithmus](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)  
  
-   Abfrage-Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]  
  
 Data Mining-Erweiterungen (DMX) ist eine von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bereitgestellte Abfragesprache, mit der Sie Miningmodelle erstellen und die Sie zum Arbeiten mit Mining-Modellen verwenden können. Die [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus erstellt Modelle, die die Produkte vorhergesagt werden können, die wahrscheinlich zusammen gekauft werden.  
  
 Ziel dieses Lernprogramms ist es, die DMX-Abfragen bereitzustellen, die in der angepassten Anwendung verwendet werden.  
  
 **Weitere Informationen:** [Data Mining-Projektmappen](../../2014/analysis-services/data-mining/data-mining-solutions.md)  
  
## <a name="mining-structure-and-mining-models"></a>Miningstruktur und Miningmodelle  
 Bevor Sie mit dem Erstellen von DMX-Anweisungen beginnen, sollten Sie sich mit dem wichtigsten Objekten vertraut machen, die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zum Erstellen von Miningmodellen verwendet werden. Die *Miningstruktur* ist eine Datenstruktur, die die Datendomäne definiert, aus der die Miningmodelle erstellt werden. Eine einzelne Miningstruktur kann mehrere enthalten *Miningmodelle* , die die gleiche Domäne gemeinsam nutzen. Ein Miningmodell wendet einen Miningmodellalgorithmus für die Daten an, welcher durch eine Miningstruktur dargestellt wird.  
  
 Die Grundbausteine der Miningstruktur sind die Miningstrukturspalten, die die in der Datenquelle enthaltenen Daten beschreiben. Diese Spalten enthalten Informationen, z. B. über den Datentyp, den Inhaltstyp und die Verteilung der Daten.  
  
 Miningmodelle müssen die in der Miningstruktur beschriebene Schlüsselspalte sowie eine Teilmenge der übrigen Spalten enthalten. Das Miningmodell definiert die Verwendung jeder einzelnen Spalte und den zum Erstellen des Miningmodells verwendeten Algorithmus. Beispiel: Sie können in DMX angeben, dass eine Spalte eine Schlüsselspalte oder ein PREDICT-Spalte ist. Eine Spalte, für die kein Typ angegeben ist, wird als Eingabespalte behandelt.  
  
 Es gibt in DMX zwei Möglichkeiten, Miningmodelle zu erstellen. Sie können die Miningstruktur und das zugehörige Miningmodell entweder zusammen mithilfe der `CREATE MINING MODEL`-Anweisung erstellen, oder Sie können zuerst mithilfe der `CREATE MINING STRUCTURE`-Anweisung eine Miningstruktur erstellen und dann der Miningstruktur mithilfe der `ALTER STRUCTURE`-Anweisung ein Miningmodell hinzufügen. Diese Methoden werden weiter unten beschrieben.  
  
 `CREATE MINING MODEL`  
 Verwenden Sie diese Anweisung, um eine Miningstruktur und ihr zugehöriges Miningmodell (unter Verwendung desselben Namens) zusammen zu erstellen. An den Namen des Miningmodells wird "Structure" angefügt, um es von der Miningstruktur zu unterscheiden.  
  
 Diese Anweisung ist hilfreich, wenn Sie eine Miningstruktur erstellen, die ein einzelnes Miningmodell enthält.  
  
 Weitere Informationen finden Sie unter [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).  
  
 CREATE MINING STRUCTURE  
 Verwenden Sie diese Anweisung, um eine neue Miningstruktur ohne Modelle zu erstellen.  
  
 Wenn Sie CREATE MINING STRUCTURE verwenden, können Sie zudem ein zurückgehaltenes Dataset erstellen. Dieses kann zum Testen aller Modelle verwendet werden, die auf der gleichen Miningstruktur basieren.  
  
 Weitere Informationen finden Sie unter [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).  
  
 `ALTER MINING STRUCTURE`  
 Verwenden Sie diese Anweisung, um einer Miningstruktur ein Miningmodell hinzuzufügen, das bereits auf dem Server vorhanden ist.  
  
 Es kann mehrere Gründe geben, warum Sie einer einzelnen Miningstruktur mehr als nur ein Miningmodell hinzufügen sollten. Ein Grund könnte beispielsweise sein, dass Sie mehrere Miningmodelle mit unterschiedlichen Algorithmen erstellen möchten, um herauszufinden, mit welchem Modell die besten Ergebnisse erzielt werden. Alternativ können Sie mehrere Miningmodelle mit demselben Algorithmus, jedoch mit einer anderen Einstellung für einen Parameter in jedem Miningmodell erstellen, um die beste Einstellung für diesen Parameter zu ermitteln.  
  
 Weitere Informationen finden Sie unter [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016).  
  
 Da Sie eine Miningstruktur erstellen, die mehrere Miningmodelle beinhaltet, verwenden Sie in diesem Lernprogramm die zweite Methode.  
  
 **Weitere Informationen**  
  
 [Datamining-Erweiterungen &#40;DMX&#41; Verweis](/sql/dmx/data-mining-extensions-dmx-reference), [verstehen die DMX Select-Anweisung](/sql/dmx/understanding-the-dmx-select-statement), [Struktur und Verwendung von DMX-Vorhersageabfragen](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)  
  
## <a name="what-you-will-learn"></a>Lernziele  
 Dieses Lernprogramm ist in die folgenden Lektionen aufgeteilt:  
  
 [Lektion 1: Erstellen der Market Basket-Miningstruktur](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)  
 In dieser Lektion erfahren Sie, wie mithilfe der `CREATE`-Anweisung Miningstrukturen erstellt werden.  
  
 [Lektion 2: Hinzufügen von Miningmodellen zur Market Basket-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
 In dieser Lektion erfahren Sie, wie einer Miningstruktur mithilfe der `ALTER`-Anweisung Miningmodelle hinzugefügt werden.  
  
 [Lektion 3: Verarbeiten der Market Basket-Miningstruktur](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
 In dieser Lektion erfahren Sie, wie mithilfe der `INSERT INTO`-Anweisung Miningstrukturen und ihre zugehörigen Miningmodelle verarbeitet werden.  
  
 [Lektion 4: Ausführen von Warenkorbvorhersagen](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
 In dieser Lektion erfahren Sie, wie mithilfe der `PREDICTION JOIN`-Anweisung Vorhersagen für Miningmodelle erstellt werden.  
  
## <a name="requirements"></a>Anforderungen  
 Stellen Sie vor dem Durchführen des Lernprogramms sicher, dass Folgendes installiert ist:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   Die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank.  
  
 Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert. So installieren Sie die offiziellen Beispieldatenbanken für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], wechseln Sie zu [ http://www.CodePlex.com/MSFTDBProdSamples ](https://go.microsoft.com/fwlink/?LinkId=88417) oder auf der Microsoft SQL Server Samples and Community Projects-Startseite im Abschnitt Microsoft SQL Server Product Samples. Klicken Sie auf **Datenbanken**und anschließend auf die Registerkarte **Releases** , und wählen Sie die gewünschten Datenbanken aus.  
  
> [!NOTE]  
>  Zur besseren Anzeige der Lernprogramme empfehlen wir Ihnen, dass Sie der Symbolleiste in der Dokumentanzeige die Schaltflächen **Nächstes Thema** und **Vorheriges Thema** hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md)   
 [Lernprogramm zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
