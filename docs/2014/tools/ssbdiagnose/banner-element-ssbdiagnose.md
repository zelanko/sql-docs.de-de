---
title: Banner-Element (Ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ccb62b49257c2f406bedb34e9bbf58c3bd40ffd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160825"
---
# <a name="banner-element-ssbdiagnose"></a>Banner-Element (ssbdiagnose)
  Identifiziert das Hilfsprogramm, das die XML-Ausgabedatei von **ssbdiagnose** generiert hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|attribute|Description|  
|---------------|-----------------|  
|`title`|Identifiziert das Hilfsprogramm, das die XML-Ausgabedatei von **ssbdiagnose** generiert hat.|  
|`product`|Identifiziert das Produkt, das die XML-Ausgabedatei von **ssbdiagnose** generiert hat.|  
|`version`|Identifiziert die Version des Hilfsprogramms, das die XML-Ausgabedatei generiert hat.|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmal pro XML-Ausgabedatei von **ssbdiagnose**|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[DiagnosticInformation-Element &#40;Ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein Banner-Element.  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  