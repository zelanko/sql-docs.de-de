---
title: Data Mining-Shapes für Visio | Microsoft-Dokumentation
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
ms.openlocfilehash: 1d30456ac3685aa3dc40af6f1c79f92796fc1404
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84525776"
---
# <a name="data-mining-shapes-for-visio"></a>Data Mining-Shapes für Visio
  Die Data Mining-Shapes für Visio stellen Vorlagen bereit, die für die Darstellung von Data Mining-Modellen angepasst wurden. Mithilfe dieser Vorlagen können Sie eine Verbindung mit einem erstellten Modell herstellen und interaktive Präsentationen erstellen, um die Ergebnisse des Data Minings zu veranschaulichen.  
  
 Die Vorlagen bieten viele Vorteile gegenüber statischen Diagrammen und Bildschirmaufzeichnungen. Sie interagieren mit den zugrunde liegenden Data Mining Modellen, die auf einer Instanz von Analysis Services gespeichert sind, und ermöglichen es Ihnen, die Art und Weise anzupassen, in der die Muster im Mining Modell angezeigt werden. Sie können ein Strukturmodell reduzieren oder erweitern, nach Datenknoten oder Attributen filtern und die Modelstatistiken, z. B. Wahrscheinlichkeiten und Koeffizienten, anzeigen.  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Die Visio-Vorlagen umfassen folgende Assistenten:  
  
-   **Abhängigkeits Netzwerkdiagramm:** Verwenden Sie diesen Assistenten, um Diagramme für Entscheidungsstrukturen und neuronale Netzwerke zu erstellen.  
  
-   **Entscheidungsstruktur Diagramm:** Verwenden Sie diesen Assistenten, um Diagramme zu erstellen, in denen die Entscheidungspunkte und Formeln angezeigt werden, die Entscheidungsstruktur Modellen zugeordnet sind. Dieses Diagramm kann auch für Regressionsmodelle verwendet werden.  
  
-   **Cluster Diagramm:** Verwenden Sie diesen Assistenten, um Farbige Diagramme für Segmentierungs Modelle zu erstellen. Sie können zwischen Sichten, wie Attributunterscheidung, Clusterprofilen und Abhängigkeiten, wechseln und die Darstellung von Clustern anpassen.  
  
## <a name="installation"></a>Installation  
 Wenn Sie die Data Mining-Vorlagen für Visio installieren, werden standardmäßig die folgenden Dateien im Ordner \<drive> \Programme\Microsoft SQL Server 2012 DM Add-Ins (oder \<drive> \ oder Programme (x86) \Microsoft SQL Server 2012 DM Add-Ins) installiert:  
  
-   **Microsoft Data Mining. VST** Diese Vorlage enthält vorgefertigte Formatierung, Layout und Assistenten, die Sie beim Arbeiten mit den Data Mining Formen unterstützen.  
  
-   **Microsoft Data Mining Shape Studio. VSS** Diese Schablonen Datei enthält Formen, die der Vorlage zugeordnet sind.  
  
## <a name="how-to-use-the-templates"></a>So verwenden Sie die Vorlagen  
 Zum Öffnen der Vorlagen können Sie auf diese Shape-Datei doppelklicken, oder Sie können Visio starten und anschließend die Shape-Vorlage öffnen.  
  
1.  Legen Sie eines der Data Mining-Shapes in Visio aus der Schablone auf einem neuen Zeichenblatt ab.  
  
2.  Der Assistent wird gestartet. Stellen Sie eine Verbindung mit dem Server her, auf dem sich das darzustellende Data Mining-Modell befindet.  
  
3.  Wählen Sie das Data Mining-Modell aus, und stimmen Sie dabei den Modelltyp auf die Art der Visualisierung ab.  
  
4.  Legen Sie Optionen für die Anzeige und Formatierung der Daten fest.  
  
5.  Nachdem Sie den Assistenten für **Data Mining**-Shapes abgeschlossen haben, verfügen Sie über ein Diagramm, das Sie mithilfe der Features von Visio ändern und verbessern können.  
  
 Weitere Informationen zum Arbeiten mit und verbessern von Visio-Modell Diagrammen finden [Sie unter Anzeigen von Data Mining-Modellen in Visio &#40;Data Mining-Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
  
-   Zum Verwenden der Vorlagen müssen Sie zuerst eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen.  
  
     Vom Assistenten werden Sie aufgefordert, einen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server auszuwählen und die Datenbank anzugeben, in der das Miningmodell enthalten ist.  
  
     Weitere Informationen zum Erstellen einer Verbindung finden Sie unter Herstellen einer Verbindung [mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
-   Bei Verwendung der Tabellenanalysetools sollen Sie sicherstellen, dass Sie die Modelle auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server speichern und keine temporären Modelle verwenden.  
  
-   Das Modell muss mithilfe eines der unterstützten Algorithmen erstellt worden sein: Clustering, Entscheidungsstrukturen, neuronale Netzwerke, Naïve Bayes/ oder logistische Regression.  
  
  
