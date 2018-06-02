---
title: SynchronizeSecurity-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f99f4c0ddf212d2fac33abd08c33ccf3dbe7998
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576482"
---
# <a name="synchronizesecurity-element-xmla"></a>SynchronizeSecurity-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Gibt an, wie sicherheitsdefinitionen wie Rollen und Berechtigungen während der Synchronisierung ein [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Synchronize>  
   ...  
   <SynchronizeSecurity>...</SynchronizeSecurity>  
   ...  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*skipMembership*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Synchronisieren](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die **Sicherheit** -Element bestimmt, ob die sicherheitsdefinitionen wie Rollen und Berechtigungen, die für eine Analysis Services-Datenbank definierten, während synchronisiert werden eine **Synchronize** Befehl. Dieses Element bestimmt außerdem, ob Windows-Benutzerkonten und Gruppen, die als Mitglieder der Sicherheitsdefinitionen definiert sind, als Teil des **Synchronize** -Befehls einbezogen werden.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*skipMembership*|Einbeziehen von Sicherheitsdefinitionen und Ausschließen von Informationen zur Mitgliedschaft während eines **Synchronize** -Befehls.|  
|*CopyAll*|Einbeziehen von Sicherheitsdefinitionen und Informationen zur Mitgliedschaft während eines **Synchronize** -Befehls.|  
|*IgnoreSecurity*|Ausschließen von Sicherheitsdefinitionen während eines **Synchronize** -Befehls.|  
  
## <a name="see-also"></a>Siehe auch
 [Sicherheitselement &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
