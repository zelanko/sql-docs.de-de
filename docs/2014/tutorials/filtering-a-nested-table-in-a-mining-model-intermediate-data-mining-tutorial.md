---
title: Filtern einer geclusterte Tabelle in einem Mining Modell (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f57d691587d658e968cd79cf4f4ab4731db29915
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63267480"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a>Filtern einer geschachtelten Tabelle in einem Miningmodell (Data Mining-Lernprogramm für Fortgeschrittene)
  Nachdem Sie das Modell erstellt und sich damit vertraut gemacht haben, möchten Sie sich mit einer Teilmenge der Kundendaten näher beschäftigen. Dazu können Sie beispielsweise nur die Einkaufskörbe betrachten, die ein bestimmtes Element enthalten, oder die demografischen Daten von Kunden analysieren, die über einen bestimmten Zeitraum keine Einkäufe getätigt haben.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet die Möglichkeit, die in einem Miningmodell verwendeten Daten zu filtern. Diese Funktion ist nützlich, da Sie keine neue Datenquellen Sicht einrichten müssen, um unterschiedliche Daten zu verwenden. Im Lernprogramm zu Data Mining-Grundlagen haben Sie gelernt, Daten in einer flachen Tabelle anhand von Bedingungen für die Falltabelle zu filtern. In dieser Aufgabe erstellen Sie einen Filter für eine geschachtelte Tabelle.  
  
## <a name="filters-on-nested-vs-case-tables"></a>Filter für geschachtelte Tabellen und Filter für Falltabellen  
 Wenn die Datenquellenansicht wie im Modell Association eine Falltabelle und eine geschachtelte Tabelle enthält, können Sie einen Filter für Werte in der Falltabelle, einen Filter für vorhandene oder nicht vorhandene Werte in der geschachtelten Tabelle oder eine Kombination aus beiden verwenden.  
  
 In dieser Aufgabe erstellen Sie zunächst eine Kopie des Modells Association und fügen die Attribute IncomeGroup und Region hinzu, um diese später als Filterkriterien für die Falltabelle verwenden zu können.  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a>So erstellen und ändern Sie eine Kopie des Modells Association  
  
1.  Klicken Sie in der Registerkarte [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] **Mining Modelle** mit der rechten `Association` Maustaste auf das Modell, und wählen Sie **Neues Mining Modell**aus.  
  
2.  Geben `Association Filtered`Sie unter **Modell Name den Namen**ein. Wählen Sie unter **Algorithmusname**die Option **Microsoft Association Rules**aus. Klicken Sie auf **OK**.  
  
3.  Klicken Sie in der Spalte für das gefilterte Assoziations Modell auf die Zeile IncomeGroup, und ändern Sie den Wert von **ignorieren** in **Eingabe**.  
  
 Anschließend erstellen Sie einen Filter für die Falltabelle im neuen Association-Modell. Durch den Filter werden nur Kunden in der Zielregion oder Kunden mit einem Einkommensniveau entsprechend den Kriterien im Modell verwendet. Nun fügen Sie eine weitere Reihe von Filterbedingungen hinzu, um anzugeben, dass nur Kunden im Modell berücksichtigt werden sollen, in deren Einkaufskorb sich mindestens ein Element befindet.  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a>So fügen Sie einem Miningmodell einen Filter hinzu  
  
1.  Klicken Sie auf der Registerkarte **Mining Modelle** mit der rechten Maustaste auf die gefilterte Modell Zuordnung, und wählen Sie **Modell Filter festlegen**aus.  
  
2.  Klicken Sie im Dialogfeld **Modellfilter** im Textfeld **Miningstrukturspalte** auf die oberste Zeile im Raster.  
  
3.  Wählen Sie im Textfeld **Mining Struktur Spalte** die Option IncomeGroup aus.  
  
     Das Symbol auf der linken Seite des Textfelds ändert sich und gibt dadurch an, dass es sich beim ausgewählten Element um eine Spalte handelt.  
  
4.  Klicken Sie auf das Textfeld **Operator** , **=** und wählen Sie den Operator aus der Liste aus.  
  
5.  Klicken Sie auf das Textfeld **Wert** , `High` und geben Sie in das Feld ein.  
  
6.  Klicken Sie auf die nächste Zeile im Raster.  
  
7.  Klicken Sie in der nächsten Zeile des Rasters auf das Textfeld **und/oder** , und wählen Sie **oder**aus.  
  
8.  Wählen Sie im Textfeld **Mining Struktur Spalte** die Option IncomeGroup aus. Geben `Moderate`Sie im Textfeld **Wert den Wert** ein.  
  
     Die von Ihnen erstellte Filterbedingung wird automatisch zum Textfeld **Ausdruck** hinzugefügt und sollte wie folgt aussehen:  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. Klicken Sie auf die nächste Zeile im Raster, und belassen Sie den Operator als Standard **und**.  
  
10. Überlassen Sie für **Operator**den Standardwert **enthält**. Klicken Sie auf das Textfeld **Wert** .  
  
11. Wählen Sie `Model`im Dialogfeld **Filter** in der ersten Zeile unter **Mining Struktur Spalte**die Option aus.  
  
12. Wählen Sie für **Operator**den Wert **ist nicht NULL**aus. Lassen Sie das Textfeld **Wert** leer. Klicken Sie auf **OK**.  
  
     Die Filterbedingung im Textfeld **Ausdruck** des Dialog Felds **Modell Filter** wird automatisch aktualisiert, um die neue Bedingung in die geclusterte Tabelle einzubeziehen. Der vollständige Ausdruck lautet wie folgt:  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a>So aktivieren Sie Drillthrough und verarbeiten das gefilterte Modell  
  
1.  Klicken Sie auf der Registerkarte **Mining Modelle** mit der `Association Filtered` rechten Maustaste auf das Modell, und wählen Sie **Eigenschaften**aus.  
  
2.  Ändern Sie die **AllowDrillThrough** -Eigenschaft in **true**.  
  
3.  Klicken Sie mit der `Association Filtered` rechten Maustaste auf das Mining Modell, und wählen Sie **Modell verarbeiten**aus.  
  
4.  Klicken Sie in der Fehlermeldung auf **Ja** , um das neue Modell [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in der Datenbank bereitzustellen.  
  
5.  Klicken Sie im Dialogfeld **Mining Struktur verarbeiten** auf **Ausführen**.  
  
6.  Klicken Sie nach Abschluss der Verarbeitung auf schließen, **um das Dialogfeld Verarbeitungs Status** zu **Schließen** , und klicken Sie erneut auf schließen, um das Dialogfeld **Mining Struktur verarbeiten** zu **Schließen** .  
  
 Im Microsoft Generic Content Tree Viewer können Sie anhand des Werts für NODE_SUPPORT feststellen, dass das gefilterte Modell weniger Fälle als das ursprüngliche Modell enthält.  
  
## <a name="remarks"></a>Hinweise  
 Mit dem Filter für eine geschachtelte Tabelle, den Sie gerade erstellt haben, wird nur überprüft, ob mindestens eine Zeile in der geschachtelten Tabelle enthalten ist. Sie können jedoch Filterbedingungen erstellen, mit denen das Vorhandensein bestimmter Produkte überprüft wird.  Beispielsweise können Sie folgenden Filter erstellen:  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 Diese Anweisung bewirkt, dass die Kunden in der Falltabelle auf Kunden eingeschränkt werden, die eine Flasche Wasser gekauft haben. Da die Anzahl der Attribute für eine geschachtelte Tabelle jedoch praktisch unbegrenzt ist, stellt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] keine Liste mit möglichen Werten zur Auswahl bereit. Sie müssen stattdessen den genauen Wert eingeben.  
  
 Sie können auf **Abfrage bearbeiten** klicken, um den Filter Ausdruck manuell zu ändern. Wenn Sie jedoch einen Teil eines Filterausdrucks manuell ändern, wird das Raster deaktiviert, und anschließend müssen Sie mit dem Filterausdruck im Textbearbeitungsmodus arbeiten. Um den Rasterbearbeitungsmodus wiederherzustellen, müssen Sie den Filterausdruck löschen und von Neuem beginnen.  
  
> [!WARNING]  
>  In einem Filter für geschachtelte Tabellen kann kein LIKE-Operator verwendet werden.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Vorhersagen von Zuordnungen &#40;Data&#41;Mining-Lernprogramms](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Modell Filter Syntax und Beispiele &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)   
 [Filter für Miningmodelle &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
