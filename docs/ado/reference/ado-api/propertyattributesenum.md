---
title: PropertyAttributesEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PropertyAttributesEnum
helpviewer_keywords:
- PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 624fa1976792a700342a114f82aa5ca6b75c70ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931564"
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
Gibt die Attribute einer [Eigenschaft](../../../ado/reference/ado-api/property-object-ado.md) Objekt.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|Gibt an, dass die Eigenschaft nicht vom Anbieter unterstützt wird.|  
|**adPropRequired**|1|Gibt an, dass der Benutzer einen Wert für diese Eigenschaft angeben muss, bevor die Datenquelle initialisiert wird.|  
|**adPropOptional**|2|Gibt an, dass der Benutzer nicht notwendigerweise an einen Wert für diese Eigenschaft vor der Initialisierung der Datenquelle.|  
|**adPropRead**|512|Gibt an, dass der Benutzer die Eigenschaft gelesen werden kann.|  
|**adPropWrite**|1024|Gibt an, dass der Benutzer die Eigenschaft festlegen kann.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.PropertyAttributes.NOTSUPPORTED|  
|AdoEnums.PropertyAttributes.REQUIRED|  
|AdoEnums.PropertyAttributes.OPTIONAL|  
|AdoEnums.PropertyAttributes.READ|  
|AdoEnums.PropertyAttributes.WRITE|  
  
## <a name="applies-to"></a>Gilt für  
 [Attributes-Eigenschaft (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
