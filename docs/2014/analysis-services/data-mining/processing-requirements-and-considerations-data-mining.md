---
title: Verarbeiten von Anforderungen und Überlegungen (Datamining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], objects
- mining structures [Analysis Services], processing
- mining models [Analysis Services], processing
ms.assetid: f7331261-6f1c-4986-b2c7-740f4b92ca44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7bc06d5ece0b81ff3da9d41abb31e2c864a29f5e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66083133"
---
# <a name="processing-requirements-and-considerations-data-mining"></a>Anforderungen und Überlegungen zur Verarbeitung (Data Mining)
  In diesem Thema werden in einige technische Überlegungen behandelt, die beim Verarbeiten von Data Mining-Objekten berücksichtigt werden sollten. Eine allgemeine Erklärung der Verarbeitung und deren Anwendung auf Data Mining finden Sie unter [Verarbeiten von Data Mining-Objekten](processing-data-mining-objects.md).  
  
 [Abfragen an relationalen Speicher](#bkmk_QueryReqs)  
  
 [Verarbeiten von Miningstrukturen](#bkmk_ProcessStructures)  
  
 [Verarbeiten von Miningmodellen](#bkmk_ProcessModels)  
  
##  <a name="bkmk_QueryReqs"></a> Abfragen an den relationalen Speicher während der Verarbeitung  
 Für Data Mining besteht der Verarbeitungsprozess aus drei Phasen: Abfragen der Quelldaten, Bestimmen der statistischen Rohdaten und Trainieren des Miningmodells mit der Modelldefinition und dem Modellalgorithmus.  
  
 Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server gibt Abfragen an die Datenbank aus, die die Rohdaten bereitstellt. Bei dieser Datenbank kann es sich um eine Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder einer früheren Version der SQL Server-Datenbank-Engine handeln. Beim Verarbeiten einer Data Mining-Struktur werden die Daten der Quelle an die Miningstruktur übertragen und in einem neuen komprimierten Format auf dem Datenträger gespeichert. Es werden nicht alle Spalten der Datenquelle verarbeitet: Es werden nur die Spalten verarbeitet, die gemäß der Definition durch die Bindungen in der Miningstruktur enthalten sind.  
  
 Mit den Rohdaten baut [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] einen Index aller Daten und diskretisierten Spalten auf und erstellt einen separaten Index für fortlaufende Spalten. Für jede geschachtelte Tabelle wird zum Erstellen des Index eine Abfrage ausgegeben. Eine weitere Abfrage wird für jede geschachtelte Tabelle generiert, um die Beziehungen zwischen den einzelnen Paaren einer geschachtelten Tabelle und Falltabelle zu verarbeiten. Es werden mehrere Abfragen erstellt, um einen besonderen internen mehrdimensionalen Datenspeicher zu verarbeiten. Sie können die Anzahl der Abfragen, die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an den relationalen Speicher gesendet werden, beschränken, indem Sie die Servereigenschaft `DatabaseConnectionPoolMax` festlegen. Weitere Informationen finden Sie unter [OLAP Properties](../server-properties/olap-properties.md).  
  
 Beim Verarbeiten des Modells liest das Modell die Daten nicht erneut von der Datenquelle, sondern ruft stattdessen die Zusammenfassung der Daten aus der Miningstruktur ab. Mit dem erstellten Cube und den zwischengespeicherten Index- und Falldaten erstellt der Server unabhängige Threads zum Trainieren der Modelle.  
  
 Weitere Informationen zu den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die parallele Modellverarbeitung unterstützen, finden Sie unter [von den SQL Server 2012-Editionen unterstützte Funktionen](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).  
  
##  <a name="bkmk_ProcessStructures"></a> Verarbeiten von Miningstrukturen  
 Eine Miningstruktur kann zusammen mit allen abhängigen Modellen oder getrennt verarbeitet werden. Die Verarbeitung einer Miningstruktur getrennt von Modellen kann nützlich sein, wenn manche Modelle voraussichtlich eine lange Verarbeitungszeit benötigen und Sie diesen Vorgang aufschieben möchten.  
  
 Weitere Informationen finden Sie unter [Process a Mining Structure](process-a-mining-structure.md).  
  
 Wenn es für Sie wichtig ist, Festplattenspeicherplatz zu sparen, beachten Sie, dass die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] beibehaltene Miningstruktur lokal zwischengespeichert wird. Das bedeutet, dass alle Trainingsdaten auf die lokale Festplatte geschrieben werden. Wenn keine Daten zwischengespeichert werden sollen, können Sie die Standardeinstellung ändern, indem Sie für die <xref:Microsoft.AnalysisServices.MiningStructureCacheMode>-Eigenschaft der Miningstruktur `ClearAfterProcessing` festlegen. Auf diese Weise wird der Zwischenspeicher nach der Verarbeitung der Modelle gelöscht, und außerdem wird Drillthrough für die Miningstruktur deaktiviert. Weitere Informationen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).  
  
 Wenn Sie den Cache löschen, können Sie außerdem nicht den Zurückhaltungstestsatz verwenden, wenn Sie einen solchen definiert haben, und die Definition der Testsatzpartition geht verloren. Weitere Informationen zu Zurückhaltungstestsätzen finden Sie unter [Trainings- und Testdatasets](training-and-testing-data-sets.md).  
  
##  <a name="bkmk_ProcessModels"></a> Verarbeiten von Miningmodellen  
 Sie können ein Miningmodell getrennt von seiner zugeordnete Miningstruktur verarbeiten, oder Sie können alle Modelle, die auf der Struktur basieren, zusammen mit der Struktur verarbeiten.  
  
 Weitere Informationen finden Sie unter [Verarbeiten eines Miningmodells](process-a-mining-model.md).  
  
 In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] und [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]können Sie jedoch nicht mehrere Miningmodelle für die Verarbeitung mit der Struktur auswählen. Wenn Sie steuern müssen, welche Modelle verarbeitet werden, müssen Sie sie einzeln auswählen oder XMLA bzw. DMX verwenden, um die Modelle seriell zu verarbeiten.  
  
