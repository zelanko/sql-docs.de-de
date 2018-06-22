---
title: EnumString-Datentyp (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- EnumString Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EnumString
- urn:schemas-microsoft-com:xml-analysis#EnumString
- http://schemas.microsoft.com/analysisservices/2003/engine#EnumString
helpviewer_keywords:
- EnumString data type
ms.assetid: 9214195e-4539-419b-95ec-b7aa75e033ab
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 034ebe0218a8effece3aee526f9920850a7df536
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149967"
---
# <a name="enumstring-data-type-xmla"></a>EnumString-Datentyp (XMLA)
  Definiert einen abgeleiteten Datentyp, der für einen gegebenen Enumerator einen Satz genannter Konstanten darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<EnumString>...</EnumString>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|`string`|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 XML for Analysis (XMLA) schränkt Zeichenfolgenwerte mithilfe von Enumerationen auf einen Satz überprüfbarer Einstellungen ein. `EnumString` verwendet den standardmäßig `string`-XML-Datentyp. Die bestimmten Werte für jede der genannten Konstanten werden mit der Enumeratordefinition angegeben. Enumeratoren werden definiert, indem Sie sie zum Hinzufügen der [DISCOVER_ENUMERATORS](../../schema-rowsets/xml/discover-enumerators-rowset.md) -Schemarowset, und kann abgerufen werden, indem die [Discover](../xml-elements-methods-discover.md) Methode mit dem DISCOVER_ENUMERATORS-Anforderungstyp.  
  
 Die folgende Tabelle beschreibt die Enumeratoren, die von einer Instanz von unterstützt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Enumerator|Description|  
|----------------|-----------------|  
|ProviderType|Unterstützt die ProviderType-Spalte in der [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md) -Schemarowset, die den Typ der Daten bestimmt, die von zurückgegeben werden, kann ein [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.<br /><br /> Diese Enumeration unterstützt zusätzlich die XMLA-Eigenschaft, `ProviderType`, die den von einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz unterstützten Providertyp bestimmt. Diese Enumeration wird auch im DISCOVER_DATASOURCES-Schemarowset verwendet.<br /><br /> Weitere Informationen zu `ProviderType`, finden Sie unter [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|AuthenticationMode|Unterstützt die AuthenticationMode-Spalte im DISCOVER_DATASOURCES-Schemarowset, die die Sicherheitsanmeldeinformationen bestimmt, die übergeben werden, müssen für den Zugriff auf eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.|  
|PropertyAccessType|Unterstützt die PropertyAccessType-Spalte in der [DISCOVER_PROPERTIES](../../schema-rowsets/xml/discover-properties-rowset.md) -Schemarowset, die für ein XMLA-Eigenschaft verfügbaren Zugriffstyp bestimmt.|  
|StateSupport|Unterstützt die XMLA-Eigenschaft, `StateSupport`, bestimmt die Ebene der statusbehaftung, die durch eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.<br /><br /> Weitere Informationen zu `StateSupport`, finden Sie unter [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|StateActionVerb|Enthält eine Liste der Verben, die von XMLA in SOAP-Headern unterstützt und zum Starten, Identifizieren und Beenden einer Sitzung verwendet werden.<br /><br /> Weitere Informationen zu Sitzungen finden Sie unter [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).|  
|ResultsetFormat|Unterstützt die XMLA-Eigenschaft, `Format`, der den Typ des in der zurückgegebenen Daten bestimmt eine [Root](../xml-elements-properties/root-element-xmla.md) Element.<br /><br /> Weitere Informationen zu `Format`, finden Sie unter [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetAxisFormat|Unterstützt die XMLA-Eigenschaft, `AxisFormat`, bestimmt das Format der achseninformationen zurückgegeben, die einem `root` -Element, das multidimensionale Daten enthält.<br /><br /> Weitere Informationen zu `AxisFormat`, finden Sie unter [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetContents|Unterstützt die XMLA-Eigenschaft, `Content`, der bestimmt, ob Metadaten oder Daten in zurückgegeben werden ein `root` Element.<br /><br /> Weitere Informationen zu `Content`, finden Sie unter [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|MDXSupportLevel|Unterstützt die XMLA-Eigenschaft, `MDXSupport`, womit MDX (Multidimensional Expressions) unterstützt, die auf eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.<br /><br /> Weitere Informationen zu `MDXSupport`, finden Sie unter [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Datentypen &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  