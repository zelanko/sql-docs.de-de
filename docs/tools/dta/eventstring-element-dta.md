---
title: EventString-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
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
ms.openlocfilehash: 7cda4271865d7e69450bff5180164748152d6483
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642858"
---
# <a name="eventstring-element-dta"></a>EventString-Element (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
|attribute|und Beschreibung|  
|---------------|-----------------|  
|**Weight**|Optional. Gibt den Gewichtungsfaktor der Abfrage (ein Faktor für die Wichtigkeit) für das angegebene Ereignis an. Sie können die Gewichtung mit einem **float** -Datentyp angeben. Beispiel: **Weight**="100.01". Der Mindestwert für **Weight** ist "0".|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|und Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|**string**, unbegrenzte Länge.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich, wenn kein anderer Arbeitsauslastungstyp angegeben ist. Sie müssen ein untergeordnetes **EventString**-, **File**- oder **Database** -Element für das übergeordnete **Workload** -Element angeben. Es kann jedoch nur ein Typ verwendet werden. Wenn Sie beispielsweise eine Arbeitsauslastung mit dem **EventString** -Element angeben, können Sie in dieser XML-Eingabedatei keine Arbeitsauslastung mit dem **File** -Element angeben.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Workload-Element &#40;DTA&#41;](../../tools/dta/workload-element-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit Inlinearbeitsauslastung &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [XML-Eingabedateireferenz &amp;amp;#40;Datenbankoptimierungsratgeber&amp;amp;#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
