---
title: Übersetzungen in mehrdimensionalen Modellen | Microsoft-Dokumentation
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
- sql12.asvs.dimensiondesigner.deletelanguagefirm.f1
ms.assetid: 5521f8ef-b10a-4861-9df7-1e43e0a1fb3f
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e018bf778a877ed62612e631951ca92258aaec0e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275566"
---
# <a name="translations-in-multidimensional-models"></a>Übersetzungen in mehrdimensionalen Modellen
  Unterstützung mehrerer Sprachen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erfolgt mithilfe von Übersetzungen. Eine Übersetzung enthält einen Sprachbezeichner und Bindungen für Eigenschaften von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekten, die in mehreren Sprachen angezeigt werden können. Beispielsweise können Sie eine Übersetzung für eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank definieren, um die Überschrift und Beschreibung dieser Datenbank in einer bestimmten Sprache anzuzeigen. Weitere Informationen zu Übersetzungen finden Sie unter [Cubeübersetzungen](../multidimensional-models-olap-logical-cube-objects/cube-translations.md).  
  
## <a name="defining-translations"></a>Definieren von Übersetzungen  
 Sie können Übersetzungen in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] definieren, indem Sie den entsprechenden Designer für das zu übersetzende [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekt verwenden. Durch Definieren einer Übersetzung wird ein `Translation` Objekt verknüpft ist, mit dem entsprechenden [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekt, das die angegebenen Literalwerte in der angegebenen Sprache, für die Eigenschaften des zugeordneten hat [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekt.  
  
 Folgenden Objekten und Eigenschaften in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] können Übersetzungen zugewiesen sein:  
  
|Objekt|Eigenschaften|Designer|  
|------------|----------------|--------------|  
|Datenbank|`Caption`, `Description`|[Allgemeine &#40;Datenbank-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../general-database-designer-analysis-services-multidimensional-data.md)|  
|Cube|`Caption`, `Description`|[Übersetzungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Measuregruppe|`Caption`|[Übersetzungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Measure|`Caption`, `DisplayFolder`|[Übersetzungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Cubedimension|`Caption`|[Übersetzungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Perspektive|`Caption`|[Übersetzungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Key Performance Indicator (KPI)|`Caption`, `Description`, `DisplayFolder`|[Übersetzungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Aktion|`Caption`|[Übersetzungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Benannte Menge|`Caption`|[Übersetzungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|berechnetes Element|`Caption`|[Übersetzungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Datenbankdimension|`Caption`, `AttributeAllMember`|[Übersetzungen &#40;Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|attribute|`Caption`, `CaptionColumn` <sup>1</sup>, `AttributeHierarchyDisplayFolder`, `NamingTemplate`, `MembersWithDataCaption`|[Übersetzungen &#40;Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|Hierarchy|`Caption`, `AllMemberName`|[Übersetzungen &#40;Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|Ebene|`Caption`|[Übersetzungen &#40;Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
  
 <sup>1</sup> der `CaptionColumn` Eigenschaft eines Attributs kann an eine Spalte in einer Datenquellensicht gebunden werden und können nicht für die Instanz, im Gegensatz zu anderen Übersetzungen angegebene eine Windows-Sortierung verwenden.  
  
### <a name="defining-attribute-translations"></a>Definieren von Attributübersetzungen  
 Übersetzungen von Attributen in Datenbankdimensionen werden auf folgende, von der Handhabung anderer Übersetzungen abweichende Weise gehandhabt:  
  
-   Eine Bindungsspalte kann an Stelle eines expliziten Literalwerts der `CaptionColumn`-Eigenschaft zugewiesen werden, sodass die Elementnamen von Elementen für dieses Attribut übersetzt werden können.  
  
-   Eine Windows-Sortierreihenfolge, die nicht für die Instanz vorgegeben ist, kann verwendet werden, um Elemente im Attribut angemessen für die in der Übersetzung angegebene Sprache zu sortieren.  
  
 Sie können die **Attributdatenübersetzung** im Dialogfeld [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] Übersetzungen für Attribute in Datenbankdimensionen zu definieren. Weitere Informationen zu den **Attributdatenübersetzung** im Dialogfeld finden Sie unter [Attribut Daten Attributdatenübersetzung (Dialogfeld) &#40;Analysis Services – mehrdimensionale Daten&#41;](../attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="resolving-translations"></a>Auflösung von Übersetzungen  
 Wenn eine Clientanwendung Informationen in einem bestimmten Sprachbezeichner anfordert, versucht die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz, Daten und Metadaten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekte in den nächstmöglichen Sprachbezeichner aufzulösen. Wenn die Clientanwendung keine Standardsprache und auch nicht den neutralen Gebietsschemabezeichner (0) oder den standardmäßigen Prozesssprachbezeichner (1024) vorgibt, dann verwendet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die Standardsprache für die Instanz, um Daten und Metadaten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekte zurückzugeben.  
  
 Wenn die Clientanwendung einen anderen als den angegebenen Standardsprachbezeichner verwendet, führt die Instanz eine Iteration durch alle verfügbaren Übersetzungen für alle verfügbaren Objekte durch. Wenn der angegebene Sprachbezeichner dem Sprachbezeichner einer Übersetzung entspricht, gibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diese Übersetzung zurück. Wenn keine Übereinstimmungen gefunden werden können, versucht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mit einer der folgenden Methoden, Übersetzungen zurückzugeben, die dem angebenen Sprachbezeichner am ähnlichsten sind:  
  
-   Für die folgenden Sprachbezeichner versucht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] einen alternativen Sprachbezeichner zu verwenden, wenn eine Übersetzung für den angegebenen Sprachbezeichner nicht definiert ist:  
  
    |Angegebener Sprachbezeichner|Alternativer Sprachbezeichner|  
    |-----------------------------------|-----------------------------------|  
    |3076 - Chinesisch (Hongkong S.A.R., Volksrepublik China)|1028 - Chinesisch (Taiwan)|  
    |5124 - Chinesisch (Macau SAR)|1028 - Chinesisch (Taiwan)|  
    |1028 - Chinesisch (Taiwan)|Standardsprache|  
    |4100 - Chinesisch (Singapur)|2052 - Chinesisch (Volksrepublik China)|  
    |2074 - Kroatisch|Standardsprache|  
    |3098 - Kroatisch (Kyrillisch)|Standardsprache|  
  
-   Für alle anderen angegebenen Sprachbezeichner extrahiert [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die Hauptsprache des angegebenen Sprachbezeichners und ruft den von Windows als beste Übereinstimmung für die Hauptsprache angegebenen Sprachbezeichner zurück. Wenn eine Übersetzung für den ähnlichsten Sprachbezeichner nicht gefunden werden kann, oder wenn der vorgegebene Sprachbezeichner am stärksten mit der Hauptsprache übereinstimmt, wird die Standardsprache verwendet.  
  
## <a name="deleting-translation-objects"></a>Löschen von Übersetzungsobjekten  
 Im Dimension- oder Cube-Designer können Sie mit der rechten Maustaste auf ein Übersetzungsobjekt klicken, um es dauerhaft zu löschen. Sie können ein gelöschtes Objekt nicht wiederherstellen oder wiederverwenden; sehen Sie sich daher die Liste der betroffenen Objekte unbedingt genau an, bevor Sie fortfahren.  
  
## <a name="see-also"></a>Siehe auch  
 [Globalisierungsszenarien für Globalisierungsszenarien für Analysis Services](../globalization-scenarios-for-analysis-services-multiidimensional.md)   
 [Sprachen und Sortierungen &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md)  
  
  
