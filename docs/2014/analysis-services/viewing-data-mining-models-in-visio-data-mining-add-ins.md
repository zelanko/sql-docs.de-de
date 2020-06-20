---
title: Anzeigen von Data Mining-Modellen in Visio (Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- diagram, modifying
- templates [Visio]
- shapes, data mining
- diagram
ms.assetid: 5841adea-6650-4fae-8526-26af33edbede
author: minewiskan
ms.author: owend
ms.openlocfilehash: fe6baff391f108e14a401a0d3b9dcacefa6da406
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938141"
---
# <a name="viewing-data-mining-models-in-visio-data-mining-add-ins"></a>Anzeigen von Data Mining-Modellen in Visio (Data Mining-Add-Ins)
  Mit Visio-Shapes für das Data Mining können Sie eine Verbindung mit einem Server herstellen und ein Diagramm erstellen, das ein vorhandenes Data Mining-Modell darstellt. Die Diagramme können anschließend mithilfe von Visio-Steuerelementen angepasst werden; Sie können jedoch auch einen Drilldown auf Daten ausführen, einige der zugrunde liegenden Statistiken verfügbar machen und mit dem zugrunde liegenden Modell arbeiten.  
  
## <a name="building-a-model-diagram"></a>Erstellen eines Modelldiagramms  
 Wenn Sie die Datei öffnen, die die Visio-Formen für Data Mining enthält, zeigt der Bereich **Formen** die folgenden Formen an.  
  
 Wenn die Data Mining-Shapes beim Öffnen von Visio nicht angezeigt werden, öffnen Sie die Vorlagendatei aus dem Installationsordner.  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Zum Verwenden eines Shapes ziehen Sie es auf das Zeichenblatt. Durch jedes der Shapes wird ein bestimmter Assistent geöffnet, der Ihnen beim Auswählen von Quelldaten, beim Festlegen von Optionen für einen bestimmten Diagrammtyp sowie beim Angeben von Schattierungs- und anderen Anzeigeoptionen hilft.  
  
 In der folgenden Tabelle sind die Modelltypen aufgeführt, die Sie mit den einzelnen Diagrammtypen verwenden können.  
  
|Visio-Shape|Unterstützte Modelle|  
|-----------------|----------------------|  
|Entscheidungsstruktur|Verwenden Sie dieses Shape für Modelle, die auf dem Decision Tree- oder Linear Regression-Algorithmus basieren.|  
|Abhängigkeitsnetzwerk|Verwenden Sie dieses Shape für Diagramme, die auf einem der folgenden Algorithmen basieren: Naive Bayes, Decision Trees oder Association Rules.|  
|Cluster|Verwenden Sie dieses Shape für Modelle, die auf den Clustering-Algorithmen basieren.|  
  
 Abhängig vom Datentyp im Miningmodell werden vom Assistenten möglicherweise verschiedene Optionen angezeigt. Spalten, die fortlaufende Zahlen enthalten, werden beispielsweise anders visualisiert als Kategorievariablen.  
  
## <a name="working-with-completed-shapes"></a>Arbeiten mit abgeschlossenen Formen  
 Nach Fertigstellung des Diagramms können Sie damit das Data Mining-Modell durchsuchen, oder Sie können das Diagramm optimieren, um es in Präsentationen einzubinden.  
  
### <a name="visio-menus"></a>Visio-Menüs  
 Visio stellt eine Vielzahl von Renderingsteuerelementen, Designs und Kontextmenüs bereit, mit denen Sie ein Diagramm optimieren können.  
  
-   Verwenden Sie Visio-Designs zum Ändern von Diagrammfarben.  
  
-   Ändern Sie Verbinder oder das Diagrammlayout.  
  
### <a name="data-mining-menus"></a>Data Mining-Menüs  
 Diese Symbolleisten und Menüelemente werden von den Add-Ins bereitgestellt, die für die einzelnen Shapes oder Modelltypen spezifisch sind.  
  
-   Jeder Diagrammtyp weist ein Kontextmenü für das Shape auf, über das Sie auf spezielle Optionen zugreifen können. Obwohl viele Optionen in diesem Menü für sämtliche Visio-Shapes verwendet werden können, gelten einige ausschließlich für Data Mining-Vorlagen.  
  
     So können Sie beispielsweise in einem Entscheidungsstrukturdiagramm auf einen einzelnen Knoten klicken und die untergeordneten Knoten reduzieren, um das Diagramm zu vereinfachen, oder die untergeordneten Knoten auf ein anderes Zeichenblatt verschieben.  
  
-   Da das Shape an die Modelldaten gebunden ist, können mithilfe des Diagramms in gewissem Umfang auch Analysen ausgeführt werden:  
  
     Filtern der angezeigten Knoten oder Ändern der Strukturebene oder der Tiefe des Diagramms.  
  
     Vergrößern der Anzeige bestimmter Abschnitte, Suchen nach Knoten, die ein bestimmtes Attribut enthalten, oder Filtern eines Abhängigkeitsdiagramms anhand seiner Ränder (Wahrscheinlichkeit).  
  
## <a name="walkthroughs"></a>Exemplarische Vorgehensweisen  
 Beispiele zum Arbeiten mit einem fertiggestellten Diagramm und zu dessen Interpretation finden Sie in den folgenden Themen:  
  
 [Exemplarische Vorgehensweise für das Clusterdiagramm](cluster-diagram-walkthrough-data-mining-add-ins.md)  
  
 [Exemplarische Vorgehensweise für das Abhängigkeitsnetzwerkdiagramm](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
 [Exemplarische Vorgehensweise für das Entscheidungsstrukturdiagramm](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
