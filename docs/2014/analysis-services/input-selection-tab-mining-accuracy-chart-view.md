---
title: Eingabeauswahl (Registerkarte) (Mining Genauigkeits Diagramm Sicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.columnmapping.f1
ms.assetid: f8b1193c-5c86-4c7e-8e35-158d293184fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4331773f9c80fee37de1c145beeafd37cee2466d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544152"
---
# <a name="input-selection-tab-mining-accuracy-chart-view"></a>Eingabeauswahl (Registerkarte, Mininggenauigkeitsdiagramm-Sicht)
  Mithilfe der Registerkarte **Eingabeauswahl** von **Mininggenauigkeitsdiagramm** können Sie die Datenquelle angeben, aus der die zum Testen des Modells und zum Erstellen des Genauigkeitsdiagramms verwendeten Daten stammen.  
  
 **Weitere Informationen:** [Tests und Überprüfung &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Optionen  
 **Vorhersagespalten und**  **-werte synchronisieren**  
 Aktivieren Sie diese Option, um die vorhersagbaren Attribute des Rasters so zu koordinieren, dass sie (selbst wenn sie einen anderen Namen tragen) beim Modelltraining aus der gleichen vorhersagbaren Miningstrukturspalte abgeleitet werden.  
  
 **Hinweis** Diese Option ist standardmäßig aktiviert. Deaktivieren Sie diese Option nur, wenn Sie sicher sind, dass zwei Miningstrukturspalten aus der gleichen zugrunde liegenden relationalen oder mehrdimensionalen Quelle abgeleitet sind und die Spalten den gleichen Status aufweisen bzw. auf die gleiche Weise diskretisiert wurden.  
  
 **Wählen Sie die vorhersagbaren Miningmodellspalten aus, die im Prognosegütediagramm angezeigt werden sollen**  
 Ein Raster mit den Spalten, die steuern, welche Modelle das Prognosegütediagramm enthalten soll und wie diese Modelle im Prognosegütediagramm verwendet werden sollen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Anzeigen**|Aktivieren Sie das Kontrollkästchen neben dem Namen jeder vorhersagbaren Spalte im Miningmodell, die im Diagramm angezeigt werden soll.<br /><br /> Wenn die Anzeige des Diagramms zu komplex wird, deaktivieren Sie das Kontrollkästchen neben mindestens einer Spalte, um das Diagramm zu vereinfachen.<br /><br /> Hinweis: Zum Erstellen eines Genauigkeitsdiagramms muss mindestens eine Spalte ausgewählt sein.|  
|**Mining Modell**|Listet die Miningmodelle auf, die in der Miningstruktur enthalten sind.|  
|**Name der vorhersagbaren Spalte**|Wählen Sie eine vorhersagbare Spalte aus, die in den zum Erstellen des Prognosegütediagramms verwendeten Miningmodellen enthalten ist.|  
|**Wert vorhersagen**|Wählen Sie einen Wert für die vorhersagbare Spalte aus. Wenn Sie keinen Wert angeben, sagt das Prognosegütediagramm die Leistung des Modells vorher, unabhängig vom Status der vorhersagbaren Spalte.|  
  
 **Dataset auswählen, das für das Genauigkeitsdiagramm verwendet werden soll**  
 Eine Optionsgruppe, die drei Optionen zum Angeben von Genauigkeitstestdaten enthält.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Testfälle für Miningmodell verwenden**|Verwenden Sie den Testsatz, der beim Partitionieren der Miningstruktur erstellt wurde, und wenden Sie den für das Modell definierten Filter an. Weitere Informationen zu Modellfiltern finden Sie unter [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)|  
|**Testfälle für Miningstruktur verwenden**|Verwenden Sie den Testsatz, der beim Partitionieren der Miningstruktur erstellt wurde.|  
|**Anderes Dataset verwenden**|Geben Sie eine Tabelle aus einer vorhandenen Datenquellensicht an, die als Testdataset verwendet werden soll.|  
  
## <a name="filtering-options"></a>Filteroptionen  
 Wenn Sie die Option **Anderes Dataset verwenden**auswählen, können Sie eine Datenquellensicht definieren und Filter erstellen, die auf die betreffenden Daten angewendet werden sollen. Wenn Sie einen Filter erstellen, erstellen Sie eine WHERE-Klausel in der Abfrage, die die Testdaten aus der Datenquellensicht zurückgibt.  
  
 **Hinweis** Mithilfe der Registerkarte **Eingabeauswahl** können Sie keinen Filter für das Mining Modell angeben. Zum Erstellen eines Modell Filters klicken Sie auf die Registerkarte **Mining Modelle** , und bearbeiten Sie die Modell Eigenschaften.  
  
 Wenn Sie beim Erstellen der Miningstruktur kein Zurückhaltungsdataset zum Testen erstellt haben, können Sie diese Option auswählen und dann die ursprüngliche Datenquellensicht als Testsatz angeben. Mit dieser Problemumgehung können Sie auch Filter für das ursprüngliche Dataset festlegen.  
  
 **Spaltenzuordnung angeben**  
 Öffnet das Dialogfeld **Spaltenzuordnung angeben**, in dem Sie die Datenquelle auswählen, Fall- und geschachtelte Tabellen angeben und externe Datenspalten den Miningstrukturspalten zuordnen können.  
  
 Weitere Informationen finden Sie unter [Spaltenzuordnung angeben &#40;Dialogfeld, Mininggenauigkeitsdiagramm&#41;](specify-column-mapping-dialog-box-mining-accuracy-chart.md).  
  
 **Filterausdruck**  
 Zeigt die Filterbedingung an, die Sie mit den Filter-Editoren erstellt haben.  
  
 **Filter-Editor öffnen**  
 Öffnet das Dialogfeld **Datasetfilter** , in dem Sie externe Tabellen auswählen und Bedingungen für Spalten der Falltabelle festlegen können, sowie das Dialogfeld **Filter** , in dem Sie Bedingungen erstellen können, die für einzelne Spalten in der ausgewählten Tabelle oder für Spalten in geschachtelten Tabellen gelten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Test-und validierungsaufgaben und Anleitungen &#40;Data Mining-&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Mining Genauigkeits Diagramm-Designer &#40;Data Mining-&#41;](mining-accuracy-chart-designer-data-mining.md)   
 [Anwenden eines Filters auf ein Mining Modell](data-mining/apply-a-filter-to-a-mining-model.md)   
 [Filter für Miningmodelle &#40;Analysis Services – Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)  
  
  
