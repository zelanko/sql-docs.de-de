---
title: Zeit der DMX-Lernprogramm für Zeitreihenvorhersagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 550d038f917af8d191c078716161a8fdb0a99868
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230113"
---
# <a name="time-series-prediction-dmx-tutorial"></a>DMX-Lernprogramm für Zeitreihenvorhersagen
  In diesem Lernprogramm erstellen Sie eine Zeitreihen-Miningstruktur sowie drei benutzerdefinierte Zeitreihen-Miningmodelle und treffen Vorhersagen unter Verwendung dieser Modelle.  
  
 Die Miningmodelle basieren auf den Daten die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Beispieldatenbank, die Daten für das fiktive Unternehmen speichert [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ist ein großes, multinationales Produktionsunternehmen.  
  
## <a name="tutorial-scenario"></a>Lernprogrammszenario  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] hat beschlossen, Datamining zu verwenden, um Prognosen zu generieren. Sie haben bereits einige regionale Vorhersagemodelle erstellt; Weitere Informationen finden Sie unter [Lektion 2: erstellen eine Forecasting-Szenarios &#40;Data Mining Tutorial für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md). Die Vertriebsabteilung muss das Data Mining-Modell jedoch von Zeit zu Zeit anhand von neuen Umsatzdaten aktualisieren. Außerdem sollen die Modelle angepasst werden, um unterschiedliche Vorhersagen zu ermöglichen.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet mehrere Tools, die zum Ausführen dieser Aufgabe verwendet werden können:  
  
-   Abfragesprache Data Mining-Erweiterungen (Data Mining Extensions, DMX)  
  
-   Microsoft Time Series-Algorithmus  
  
-   Abfrage-Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]  
  
 Mit dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus werden Modelle für Vorhersagen im Zusammenhang mit zeitbezogenen Daten erstellt. Data Mining Extensions (DMX) ist eine Abfragesprache, die von bereitgestellte [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , Sie verwenden können, Miningmodelle und Vorhersageabfragen erstellen.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Tutorial wird davon ausgegangen, dass Sie bereits mit den Objekten vertraut sind, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet, um Miningmodelle zu erstellen. Wenn Sie nicht bereits eine Miningstruktur oder Miningmodell erstellt haben mithilfe von DMX, finden Sie unter [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).  
  
 Dieses Lernprogramm ist in die folgenden Lektionen aufgeteilt:  
  
 [Lektion 1: Erstellen eines Miningmodells und einer Miningstruktur für eine Zeitreihe](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)  
 In dieser Lektion lernen Sie, wie Sie mit der `CREATE MINING MODEL` -Anweisung ein neues Vorhersagemodell sowie ein verknüpftes Miningmodell hinzugefügt.  
  
 [Lektion 2: Hinzufügen von Miningmodellen zur Zeitreihen-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
 In dieser Lektion erfahren Sie, wie der Zeitreihenstruktur mithilfe der ALTER MINING STRUCTURE-Anweisung neue Miningmodelle hinzugefügt werden. Außerdem erfahren Sie, wie der Algorithmus, der zum Analysieren einer Zeitreihe verwendet wird, angepasst wird.  
  
 [Lektion 3: Verarbeiten der Zeitreihenstruktur und -modelle](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
 In dieser Lektion erfahren Sie, wie zum Trainieren der Modelle mithilfe der `INSERT INTO` -Anweisung und die Struktur mit Daten aus der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenbank.  
  
 [Lektion 4: Erstellen von Zeitreihenvorhersagen mit DMX](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
 In dieser Lektion erfahren Sie, wie Zeitreihenvorhersagen erstellt werden.  
  
 [Lektion 5: Erweitern des Zeitreihenmodells](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
 In dieser Lektion lernen Sie, wie Sie mit der `EXTEND_MODEL_CASES` Parameter, um das Modell mit neuen Daten aktualisiert werden, beim Erstellen von Vorhersagen.  
  
## <a name="requirements"></a>Anforderungen  
 Stellen Sie vor dem Durchführen des Lernprogramms sicher, dass Folgendes installiert ist:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   Die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenbank  
  
 Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert. So installieren Sie die offiziellen Beispieldatenbanken für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], wechseln Sie zu [ http://www.CodePlex.com/MSFTDBProdSamples ](http://go.microsoft.com/fwlink/?LinkId=88417) oder auf der Microsoft SQL Server Samples and Community Projects-Startseite im Abschnitt Microsoft SQL Server Product Samples. Klicken Sie auf **Datenbanken**und anschließend auf die Registerkarte **Releases** , und wählen Sie die gewünschten Datenbanken aus.  
  
> [!NOTE]  
>  Zur besseren Anzeige der Lernprogramme empfehlen wir Ihnen, dass Sie der Symbolleiste in der Dokumentanzeige die Schaltflächen **Nächstes Thema** und **Vorheriges Thema** hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramm zu Datamining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Datamining-Lernprogramm für fortgeschrittene &#40;Analysis Services – Datamining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
