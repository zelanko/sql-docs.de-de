---
title: Multiplizitätselement (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2740e920332d55fd2826b8d91d6f7434d2f59e91
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="multiplicity-element-assl"></a>Multiplizitätselement (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert||  
|Kardinalität|1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[' RelationshipEnd '](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*eine*|Dies ist das Primärschlüsselende.|  
|*Viele*|Dies ist das Fremdschlüsselende.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **Rolle** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Multiplicity>.  
  
  
