---
title: EventString-Element (DTA) | Microsoft-Dokumentation
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
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0ecfed53ebcecf38bbd46a6d3b15d1a8a8c741fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156020"
---
# <a name="eventstring-element-dta"></a>EventString-Element (DTA)
  Gibt eine auf einem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript basierende Arbeitsauslastung direkt in der XML-Eingabedatei an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|attribute|Description|  
|---------------|-----------------|  
|`Weight`|Optional. Gibt den Gewichtungsfaktor der Abfrage (ein Faktor für die Wichtigkeit) für das angegebene Ereignis an. Verwenden einer `float` -Datentyp geben Sie die Gewichtung an. Beispiel: `Weight`="100,01". Der Mindestwert für `Weight` ist "0".|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|`string`, Länge ist unbegrenzt.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich, wenn kein anderer Arbeitsauslastungstyp angegeben ist. Müssen Sie angeben einer `EventString`, ein `File`, oder ein `Database` untergeordnete Element für die `Workload` übergeordneten, jedoch nur ein Typ kann verwendet werden. Angenommen, Sie geben Sie eine arbeitsauslastung mit der `EventString` -Element, dann kann nicht auch angeben, eine arbeitsauslastung mit der `File` Element in der gleichen XML-Eingabedatei.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Workload-Element &#40;DTA&#41;](workload-element-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit Inlinearbeitsauslastung &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
