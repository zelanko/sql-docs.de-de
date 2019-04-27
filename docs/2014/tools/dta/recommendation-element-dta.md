---
title: Recommendation-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bcc0a95028b1f107f15752692d3dcad090fbe8b1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659578"
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
|**Vorkommen**|Dies ist optional. Einmalige Verwendung pro `Table`-Element möglich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Table-Element für Schema &#40;DTA&#41;](table-element-for-schema-dta.md)|  
|**Untergeordnete Elemente**|[Create Element &#40;DTA&#41;](create-element-dta.md)<br /><br /> `Drop`-Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element hat den Namen **CreateTypecomplexType** im XML-Schema des Datenbankoptimierungsratgebers. Es wird zur Angabe von Indizes für eine hypothetische Konfiguration verwendet. Dieses `Recommendation`-Element ist nicht mit den anderen Typen identisch, die zum Angeben von Partitionierungen (`RecommendationPType`) oder Sichten (`RecommendationViewType`) verwendet werden können. Informationen zu diesen anderen `Recommendation` Elementtypen finden Sie unter den [-Datenbank-Engine Tuning Advisor XML-Schema](https://go.microsoft.com/fwlink/?linkid=43100).  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
