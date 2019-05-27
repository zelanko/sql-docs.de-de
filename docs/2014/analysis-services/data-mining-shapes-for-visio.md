---
title: Datamining-Shapes für Visio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining shapes
- templates [Visio]
- Visio shapes
- shapes, data mining
ms.assetid: 11a821d9-1c0a-442e-b735-92208ce479dc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6ebe206d4f4942e9a9456ba10b00d33514ef6212
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66086396"
---
# <a name="data-mining-shapes-for-visio"></a>Data Mining-Shapes für Visio
  Die Data Mining-Shapes für Visio stellen Vorlagen bereit, die für die Darstellung von Data Mining-Modellen angepasst wurden. Mithilfe dieser Vorlagen können Sie eine Verbindung mit einem erstellten Modell herstellen und interaktive Präsentationen erstellen, um die Ergebnisse des Data Minings zu veranschaulichen.  
  
 Die Vorlagen bieten zahlreiche Vorteile gegenüber statischen Diagrammen und Bildschirmaufnahmen – sie interagieren mit der zugrunde liegenden Datamining-Modelle, die auf einer Instanz von Analysis Services gespeichert sind, und lassen Sie die Darstellung anpassen, dass die Muster im Miningmodell angezeigt werden. Sie können ein Strukturmodell reduzieren oder erweitern, nach Datenknoten oder Attributen filtern und die Modelstatistiken, z. B. Wahrscheinlichkeiten und Koeffizienten, anzeigen.  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Die Visio-Vorlagen umfassen folgende Assistenten:  
  
-   **Abhängigkeitsnetzwerk-Diagramm:** Verwenden Sie diesen Assistenten, um Diagramme für Entscheidungsstrukturen und neuronale Netzwerke zu erstellen.  
  
-   **Entscheidungsstrukturdiagramm:** Verwenden Sie diesen Assistenten zum Erstellen von Diagrammen, die zeigen, die Entscheidungspunkte und Formeln, die entscheidungsstrukturmodellen zugeordnet. Dieses Diagramm kann auch für Regressionsmodelle verwendet werden.  
  
-   **Clusterdiagramm:** Verwenden Sie diesen Assistenten, um farbige Diagramme für Segmentierungsmodelle zu erstellen. Sie können zwischen Sichten, wie Attributunterscheidung, Clusterprofilen und Abhängigkeiten, wechseln und die Darstellung von Clustern anpassen.  
  
## <a name="installation"></a>Installation  
 Bei der Installation von Data Mining-Vorlagen für Visio werden standardmäßig die folgenden Dateien werden installiert \<Laufwerk > \Programme\Microsoft SQL Server 2012 DM-Add-Ins (oder \<Laufwerk > \ oder Programme (x86) \Microsoft SQL Server 2012 DM Add-Ins):  
  
-   **Microsoft Data Mining.vst** diese Vorlage enthält vordefinierte Formatierungen, Layout und -Assistenten können Sie die Arbeit mit Datamining-Shapes.  
  
-   **Microsoft Data Mining Shape Studio.vss** Diese Schablonendatei enthält Formen, die der Vorlage zugeordnet.  
  
## <a name="how-to-use-the-templates"></a>So verwenden Sie die Vorlagen  
 Zum Öffnen der Vorlagen können Sie auf diese Shape-Datei doppelklicken, oder Sie können Visio starten und anschließend die Shape-Vorlage öffnen.  
  
1.  Legen Sie eines der Data Mining-Shapes in Visio aus der Schablone auf einem neuen Zeichenblatt ab.  
  
2.  Der Assistent wird gestartet. Stellen Sie eine Verbindung mit dem Server her, auf dem sich das darzustellende Data Mining-Modell befindet.  
  
3.  Wählen Sie das Data Mining-Modell aus, und stimmen Sie dabei den Modelltyp auf die Art der Visualisierung ab.  
  
4.  Legen Sie Optionen für die Anzeige und Formatierung der Daten fest.  
  
5.  Nach Abschluss der **Data Mining-Shape-Assistenten**, Sie haben ein Diagramm, das Sie ändern und verbessern können, mithilfe der Funktionen von Visio.  
  
 Weitere Informationen über das Arbeiten mit und Verbessern von Modelldiagrammen in Visio finden Sie unter [Anzeigen von Data Mining-Modellen in Visio &#40;Data Mining-Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)  
  
## <a name="requirements"></a>Anforderungen  
  
-   Zum Verwenden der Vorlagen müssen Sie zuerst eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen.  
  
     Vom Assistenten werden Sie aufgefordert, einen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server auszuwählen und die Datenbank anzugeben, in der das Miningmodell enthalten ist.  
  
     Informationen dazu, wie Sie eine Verbindung zu erstellen, finden Sie unter [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
-   Bei Verwendung der Tabellenanalysetools sollen Sie sicherstellen, dass Sie die Modelle auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server speichern und keine temporären Modelle verwenden.  
  
-   Das Modell muss mithilfe eines der unterstützten Algorithmen erstellt worden sein: Clustering, Entscheidungsstrukturen, neuronale Netzwerke, Naïve Bayes/ oder logistische Regression.  
  
  
