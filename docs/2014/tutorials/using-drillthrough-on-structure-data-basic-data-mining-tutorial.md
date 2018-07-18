---
title: Verwenden von Drillthrough für Strukturdaten (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec32e6f46f63c6de342b6b4cab63bb8e6556bfb8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198350"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a>Verwenden von Drillthrough für Strukturdaten (Lernprogramm zu Data Mining-Grundlagen)
  Als Teil des Werbekampagne [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] sendet einen Prospekt an potenziellen Kunden im Alter von 34 bis 40 Jahren demografische. Die marketingabteilung hat beschlossen, dass sie auch das Adressfeld für den Kunden zu senden, die Fahrräder von gekauft haben möchten [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] vor mehr als fünf Jahren. In dieser Lektion identifizieren Sie Kunden mit älteren Fahrrädern und rufen ihre Kontaktinformationen ab. Diese Informationen sind nicht im Modell, sondern in der Struktur enthalten. Stellen Sie zunächst sicher, dass die Drillthroughfunktion für die Struktur aktiviert ist, um die Kontaktinformationen abzurufen. Rufen Sie dann die Namen und Adressen der Kundenzielgruppe ab, indem Sie einen Drillthrough ausführen.  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>So aktivieren Sie Drillthrough für ein Miningmodell  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf die **Miningmodelle** Registerkarte Data Mining-Designer, Informationen zu diesem mit der rechten Maustaste die **TM_Decision_Tree** Modell, und wählen **Eigenschaften**.  
  
2.  Klicken Sie im Eigenschaftenfenster auf **AllowDrillthrough**, und wählen Sie **True**aus.  
  
3.  Klicken Sie auf der Registerkarte **Miningmodelle**mit der rechten Maustaste auf das Modell, und wählen Sie Modell verarbeiten aus.  
  
 Weitere Informationen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>So zeigen Sie Drillthroughdaten von einem Miningmodell an  
  
1.  Klicken Sie im Data Mining-Designer auf die Registerkarte **Miningmodell-Viewer** .  
  
2.  Wählen Sie das **TM_Decision_Tree** -Modell aus der Liste **Miningmodell** aus.  
  
3.  Ändern der **Hintergrund** Wert `1`. Auf diese Weise zeigen Sie nur den Teil des Modells an, der sich auf Kunden bezieht, die Fahrräder gekauft haben.  
  
4.  Wählen Sie den Microsoft Struktur-Viewer aus der Liste **Viewer** aus. Dadurch wird eine Aktualisierung des Viewers mit den neuen Filterbedingungen erzwungen. Suchen Sie anschließend die **Age > = 34 und < 41** Knoten und mit der rechten Maustaste den Knoten.  
  
5.  Wählen Sie **Drillthrough**und anschließend **Modell- und Strukturspalten** aus, um das Fenster **Drillthrough** zu öffnen.  
  
6.  Führen Sie einen Bildlauf zur Spalte **Structure.Date First Purchase** durch, um die Kaufdaten für die älteren Fahrräder anzuzeigen.  
  
7.  Um die Daten in die Zwischenablage zu kopieren, klicken Sie mit der rechten Maustaste auf eine beliebige Zeile in der Tabelle, und wählen Sie **Alle kopieren**.  
  
 Gratulation – Sie haben das Lernprogramm zu Data Mining-Grundlagen abgeschlossen. Nachdem Sie sich mit der Verwendung der Data Mining-Tools vertraut gemacht haben, wird empfohlen, das Data Mining-Lernprogramm für Fortgeschrittene zu absolvieren. Darin wird das Erstellen von Modellen für Vorhersagen, Market Basket-Analysen und Sequenzcluster veranschaulicht.  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Erstellen von Vorhersagen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Vorhersageabfragen mithilfe des Generators für Vorhersageabfragen](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
