---
title: Definieren Sie Semiadditives Verhalten (Business Intelligence-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.semiadditivememberdetection.f1
ms.assetid: e57080ba-ce96-40f8-bca7-6701d1725b3c
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 201a5a24e8bafa2f2f919f6ad0b072ca801a694e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310810"
---
# <a name="define-semiadditive-behavior-business-intelligence-wizard"></a>Semiadditives Verhalten definieren (Business Intelligence-Assistent)
  Verwenden Sie die Seite **Semiadditives Verhalten definieren**, um das semiadditive Verhalten für Measures zu aktivieren oder zu deaktivieren. Das semiadditive Verhalten bestimmt, wie in einem Cube enthaltene Measures über eine Zeitdimension aggregiert werden.  
  
> [!NOTE]  
>  Mit Ausnahme von LastChild, das in der Standard Edition verfügbar ist, ist semiadditives Verhalten nur in der Business Intelligence Edition oder der Enterprise Edition verfügbar. Da semiadditives Verhalten darüber hinaus nur für Measures und nicht für Dimensionen definiert wird, wird diese Seite im Business Intelligence-Assistenten nicht angezeigt, wenn er über den Dimensions-Designer oder durch Klicken mit der rechten Maustaste auf eine Dimension im Projektmappen-Explorer von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]gestartet wird.  
  
## <a name="options"></a>Tastatur  
 **Semiadditives Verhalten deaktivieren**  
 Deaktiviert das semiadditive Verhalten in allen Measures, die im Cube enthalten sind.  
  
 **Der Assistent wurde die \<Dimensionsname > Kontodimension, die semiadditive Elemente enthält. Elemente dieser Dimension gemäß dem semiadditiven Verhalten, die für den jeweiligen Kontotyp angegeben werden vom Server aggregiert.**  
 Aktiviert das semiadditive Verhalten für Kontodimensionen mit semiadditiven Elementen. Nach Auswahl dieser Option wird Sie die Aggregatfunktion aller Measures in Measuregruppen, die die Kontodimension auf verweisen `ByAccount`.  
  
 Weitere Informationen zu Kontodimensionen finden Sie unter [Erstellen eines Finanzkontos des über- und untergeordneten Typs Dimension](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md).  
  
 **Semiadditives Verhalten für einzelne Measures definieren**  
 Aktiviert Semiadditives Verhalten für bestimmte Measures und gibt die Aggregatfunktion für bestimmte Measures an. Die Aggregatfunktion gilt für all jene Dimensionen, auf die durch die Measuregruppe mit dem Measure verwiesen wird.  
  
 **Measures**  
 Zeigt den Namen eines im Cube enthaltenen Measures an.  
  
 **Semiadditive Funktion**  
 Wählen Sie die Aggregatfunktion für das ausgewählte Measure aus. In der folgenden Tabelle sind die verfügbaren Aggregatfunktionen aufgelistet.  
  
|value|Description|  
|-----------|-----------------|  
|**AverageOfChildren**|Wird durch Zurückgeben des Durchschnitts der dem Measure untergeordneten Elemente aggregiert.|  
|`ByAccount`|Wird durch die Aggregatfunktion aggregiert, die dem angegebenen Kontotyp des Attributs in der Kontodimension zugeordnet ist.|  
|`Count`|Wird mit der `Count`-Funktion aggregiert.|  
|`DistinctCount`|Wird mit der `DistinctCount`-Funktion aggregiert.|  
|**FirstChild**|Wird durch Zurückgeben des ersten untergeordneten Elements des Measures über eine Zeitdimension aggregiert.|  
|**FirstNonEmpty**|Wird durch Zurückgeben des ersten nicht leeren Elements des Measures über eine Zeitdimension aggregiert.|  
|**LastChild**|Wird durch Zurückgeben des letzten untergeordneten Elements des Measures über eine Zeitdimension aggregiert.|  
|**LastNonEmpty**|Wird durch Zurückgeben des letzten nicht leeren Elements des Measures über eine Zeitdimension aggregiert.|  
|`Max`|Wird mit der `Max`-Funktion aggregiert.|  
|`Min`|Wird mit der `Min`-Funktion aggregiert.|  
|**Keine**|Aggregation wird nicht ausgeführt.|  
|`Sum`|Wird mit der `Sum`-Funktion aggregiert.|  
  
> [!NOTE]  
>  Die für diese Option getroffene Auswahl gilt nur, wenn **Semiadditives Verhalten für einzelne Measures definieren** ausgewählt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Business Intelligence-Assistent F1-Hilfe](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Dimensions-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
