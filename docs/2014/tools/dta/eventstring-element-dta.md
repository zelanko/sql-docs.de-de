---
title: EventString-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30e46515fda5bf03a96e9f1168b470f635698d07
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52769512"
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
  
|Attribut|Description|  
|---------------|-----------------|  
|`Weight`|Dies ist optional. Gibt den Gewichtungsfaktor der Abfrage (ein Faktor für die Wichtigkeit) für das angegebene Ereignis an. Sie können die Gewichtung mit einem `float`-Datentyp angeben. Beispiel: `Weight`="100,01". Der Mindestwert für `Weight` ist "0".|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|`string`, Länge ist unbegrenzt.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich, wenn kein anderer Arbeitsauslastungstyp angegeben ist. Sie müssen ein untergeordnetes `EventString`-, `File`- oder `Database`-Element für das übergeordnete `Workload`-Element angeben. Es kann jedoch nur ein Typ verwendet werden. Wenn Sie beispielsweise eine Arbeitsauslastung mit dem `EventString`-Element angeben, können Sie in dieser XML-Eingabedatei keine Arbeitsauslastung mit dem `File`-Element angeben.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Workload-Element &#40;DTA&#41;](workload-element-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit Inlinearbeitsauslastung &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
