---
title: StorageBoundInMB-Element (DTA) | Microsoft-Dokumentation
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
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6931edc68458caf16c53b5d0671941ebd181d100
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51290652"
---
# <a name="storageboundinmb-element-dta"></a>StorageBoundInMB-Element (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Gibt die maximale Größe des Speicherplatzes in Megabyte an, der von der Optimierungsempfehlung des Datenbankoptimierungsratgebers (Index und Partitionierung) beansprucht werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|**unsignedInt**, unbegrenzte Länge.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Optional. Kann nur einmalig für das **TuningOptions** -Element verwendet werden.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|None|  
  
## <a name="remarks"></a>Remarks  
 Wenn mehrere Datenbanken optimiert werden, werden bei der Berechnung des Speicherplatzes Empfehlungen für alle Datenbanken berücksichtigt. Standardmäßig nimmt der Datenbankoptimierungsratgeber die kleinere der folgenden Speichergrößen an:  
  
-   Das Dreifache der aktuellen Rohdatengröße, einschließlich der Gesamtgröße von Heaps und gruppierten Indizes für Tabellen.  
  
-   Der freie Speicherplatz auf allen angefügten Laufwerken plus die Rohdatengröße.  
  
 Nicht im Standardspeicherplatz enthalten sind nicht gruppierte Indizes und indizierte Sichten.  
  
 Wenn der für das **StorageBoundInMB** -Element angegebene Wert den tatsächlichen Speicherplatz überschreitet, meldet der Datenbankoptimierungsratgeber einen Fehler, fährt aber mit der Optimierung fort. Nach der Optimierung können Sie Speicherplatz hinzufügen, wenn Sie die Empfehlung implementieren möchten.  
  
## <a name="example"></a>Beispiel  
  
## <a name="description"></a>Beschreibung  
 Im folgenden Codebeispiel wird veranschaulicht, wie 1500 Megabytes als maximaler Speicherplatz festgelegt werden, der von einer Empfehlung zur Optimierung belegt werden kann:  
  
## <a name="code"></a>Code  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [XML-Eingabedateireferenz &amp;amp;#40;Datenbankoptimierungsratgeber&amp;amp;#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
