---
title: Verwendungsbasierte Optimierung-Assistent F1-Hilfe | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b703234bb779042bdd341140e603938b16ebb412
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046264"
---
# <a name="usage-based-optimization-wizard-f1-help"></a>Assistent für verwendungsbasierte Optimierung (F1-Hilfe)
  Der Assistent für verwendungsbasierte Optimierung ist hinsichtlich der Ausgabe dem Aggregationsentwurfs-Assistenten ähnlich und wird zum Entwerfen von Aggregationen für eine Partition verwendet. Die vom Assistenten für verwendungsbasierte Optimierung entworfenen Aggregationen basieren jedoch auf bestimmten Verwendungsmustern, die in dem Abfrageprotokoll einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz aufgezeichnet wurden. Aggregationen führen zu Leistungssteigerungen, indem sie [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ermöglichen, vorher berechnete Ergebnisse direkt aus dem Cubespeicher abzurufen, statt die Daten aus einer zugrunde liegenden Datenquelle bei jeder Abfrage erneut zu berechnen.  
  
 Öffnen Sie den Cube-Designer für ein [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]-Projekt, und klicken Sie anschließend auf die Registerkarte [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Aggregationen **, um den Assistenten für verwendungsbasierte Optimierung in** zu öffnen. Klicken Sie in der Symbolleiste auf die Schaltfläche **Verwendungsbasierte Optimierung** .  
  
 Stellen Sie eine Verbindung mit einer [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Datenbank her, und öffnen Sie anschließend den Ordner [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cubes **, um den Assistenten für verwendungsbasierte Optimierung in** zu öffnen. Wählen Sie einen Cube aus, öffnen Sie anschließend den Ordner **Measuregruppen** , und erweitern Sie die Measuregruppe, die Sie ändern möchten. Klicken Sie mit der rechten Maustaste auf den Ordner **Partitionen** , und wählen Sie dann die Option **Verwendungsbasierte Optimierung**aus.  
  
 Sie können den Aggregationsentwurfs-Assistenten verwenden, um diese Aggregationen zu entwerfen. Dieser Assistent führt Sie durch die folgenden Schritte:  
  
-   Auswählen von Standard- oder benutzerdefinierten Einstellungen für die Speicherungs- und Zwischenspeicherungsoptionen einer Partition, einer Measuregruppe oder eines Cubes.  
  
-   Bereitstellen von geschätzten oder tatsächlichen Werten für Objekte, auf die die Partition, die Measuregruppe oder der Cube verweist.  
  
-   Abgeben von Aggregationsoptionen und Grenzwerten, um den Speicher und die Abfrageleistung der entworfenen Aggregationen zu optimieren.  
  
-   Speichern und optionales Verarbeiten der Partition, der Measuregruppe oder des Cubes, um die definierten Aggregationen zu generieren.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Stellt den Aggregationsentwurfs-Assistent zum Entwerfen von Aggregationen basierend auf statistischen Analysen der Struktur der Partition, um einen Aggregationsentwurf zu erstellen, durch die Speicherplatzgröße begrenzt werden kann oder geschätzten Leistungsgewinn. Sie können den Aggregationsentwurfs-Assistenten dazu verwenden, die Gesamtleistung einer Partition zu steigern, aber der Aggregationsentwurf ist dann nicht auf die speziellen Bedürfnisse Ihrer gewerblichen Benutzer ausgerichtet. Mit dem Assistenten für verwendungsbasierte Optimierung können Sie einen Aggregationsentwurf bereitstellen, der auf diese speziellen Bedürfnisse ausgerichtet ist. Das ist aber nur möglich, wenn das Abfrageprotokoll der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz genügend Informationen zum Erstellen solcher Abfragen enthält.  
  
 Normalerweise werden beide Assistenten zusammen verwendet, um die Leistung sowohl in Bezug auf die Bereitstellung als auch in Bezug auf den Zeitverlauf zu steigern. Der Aggregationsentwurfs-Assistent sollte zuerst verwendet werden, wenn die Partition (bzw. der Cube oder die Measuregruppe, die die Partition enthält) erstmalig bereitgestellt wird, um von einer besseren Gesamtleistung zu profitieren. Nach einem bestimmten Zeitraum, in dem die Abfragen der gewerblichen Benutzer für die Partition im Abfrageprotokoll aufgezeichnet wurden, können Sie den Assistenten für verwendungsbasierte Optimierung verwenden, um den Aggregationsentwurf stärker auf die bessere Erfüllung der Leistungs- und Abfrageanforderungen Ihrer gewerblichen Benutzer zu fokussieren.  
  
> [!NOTE]  
>  Informationen zum Konfigurieren des Abfrageprotokolls finden Sie unter [Konfigurieren des Abfrageprotokolls von Analysis Services](http://www.microsoft.com/technet/prodtechnol/sql/2005/technologies/config_ssas_querylog.mspx).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Wählen Sie die zu ändernde Partitionen &#40;Verwendungsbasierte Optimierung-Assistent&#41;](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [Geben Sie die Abfragekriterien &#40;Verwendungsbasierte Optimierung-Assistent&#41;](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [Überprüfen Sie die Abfragen, die optimiert werden &#40;Verwendungsbasierte Optimierung-Assistent&#41;](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [Aggregationsverwendung überprüfen &#40;Verwendungsbasierte für Verwendungsbasierte Optimierung-Assistenten&#41;](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [Objektanzahl angeben &#40;Verwendungsbasierte Optimierung-Assistent&#41;](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [Aggregationsoptionen festlegen &#40;Verwendungsbasierte Optimierung-Assistent&#41;](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [Fertigstellen des Assistenten &#40;Verwendungsbasierte Optimierung-Assistent&#41;](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Aggregationen und Aggregationsentwürfe](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [Cubes in mehrdimensionalen Modellen](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Aggregationsentwurfs-Assistent F1 Hilfe](aggregation-design-wizard-f1-help.md)   
 [Analysis Services-Assistenten &#40;mehrdimensionale Daten&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  