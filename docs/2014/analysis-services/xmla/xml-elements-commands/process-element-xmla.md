---
title: Element (XMLA) verarbeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Process Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Process
- http://schemas.microsoft.com/analysisservices/2003/engine#Process
- microsoft.xml.analysis.process
helpviewer_keywords:
- Process command
ms.assetid: 886fd480-c0e6-4c9b-b65e-da47f874d938
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec706973bca433a64d6a27201264509ade5ce773
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149460"
---
# <a name="process-element-xmla"></a>Process-Element (XMLA)
  Verarbeitet Objekte auf einer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Process>  
      <Type>...</Type>  
      <Object>...</Object>  
      <Bindings>...</Bindings>  
      <DataSource>...</DataSource>  
      <DataSourceView>...</DataSourceView>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <WriteBackTableCreation>...</WriteBackTableCreation>  
   </Process>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Bindungen](../xml-elements-properties/bindings-element-xmla.md), [DataSource](../xml-elements-properties/source-element-xmla.md), [DataSourceView](../xml-elements-properties/datasourceview-element-xmla.md), [ErrorConfiguration](../xml-elements-properties/errorconfiguration-element-xmla.md), [Objekt](../xml-elements-properties/object-element-xmla.md), [Typ Element &#40;XMLA&#41;](../xml-elements-properties/type-element-xmla.md), [WriteBackTableCreation](../xml-elements-properties/writebacktablecreation-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Verarbeitung von Objekten finden Sie unter [Verarbeiten von Objekten &#40;XMLA&#41;](../xml-elements-objects.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
