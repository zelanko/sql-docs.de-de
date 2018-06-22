---
title: NullProcessing-Element (ASSL) | Microsoft Docs
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
- NullProcessing Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullProcessing
helpviewer_keywords:
- NullProcessing element
ms.assetid: 697be5c6-e9a6-4f74-9ff4-5f31400c2178
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 54b75b2e1a7bddd6f7b5df1aeda0311c1b60ff99
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047690"
---
# <a name="nullprocessing-element-assl"></a>NullProcessing Element (ASSL)
  Definiert, wie NULL-Werte verarbeitet werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataItem>  
   ...  
   <NullProcessing>...</NullProcessing>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Automatic*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Beibehalten*|Behält den NULL-Wert bei. **Hinweis:** dieser Wert wird für distinct Count Measures nicht unterstützt.|  
|*Fehler*|Löst einen NULL-Schlüsselfehler aus. Der Wert der [NullKeyNotAllowed](nullkeynotallowed-element-assl.md) bestimmt, wie die Instanz auf den Fehler reagiert. **Hinweis:** dieser Wert wird für Measures nicht unterstützt.|  
|*UnknownMember*|Generiert ein unbekanntes Element und löst einen NULL-Konvertierungsfehler aus. Der Wert der [NullKeyConvertedToUnknown](nullkeyconvertedtounknown-element-assl.md) bestimmt, wie die Instanz auf den Fehler reagiert. **Hinweis:** dieser Wert wird nicht unterstützt, für Spalten, die Measures zugeordnet.|  
|*ZeroOrBlank*|Konvertiert den NULL-Wert zu 0 (für numerische Daten) oder in eine leere Zeichenfolge (für Daten in Zeichenfolge). **Hinweis:** dieser Wert stellt die Kompatibilität mit früheren Versionen von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Automatic*|Nutzt die für das Element geeignete Standardverarbeitung:<br /><br /> -   *ZeroOrBlank* für OLAP-Datenelemente.<br />-   *UnknownMember* für Data mining-Datenelemente.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `NullProcessing` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.NullProcessing>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  