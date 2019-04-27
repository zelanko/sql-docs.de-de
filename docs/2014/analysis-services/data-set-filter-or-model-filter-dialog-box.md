---
title: Datasetfilter oder Modell Modellfilter (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a9602174-b7e2-4e16-8ded-dfd8eb9264d7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 923467270901b91c35b40005c75207e7b1799194
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62732595"
---
# <a name="data-set-filter-or-model-filter-dialog-box"></a>Datasetfilter oder Modellfilter (Dialogfeld)
  In diesem Dialogfeld können Sie die Filter erstellen, die Sie auf ein Dataset anwenden können.  Bei dem Dataset kann es sich um ein zum Testen verwendetes externes Dataset oder um die Falldaten für ein Miningmodell handeln. Der Name des Dialogfelds ändert sich je nachdem, ob der Filter für ein externes Dataset oder für ein Miningmodell gilt.  
  
 Wenn Sie den Filter auf ein neues Dataset anwenden, werden zum Auswerten des Data Mining-Modells nur die Fälle in den Daten verwendet, die die Bedingungen erfüllen. Wenn Sie den Filter auf das Miningmodell direkt anwenden, werden zum Trainieren und Testen des Modells nur die Fälle in den vorhandenen Testdaten verwendet, die den Filterkriterien entsprechen.  
  
-   Das Dialogfeld **Datasetfilter** kann über die Registerkarte **Eingabeauswahl** von **Mininggenauigkeitsdiagramm** aufgerufen werden.  
  
-   Das Dialogfeld **Modellfilter** kann über die Registerkarte **Miningmodelle** des Data Mining-Designers aufgerufen werden.  
  
-   Das Raster **Bedingungen** weist Spalten auf, in denen Sie einen Tabellen- oder Spaltennamen, einen Operator oder Zielwerte angeben können. Mithilfe dieses Raster erstellen Sie in Wirklichkeit eine WHERE-Klausel.  
  
> [!TIP]  
>  Zum Testen der Genauigkeit einer Untergruppe der ursprünglichen Trainingsdaten können Sie die Datenquellensicht hinzufügen, mit der der Trainingssatz als externe Testdaten definiert wurde, und dann Bedingungen im Raster **Datasetfilter** hinzufügen.  
  
 **Weitere Informationen:** [Tests und Überprüfung &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Optionen  
 **Bedingungen**  
 Zeigt Tabellennamen gefolgt von Spaltennamen mit Bedingungen an.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Und/Oder**|Wählen Sie einen Operator aus, um mehrere Bedingungen zu verknüpfen.|  
|**Miningstrukturspalte**|Klicken Sie hierauf, um eine Datenquelle auszuwählen, und klicken Sie dann im Raster auf aufeinander folgenden Zeilen, um Spalten aus der Datenquelle hinzuzufügen.<br /><br /> Die erste Zeile im Raster gibt die Datenquellensicht an. Nach Auswahl einer Datenquellensicht wird im Feld **Miningstrukturspalte** ein Tabellensymbol angezeigt, und im Feld **Wert** wird die Kombination aller Kriterien angezeigt, die Sie für diese Datenquelle definiert haben.<br /><br /> Nach Auswahl einer Datenquelle wird im Feld **Miningstrukturspalte** eine Dropdownliste mit den einzelnen Spalten in der Datenquelle angezeigt.|  
|**Operator**|Wählen Sie in der Liste einen Operator aus.|  
|**Wert**|Bei Tabellen wird im Feld **Wert** die Kombination aller auf die Datenquelle angewendeten Filter angezeigt. Sie können auch den Build klicken **(...)**  Schalfläche rechts neben dem Textfeld zum Öffnen der **Filter** Dialogfeld und eine Bedingung zu erstellen.|  
  
 **Ausdruck**  
 Zeigt die Gruppe von Kriterien an, die Sie mit dem Raster erstellt haben.  
  
 **Abfrage bearbeiten**  
 Ändert den Filterbearbeitungsmodus, sodass Sie einen Filterausdruck direkt in das Textfeld **Ausdruck** eingeben können.  
  
> [!NOTE]  
>  Wenn Sie manuell Änderungen am Filterausdruck vorgenommen haben, können Sie nicht mehr in den Rasterbearbeitungsmodus zurückkehren, und zwar auch dann nicht, wenn Sie den Ausdruck auf der Registerkarte **Eingabeauswahl** im Feld **Filterausdruck** gespeichert haben. Wenn Sie einen Ausdruck mithilfe des Rasters erstellen möchten, müssen Sie den vorhandenen Filterausdruck löschen und von Neuem beginnen.  
  
 **Abfragebearbeitung wiederherstellen**  
 Stellt den vorherigen Zustand des Rasters wieder her und verwirft alle am Filterausdruck vorgenommenen Änderungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Tests und Überprüfung miningmodelltasks und Anweisungen &#40;Datamining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Mining-Genauigkeitsdiagramm-Designer &#40;Datamining&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  
