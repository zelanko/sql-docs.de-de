---
title: Datenquellensicht-Designer (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.f1
helpviewer_keywords:
- Data Source View Designer
ms.assetid: 6f40a074-761f-440b-a999-09b755bd86ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9153a2d07653872ca6ce1f90e39c90f32da21fba
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66082521"
---
# <a name="data-source-view-designer-analysis-services---multidimensional-data"></a>Datenquellensicht-Designer (Analysis Services – Mehrdimensionale Daten)
  Eine Datenquellensicht (DSV) ist eine logische Sicht einer externen relationalen Datenquelle, die zum Erstellen von Cubes und Dimensionen in einem mehrdimensionalen Modell verwendet wird.  
  
 Nach dem Generieren einer Datenquellensicht können Sie den **Datenquellensicht-Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] verwenden, um direkt in der Datenquellensicht zu arbeiten. Das kann hilfreich sein, wenn in der zugrunde liegenden Datenquelle Datenelemente fehlen, die in einem mehrdimensionalen Modell benötigt werden.  
  
 So öffnen Sie den **Datenquellensicht-Designer** :  
  
-   Doppelklicken Sie auf eine Datenquellensicht im **Projektmappen-Explorer**.  
  
-   Klicken Sie mit der rechten Maustaste auf eine Datenquellensicht im **Projektmappen-Explorer** , und wählen Sie **Öffnen** oder **Sicht-Designer**aus.  
  
 Der **Datenquellensicht-Designer** enthält eine Symbolleiste, ein Diagramm zur Darstellung der in der Datenquellensicht enthaltenen Objekte und Beziehungen, einen Tabellenbereich mit den alphabetisch sortierten Tabellen und benannten Abfragen sowie den Bereich Diagrammplaner, in dem Sie bestimmte Diagramme der Datenquellensicht erstellen und anzeigen können. Sie können mit der rechten Maustaste auf eine Tabelle oder Beziehung klicken, um auf kontextabhängige Befehle zuzugreifen.  
  
 ![Datenquellensicht-Designer](media/ssas-dsvdesigner.PNG "Datenquellensicht-Designer")  
  
 Eine Datenquellensicht enthält mindestens die relationalen Datenbanktabellen, die verwendet werden, um Modellobjekte während der Verarbeitung mit Daten aufzufüllen. Eine Datenquellensicht wird normalerweise mit dem Datenquellensicht-Assistenten generiert. Tabellen, Spalten und Beziehungen in der Datenquellensicht bilden die Grundlage für Dimensionen und Measures in einem Cube. Nachdem die Datenquellensicht erstellt wurde, können Sie sie mit dem Datenquellensicht-Designer ändern.  
  
 Meistens verwenden Analysis Services-Entwickler generierte Datenquellensichten in ihrem Originalzustand oder nur mit geringfügigen Anpassungen. Dies ist insbesondere dann üblich, wenn Quelldaten aus einer Sicht einer SQL Server-Datenbank stammen. In diesem Fall ziehen Sie es möglicherweise vor, Datenbeziehungen und Berechnungen in einer T-SQL-Ansicht anstatt in einer Analysis Services-Datenquellensicht zu verwalten. Wenn Sie jedoch nicht der Besitzer der zugrunde liegenden Datenbank sind, können Sie die Datenquellensicht in Analysis Services ändern, um die im Modell verwendeten Datenstrukturen weiter zu verfeinern.  
  
## <a name="tasks-in-data-source-view-designer"></a>Aufgaben im Datenquellensicht-Designer  
 Mithilfe des Datenquellensicht-Designers können Sie folgende Änderungen an einer Datenquellensicht vornehmen:  
  
|||  
|-|-|  
|Umbenennen von Spalten oder Tabellen bzw. Erstellen neuer berechneter Spalten. Beispielsweise können Sie einen Vornamen und einen Nachnamen in einer neuen Spalte mit vollständigen Namen verketten.|[Definieren von benannten Berechnungen in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)|  
|Manuelles Hinzufügen von Tabellenbeziehungen|[Definieren von logischen Beziehungen in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/define-logical-relationships-in-a-data-source-view-analysis-services.md)|  
|Erstellen einer benannten Abfrage, um ein neues Objekt auf der Grundlage einer T-SQL-Abfrage zu definieren.|[Definieren von benannten Abfragen in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)|  
|Untersuchen zugrunde liegender Daten, um die eigentlichen Datenwerte anzuzeigen, die von Modellobjekten dargestellt werden.<br /><br /> Durch das Durchsuchen von Daten können Sie Daten, die von der zugrunde liegenden dimensionalen Tabelle oder Abfrage zurückgegeben wurden, visuell überprüfen und kopieren. Beim Durchsuchen von Daten wird standardmäßig die Stichprobenmethode "Anzahl erste Daten" mit einer Stichprobenanzahl von 5000 verwendet, Sie können diese Einstellungen jedoch ändern.|[Durchsuchen von Daten in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/explore-data-in-a-data-source-view-analysis-services.md)|  
|Grafische Darstellung aller oder einer Teilmenge der Tabellen und Beziehungen in einer Datenquellensicht|[Verwenden von Diagrammen im Datenquellensicht-Designer &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellsichten in mehrdimensionalen Modellen](multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Hinzufügen oder Entfernen von Tabellen oder Sichten in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)  
  
  
