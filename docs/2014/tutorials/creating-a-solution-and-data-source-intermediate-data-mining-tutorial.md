---
title: Erstellen einer Projekt Mappe und einer Datenquelle (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0488b231-1045-4169-aabb-c1005d86ca30
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 21bedc825f5890e3eb6551818dc5dc10724d2bf8
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68891440"
---
# <a name="creating-a-solution-and-data-source-intermediate-data-mining-tutorial"></a>Erstellen einer Projektmappe und einer Datenquelle (Data Mining-Lernprogramm für Fortgeschrittene)
  Um mit Data Mining zu arbeiten, müssen Sie zunächst mit der Vorlage für multidimensionale Projekte bzw. Data Mining-Projekte von Analysis Services [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] **ein Projekt in**erstellen. Wenn Sie die Vorlage öffnen, werden alle Schemas in den Designer geladen, die Sie möglicherweise für Data Mining benötigen: Datenquellen, Miningstrukturen und Miningmodelle und sogar Cubes, wenn die Miningstruktur mehrdimensionale Daten verwendet.  
  
 Wenn Sie das Projekt erstellen, wird Ihre Lösung bis zur Bereitstellung als lokale Datei gespeichert. Wenn Sie die Lösung bereitstellen, sucht [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nach dem in den Projekteigenschaften angegebenen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Server und erstellt eine neue [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank mit dem gleichen Namen wie das Projekt. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet standardmäßig die **localhost** -Instanz für neue Projekte. Wenn Sie eine benannte Instanz verwenden oder einen anderen Namen für die Standardinstanz angegeben haben, müssen Sie für die Eigenschaft der Bereitstellungsdatenbank des Projekts den Speicherort angeben, an dem Data Mining-Objekte erstellt werden sollen.  
  
 Weitere Informationen zu [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekten finden Sie unter [Erstellen eines Analysis Services &#40;Project SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt).  
  
### <a name="to-create-a-new-analysis-services-project-for-this-tutorial"></a>So erstellen Sie ein neues Analysis Services-Projekt für dieses Lernprogramm  
  
1.  Öffnen Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Wählen Sie die Vorlage für multidimensionale Projekte bzw. **Data Mining-Projekte von Analysis Services** aus dem Bereich **Installierte Vorlagen** aus.  
  
4.  Geben Sie im Feld **Name** den Namen **DM Intermediate**für das neue Projekt ein.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored-optional"></a>So ändern Sie die Instanz, in der Data Mining-Objekte gespeichert werden (optional)  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf der linken Seite des Bereichs **Eigenschaftenseiten** auf **Bereitstellung**.  
  
3.  Überprüfen Sie, dass als **Servername** der Name **localhost**verwendet wird. Wenn Sie eine andere Instanz verwenden, geben Sie den Namen der Instanz ein. Wenn Sie eine benannte Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]verwenden, geben Sie den Computernamen und dann den Namen der Instanz ein. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-deployment-properties-for-a-project-optional"></a>So ändern Sie die Bereitstellungseigenschaften für ein Projekt (optional)  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt und klicken Sie dann auf **Eigenschaften**.  
  
     – oder –  
  
     Wählen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im Menü **Projekt** den Befehl **Eigenschaften**aus.  
  
2.  Klicken Sie auf der linken Seite des Bereichs **Eigenschaftenseiten** auf **Bereitstellung**.  
  
     Wählen Sie im Bereich **Optionen** den **Bereitstellungsmodus**aus. Wählen Sie **Alle Objekte bereitstellen** aus, um Objekte zu überschreiben, oder wählen Sie **Nur geänderte Objekte bereitstellen** aus, um Objekte zu aktualisieren oder neue Objekte hinzuzufügen.  
  
## <a name="creating-a-data-source"></a>Erstellen einer Datenquelle  
 Im Lernprogramm zu Data Mining-Grundlagen haben Sie eine *Datenquelle* zur Speicherung der Verbindungsinformationen für die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank erstellt. Führen Sie die gleichen Schritte aus, um die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenquelle in dieser Lösung zu erstellen.  
  
#### <a name="to-create-a-data-source"></a>So erstellen Sie eine Datenquelle  
  
-   [Erstellen eines Lernprogramms &#40;zu Data Mining-Grundlagen&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 Eine Datenquelle kann mehrere Datenquellensichten unterstützten und die einzelnen Datenquellensichten können mehrere Tabellen aufweisen. Da die Datenquelle und die Datenquellensicht jedoch für die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank zusammen mit den von Ihnen erstellten Data Mining-Modellen bereitgestellt werden, wird empfohlen, nur die Tabellen in die Datenquellensicht aufzunehmen, die für das jeweilige Data Mining-Modell oder die entsprechende Gruppe von Modellen erforderlich sind.  
  
 In den folgenden Lektionen fügen Sie Datenquellensichten zur Unterstützung jedes neuen Szenarios hinzu. Nur in der Market Basket- und der Sequenzcluster-Lektion wird die gleiche Datenquellensicht verwendet. Sonst wird für jedes Szenario eine andere Datenquellensicht verwendet, sodass die Lektionen keine weiteren Gemeinsamkeiten aufweisen und unabhängig voneinander abgeschlossen werden können.  
  
|Szenario|In der Datenquellensicht enthaltene Daten|  
|--------------|-------------------------------------------|  
|[Lektion 2: Aufbauen eines Data Mining &#40;-Lernprogramms für Vorhersage Szenarios&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)|Monatliche Verkaufsberichte für Fahrradmodelle in unterschiedlichen Regionen (als einzelne Sicht gesammelt).|  
|[Lektion 3: Tutorial zum Aufbauen eines Market &#40;Basket-Szenarios mit Data Mining&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)|Eine Tabelle, die eine Liste mit Kundenaufträgen und eine geschachtelte Tabelle, in der die einzelnen Käufe für jeden Kunden angezeigt werden, enthält.|  
|[Lektion 4: Tutorial zum Entwickeln eines Sequence Clustering-Szenarios &#40;zwischen Data Mining&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)|Die gleichen Daten, die für die Warenkorbanalyse verwendet werden, sowie ein Bezeichner, der die Reihenfolge anzeigt, in der Elemente gekauft wurden.|  
|[Lesson 5: Tutorial zum Entwickeln von neuronalen Netz &#40;Werken und logistischen Regressionsmodellen&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)|Eine einzelne Tabelle, die vorläufige Nachverfolgungsdaten für die Leistung in einem Callcenter enthält.|  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Aufbauen eines Data Mining &#40;-Lernprogramms für Vorhersage Szenarios&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Projekte](../../2014/analysis-services/data-mining/data-mining-projects.md)   
 [Datenquellsichten in mehrdimensionalen Modellen](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
