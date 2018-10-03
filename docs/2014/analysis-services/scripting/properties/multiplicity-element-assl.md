---
title: Multiplicity-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 441e3829-9009-4b32-a8c6-fa580663387f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e2e4335e6e8087fd94809678f5d3b04f9aee02ea
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076170"
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
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Eine*|Dies ist das Primärschlüsselende.|  
|*Viele*|Dies ist das Fremdschlüsselende.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `role` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Multiplicity>.  
  
  
