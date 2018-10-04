---
title: ReadWriteMode-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- ReadWriteMode command
ms.assetid: 379bcaca-bb7e-4934-a9e7-21f8ede2fdc7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa1febe828bf8711ff87f50cfd5a8ce7cbd6eed8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166650"
---
# <a name="readwritemode-element"></a>ReadWriteMode-Element
  Die `ReadWriteMode`-Datenbankeigenschaft gibt an, ob sich die Datenbank im `ReadWrite`-Modus oder im `ReadOnly`-Modus befindet. Hierbei handelt es sich um die beiden einzigen möglichen Werte der Eigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|ReadWrite|  
|Cardinality|0-1: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Datenbank](database-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Datenbanken können nur im `ReadWrite`-Modus erstellt werden. Datenbanken können nicht im `ReadOnly`-Modus erstellt werden.  
  
 Der Wert des der `ReadWriteMode` -Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*ReadOnly*|Es können keine Änderungen oder Updates auf die Datenbank angewendet werden.|  
|*"ReadWrite"*|Es können Änderungen oder Updates auf die Datenbank angewendet werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Attach-Element](../xml-elements-commands/attach-element.md)   
 [Anfügen und Trennen von Analysis Services-Datenbanken](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Verschieben einer Analysis Services-Datenbank](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Datenbank-ReadWriteModes](../../multidimensional-models/database-readwritemodes.md)   
 [Umschalten einer Analysis Services-Datenbank zwischen Schreib-und Lesemodus](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
