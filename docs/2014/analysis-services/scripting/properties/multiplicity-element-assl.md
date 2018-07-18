---
title: Multiplicity-Element (ASSL) | Microsoft-Dokumentation
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 98eb9ba8186c395b598bff6a7ad2ea63ed101999
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261316"
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
  
  
