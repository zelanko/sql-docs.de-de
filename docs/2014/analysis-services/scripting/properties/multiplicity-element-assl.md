---
title: Multiplizitätselement (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 441e3829-9009-4b32-a8c6-fa580663387f
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 91ecb8a8b7ada49666d2b6144d1ba258a7c26b58
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162555"
---
# <a name="multiplicity-element-assl"></a>Multiplizitätselement (ASSL)
  Gibt an, ob die Attribute in RelationshipEnd zur Seite "one" oder der Seite "many" einer Beziehung sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<RelationshipEnd>  
   ...  
   <Multiplicity>...</Multiplicity>  
   ...  
</RelationshipEnd>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert||  
|Cardinality|1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[' RelationshipEnd '](../data-type/relationshipend-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Eine*|Dies ist das Primärschlüsselende.|  
|*Viele*|Dies ist das Fremdschlüsselende.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `role` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Multiplicity>.  
  
  