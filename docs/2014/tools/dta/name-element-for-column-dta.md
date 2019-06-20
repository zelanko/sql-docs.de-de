---
title: Namen von Element für Spalte (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: f93b61de-01fe-4237-ada4-f1e481550564
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d3d95ce69743caaa6b587195ba107774d8cd8454
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63297519"
---
# <a name="name-element-for-column-dta"></a>Name-Element für Spalte (DTA)
  Gibt den Namen für eine Indexspalte in einer benutzerdefinierten Konfiguration an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Index>  
    <Column>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|`string`, unbegrenzte Länge.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Für jedes `Column`-Element erforderlich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Column-Element für Index &#40;DTA&#41;](column-element-for-index-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
