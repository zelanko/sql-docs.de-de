---
title: Filtern (Dialog Feld) (Mining Genauigkeits Diagramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71e884a9-7ec4-4459-a4c4-87f6c796d478
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 554c7c0f375d63710c86e37666ee98c6dac6daf6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66081173"
---
# <a name="filter-dialog-box-mining-accuracy-chart"></a>Filter (Dialogfeld, Mininggenauigkeitsdiagramm)
  Im Dialogfeld **Filter** können Sie die Bedingungen erstellen, die Sie auf ein Dataset anwenden können. Bei dem Dataset kann es sich um ein zum Testen verwendetes externes Dataset oder um die Falldaten zum Trainieren eines Miningmodells handeln. In diesem Dialogfeld können Sie die Kriterien erstellen, die als Teil von komplexeren Filterkriterien in einem der beiden Dialogfelder **Datasetfilter** oder **Modellfilter** gespeichert werden können.  
  
-   Das Dialogfeld **Datasetfilter** kann über die Registerkarte **Eingabeauswahl** von **Mininggenauigkeitsdiagramm** aufgerufen werden.  
  
-   Das Dialogfeld **Modellfilter** kann über die Registerkarte **Miningmodelle** des Data Mining-Designers aufgerufen werden.  
  
 Wenn Sie einen Filter auf ein Miningmodell anwenden, wählen Sie als erstes im Dialogfeld **Modellfilter** eine Tabelle aus. Dann können Sie im Dialogfeld **Filter** die Bedingungen erstellen, die nur auf diese Tabelle angewendet werden.  
  
 Wenn Sie einen Filter erstellen, der auf ein externes Dataset angewendet werden soll, wählen Sie im Dialogfeld **Datasetfilter** eine Tabelle aus der Liste mit den in einer Datenquellensicht vorhandenen Tabellen aus. Dann erstellen Sie im Dialogfeld **Filter** die Bedingungen, die nur auf diese Tabelle angewendet werden.  
  
 Nachdem Sie einen Satz von Bedingungen erstellt haben, die für eine einzelne Tabelle gelten, [!INCLUDE[clickOK](../includes/clickok-md.md)]. Die von Ihnen im Dialogfeld **Filter** vorgenommenen Änderungen werden automatisch zum Filterausdruck in einem der übergeordneten Dialogfelder **Datasetfilter** oder **Modellfilter**hinzugefügt.  
  
 Wenn Sie den Filter auf das neue Dataset anwenden, werden zum Auswerten des vorhandenen Data Mining-Modells nur die Fälle in den Daten verwendet, die die Bedingungen erfüllen. Wenn Sie den Filter jedoch auf das Miningmodell anwenden, wird die Genauigkeit des Modells nur für die Fälle im Miningmodell bewertet, die diese Bedingungen erfüllen.  
  
 **Weitere Informationen finden Sie unter:** [Testen und validieren &#40;Data Mining-&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Tastatur  
 **Voraus**  
 Ein Raster mit Spalten, in denen die Bedingungen für die Spalten aus der Tabelle festgelegt werden, die im Dialogfeld **Datasetfilter** ausgewählt wurden.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Und/oder**|Klicken Sie auf diese Option, um anzugeben, ob der AND-Operator oder der OR-Operator auf die Bedingung in dieser Zeile angewendet werden soll. Diese Werte sind nur dann verfügbar, wenn Sie eine Spalte aus der Liste **Miningstrukturspalte** ausgewählt haben.|  
|**Miningstrukturspalte**|Klicken Sie auf diese Option, um eine Spalte aus der Liste mit den Spalten der Tabelle auszuwählen, die Sie aus den Datenquellen im Dialogfeld **Datasetfilter** ausgewählt haben.|  
|**Operator**|Wählen Sie in der Liste einen Operator aus. Die verfügbaren Operatoren hängen vom Datentyp der Spalte ab.<br /><br /> Wenn die Spalte diskrete Werte enthält, sind nur folgende Operatoren verfügbar:<br /><br /> = (ist gleich), <> (ist nicht gleich), IS NOT NULL, IS NULL.<br /><br /> Wenn die Spalte kontinuierliche Werte enthält, werden auch Operatoren für größer als- und kleiner als-Vorgänge unterstützt.|  
|**Wert**|Geben Sie einen Wert ein, der als Bedingung verwendet werden soll.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Test-und validierungsaufgaben und Anleitungen &#40;Data Mining-&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Mining Genauigkeits Diagramm-Designer &#40;Data Mining-&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  
