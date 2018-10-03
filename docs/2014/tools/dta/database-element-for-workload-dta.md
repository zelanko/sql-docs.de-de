---
title: Database-Element zur Arbeitsauslastung (DTA) | Microsoft-Dokumentation
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
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f3f5f7d912a41476588662c4543b20c041b02672
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172140"
---
# <a name="database-element-for-workload-dta"></a>Database-Element zur Arbeitsauslastung (DTA)
  Gibt die Datenbank an, in der sich die Ablaufverfolgungstabelle der Arbeitsauslastung befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich, wenn kein anderer Arbeitsauslastungstyp angegeben ist. Müssen Sie angeben einer `EventString`, ein `File`, oder ein `Database` untergeordnete Element für die `Workload` übergeordneten, jedoch nur ein Typ kann verwendet werden. Angenommen, Sie geben Sie eine arbeitsauslastung mit dem `Database` -Element darf nicht auch Geben Sie eine arbeitsauslastung mit der `File` Element in der gleichen XML-Eingabedatei.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Workload-Element &#40;DTA&#41;](workload-element-dta.md)|  
|**Untergeordnete Elemente**|[Namen von Element für Datenbank &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Schema-Element für Datenbank &#40;DTA&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element hat den Namen **DatabaseDetailsTypecomplexType** im XML-Schema des Datenbankoptimierungsratgebers. Dieses `Database`-Element ist nicht mit dem identisch, dessen übergeordnetes Stammelement das `Configuration`-Element ist. (Weitere Informationen finden Sie unter [Database-Element für Konfiguration &#40;DTA&#41;](database-element-for-configuration-dta.md).)  
  
## <a name="example"></a>Beispiel  
 Ein Verwendungsbeispiel dieser `Database` Element finden Sie im Codebeispiel in [Workload-Element &#40;DTA&#41;](workload-element-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
