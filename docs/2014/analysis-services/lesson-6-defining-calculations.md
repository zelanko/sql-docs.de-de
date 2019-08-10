---
title: 'Lektion 6: Definieren von Berechnungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e0a1e354-e879-4eb8-bb2b-6c3809e32cb6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fcfa51678379ecf7f54a956db17089544b22f6be
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68888047"
---
# <a name="lesson-6-defining-calculations"></a>Lektion 6: Definieren von Berechnungen
  In dieser Lektion erfahren Sie, wie Berechnungen definiert werden, bei denen es sich um MDX-Ausdrücke oder -Skripts (Multidimensional Expressions) handelt. Berechnungen ermöglichen es Ihnen, berechnete Elemente und benannte Mengen zu definieren und weitere Skriptbefehle auszuführen, um die Fähigkeiten eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Cubes zu erweitern. Sie können z. B. einen Skriptbefehl ausführen, um einen Teilcube zu definieren und dann den Zellen im Teilcube eine Berechnung zuordnen.  
  
 Wenn Sie eine neue Berechnung im Cube-Designer definieren, wird die Berechnung dem Bereich **Skriptplaner** der Registerkarte **Berechnungen** im Cube-Designer hinzugefügt, und die Felder für den jeweiligen Berechnungstyp werden in einem Berechnungsformular im Bereich **Berechnungsausdrücke** angezeigt. Berechnungen werden in der Reihenfolge ausgeführt, in der sie im Bereich **Skriptplaner** aufgelistet sind. Durch Klicken mit der rechten Maustaste auf eine bestimmte Berechnung und Auswählen von **Nach oben** oder **Nach unten**oder durch Klicken auf eine bestimmte Berechnung und Verwenden der Symbole **Nach oben** oder **Nach unten** auf der Symbolleiste der Registerkarte **Berechnungen** können Sie die Reihenfolge der Berechnungen ändern.  
  
 Auf der Registerkarte **Berechnungen** können Sie neue Berechnungen hinzufügen und anzeigen oder vorhandene Berechnungen in einer der folgenden Ansichten im Bereich **Berechnungsausdrücke** bearbeiten:  
  
-   Formularansicht. In dieser Ansicht werden die Ausdrücke und Eigenschaften eines einzelnen Befehls in einem Grafikformat angezeigt. Beim Bearbeiten eines MDX-Skripts wird in der Formularansicht ein Ausdrucksfeld angezeigt.  
  
-   Skriptansicht. In dieser Ansicht werden alle Berechnungsskripts in einem Code-Editor angezeigt, mit dem Sie die Berechnungsskripts problemlos ändern können. Wird der Bereich **Berechnungsausdrücke** in der Skriptansicht angezeigt, ist der **Skriptplaner** ausgeblendet. In der Skriptansicht stehen Farbcodierung, Vervollständigen von Klammern, automatische Vervollständigung und MDX-Codebereiche zur Verfügung. Zur einfacheren Bearbeitung der MDX-Codebereiche können diese erweitert oder reduziert werden.  
  
 Wenn Sie zwischen diesen Ansichten im Bereich **Berechnungsausdrücke** wechseln möchten, klicken Sie auf der Symbolleiste der Registerkarte **Berechnungen** auf **Formularansicht** oder **Skriptansicht** .  
  
> [!NOTE]  
>  Wird von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ein Syntaxfehler in einer Berechnung erkannt, wird die Formularansicht erst dann wieder angezeigt, wenn der Fehler in der Skriptansicht behoben wurde.  
  
 Sie können auch den Business Intelligence-Assistenten verwenden, um einem Cube bestimmte Berechnungen hinzuzufügen. Mithilfe des Assistenten können Sie beispielsweise einem Cube Zeitintelligenz hinzufügen, indem Sie berechnete Elemente für zeitgestützte Berechnungen definieren, wie z. B. Zeitraum bis Datum, gleitender Durchschnitt oder zeitraumbasiertes Wachstum. Weitere Informationen finden Sie unter [Definieren von Zeitintelligenzberechnungen mithilfe des Business Intelligence-Assistenten](multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).  
  
> [!IMPORTANT]  
>  Auf der Registerkarte **Berechnungen** beginnt das Berechnungsskript mit dem CALCULATE-Befehl. Über den CALCULATE-Befehl wird die Aggregation der Zellen im Cube gesteuert; Sie sollten diesen Befehl nur bearbeiten, wenn Sie die Aggregation der Cubezellen manuell angeben möchten.  
  
 Weitere Informationen finden Sie unter [Berechnungen](multidimensional-models-olap-logical-cube-objects/calculations.md)und [Berechnungen in mehrdimensionalen Modellen](multidimensional-models/calculations-in-multidimensional-models.md).  
  
> [!NOTE]  
>  Für alle Lektionen in diesem Lernprogramm sind abgeschlossene Projekte online verfügbar. Sie können jede Lektion aufrufen, indem Sie ein abgeschlossenes Projekt aus der vorherigen Lektion als Ausgangspunkt verwenden. [Klicken Sie hier](https://go.microsoft.com/fwlink/?LinkID=221866) , um die Beispielprojekte für dieses Lernprogramm herunterzuladen.  
  
 Diese Lektion enthält die folgenden Aufgaben:  
  
 [Definieren berechneter Elemente](https://docs.microsoft.com/analysis-services/lesson-6-1-defining-calculated-members)  
 In dieser Aufgabe erfahren Sie, wie berechnete Elemente definiert werden.  
  
 [Definieren von benannten Mengen](https://docs.microsoft.com/analysis-services/lesson-6-2-defining-named-sets)  
 In diesem Task erfahren Sie, wie benannte Mengen definiert werden.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 7: Definieren von &#40;KPIs für Key Performance Indicator&#41;](https://docs.microsoft.com/analysis-services/lesson-7-defining-key-performance-indicators-kpis)  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Tutorial-Szenario](https://docs.microsoft.com/analysis-services/analysis-services-tutorial-scenario)   
 [Tutorial zur &#40;mehrdimensionalen Modellierung von Adventure Works&#41;](https://docs.microsoft.com/analysis-services/multidimensional-modeling-adventure-works-tutorial)   
 [Benannte Mengen erstellen](multidimensional-models/create-named-sets.md)   
 [Erstellen von berechneten Elementen](multidimensional-models/create-calculated-members.md)  
  
  
