---
title: ConnectionStringSecurity-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6237271e3952c05c9c7b231332454aaf2aa0c3ed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219427"
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
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataSource](../objects/datasource-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*PasswordRemoved*|Das Kennwort wurde aus der Verbindungszeichenfolge entfernt.|  
|*unverändert*|Die Verbindungszeichenfolge wurde nicht geändert.|  
  
 Die Enumeration, der den zulässigen Werten für `ConnectionStringSecurity` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ConnectionStringSecurity>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
