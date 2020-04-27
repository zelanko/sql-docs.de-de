---
title: Anwenden eines Filters auf ein Mining Modell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filters [data mining]
- filtering input rows [Analysis Services]
- filtering data [Analysis Services]
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0370d4fceada5c0a287c4a071691ea20d5a28f6c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66086220"
---
# <a name="apply-a-filter-to-a-mining-model"></a>Anwenden eines Filters auf ein Miningmodell
  Wenn Ihre Miningstruktur eine geschachtelte Tabelle enthält, können Sie einen Filter auf die Falltabelle und/oder die geschachtelte Tabelle anwenden.  
  
 Die folgende Vorgehensweise veranschaulicht das Erstellen beider Filterarten: Fallfilter und Filter in den Zeilen der geschachtelten Tabelle.  
  
 Die Bedingung in der Falltabelle schränkt Kunden auf Kunden mit einem Einkommen zwischen 30000 und 40000 ein. Die Bedingung in der geschachtelten Tabelle schränkt die Kunden auf Kunden ein, die einen bestimmten Artikel nicht gekauft haben.  
  
 Die vollständige in diesem Beispiel erstellte Filterbedingung lautet wie folgt:  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### <a name="to-create-a-case-filter-on-a-mining-model"></a>So erstellen Sie einen Fallfilter für ein Miningmodell  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Projektmappen-Explorer auf die Miningstruktur, die das Miningmodell enthält, auf das Sie einen Filter anwenden möchten.  
  
2.  Klicken Sie auf die Registerkarte **Miningmodelle** .  
  
3.  Wählen Sie das Modell aus, und klicken Sie mit der rechten Maustaste, um das Kontextmenü zu öffnen.  
  
     - oder -  
  
     Wählen Sie das Modell aus. Wählen Sie dann im Menü **Miningmodell** die Funktion **Modellfilter festlegen**aus.  
  
4.  Klicken Sie im Dialogfeld **Modellfilter** im Textfeld **Miningstrukturspalte** auf die oberste Zeile im Raster.  
  
5.  Wenn die Datenquelle eine einzelne flache Tabelle enthält, zeigt die Dropdown-Liste nur die Namen der Spalten in dieser Tabelle an.  
  
     Wenn die Miningstruktur mehrere Tabellen enthält, zeigt die Liste die Namen der Quelltabellen an. Die Spaltennamen werden nur angezeigt, wenn eine Tabelle ausgewählt wurde.  
  
     Wenn die Miningstruktur eine Falltabelle und eine geschachtelte Tabelle enthält, werden in der Dropdown-Liste Spalten aus der Falltabelle sowie der Name der geschachtelten Tabelle angezeigt.  
  
6.  Wählen Sie eine Spalte aus der Dropdownliste aus.  
  
     Das Symbol auf der linken Seite des Textfelds ändert sich und gibt dadurch an, dass es sich beim ausgewählten Element um eine Tabelle oder eine Spalte handelt.  
  
7.  Klicken Sie auf das Textfeld **Operator** , und wählen Sie einen Operator aus der Liste aus. Die gültigen Operatoren hängen vom Datentyp der Spalte ab, die Sie ausgewählt haben.  
  
8.  Klicken Sie auf das Textfeld **Wert** , und geben Sie einen Wert ein.  
  
     Wählen Sie `Income` z. b. als Spalte aus, wählen Sie den Operator "größer als" (> `30000`) aus, und geben Sie dann ein.  
  
9. Klicken Sie auf die nächste Zeile im Raster.  
  
     Die erstellte Filterbedingung wird automatisch zum Textfeld Ausdruck hinzugefügt. Beispiel: `[Income] > '30000'`  
  
10. Klicken Sie in der nächsten Zeile des Rasters auf das Textfeld **AND/OR** , um eine Bedingung hinzuzufügen.  
  
     Um z. b. eine between-Bedingung zu `AND` erstellen, wählen Sie aus der Dropdown Liste der logischen Operanden aus.  
  
11. Wählen Sie einen Operator aus, und geben Sie einen Wert ein, wie in Schritt 7 und 8 beschrieben.  
  
     Wählen Sie `Income` z. b. erneut als Spalte aus, wählen Sie den Operator kleiner als (<) aus `40000`, und geben Sie dann ein.  
  
12. Klicken Sie auf die nächste Zeile im Raster.  
  
