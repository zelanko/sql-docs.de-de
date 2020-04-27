---
title: Partitionierungs Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Partitioning element
ms.assetid: 9bc5d1d5-27a7-4434-966f-c3935794af27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: acf6d033595952186b411ef0e547858f8b59771b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62657235"
---
# <a name="partitioning-element-dta"></a>Partitioning-Element (DTA)
  Enthält das Partitionierungsschema, das der Datenbankoptimierungsratgeber bei der Analyse verwenden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <Partitioning>...</Partitioning>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|`string`, keine maximale Länge.|  
|**Zulässige Werte**|**NONE**<br /> Keine Partitionierung.<br /><br /> **FULL**<br /> Vollständige Partitionierung. (Erhöht die Leistung.)<br /><br /> **ALIGNED**<br /> Nur ausgerichtete Partitionierung. (Erleichtert die Verwaltbarkeit.)<br /><br /> Verwenden Sie nur einen dieser Werte mit diesem Element.<br /><br /> **ALIGNED** bedeutet, dass in der vom Datenbankoptimierungsratgeber generierten Empfehlung jeder vorgeschlagene Index auf exakt dieselbe Weise partitioniert wird wie die zugrunde liegende Tabelle, für die der Index definiert ist. Nicht gruppierte Indizes für eine indizierte Sicht werden mit der indizierten Sicht ausgerichtet.|  
|**Standardwert**|**NONE**|  
|**Vorkommen**|Einmalig erforderlich für das `TuningOptions`-Element, es sei denn, das `DropOnlyMode`-Element wird verwendet. Wird das `DropOnlyMode`-Element verwendet, kann das `Partitioning`-Element nicht verwendet werden. Diese Elemente schließen sich gegenseitig aus.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine einfache XML-Eingabedatei &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
