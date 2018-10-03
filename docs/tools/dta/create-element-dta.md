---
title: Create-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc05d9c20affd1d995312c261b68dac178f8ddb7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47754578"
---
# <a name="create-element-dta"></a>Create-Element (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Enthält Informationen zu den Indizes, Statistiken oder Heapstrukturen in einer benutzerspezifischen Konfiguration.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|und Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich pro physischem Entwurfsstrukturtyp (Indizes, Statistiken oder Heapstrukturen).|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Recommendation-Element &#40;DTA&#41;](../../tools/dta/recommendation-element-dta.md)|  
|**Untergeordnete Elemente**|[Index-Element &#40;DTA&#41;](../../tools/dta/index-element-dta.md)<br /><br /> **Statistics**-Element (weitere Informationen finden Sie im Thema zum [XML-Schema für den Datenbankoptimierungsratgeber](http://schemas.microsoft.com/sqlserver/))<br /><br /> **Heap** -Element (weitere Informationen finden Sie im Thema zum [XML-Schema für den Datenbankoptimierungsratgeber](http://schemas.microsoft.com/sqlserver/) )|  
  
## <a name="remarks"></a>Remarks  
 Dieses Element hat den Namen **CreateTypecomplexType** im XML-Schema des Datenbankoptimierungsratgebers. Es wird zum Erstellen von Indizes, Statistiken und Heapstrukturen für eine benutzerspezifische Konfiguration verwendet. Dieses **Create** -Element ist nicht mit den anderen Typen identisch, mit denen Sichten (**CreateViewType**) oder Partitionierungen (**CreatePType**) erstellt werden können. Unter [XML-Schema für den Datenbankoptimierungsratgeber](http://schemas.microsoft.com/sqlserver/) finden Sie Informationen zu diesen anderen **Create** -Elementtypen.  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [XML-Eingabedateireferenz &amp;amp;#40;Datenbankoptimierungsratgeber&amp;amp;#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
