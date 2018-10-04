---
title: Database-Element für Konfiguration (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1a3547d10f325e047174f7106267b480084e88df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062034"
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
  
  
