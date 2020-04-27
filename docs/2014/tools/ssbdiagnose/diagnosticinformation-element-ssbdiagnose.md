---
title: DiagnosticInformation-Element (ssbdiagnose) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 55da8efd6ee5b330e259ed78bdd152720403f310
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63186903"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a>DiagnosticInformation-Element (ssbdiagnose)
  Das **DiagnosticInformation** -Element enthält alle Elemente, die die vom Hilfsprogramm gefundenen Diagnoseinformationen melden. **DiagnosticInformation** ist das Stammelement einer XML-Ausgabedatei von **ssbdiagnostic** .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|`None`|–|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine|  
|**Standardwert**|Keine|  
|**Vorkommt**|Einmal pro **ssbdiagnose** -XML-Ausgabedatei|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|Keine|  
|**Untergeordnete Elemente**|[Banner-Element &#40;ssbdiagnose&#41;](banner-element-ssbdiagnose.md)<br /><br /> [Issue-Element &#40;ssbdiagnose&#41;](issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu XML-Namespaces finden Sie unter [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) (in Englisch) in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  
