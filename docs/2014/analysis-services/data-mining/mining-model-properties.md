---
title: Eigenschaften von Miningmodellen | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining models [Analysis Services], properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- Data Mining Designer
- properties [data mining]
ms.assetid: c5194619-8b31-42be-a95f-585711462945
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4b0d00f10bd4ab4ac5f11b0af3e798c873cc5493
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149529"
---
# <a name="mining-model-properties"></a>Miningmodelleigenschaften
  Miningmodelle verfügen über die folgenden Arten von Eigenschaften:  
  
-   Von der Miningstruktur geerbte Eigenschaften, die den Daten- und Inhaltstyp der von dem Modell verwendeten Daten definieren  
  
-   Eigenschaften, die sich auf den Algorithmus beziehen, der zum Erstellen des Miningmodells verwendet wurde, einschließlich sämtlicher Kundenparameter  
  
-   Eigenschaften, die auf dem Modell einen Filter definieren, die zum Trainieren des Modells verwendet wurden  
  
 Die Eigenschaften eines Miningmodells werden anfänglich definiert, wann Sie das Modell erstellen. Sie können später die meisten Eigenschaften, einschließlich der Algorithmusparameter, Filter und Spaltenverwendungseigenschaften, jedoch ändern. Mithilfe der Registerkarte **Miningmodelle** des Data Mining-Designers oder mit AMO oder XMLA können Sie Eigenschaften für Miningmodelle anpassen.  
  
 Nach dem Ändern einer Eigenschaft müssen Sie das Modell erneut verarbeiten, damit sich die Änderungen im Modell widerspiegeln. Eine erneute Verarbeitung ist auch dann erforderlich, wenn die Änderung nur Metadaten betrifft, wie beispielsweise das Hinzufügen eines Spaltenalias oder einer Spaltenbeschreibung.  
  
## <a name="properties-of-models"></a>Eigenschaften von Modellen  
 In der folgenden Tabelle werden die Eigenschaften, die für Miningmodelle spezifisch sind, beschrieben. Darüber hinaus gibt es Eigenschaften, die Sie im Mining in einzelnen Spalten festlegen können.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**Algorithmus**|Legt den Algorithmustyp für das Miningmodell fest.|  
|**AlgorithmParameters**|Legt Werte für die zu jedem Algorithmustyp verfügbaren Algorithmusparameter fest.|  
|**Filter**|Legt einen Filter fest, der auf die Daten angewendet wird, die zum Trainieren und Testen des Miningmodells verwendet werden. Die Filterdefinition wird mit dem Modell gespeichert und kann optional verwendet werden, wenn Sie Vorhersageabfragen erstellen oder die Genauigkeit des Modells testen.<br /><br /> Beim Trainieren des Modells ist der Modellfilter nicht optional.|  
|**Name**|Legt den Namen des Miningmodells fest.|  
|**AllowDrillThrough**|Gibt an, ob Drillthrough für das Miningmodell aktiviert ist.|  
  
## <a name="properties-of-model-columns"></a>Eigenschaften der Modellspalte  
 Sie können die folgenden für Data Mining spezifischen Eigenschaften für jede Spalte in einem Miningmodell festlegen. Diese Eigenschaften können für jedes Miningmodell in einer Miningstruktur auf einen unterschiedlichen Wert festgelegt werden.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**Beschreibung**|Beschreibt den Zweck der Miningspalte.|  
|**Name**|Legt den Namen der Miningmodellspalte fest. Sie können einen neuen Namen eingeben, um einen Alias für die Miningmodellspalte anzugeben.|  
|**ModelingFlags**|Legt algorithmusspezifische Flags für die Spalte fest.|  
|**SourceColumnID**|Gibt den Namen der Miningstrukturspalte an, auf der die Modellspalte basiert.<br /><br /> Diese Eigenschaft ist schreibgeschützt.|  
|**Usage**|Legt fest, wie die Spalte vom Miningmodell verwendet wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodellspalten](mining-model-columns.md)   
 [Miningstrukturen &#40;Analysis Services – Datamining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Miningmodelltasks und Anweisungen Mining](mining-model-tasks-and-how-tos.md)   
 [Ändern der Eigenschaften eines Miningmodells](change-the-properties-of-a-mining-model.md)   
 [Datamining-Tools](data-mining-tools.md)   
 [Erstellen Sie eine relationale Miningstruktur](create-a-relational-mining-structure.md)   
 [Erstellen eines Alias für eine Modellspalte](create-an-alias-for-a-model-column.md)  
  
  