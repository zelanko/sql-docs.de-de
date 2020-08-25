---
description: PropertyAttributesEnum
title: Propertyattributesumum | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 823505aae912c64c2fd7d3375b3426cb6428bcdd
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88772869"
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
Gibt die Attribute eines [Eigenschafts](./property-object-ado.md) Objekts an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adpropnotsupported**|0|Gibt an, dass die Eigenschaft vom Anbieter nicht unterstützt wird.|  
|**adproprequired**|1|Gibt an, dass der Benutzer einen Wert für diese Eigenschaft angeben muss, bevor die Datenquelle initialisiert wird.|  
|**adpropoptional**|2|Gibt an, dass der Benutzer keinen Wert für diese Eigenschaft angeben muss, bevor die Datenquelle initialisiert wird.|  
|**adpropread**|512|Gibt an, dass der Benutzer die Eigenschaft lesen kann.|  
|**adpropwrite**|1024|Gibt an, dass der Benutzer die-Eigenschaft festlegen kann.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. PropertyAttribute. NotSupported|  
|Adoumums. PropertyAttribute. required|  
|Adoumums. PropertyAttribute. optional|  
|Adoumums. PropertyAttribute. Read|  
|Adoumums. PropertyAttribute. Write|  
  
## <a name="applies-to"></a>Gilt für  
 [Attributes-Eigenschaft (ADO)](./attributes-property-ado.md)