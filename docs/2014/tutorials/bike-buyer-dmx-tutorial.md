---
title: Bike Buyer DMX Tutorial | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/19/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 4b634cc1-86dc-42ec-9804-a19292fe8448
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3cf9a0c9e6059330c0b8edbd8228f617ba093564
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140556"
---
# <a name="bike-buyer-dmx-tutorial"></a>Bike Buyer-Lernprogramm zur DMX-Abfragesprache
  In diesem Lernprogramm erfahren Sie, wie Miningmodelle mithilfe der Abfragesprache Data Mining-Erweiterungen (Data Mining Extensions, DMX) erstellt, trainiert und analysiert werden. Anschließend verwenden Sie diese Miningmodelle zum Erstellen von Vorhersagen, mit denen sich bestimmen lässt, ob ein Kunde ein Fahrrad kaufen wird.  
  
 Die Miningmodelle werden aus Daten erstellt, die in der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]-Beispieldatenbank enthalten sind. In dieser Datenbank werden Daten für das fiktive Unternehmen [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] gespeichert. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ist ein großes, multinationales Produktionsunternehmen. Das Unternehmen fertigt und verkauft Fahrräder aus Metall und Verbundwerkstoffen auf dem nordamerikanischen, europäischen und asiatischen Markt. Der Hauptsitz befindet sich mit 290 Mitarbeitern in Bothell, Washington. Darüber hinaus sind mehrere regionale Vertriebsteams über die internationalen Zielmärkte des Unternehmens verteilt.  
  
## <a name="tutorial-scenario"></a>Lernprogrammszenario  
 Das Unternehmen [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] hat entschieden, seine Datenanalyse auszuweiten. Dazu soll eine benutzerdefinierte Anwendung erstellt werden, die Data Mining-Funktionalität verwendet. Das Unternehmen erwartet von dieser benutzerdefinierten Anwendung, dass sie folgende Aufgaben ausführen kann:  
  
-   Spezifische Merkmale eines potenziellen Kunden erfassen und vorhersagen, ob der Kunde ein Fahrrad kaufen wird.  
  
-   Eine Liste potenzieller Kunden erstellen, spezifische Merkmale dieser Kunden erfassen und vorhersagen, welche Kunden ein Fahrrad kaufen werden.  
  
 Im ersten Fall werden Kundendaten von einer Kundenregistrierungsseite bereitgestellt, im zweiten Fall stellt die Marketingabteilung von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] eine Liste potenzieller Kunden zur Verfügung.  
  
 Darüber hinaus möchte die Marketingabteilung über die Möglichkeit verfügen, vorhandene Kunden in Kategorien zu gruppieren, die auf Merkmalen wie Wohnort, Anzahl der Kinder und Arbeitsweg basieren. Die Mitarbeiter der Marketingabteilung möchten untersuchen, ob mithilfe dieser Cluster bestimmte Kundengruppen gezielt angesprochen werden können. Dies erfordert ein zusätzliches Miningmodell.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet mehrere Tools, die verwendet werden können, um diese Aufgaben auszuführen:  
  
-   Die DMX-Abfragesprache  
  
-   Die [Microsoft Decision Trees-Algorithmus](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) und [Microsoft Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)  
  
-   Abfrage-Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]  
  
 Data Mining-Erweiterungen (DMX) ist eine von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bereitgestellte Abfragesprache, mit der Sie Miningmodelle erstellen und die Sie zum Arbeiten mit Mining-Modellen verwenden können. Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus erstellt Modelle, mit denen sich vorhersagen lässt, ob eine Person ein Fahrrad kaufen wird. Das resultierende Modell akzeptiert als Eingabe einen einzelnen Kunden oder eine Tabelle mit Kunden. Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus kann Gruppierungen von Kunden auf der Basis gemeinsamer Merkmale erstellen. Ziel dieses Lernprogramms ist es, die DMX-Skripts bereitzustellen, die in der benutzerdefinierten Anwendung verwendet werden.  
  
 **Weitere Informationen:** [Data Mining-Projektmappen](../../2014/analysis-services/data-mining/data-mining-solutions.md)  
  
