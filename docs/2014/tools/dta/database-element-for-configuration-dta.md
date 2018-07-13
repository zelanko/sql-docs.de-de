---
title: Database-Element für Konfiguration (DTA) | Microsoft-Dokumentation
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
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fa99c86b6e4cc6705a04f0b1eecd1695033f50de
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263886"
---
# <a name="database-element-for-configuration-dta"></a>Database-Element für Konfiguration (DTA)
  Gibt die Datenbank, die für die der Datenbankoptimierungsratgeber die hypothetische Konfiguration auswerten soll (angegeben durch die `Configuration` Element).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Erforderlich einmal oder mehrmals pro `Server` Element.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Server-Element für Konfiguration &#40;DTA&#41;](server-element-for-configuration-dta.md)|  
|**Untergeordnete Elemente**|[Namen von Element für Datenbank &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Schema-Element für Datenbank &#40;DTA&#41;](schema-element-for-database-dta.md)<br /><br /> [Recommendation-Element &#40;DTA&#41;](recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element hat den Namen **DatabaseTypecomplexType** im XML-Schema des Datenbankoptimierungsratgebers. Dieses `Database`-Element ist nicht mit dem Element identisch, dessen übergeordnetes Stammelement das `Server`-Element ist. Dieses Element wird oben in der XML-Eingabedatei angezeigt. Weitere Informationen finden Sie unter [Database-Element für Server &#40;DTA&#41;](database-element-for-server-dta.md).  
  
## <a name="example"></a>Beispiel  
 Ein Verwendungsbeispiel dieser `Database` Element finden Sie unter den [XML-Eingabe-Beispieldatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 
  [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
