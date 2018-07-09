---
title: Recommendation-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6bd7c8b2315f853166e4172030aa191748506b27
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260062"
---
# <a name="recommendation-element-dta"></a>Recommendation-Element (DTA)
  Enthält Informationen zu den hypothetischen Indizes, die Teil einer benutzerspezifischen Konfiguration sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Optional. Können Sie einmal für jede `Table` Element.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Element für Schema Tabelle &#40;DTA&#41;](table-element-for-schema-dta.md)|  
|**Untergeordnete Elemente**|[Create-Element &#40;DTA&#41;](create-element-dta.md)<br /><br /> `Drop` Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element hat den Namen **CreateTypecomplexType** im XML-Schema des Datenbankoptimierungsratgebers. Es wird zur Angabe von Indizes für eine hypothetische Konfiguration verwendet. Verwechseln Sie dies nicht `Recommendation` Element mit den anderen Typen, die verwendet werden können, zum Angeben von Partitionierungen (`RecommendationPType`) oder Sichten (`RecommendationViewType`). Informationen zu diesen anderen `Recommendation` Elementtypen finden Sie unter den [-Datenbank-Engine Tuning Advisor XML-Schema](http://go.microsoft.com/fwlink/?linkid=43100).  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 
  [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
