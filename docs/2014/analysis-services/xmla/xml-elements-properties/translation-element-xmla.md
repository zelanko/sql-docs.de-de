---
title: Translation-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Translation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Translation
- microsoft.xml.analysis.translation
- http://schemas.microsoft.com/analysisservices/2003/engine#Translation
helpviewer_keywords:
- Translation element
ms.assetid: ce962d4b-dda9-4a16-a56c-ff7a5275c48a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7dce14aae6cd8df63d0405869b23f71874cff378
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100460"
---
# <a name="translation-element-xmla"></a>Translation-Element (XMLA)
  Definiert eine Übersetzung für ein Attributelement.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Translations>  
   ...  
   <Translation>  
      <Language>...</Language>  
      <Name>...</Name>  
   </Translation>  
   ...  
</Translations>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Translations (Übersetzungen)](translations-element-xmla.md)|  
|Untergeordnete Elemente|[Language](language-element-xmla.md), [Name](name-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Ein `Translation` -Element definiert die für ein Attributelement einer Übersetzung für ein bestimmtes Attribut während des definierten zuzuordnen erforderlichen Informationen ein [einfügen](../xml-elements-commands/insert-element-xmla.md) oder [Update](../xml-elements-commands/update-element-xmla.md) Befehl.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
