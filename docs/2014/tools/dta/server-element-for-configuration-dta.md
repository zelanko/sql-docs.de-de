---
title: Server-Element für Konfiguration (DTA) | Microsoft-Dokumentation
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
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 21efaa212459a89622d920c0dc4adcf2f828f1bf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37214270"
---
# <a name="server-element-for-configuration-dta"></a>Server-Element für Konfiguration (DTA)
  Enthält die Identifikationsinformationen für den Server, der Datenbankoptimierungsratgeber die hypothetische Konfiguration auswerten soll (angegeben durch die `Configuration` Element).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Erforderlich einmal pro `Configuration` Element.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Konfigurationselement &#40;DTA&#41;](configuration-element-dta.md)|  
|**Untergeordnete Elemente**|[Benennen Sie Element für Server &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Database-Element für Konfiguration &#40;DTA&#41;](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Hinweise  
 Geben Sie nur einen `Server` -Element für die `Configuration` Element. Dieses Element hat den Namen **ServerTypecomplexType** im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100). Verwechseln Sie dies nicht `Server` Element mit dem das untergeordnete Element ist die `DTAInput` Element. Weitere Informationen finden Sie unter [Server-Element &#40;DTA&#41;](server-element-dta.md).  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Syntax finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 
  [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