## <a name="mining-structure-and-mining-models"></a>Miningstruktur und Miningmodelle  
 Bevor Sie mit dem Erstellen von DMX-Anweisungen beginnen, sollten Sie sich mit dem wichtigsten Objekten vertraut machen, die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zum Erstellen von Miningmodellen verwendet werden. Die Miningstruktur ist eine Datenstruktur, die die Datendomäne, aus der die Miningmodelle erstellt werden, definiert. Eine einzelne Miningstruktur kann mehrere Miningmodelle enthalten, die dieselbe Domäne verwenden. Ein Miningmodell wendet einen Miningmodellalgorithmus für die Daten an, welcher durch eine Miningstruktur dargestellt wird.  
  
 Die Grundbausteine der Miningstruktur sind die Miningstrukturspalten, die die in der Datenquelle enthaltenen Daten beschreiben. Diese Spalten enthalten Informationen, z. B. über den Datentyp, den Inhaltstyp und die Verteilung der Daten.  
  
 Miningmodelle müssen die in der Miningstruktur beschriebene Schlüsselspalte sowie eine Teilmenge der übrigen Spalten enthalten. Das Miningmodell definiert die Verwendung jeder einzelnen Spalte und den zum Erstellen des Miningmodells verwendeten Algorithmus. Beispiel: Sie können in DMX angeben, dass eine Spalte eine Schlüsselspalte oder ein PREDICT-Spalte ist. Eine Spalte, für die kein Typ angegeben ist, wird als Eingabespalte behandelt.  
  
 Es gibt in DMX zwei Möglichkeiten, Miningmodelle zu erstellen. Sie können die Mininstruktur und das zugehörige Miningmodell entweder zusammen mithilfe der CREATE MINING MODEL-Anweisung erstellen, oder Sie können zuerst mithilfe der CREATE MINING STRUCTURE-Anweisung eine Miningstruktur erstellen und dann der Miningstruktur mithilfe der ALTER STRUCTURE-Anweisung ein Miningmodell hinzufügen. Eine Beschreibung dieser Methoden finden Sie in der folgenden Tabelle.  
  
 CREATE MINING MODEL  
 Verwenden Sie diese Anweisung, um eine Miningstruktur und ihr zugehöriges Miningmodell (unter Verwendung desselben Namens) zusammen zu erstellen. An den Namen des Miningmodells wird "Structure" angefügt, um es von der Miningstruktur zu unterscheiden. Diese Anweisung ist hilfreich, wenn Sie eine Miningstruktur erstellen, die ein einzelnes Miningmodell enthält.  
  
 Weitere Informationen finden Sie unter [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).  
  
 ALTER MINING STRUCTURE  
 Verwenden Sie diese Anweisung, um einer Miningstruktur ein Miningmodell hinzuzufügen, das bereits auf dem Server vorhanden ist. Diese Anweisung ist hilfreich, wenn Sie eine Miningstruktur erstellen möchten, die mehrere unterschiedliche Miningmodelle enthält. Es kann mehrere Gründe geben, warum Sie einer einzelnen Miningstruktur mehr als nur ein Miningmodell hinzufügen sollten. Ein Grund könnte beispielsweise sein, dass Sie mehrere Miningmodelle mithilfe unterschiedlicher Algorithmen erstellen möchten, um herauszufinden, mit welchem Algorithmus die besten Ergebnisse erzielt werden. Oder Sie möchten beispielsweise mehrere Miningmodelle mithilfe desselben Algorithmus erstellen, einen Parameter für jedes Miningmodell jedoch anders festlegen, um die beste Einstellung für den Parameter zu ermitteln.  
  
 Weitere Informationen finden Sie unter [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016).  
  
 Da Sie eine Miningstruktur erstellen, die mehrere Miningmodelle beinhaltet, verwenden Sie in diesem Lernprogramm die zweite Methode.  
  
 **Weitere Informationen**  
  
 [Datamining-Erweiterungen &#40;DMX&#41; Verweis](/sql/dmx/data-mining-extensions-dmx-reference), [verstehen die DMX Select-Anweisung](/sql/dmx/understanding-the-dmx-select-statement), [Struktur und Verwendung von DMX-Vorhersageabfragen](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)  
  
## <a name="what-you-will-learn"></a>Lernziele  
 Dieses Lernprogramm ist in die folgenden Lektionen aufgeteilt:  
  
 [Lektion 1: Erstellen der Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)  
 In dieser Lektion erfahren Sie, wie mithilfe der `CREATE`-Anweisung Miningstrukturen erstellt werden.  
  
 [Lektion 2: Hinzufügen von Miningmodellen zur Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
 In dieser Lektion erfahren Sie, wie einer Miningstruktur mithilfe der `ALTER`-Anweisung Miningmodelle hinzugefügt werden.  
  
 [Lektion 3: Verarbeiten der Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
 In dieser Lektion erfahren Sie, wie mithilfe der `INSERT INTO`-Anweisung Miningstrukturen und die zugehörigen Miningmodelle verarbeitet werden.  
  
 [Lektion 4: Durchsuchen der Bike Buyer-Miningmodells](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
 In dieser Lektion erfahren Sie, wie mithilfe der `SELECT`-Anweisung der Inhalt der Miningmodelle untersucht wird.  
  
 [Lesson 5: Ausführen von Vorhersageabfragen](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
 In dieser Lektion erfahren Sie, wie mithilfe der `PREDICTION JOIN`-Anweisung Vorhersagen für Miningmodelle erstellt werden.  
  
## <a name="requirements"></a>Anforderungen  
 Stellen Sie vor dem Durchführen des Lernprogramms sicher, dass Folgendes installiert ist:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)], [!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)], [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], oder [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   Die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank. Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert. So installieren Sie die offiziellen Beispieldatenbanken für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], besuchen Sie die [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) Seite und wählen Sie die Datenbanken, die Sie installieren möchten...  
  
> [!NOTE]  
>  Zur besseren Anzeige der Lernprogramme empfehlen wir Ihnen, dass Sie der Symbolleiste in der Dokumentanzeige die Schaltflächen **Nächstes Thema** und **Vorheriges Thema** hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Market Basket DMX-Lernprogramm](../../2014/tutorials/market-basket-dmx-tutorial.md)   
 [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
  
