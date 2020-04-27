---
title: Assistent für Verwendungs basierte Optimierung (F1-Hilfe) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e5e94818245ba1e87d90f87539ae07e9531e5450
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66065572"
---
# <a name="usage-based-optimization-wizard-f1-help"></a>Assistent für verwendungsbasierte Optimierung (F1-Hilfe)
  Der Assistent für verwendungsbasierte Optimierung ist hinsichtlich der Ausgabe dem Aggregationsentwurfs-Assistenten ähnlich und wird zum Entwerfen von Aggregationen für eine Partition verwendet. Die vom Assistenten für verwendungsbasierte Optimierung entworfenen Aggregationen basieren jedoch auf bestimmten Verwendungsmustern, die in dem Abfrageprotokoll einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz aufgezeichnet wurden. Aggregationen bieten Leistungsverbesserungen, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] indem Sie zulassen, dass vorab berechnete Summen direkt aus dem Cube-Speicher abgerufen werden, anstatt Daten aus einer zugrunde liegenden Datenquelle für jede Abfrage neu zu berechnen.  
  
 Öffnen Sie den Cube- [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Designer für ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt, und klicken Sie dann auf die Registerkarte **Aggregationen** , um den Assistenten für Verwendungs basierte Optimierung in zu öffnen. Klicken Sie auf der Symbolleiste auf die Schaltfläche **Verwendungs basierte Optimierung** .  
  
 Stellen Sie eine Verbindung mit einer [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Datenbank her, und öffnen Sie anschließend den Ordner [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cubes **, um den Assistenten für verwendungsbasierte Optimierung in** zu öffnen. Wählen Sie einen Cube aus, öffnen Sie anschließend den Ordner **Measuregruppen** , und erweitern Sie die Measuregruppe, die Sie ändern möchten. Klicken Sie mit der rechten Maustaste auf den Ordner **Partitionen** , und wählen Sie dann die Option **Verwendungsbasierte Optimierung**aus.  
  
 Sie können den Aggregationsentwurfs-Assistenten verwenden, um diese Aggregationen zu entwerfen. Dieser Assistent führt Sie durch die folgenden Schritte:  
  
-   Auswählen von Standard- oder benutzerdefinierten Einstellungen für die Speicherungs- und Zwischenspeicherungsoptionen einer Partition, einer Measuregruppe oder eines Cubes.  
  
-   Bereitstellen von geschätzten oder tatsächlichen Werten für Objekte, auf die die Partition, die Measuregruppe oder der Cube verweist.  
  
-   Abgeben von Aggregationsoptionen und Grenzwerten, um den Speicher und die Abfrageleistung der entworfenen Aggregationen zu optimieren.  
  
-   Speichern und optionales Verarbeiten der Partition, der Measuregruppe oder des Cubes, um die definierten Aggregationen zu generieren.  
  
 In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wird der Aggregationsentwurfs-Assistent zum Entwerfen von Aggregationen bereitgestellt, die auf statistischen Analysen der Struktur der Partition basieren, um einen Aggregationsentwurf zu erstellen, der durch die Speicherplatzgröße oder den geschätzten Leistungsgewinn begrenzt werden kann. Sie können den Aggregationsentwurfs-Assistenten dazu verwenden, die Gesamtleistung einer Partition zu steigern, aber der Aggregationsentwurf ist dann nicht auf die speziellen Bedürfnisse Ihrer gewerblichen Benutzer ausgerichtet. Mit dem Assistenten für verwendungsbasierte Optimierung können Sie einen Aggregationsentwurf bereitstellen, der auf diese speziellen Bedürfnisse ausgerichtet ist. Das ist aber nur möglich, wenn das Abfrageprotokoll der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz genügend Informationen zum Erstellen solcher Abfragen enthält.  
  
 Normalerweise werden beide Assistenten zusammen verwendet, um die Leistung sowohl in Bezug auf die Bereitstellung als auch in Bezug auf den Zeitverlauf zu steigern. Der Aggregationsentwurfs-Assistent sollte zuerst verwendet werden, wenn die Partition (bzw. der Cube oder die Measuregruppe, die die Partition enthält) erstmalig bereitgestellt wird, um von einer besseren Gesamtleistung zu profitieren. Nach einem bestimmten Zeitraum, in dem die Abfragen der gewerblichen Benutzer für die Partition im Abfrageprotokoll aufgezeichnet wurden, können Sie den Assistenten für verwendungsbasierte Optimierung verwenden, um den Aggregationsentwurf stärker auf die bessere Erfüllung der Leistungs- und Abfrageanforderungen Ihrer gewerblichen Benutzer zu fokussieren.  
  
> [!NOTE]  
>  Informationen zum Konfigurieren des Abfrageprotokolls finden Sie unter [Konfigurieren des Abfrageprotokolls von Analysis Services](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Wählen Sie Partitionen aus, um den Assistenten für Verwendungs basierte Optimierung zu &#40;ändern&#41;](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [Geben Sie die Abfrage Kriterien &#40;Assistenten für Verwendungs basierte Optimierung an&#41;](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [Überprüfen Sie die Abfragen, die &#40;Assistenten für die Verwendungs basierte Optimierung optimiert werden&#41;](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [Überprüfen Sie die Aggregations Verwendung &#40;Verwendungs basierten Optimierungs-Assistenten&#41;](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [Objekt Anzahl &#40;Verwendungs basierten Optimierungs Assistenten angeben&#41;](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [Festlegen der Aggregations Optionen &#40;Verwendungs basierte Optimierung-Assistent&#41;](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [Der Assistent &#40;Assistenten für Verwendungs basierte Optimierung abgeschlossen&#41;](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aggregationen und Aggregations Entwürfe](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [Cubes in mehrdimensionalen Modellen](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Aggregations Entwurfs-Assistent F1-Hilfe](aggregation-design-wizard-f1-help.md)   
 [Analysis Services Assistenten &#40;Mehrdimensionale Daten&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
