---
title: PermissionsSet-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PermissionSet Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PermissionSet
helpviewer_keywords:
- PermissionSet element
ms.assetid: da5a9175-48e4-4b5e-a780-3e0077939974
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a6246058af826a73b589f1854b0236de946a4d65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149734"
---
# <a name="permissionset-element-assl"></a>PermissionsSet-Element (ASSL)
  Identifiziert den zugeordneten Berechtigungssatz eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework-Assembly.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ClrAssembly>  
   ...  
   <PermissionSet>...</PermissionSet>  
  
</ClrAssembly>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Safe*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Safe*|Nur interne Berechnung und lokaler Datenzugriff werden ermöglicht. *Safe* ist der restriktivste Berechtigungssatz. Code, der von einer Assembly mit *Safe* -Berechtigungen ausgeführt wird, hat keinen Zugriff auf externe Systemressourcen wie Dateien, das Netzwerk, Umgebungsvariablen oder die Registrierung.|  
|*"ExternalAccess"*|*Safe*, mit der zusätzlichen Fähigkeit, auf externe Systemressourcen wie Dateien, Netzwerke, Webdienste, Umgebungsvariablen und die Registrierung zuzugreifen.|  
|*Nicht eingeschränkt*|Uneingeschränkte ermöglicht Assemblys den uneingeschränkten Zugriff auf Ressourcen sowohl innerhalb als auch außerhalb [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Code, der innerhalb einer *Unrestricted* -Assembly ausgeführt wird, kann nicht verwalteten Code aufrufen.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `PermissionSet` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.PermissionSet>.  
  
## <a name="see-also"></a>Siehe auch  
 [ComAssembly-Datentyp &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Assemblies-Element &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Database-Element &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Server-Element &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  