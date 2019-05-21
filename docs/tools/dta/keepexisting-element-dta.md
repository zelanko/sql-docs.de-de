---
title: KeepExisting-Element (DTA) | Microsoft-Dokumentation
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
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ece977251d71ff25a0dba52a0ba4f2d1f72d55a1
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51290826"
---
# <a name="keepexisting-element-dta"></a>KeepExisting-Element (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Gibt die physischen Entwurfsstrukturen (Indizes, indizierte Sichten oder Partitionierung) an, die der Datenbankoptimierungsratgeber beim Generieren der Empfehlung beibehalten muss.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|**string**, Grenzwert für die Länge wird vom Server erzwungen.|  
|**Zulässige Werte**|**NONE**<br /> Keine vorhandenen Strukturen.<br /><br /> **ALL**<br /> Alle vorhandenen Strukturen.<br /><br /> **ALIGNED**<br /> Alle Strukturen mit ausgerichteten Partitionen.<br /><br /> **CL_IDX**<br /> Alle gruppierten Indizes für Tabellen.<br /><br /> **IDX**<br /> Alle gruppierten und nicht gruppierten Indizes für Tabellen.<br /><br /> Verwenden Sie nur einen dieser Werte mit diesem Element.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Optional. Nur einmalige Verwendung pro **TuningOptions** -Element möglich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine einfache XML-Eingabedatei &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [XML-Eingabedateireferenz &amp;amp;#40;Datenbankoptimierungsratgeber&amp;amp;#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
