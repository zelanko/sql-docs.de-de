---
title: Filtern einer geschachtelten Tabelle in einem Miningmodell (Datamining-Lernprogramm für fortgeschrittene) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9b11971c6e6005c7e1d65a1728e8b8aac818b41c
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312318"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a>Filtern einer geschachtelten Tabelle in einem Miningmodell (Data Mining-Lernprogramm für Fortgeschrittene)
  Nachdem Sie das Modell erstellt und sich damit vertraut gemacht haben, möchten Sie sich mit einer Teilmenge der Kundendaten näher beschäftigen. Dazu können Sie beispielsweise nur die Einkaufskörbe betrachten, die ein bestimmtes Element enthalten, oder die demografischen Daten von Kunden analysieren, die über einen bestimmten Zeitraum keine Einkäufe getätigt haben.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet die Möglichkeit, die in einem Miningmodell verwendeten Daten zu filtern. Diese Funktion ist nützlich, da Sie nicht benötigen, um eine neue Datenquellensicht einrichten, um andere Daten verwenden. Im Lernprogramm zu Data Mining-Grundlagen haben Sie gelernt, Daten in einer flachen Tabelle anhand von Bedingungen für die Falltabelle zu filtern. In dieser Aufgabe erstellen Sie einen Filter für eine geschachtelte Tabelle.  
  
## <a name="filters-on-nested-vs-case-tables"></a>Filter für geschachtelte Tabellen und Filter für Falltabellen  
 Wenn die Datenquellenansicht wie im Modell Association eine Falltabelle und eine geschachtelte Tabelle enthält, können Sie einen Filter für Werte in der Falltabelle, einen Filter für vorhandene oder nicht vorhandene Werte in der geschachtelten Tabelle oder eine Kombination aus beiden verwenden.  
  
 In dieser Aufgabe erstellen Sie zunächst eine Kopie des Modells Association und fügen die Attribute IncomeGroup und Region hinzu, um diese später als Filterkriterien für die Falltabelle verwenden zu können.  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a>So erstellen und ändern Sie eine Kopie des Modells Association  
  
1.  In der **Miningmodelle** Registerkarte [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], mit der rechten Maustaste die `Association` Modell, und wählen **Neues Miningmodell**.  
  
2.  Für **Modellname**, Typ `Association Filtered`. Für **Algorithmusname**Option **Microsoft Association Rules**. Klicken Sie auf **OK**.  
  
3.  Klicken Sie in der Spalte für das Modell Association Filtered, klicken Sie auf die Zeile IncomeGroup, und ändern Sie den Wert von **ignorieren** auf **Eingabe**.  
  
 Anschließend erstellen Sie einen Filter für die Falltabelle im neuen Association-Modell. Durch den Filter werden nur Kunden in der Zielregion oder Kunden mit einem Einkommensniveau entsprechend den Kriterien im Modell verwendet. Nun fügen Sie eine weitere Reihe von Filterbedingungen hinzu, um anzugeben, dass nur Kunden im Modell berücksichtigt werden sollen, in deren Einkaufskorb sich mindestens ein Element befindet.  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a>So fügen Sie einem Miningmodell einen Filter hinzu  
  
1.  In der **Miningmodelle** , mit der rechten Maustaste in des Modells Association Filtered, und wählen Sie **Modellfilter festlegen**.  
  
2.  Klicken Sie im Dialogfeld **Modellfilter** im Textfeld **Miningstrukturspalte** auf die oberste Zeile im Raster.  
  
3.  In der **Miningstrukturspalte** Textfeld select IncomeGroup.  
  
     Das Symbol auf der linken Seite des Textfelds ändert sich und gibt dadurch an, dass es sich beim ausgewählten Element um eine Spalte handelt.  
  
4.  Klicken Sie auf die **Operator** Textfeld und wählen Sie die **=** Operator aus der Liste.  
  
5.  Klicken Sie auf die **Wert** Textfeld, und geben `High` in das Feld.  
  
6.  Klicken Sie auf die nächste Zeile im Raster.  
  