## <a name="when-reprocessing-is-required"></a>Wenn Neuverarbeitung erforderlich ist  
 Sie müssen die von Ihnen definierten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Modelle verarbeiten, bevor Sie damit arbeiten können. Darüber hinaus müssen Sie die Miningmodelle immer dann neu verarbeiten, wenn Sie Änderungen an der Struktur des Miningmodells vornehmen, die Trainingsdaten aktualisieren, ein vorhandenes Miningmodell ändern oder der Struktur ein neues Miningmodell hinzufügen.  
  
 Miningmodelle werden auch in folgenden Szenarien verarbeitet:  
  
 **Bereitstellung eines Projekts**: Je nach den projekteinstellungen und den aktuellen Zustand des Projekts werden die Miningmodelle im Projekt in der Regel vollständig verarbeitet, wenn das Projekt bereitgestellt wird.  
  
 Beim Initiieren der Bereitstellung beginnt die Verarbeitung automatisch, es sei denn, auf dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server befindet sich eine zu einem früheren Zeitpunkt verarbeitete Version und es gibt keine strukturellen Änderungen. Wählen Sie in der Dropdownliste **Projektmappe bereitstellen** aus, oder drücken Sie F5, um ein Projekt bereitzustellen. Folgende Aktionen sind möglich:  
  
 Weitere Informationen zum Festlegen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Bereitstellungseigenschaften, die steuern, wie Miningmodelle bereitgestellt werden, finden Sie unter [Bereitstellen von Data Mining-Lösungen](deployment-of-data-mining-solutions.md).  
  
 **Verschieben eines Miningmodells**: Wenn Sie ein Miningmodell verschieben, indem Sie mithilfe des Befehls EXPORTIEREN, wird nur die Definition des Modells exportiert, dazu gehört der Name der Miningstruktur, die Daten für das Modell bereitstellen soll.  
  
 Neuverarbeitungsanforderungen für die folgenden Szenarien, die die Befehle EXPORT und IMPORT verwenden:  
  
-   Die Miningstruktur ist auf der Zielinstanz vorhanden, und die Miningstruktur befindet sich in einem nicht verarbeiteten Status.  
  
     Sowohl die Struktur als auch das Modell müssen erneut verarbeitet werden.  
  
-   Die Miningstruktur ist auf der Zielinstanz vorhanden, und die Miningstruktur wurde verarbeitet. Nur das Miningmodell wurde exportiert.  
  
     Das Modell kann ohne Verarbeitung verwendet werden.  
  
-   Die Miningstrukturdefinition wurde ebenfalls mit dem WITH DEPENDENCIES-Schlüsselwort exportiert.  
  
     Sowohl die Struktur als auch das Modell müssen erneut verarbeitet werden.  
  
 Weitere Informationen finden Sie unter [Exportieren und Importieren von Data Mining-Objekten](export-and-import-data-mining-objects.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Verarbeitung von mehrdimensionalen Modellobjekten](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
