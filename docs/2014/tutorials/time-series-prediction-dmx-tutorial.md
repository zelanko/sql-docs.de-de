---
title: DMX-Tutorial für Zeitreihen Vorhersage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 1623f824c062c270268323fd45ebf0e9533c8788
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044183"
---
# <a name="time-series-prediction-dmx-tutorial"></a>DMX-Lernprogramm für Zeitreihenvorhersagen
  In diesem Lernprogramm erstellen Sie eine Zeitreihen-Miningstruktur sowie drei benutzerdefinierte Zeitreihen-Miningmodelle und treffen Vorhersagen unter Verwendung dieser Modelle.  
  
 Die Miningmodelle werden aus Daten erstellt, die in der  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Beispieldatenbank enthalten sind. In dieser Datenbank werden Daten für das fiktive Unternehmen [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]gespeichert. 
  [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ist ein großes, multinationales Produktionsunternehmen.  
  
## <a name="tutorial-scenario"></a>Lernprogrammszenario  
 
  [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] hat sich entschieden, Umsatzprognosen unter Einsatz von Data Mining zu generieren. Sie haben bereits einige regionale Vorhersagemodelle erstellt. Weitere Informationen finden Sie unter [Lektion 2: Erstellung eines Vorhersage Szenarios &#40;Data Mining ](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)-Lernprogramm für fortgeschrittene&#41;. Die Vertriebsabteilung muss das Data Mining-Modell jedoch von Zeit zu Zeit anhand von neuen Umsatzdaten aktualisieren. Außerdem sollen die Modelle angepasst werden, um unterschiedliche Vorhersagen zu ermöglichen.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stellt mehrere Tools bereit, die zum Ausführen dieser Aufgabe verwendet werden [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] können:  
  
-   Abfragesprache Data Mining-Erweiterungen (Data Mining Extensions, DMX)  
  
-   Microsoft Time Series-Algorithmus  
  
-   Abfrage-Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]  
  
 Mit dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus werden Modelle für Vorhersagen im Zusammenhang mit zeitbezogenen Daten erstellt. Data Mining-Erweiterungen (DMX) ist eine Abfragesprache von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , mit der Sie Miningmodelle und Vorhersageabfragen erstellen können.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm wird davon ausgegangen, dass Sie bereits mit den Objekten vertraut sind, die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zum Erstellen von Miningmodellen verwendet werden. Wenn Sie noch keine Miningstrukturen oder Miningmodelle mit DMX erstellt haben, finden Sie unter [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md)weitere Informationen.  
  
 Dieses Lernprogramm ist in die folgenden Lektionen aufgeteilt:  
  
 [Lektion 1: Erstellen eines Miningmodells und einer Miningstruktur für eine Zeitreihe](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)  
 In dieser Lektion erfahren Sie, wie mithilfe der `CREATE MINING MODEL`-Anweisung ein neues Vorhersagemodell sowie ein entsprechendes Miningmodell hinzugefügt werden.  
  
 [Lektion 2: Hinzufügen von Miningmodellen zur Zeitreihen-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
 In dieser Lektion erfahren Sie, wie der Zeitreihenstruktur mithilfe der ALTER MINING STRUCTURE-Anweisung neue Miningmodelle hinzugefügt werden. Außerdem erfahren Sie, wie der Algorithmus, der zum Analysieren einer Zeitreihe verwendet wird, angepasst wird.  
  
 [Lektion 3: Verarbeiten der Zeitreihenstruktur und -modelle](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
 In dieser Lektion erfahren Sie, wie die Modelle mit der `INSERT INTO`-Anweisung trainiert und wie die Struktur mit Daten aus der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]-Datenbank gefüllt werden.  
  
 [Lektion 4: Erstellen von Zeitreihenvorhersagen mit DMX](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
 In dieser Lektion erfahren Sie, wie Zeitreihenvorhersagen erstellt werden.  
  
 [Lektion 5: Erweitern des Zeitreihenmodells](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
 In dieser Lektion erfahren Sie, wie das Modell mit dem `EXTEND_MODEL_CASES`-Parameter beim Erstellen von Vorhersagen mit neuen Daten aktualisiert wird.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Stellen Sie vor dem Durchführen des Lernprogramms sicher, dass Folgendes installiert ist:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   Die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank.  
  
 Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert. Um die offiziellen Beispiel Datenbanken für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zu installieren, wechseln [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) Sie zu oder auf der Startseite Microsoft SQL Server Samples and Community Projects des Abschnitts Microsoft SQL Server Product Samples. Klicken Sie auf **Datenbanken**und anschließend auf die Registerkarte **Releases** , und wählen Sie die gewünschten Datenbanken aus.  
  
> [!NOTE]  
>  Wenn Sie Tutorials überprüfen, empfiehlt es sich, der Symbolleiste in der Dokument Anzeige die Schaltflächen **Nächstes Thema** und **Vorheriges Thema** hinzuzufügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Data Mining-Lernprogramm für fortgeschrittene &#40;Analysis Services-Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