7.  Klicken Sie auf die **und/oder** Textfeld in der nächsten Zeile des Rasters, und wählen **oder**.  
  
8.  In der **Miningstrukturspalte** Textfeld select IncomeGroup. In der **Wert** Textfeld `Moderate`.  
  
     Die erstellte filterbedingung wird automatisch hinzugefügt, die **Ausdruck** Textfeld, und sollte wie folgt angezeigt:  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. Klicken Sie auf die nächste Zeile im Raster, verlassen den Standardoperator, **AND**.  
  
10. Für **Operator**, behalten Sie den Standardwert **Contains**. Klicken Sie auf die **Wert** Textfeld.  
  
11. In der **Filter** (Dialogfeld), in der ersten Zeile unter **Miningstrukturspalte**Option `Model`.  
  
12. Für **Operator**Option **IS NOT NULL**. Lassen Sie die **Wert** Textfeld leer. Klicken Sie auf **OK**.  
  
     Die filterbedingung in die **Ausdruck** Textfeld mit der die **Modellfilter** Dialogfeld wird automatisch aktualisiert, um die neue Bedingung für die geschachtelte Tabelle einzuschließen. Der vollständige Ausdruck lautet wie folgt:  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a>So aktivieren Sie Drillthrough und verarbeiten das gefilterte Modell  
  
1.  In der **Miningmodelle** Registerkarte der rechten Maustaste auf die `Association Filtered` Modell, und wählen **Eigenschaften**.  
  
2.  Ändern der **AllowDrillThrough** Eigenschaft **"true"**.  
  
3.  Mit der rechten Maustaste die `Association Filtered` mining-Modell, und wählen Sie **Prozessmodell**.  
  
4.  Klicken Sie auf **Ja** in der Fehlermeldung, um das neue Modell zum Bereitstellen der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenbank.  
  
5.  In der **Miningstruktur verarbeiten** (Dialogfeld), klicken Sie auf **ausführen**.  
  
6.  Nach Abschluss der Verarbeitung klicken Sie auf **schließen** zum Beenden der **Verarbeitungsstatus** (Dialogfeld), und klicken Sie auf **schließen** wieder zu schließen die **Miningstruktur verarbeiten**  (Dialogfeld).  
  
 Im Microsoft Generic Content Tree Viewer können Sie anhand des Werts für NODE_SUPPORT feststellen, dass das gefilterte Modell weniger Fälle als das ursprüngliche Modell enthält.  
  
## <a name="remarks"></a>Hinweise  
 Mit dem Filter für eine geschachtelte Tabelle, den Sie gerade erstellt haben, wird nur überprüft, ob mindestens eine Zeile in der geschachtelten Tabelle enthalten ist. Sie können jedoch Filterbedingungen erstellen, mit denen das Vorhandensein bestimmter Produkte überprüft wird.  Beispielsweise können Sie folgenden Filter erstellen:  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 Diese Anweisung bewirkt, dass die Kunden in der Falltabelle auf Kunden eingeschränkt werden, die eine Flasche Wasser gekauft haben. Da die Anzahl der Attribute für eine geschachtelte Tabelle jedoch praktisch unbegrenzt ist, stellt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] keine Liste mit möglichen Werten zur Auswahl bereit. Sie müssen stattdessen den genauen Wert eingeben.  
  
 Klicken Sie auf **Abfrage bearbeiten** um den Filterausdruck manuell zu ändern. Wenn Sie jedoch einen Teil eines Filterausdrucks manuell ändern, wird das Raster deaktiviert, und anschließend müssen Sie mit dem Filterausdruck im Textbearbeitungsmodus arbeiten. Um den Rasterbearbeitungsmodus wiederherzustellen, müssen Sie den Filterausdruck löschen und von Neuem beginnen.  
  
> [!WARNING]  
>  In einem Filter für geschachtelte Tabellen kann kein LIKE-Operator verwendet werden.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Vorhersagen von Zuordnungen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Modellfiltersyntax und Beispiele für &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)   
 [Filter für Miningmodelle &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  