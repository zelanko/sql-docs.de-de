---
title: KeepExisting-Element (DTA)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 50741d36bfd0dd3b9f566954d1ef53b86be14609
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307641"
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
  
|Merkmal|BESCHREIBUNG|  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
