---
title: ConnectionStringSecurity-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ConnectionStringSecurity Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ConnectionStringSecurity
helpviewer_keywords:
- ConnectionStringSecurity element
ms.assetid: f25c4448-bb0d-4945-bc84-9c015eefa0eb
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fce202b78364b4a3de68a33416922b929521727c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149517"
---
# <a name="connectionstringsecurity-element-assl"></a>ConnectionStringSecurity-Element (ASSL)
  Gibt an, ob das Kennwort des Benutzers von der Datenquellenverbindungszeichenfolge aus Sicherheitsgründen gelöscht wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataSource>  
   ...  
   <ConnectionStringSecurity>...</ConnectionStringSecurity>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataSource](../objects/datasource-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*PasswordRemoved*|Das Kennwort wurde aus der Verbindungszeichenfolge entfernt.|  
|*Unverändert*|Die Verbindungszeichenfolge wurde nicht geändert.|  
  
 Die Enumeration, die den zulässigen Werten für die entsprechende `ConnectionStringSecurity` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ConnectionStringSecurity>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  