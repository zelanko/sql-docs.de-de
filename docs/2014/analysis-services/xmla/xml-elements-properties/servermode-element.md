---
title: ServerMode-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: c2f8cb39-dad7-433b-b7b7-fb1625f76a84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6e714c9f5bbc7626030d83faa7d0058c7aa13752
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140180"
---
# <a name="servermode-element"></a>ServerMode-Element
  Das `ServerMode`-Serverelement gibt den Modus an, in dem der Server arbeitet.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Server>  
...  
   <ddl300:ServerMode>...</ddl300:ServerMode>  
...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|(none)|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Server](../../scripting/objects/server-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Server arbeitet in einem der folgenden beiden Modi:  
  
|value|Description|  
|-----------|-----------------|  
|*Mehrdimensionale*|Mehrdimensionaler und Data Mining-Modus|  
|*Tabellarisch*|Tabellenmodus|  
|*SharePoint*|SharePoint-Modus|  
  
## <a name="see-also"></a>Siehe auch  
 [Server](../../scripting/objects/server-element-assl.md)  
  
  
