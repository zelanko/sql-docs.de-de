---
title: Aggregieren der Transformations-Editor (Registerkarte Erweitert) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.advanced.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 419a63f9a98e51b9601d7d38f70528ff4ae05970
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66061593"
---
# <a name="aggregate-transformation-editor-advanced-tab"></a>Transformations-Editor für Aggregieren (Registerkarte Erweitert)
  Mithilfe der Registerkarte **Erweitert** des Dialogfelds **Transformations-Editor für Aggregieren** können Sie Komponenteneigenschaften festlegen, Aggregationen angeben und die Eigenschaften von Eingabe- und Ausgabespalten festlegen.  
  
> [!NOTE]  
>  Die Optionen für die Anzahl an Schlüsseln, die Schlüsselskala, die Anzahl unterschiedlicher Schlüssel sowie für unterschiedliche Schlüsselskalen gelten auf der Komponentenebene, wenn sie auf der Registerkarte **Erweitert** angegeben wurden; sie gelten auf der Ausgabeebene, wenn sie in der erweiterten Ansicht der Registerkarte **Aggregationen** angegeben wurden und auf der Spaltenebene, wenn sie in der Spaltenliste im unteren Bereich der Registerkarte **Aggregationen** angegeben wurden.  
>   
>  In der Transformation für das Aggregieren beziehen sich **Schlüssel** und **Schlüsselskala** auf die Anzahl der Gruppen, die als Ergebnis eines **GROUP BY** -Vorgangs erwartet werden. **COUNT DISTINCT-Schlüssel** und **COUNT DISTINCT-Skala** beziehen sich auf die Anzahl der unterschiedlichen Werte, die als Ergebnis eines **DISTINCT COUNT** -Vorgangs erwartet werden.  
  
 Weitere Informationen zur Transformation für das Aggregieren finden Sie unter [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Schlüsselskala**  
 Gibt optional die ungefähre Anzahl an Schlüsseln an, die von der Aggregation erwartet werden. Für die Transformation wird diese Information verwendet, um die anfängliche Cachegröße zu optimieren. Der Standardwert für diese Option ist **Keine Angabe**. Wenn sowohl **Schlüsselskala** als auch **Anzahl von Schlüsseln** angegeben wurden, hat **Anzahl von Schlüsseln** Vorrang.  
  
|Wert|Description|  
|-----------|-----------------|  
|Keine Angabe|Die Eigenschaft **Schlüsselskala** wird nicht verwendet.|  
|Low|Die Aggregation kann ungefähr 500.000 Schlüssel schreiben.|  
|Medium|Die Aggregation kann ungefähr 5.000.000 Schlüssel schreiben.|  
|High|Die Aggregation kann mehr als 25.000.000 Schlüssel schreiben.|  
  
 **Anzahl von Schlüsseln**  
 Gibt optional die genaue Anzahl an Schlüsseln an, die von der Aggregation erwartet werden. Für die Transformation wird diese Information verwendet, um die anfängliche Cachegröße zu optimieren. Wenn sowohl **Schlüsselskala** als auch **Anzahl von Schlüsseln** angegeben wurden, hat **Anzahl von Schlüsseln** Vorrang.  
  
 **COUNT DISTINCT-Skala**  
 Gibt optional die ungefähre Anzahl unterschiedlicher Werte an, die durch die Aggregation geschrieben werden können. Der Standardwert für diese Option ist **Keine Angabe**. Wenn sowohl **COUNT DISTINCT-Skala** als auch **COUNT DISTINCT-Schlüssel** angegeben wurden, hat **COUNT DISTINCT-Schlüssel** Vorrang.  
  
|Wert|Description|  
|-----------|-----------------|  
|Keine Angabe|Die CountDistinctScale-Eigenschaft wird nicht verwendet.|  
|Low|Die Aggregation kann ungefähr 500.000 unterschiedliche Werte schreiben.|  
|Medium|Die Aggregation kann ungefähr 5.000.000 unterschiedliche Werte schreiben.|  
|High|Die Aggregation kann mehr als 25.000.000 unterschiedliche Werte schreiben.|  
  
 **COUNT DISTINCT-Schlüssel**  
 Gibt optional die genaue Anzahl unterschiedlicher Werte an, die durch die Aggregation geschrieben werden können. Wenn sowohl **COUNT DISTINCT-Skala** als auch **COUNT DISTINCT-Schlüssel** angegeben wurden, hat **COUNT DISTINCT-Schlüssel** Vorrang.  
  
 **Faktor für automatische Erweiterung**  
 Verwenden Sie einen Wert zwischen 1 und 100, um den Prozentsatz anzugeben, um den der Arbeitsspeicher während der Aggregation erweitert werden kann. Der Standardwert für diese Option ist **25 %** .  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor für Aggregieren &#40;Registerkarte Aggregationen&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md)   
 [Aggregieren von Werten in einem Dataset mithilfe der Transformation für das Aggregieren](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
