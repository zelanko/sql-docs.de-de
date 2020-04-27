---
title: TuningOptions-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3050ce285cc98386f6de6278bedd2520cb39ba36
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63061064"
---
# <a name="tuningoptions-element-dta"></a>TuningOptions-Element (DTA)
  Enthält die Optimierungsoptionen für eine bestimmte Optimierungssitzung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Optional. Kann bei Verwendung nur einmalig pro `DTAInput`-Element verwendet werden.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[DTAInput-Element &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Untergeordnete Elemente**|`ReportSet`-Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `TuningLogTable`-Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `NumberOfEvents`-Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TuningTimeInMin-Element &#40;DTA&#41;](tuningtimeinmin-element-dta.md)<br /><br /> [StorageBoundInMB-Element &#40;DTA&#41;](storageboundinmb-element-dta.md)<br /><br /> `MaxKeyColumnsInIndex`-Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MaxColumnsInIndex`-Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MinPercentageImprovement`-Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TestServer-Element &#40;DTA&#41;](server-element-dta.md)<br /><br /> [FeatureSet-Element &#40;DTA&#41;](featureset-element-dta.md)<br /><br /> [Partitioning-Element &#40;DTA&#41;](partitioning-element-dta.md)<br /><br /> [DropOnlyMode-Element &#40;DTA&#41;](droponlymode-element-dta.md)<br /><br /> [KeepExisting-Element &#40;DTA&#41;](keepexisting-element-dta.md)<br /><br /> [OnlineIndexOperation-Element &#40;DTA&#41;](onlineindexoperation-element-dta.md)<br /><br /> [DatabaseToConnect-Element &#40;DTA&#41;](databasetoconnect-element-dta.md)<br /><br /> `IgnoreConstantsInWorkload`-Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `RetainShellDB`-Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Beispiel  
 Beispiele für das `TuningOptions` -Element finden Sie unter Beispiele für die [XML-Eingabedatei &#40;DTA&#41;](xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
