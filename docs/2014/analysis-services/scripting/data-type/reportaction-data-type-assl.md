---
title: ReportAction-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportAction Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportAction
helpviewer_keywords:
- ReportAction data type
ms.assetid: b22f0d52-ed3a-4239-840e-0eaf172d7276
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eb1679d0275e6662116976b572f612f9ab113bb1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164321"
---
# <a name="reportaction-data-type-assl"></a>ReportAction-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der eine Aktion darstellt, die generiert eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Bericht.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ReportAction>  
   <!-- The following elements extend Action -->  
   <ReportServer>...</ReportServer>  
   <Path>...</Path>  
   <ReportParameters>...</ReportParameters>  
   <ReportFormatParameters>...</ReportFormatParameters>  
</ReportAction>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Aktion](action-data-type-assl.md)|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[Pfad](../properties/path-element-assl.md), [ReportFormatParameters](../collections/reportformatparameters-element-assl.md), [ReportParameters](../collections/reportparameters-element-assl.md), [ReportServer](../objects/server-element-assl.md)|  
|Abgeleitete Elemente|[Aktion](../objects/action-element-assl.md) ([Aktionen](../collections/actions-element-assl.md) Auflistung von [Cube](../objects/cube-element-assl.md) oder [Perspektive](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Der Berichtsserver antwortet auf URL-basierte Anforderungen nach Berichten. Die Berichtsaktion wird über einen Typen- *Report*definiert. Die Ressourcen und Parameter werden als Bestandteil der URL-Zeichenfolge an den Server gesendet, wenn die Aktion erstellt wird. Der Server macht die Aktion als Aktion des Typrowsets verfügbar.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
