---
title: Allgemein (Dialogfeld Partitionseigenschaften) (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.general.f1
ms.assetid: efb505be-354f-4d23-8f2d-3e76fa50d27b
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0008344f56afefca65c9c94b1b4446b5d84455dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050425"
---
# <a name="general-partition-properties-dialog-box-ssms"></a>Allgemein (Dialogfeld Partitionseigenschaften) (SSMS)
  Mithilfe der Registerkarte **Allgemein** des Dialogfelds **Partitionseigenschaften** in SQL Server Management Studio können Sie die allgemeinen Eigenschaften einer Partition in einer Measuregruppe für einen Cube in einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank festlegen.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Aggregationsentwurfs-ID**|Zeigt den Bezeichner des von der Partition verwendeten Aggregationsentwurfs an.|  
|**Aggregationspräfix**|Zeigt das Standardpräfix von Aggregationsinstanzen an, die in der Partition enthalten sind.|  
|**Timestamp erstellen**|Zeigt das Datum und die Uhrzeit der Erstellung der Partition an.|  
|**Aktueller Speichermodus**|Zeigt den aktuellen Speichermodus der Partition an.<br /><br /> Hinweis: Dieser Modus kann in Abhängigkeit von den für die Partition geltenden Einstellungen für das proaktive Zwischenspeichern variieren. Weitere Informationen zum proaktiven Zwischenspeichern finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Beschreibung**|Hier können Sie per Eingabe die Beschreibung der Partition ändern.|  
|**Geschätzte Zeilen**|Geben Sie die geschätzte Anzahl an Zeilen in der zugrunde liegenden Datenquelle an, die durch die Partition dargestellt wird. Dieser Wert wird während der Verarbeitung verwendet, um die für die Verarbeitung der Partition erforderliche Zeit und den erforderlichen Speicherplatz zu schätzen.|  
|**Geschätzte Größe**|Zeigt die geschätzte Größe der Partition an.|  
|**ID**|Zeigt den Bezeichner der Partition an.|  
|**Zuletzt verarbeitet**|Zeigt das Datum und die Uhrzeit an, zu der die Partition zuletzt verarbeitet wurde.|  
|**Letztes Schemaupdate**|Zeigt das Datum und die Uhrzeit des letzten Updates der Metadaten für die Partition an.|  
|**Name**|Zeigt den Namen der Partition an.|  
|**Verarbeitungsmodus**|Wählen Sie den Verarbeitungsmodus für die Partition aus. Weitere Informationen zu Verarbeitungsmodi für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] anzuzeigen, [mehrdimensionalen Modell Objekt verarbeiten](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).|  
|**Remotedatenquellen-ID**|Zeigt den Bezeichner der Remotedatenquelle an, von der die Quelldaten für die Partition abgerufen werden.<br /><br /> Hinweis: Diese Eigenschaft enthält nur einen Wert für Remotepartitionen.|  
|**Slice**|Zeigt den Ausdruck an, durch den der Datenslice identifiziert wird, den die Partition darstellt.|  
|**Quelle**|Zeigt die Tabelle oder die Abfrage an, durch die der Partition die Quelldaten bereitgestellt werden.|  
|**Status**|Zeigt den aktuellen Verarbeitungsstatus der Partition an.|  
|**Speicherort**|Zeigt den Ordner an, in dem die Daten für die Partition gespeichert sind.<br /><br /> Hinweis: Diese Eigenschaft enthält nur dann einen Wert, wenn für die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz ein anderer Speicherort als der Standardspeicherort angegeben wurde.|  
|**Typ**|Zeigt den Typ der Partition an.|  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Remotepartitionen](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)   
 [Partitions-Eigenschaftendialogfeld &#40;SSMS&#41;](partition-properties-dialog-box-ssms.md)   
 [Auswahl &#40;partitionieren Eigenschaftendialogfeld&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)   
 [Proaktives Zwischenspeichern &#40;partitionieren Eigenschaftendialogfeld&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)   
 [Fehlerkonfiguration für die Dimensionsverarbeitung von Cubes, Partition und &#40;SSAS – mehrdimensional&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  