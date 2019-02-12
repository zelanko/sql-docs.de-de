---
title: Verwenden von Drillthrough für Strukturdaten (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 68d5d29a4aed7380bd7a53c65d140aac24912392
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012761"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a>Verwenden von Drillthrough für Strukturdaten (Lernprogramm zu Data Mining-Grundlagen)
  Im Rahmen einer Werbekampagne sendet [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] einen Prospekt an alle potenziellen Kunden im Alter von 34 bis 40 Jahren. Der gleiche Prospekt soll auf Wunsch der Marketingabteilung auch an Kunden gesendet werden, die vor mehr als fünf Jahren ein Fahrrad von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] gekauft haben. In dieser Lektion identifizieren Sie Kunden mit älteren Fahrrädern und rufen ihre Kontaktinformationen ab. Diese Informationen sind nicht im Modell, sondern in der Struktur enthalten. Stellen Sie zunächst sicher, dass die Drillthroughfunktion für die Struktur aktiviert ist, um die Kontaktinformationen abzurufen. Rufen Sie dann die Namen und Adressen der Kundenzielgruppe ab, indem Sie einen Drillthrough ausführen.  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>So aktivieren Sie Drillthrough für ein Miningmodell  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im Data Mining-Designer auf der Registerkarte **Miningmodelle** mit der rechten Maustaste auf das **TM_Decision_Tree** -Modell, und wählen Sie **Eigenschaften**aus.  
  
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
 [Erstellen von Vorhersagen &#40;Tutorial zu Data Mining-Grundlagen&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Vorhersageabfragen mithilfe des Generators für Vorhersageabfragen](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