13. Die Filterbedingung im Textfeld Ausdruck wird automatisch aktualisiert, um die neue Bedingung einzuschließen. Der vollständige Ausdruck lautet wie folgt: `[Income] > '30000'AND [Income] < '40000'`  
  
### <a name="to-add-a-filter-on-the-nested-table-in-a-mining-model"></a>So fügen Sie einen Filter in der geschachtelten Tabelle in einem Miningmodell hinzu  
  
1.  Klicken Sie im Dialog Feld ** \<Name>Modell Filter** auf eine leere Zeile im Raster unter **Mining Struktur Spalte**.  
  
2.  Wählen Sie den Namen der geschachtelten Tabelle aus der Dropdown-Liste aus.  
  
     Das Symbol auf der linken Seite des Textfelds ändert sich und gibt dadurch an, dass es sich beim ausgewählten Element um den Namen einer Tabelle handelt.  
  
3.  Klicken Sie auf das Textfeld **Operator** , und wählen Sie **Enthält** oder **Enthält nicht**aus.  
  
     Dies sind die einzigen Bedingungen, die für die geschachtelte Tabelle im Dialogfeld **Modellfilter** verfügbar sind, da Sie die Falltabelle auf die Fälle einschränken, die einen bestimmten Wert in der verschachtelten Tabelle enthalten. Den Wert für die Bedingung in der geschachtelten Tabelle legen Sie im nächsten Schritt fest.  
  
4.  Klicken Sie auf das Feld **Wert** , und klicken Sie dann auf die Schaltfläche **(...)** , um einen Ausdruck zu erstellen.  
  
     Das Dialogfeld ** \<Name>Filter** wird geöffnet. Dieses Dialogfeld kann Bedingungen nur für die aktuelle Tabelle festlegen. In diesem Fall ist dies die geschachtelte Tabelle.  
  
5.  Klicken Sie auf das Feld **Miningstrukturspalte** , und wählen Sie einen Spaltennamen aus den Dropdown-Listen der Spalten der verschachtelten Tabelle aus.  
  
6.  Klicken Sie auf **Operator** , und wählen Sie einen Operator aus der Liste der gültigen Operatoren für die Spalte aus.  
  
7.  Klicken Sie auf **Wert** , und geben Sie einen Wert ein.  
  
     Wählen Sie `Model`z. b. für **Mining Struktur Spalte** die Option aus. Wählen **Operator**Sie für Operator `<>`die Option aus, und `Water Bottle`geben Sie den Wert ein. Diese Bedingung erstellt den folgenden Filterausdruck:  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  Da die Anzahl der Attribute für eine geschachtelte Tabelle praktisch unbegrenzt ist, stellt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] keine Liste mit möglichen Werten zur Auswahl bereit. Sie müssen den genauen Wert eingeben. Außerdem können Sie in einer geschachtelten Tabelle keinen LIKE-Operator verwenden.  
  
1.  Fügen Sie nach Bedarf weitere Bedingungen hinzu, und kombinieren `AND` Sie `OR` die Bedingungen, indem Sie oder im Feld **und/oder** auf der linken Seite des Rasters **Bedingungen** auswählen. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  Prüfen Sie im Dialogfeld **Modellfilter** die von Ihnen erstellten Bedingungen mithilfe des Dialogfelds **Filter** . Die Bedingungen für die geschachtelte Tabelle werden den Bedingungen für die Falltabelle hinzugefügt. Der gesamte Satz der Filterbedingungen wird im Textfeld **Ausdruck** angezeigt.  
  
3.  Sie können optional auf **Abfrage bearbeiten** klicken, um den Filterausdruck manuell zu ändern.  
  
    > [!NOTE]  
    >  Wenn Sie einen Teil eines Filterausdrucks manuell ändern, wird das Raster deaktiviert. Anschließend müssen Sie mit dem Filterausdruck im Textbearbeitungsmodus arbeiten. Um den Rasterbearbeitungsmodus wiederherzustellen, müssen Sie den Filterausdruck löschen und von Neuem beginnen.  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filter für Mining Modelle &#40;Analysis Services Data Mining-&#41;](mining-models-analysis-services-data-mining.md)   
 [Mining Modell Tasks und Anleitungen](mining-model-tasks-and-how-tos.md)   
 [Löschen eines Filters aus einem Miningmodell](delete-a-filter-from-a-mining-model.md)  
  
  
