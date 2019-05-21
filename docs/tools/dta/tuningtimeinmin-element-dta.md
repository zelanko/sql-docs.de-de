---
title: TuningTimeInMin-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningTimeInMin element
ms.assetid: 4973d9ac-20fd-4ac3-bc9f-5d60e39fdb7d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 908b4b6b8f4551fd5b611997dabedc5f1cf1c474
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51292406"
---
# <a name="tuningtimeinmin-element-dta"></a>TuningTimeInMin-Element (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Gibt die maximale Dauer einer Optimierungssitzung in Minuten an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <TuningTimeInMin>...</TuningTimeInMin>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|**unsignedInt**, unbegrenzte Länge.|  
|**Standardwert**|480 Minuten (8 Stunden).|  
|**Vorkommen**|Erforderlich, sofern kein Wert für das **NumberOfEvents** -Element festgelegt wurde.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|None|  
  
## <a name="example"></a>Beispiel  
  
## <a name="description"></a>Beschreibung  
 Im folgenden Codebeispiel wird gezeigt, wie 12 Stunden als maximale Optimierungszeit festgelegt werden:  
  
## <a name="code"></a>Code  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <TuningTimeInMin>720</TuningTimeInMin>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [XML-Eingabedateireferenz &amp;amp;#40;Datenbankoptimierungsratgeber&amp;amp;#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
