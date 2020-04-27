---
title: DropOnlyMode-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f1d449defa98112c87a4b5789f1cff6f764252e3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62659574"
---
# <a name="droponlymode-element-dta"></a>DropOnlyMode-Element (DTA)
  Gibt an, dass der Datenbankoptimierungsratgeber während der Optimierungssitzung nur vorhandene Indizes, indizierte Sichten oder Partitionen löschen soll. Wenn diese Optimierungsoption angegeben ist, werden keine neuen physischen Entwurfsstrukturen berücksichtigt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine|  
|**Standardwert**|Keine|  
|**Vorkommt**|Optional. Nur einmalige Verwendung pro `TuningOptions`-Element möglich. Keine Verwendung möglich, wenn im `TuningOptions`-Element die folgenden Elemente angegeben sind:<br /><br /> [FeatureSet-Element &#40;DTA&#41;](featureset-element-dta.md)<br /><br /> [Partitioning-Element &#40;DTA&#41;](partitioning-element-dta.md)<br /><br /> [KeepExisting-Element &#40;DTA&#41;](keepexisting-element-dta.md) ist auf **ALL** festgelegt|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|Keine|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht den `TuningOptions`-Abschnitt einer XML-Eingabedatei des Datenbankoptimierungsratgebers, wobei `DropOnlyMode` angegeben ist. In diesem Beispiel ist die Optimierungszeit auf 24 Stunden (1440 Minuten) begrenzt, und alle vorhandenen gruppierten und nicht gruppierten Indizes sollen gelöscht werden:  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
