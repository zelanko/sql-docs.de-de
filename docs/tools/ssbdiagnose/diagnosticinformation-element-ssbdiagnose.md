---
title: DiagnosticInformation-Element (ssbdiagnose) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0d20ef070a390eb942b29498381da9e2479d0218
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986180"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a>DiagnosticInformation-Element (ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das **DiagnosticInformation** -Element enthält alle Elemente, die die vom Hilfsprogramm gefundenen Diagnoseinformationen melden. **DiagnosticInformation** ist das Stammelement einer XML-Ausgabedatei von **ssbdiagnostic** .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|attribute|und Beschreibung|  
|---------------|-----------------|  
|**None**|–|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|und Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmal pro **ssbdiagnose** -XML-Ausgabedatei|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|Keine.|  
|**Untergeordnete Elemente**|[Banner-Element &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)<br /><br /> [Issue-Element &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen zu XML-Namespaces finden Sie unter [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) (in Englisch) in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
