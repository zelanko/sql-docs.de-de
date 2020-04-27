---
title: Tutorial zu Data Mining-Grundlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 6602edb6-d160-43fb-83c8-9df5dddfeb9c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d434df95a26485d4d7795d3ab960b8d2457b8ff6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63185574"
---
# <a name="basic-data-mining-tutorial"></a>Lernprogramm zu Data Mining-Grundlagen
  Willkommen beim [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Lernprogramm zu Data Mining-Grundlagen. [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bietet eine integrierte Umgebung zum Erstellen von Data Mining Modellen und zum Treffen von Vorhersagen. In diesem Lernprogramm führen Sie ein Szenario für eine zielgerichtete Mailingkampagne aus, indem Sie Computerlernverfahren verwenden, um das Kaufverhalten von Kunden zu analysieren und vorherzusagen. Im Lernprogramm wird die Verwendung von drei der wichtigsten Data Mining-Algorithmen veranschaulicht: Clustering, Entscheidungsstrukturen und Naive Bayes. Darüber hinaus erfahren Sie, wie Sie Ihre Ergebnisse mit den Mining Modell-Viewern analysieren und Vorhersagen und Genauigkeits Diagramme mithilfe der Data Mining Tools erstellen [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], die in enthalten sind. In allen Beispielen wird das fiktive Unternehmen [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]verwendet.  
  
 Wenn Sie mit der Verwendung der Data Mining Tools vertraut sind, empfiehlt es sich, auch das Data Mining-Lernprogramm für fort [geschrittene &#40;Analysis Services Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)abzuschließen. In den Lektionen wird die Verwendung von Vorhersagen, Warenkorbanalysen, Zeitreihen, Zuordnungsmodellen, geschachtelten Tabellen und Sequence Clustering veranschaulicht.  
  
## <a name="tutorial-scenario"></a>Lernprogrammszenario  
 In diesem Lernprogramm sind Sie Mitarbeiter von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] , der beauftragt wurde, anhand ihrer bisherigen Käufe mehr über die Kunden des Unternehmens zu erfahren und mithilfe dieser historischen Daten Vorhersagen zu treffen, die für das Marketing verwendet werden können. Das Unternehmen hat noch nie zuvor Data Mining ausgeführt. Daher müssen Sie eigens für das Data Mining eine neue Datenbank anlegen und mehrere Data Mining-Modelle einrichten.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie, wie Sie verschiedene Typen von Computerlernmethoden entwickeln und verwenden. Sie lernen außerdem, wie Sie eine Kopie eines Miningmodells erstellen und einen Filter auf die Eingabedaten anwenden, um unterschiedliche Ergebnisse zu erhalten. Anschließend können Sie die Ergebnisse beider Modelle mit einem Prognosegütediagramm vergleichen. Zum Schluss rufen Sie mit der Drillthroughfunktion weitere Daten aus der zugrunde liegenden Miningstruktur ab.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Data Mining umfasst die folgenden Funktionen, mit denen Sie problemlos mehrere Vorhersagemodelle entwickeln und vergleichen und anschließend Aktionen für die Ergebnisse durchführen können:  
  
-   *Zurückhaltungstestsätze*– Beim Erstellen einer Miningstruktur können Sie nun die darin enthaltenen Daten in Trainings- und Testsätze aufteilen. Auf diese Weise können Sie Modelle an ähnlichen Datasets testen und die Genauigkeit verwandter Modelle testen.  
  
-   *Miningmodellfilter*– Sie können nun Filter an ein Miningmodell anfügen und diese beim Trainieren und Testen anwenden. Dies erleichtert die Erstellung verwandter Modelle für unterschiedliche Teilmengen der Daten.  
  
-   *Drillthrough zu Strukturfällen und Strukturspalten* – Sie können nun einfach von allgemeinen Mustern im Miningmodell zu aussagekräftigen Details in der Datenquelle wechseln.  
  
 Dieses Lernprogramm ist in die folgenden Lektionen aufgeteilt:  
  
 [Lektion 1: Vorbereiten der Analysis Services Datenbank &#40;Data Mining-Lernprogramm für grundlegende&#41;](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
 In dieser Lektion lernen Sie, wie Sie eine neue [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank anlegen, eine Datenquelle und Datenquellensicht hinzufügen und die neue Datenbank für die Verwendung von Data Mining vorbereiten.  
  
 [Lektion 2: aufbauen einer Ziel-Mailing Struktur &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
 In dieser Lektion erfahren Sie, wie Sie eine Miningmodellstruktur anlegen, die in einem Targeted Mailing-Szenario verwendet werden kann.  
  
 [Lektion 3: Hinzufügen und Verarbeiten von Modellen](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
 In dieser Lektion erfahren Sie, wie einer Struktur Modelle hinzugefügt werden. Die Modelle, die Sie erstellen, werden mit den folgenden Algorithmen erstellt:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes  
  
 [Lektion 4: Untersuchen der Ziel-Mailing-Modelle &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
 In dieser Lektion lernen Sie, die Ergebnisse der einzelnen Modelle mit Viewern zu untersuchen und zu interpretieren.  
  
 [Lektion 5: Testen von Modellen &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
 In dieser Lektion erstellen Sie eine Kopie des Targeted Mailing-Modells, fügen einen Miningmodellfilter hinzu, um die Trainingsdaten auf eine bestimmte Kundengruppe zu beschränken und bewerten anschließend die Verwendbarkeit des Modells.  
  
 [Lektion 6: Erstellen und Verwenden von Vorhersagen &#40;Tutorial zu Data Mining-Grundlagen&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
 In der Abschlusslektion des Lernprogramms zu Data Mining-Grundlagen sagen Sie anhand des Modells voraus, welche Kunden am wahrscheinlichsten ein Fahrrad kaufen werden. Danach führen Sie einen Drillthrough zu den zugrunde liegenden Fällen durch, um die Kontaktinformationen abzurufen.  
  
## <a name="requirements"></a>Anforderungen  
 Stellen Sie sicher, dass Folgendes installiert ist:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   Die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank.  
  
 Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht zusammen mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]installiert. Um die offiziellen Beispieldatenbanken für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zu installieren, rufen Sie die Seite [Microsoft SQL-Beispieldatenbanken](https://go.microsoft.com/fwlink/?LinkId=88417) auf und wählen Sie [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]aus.  
  
> [!NOTE]  
>  Wenn Sie ein Tutorial durcharbeiten, ist es möglicherweise einfacher, zwischen den Schritten zwischen den einzelnen Schritten zu wechseln, wenn Sie der Symbolleiste in der Dokument Anzeige die Schaltflächen **Nächstes Thema** und **Vorheriges Thema** hinzufügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Lösungen](../../2014/analysis-services/data-mining/data-mining-solutions.md)   
 [Mining Modell Tasks und Anleitungen](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Erstellen und Abfragen von Data Mining-Modellen mit DMX: Lernprogramme &#40;Analysis Services – Data Mining&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)  
  
  
