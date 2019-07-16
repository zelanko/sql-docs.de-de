---
title: Property-Objekt (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Property
helpviewer_keywords:
- Property object [ADO]
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 43bfa816a9ca8a93cdc1188a98e54d3e0d9111b1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917556"
---
# <a name="property-object-ado"></a>Property-Objekt (ADO)
Repräsentiert eine dynamische Eigenschaft eines ADO-Objekts, das vom Anbieter definiert ist.  
  
## <a name="remarks"></a>Hinweise  
 ADO-Objekte verfügen über zwei Typen von Eigenschaften: integrierte und dynamische.  
  
 Integrierte Eigenschaften sind diese Eigenschaften in ADO implementiert und kann sofort auf eine neue Objekt mithilfe der `MyObject.Property` Syntax. Sie erscheinen nicht als **Eigenschaft** Objekte in ein Objekt des [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung, damit Sie ihre Werte können jedoch ändern, können Sie ihre Merkmale nicht ändern.  
  
 Dynamische Eigenschaften werden von den zugrunde liegenden Datenanbieter definiert und werden in der **Eigenschaften** Auflistung für den entsprechenden ADO-Objekts. Beispielsweise kann eine Eigenschaft, die für den Anbieter spezifisch angibt, ob eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt unterstützt, Transaktionen oder aktualisieren. Diese zusätzlichen Eigenschaften werden angezeigt, als **Eigenschaft** Objekte in diesem **Recordset** des Objekts **Eigenschaften** Auflistung. Dynamische Eigenschaften verwiesen werden können, nur über die Auflistung, mit der `MyObject.Properties(0)` oder `MyObject.Properties("Name")` Syntax.  
  
 Beide Arten der Eigenschaft kann nicht gelöscht werden.  
  
 Eine dynamische **Eigenschaft** Objekt verfügt über vier integrierte Eigenschaften selbst:  
  
-   Die [Namen](../../../ado/reference/ado-api/name-property-ado.md) Eigenschaft ist eine Zeichenfolge, die die Eigenschaft identifiziert.  
  
-   Die [Typ](../../../ado/reference/ado-api/type-property-ado.md) -Eigenschaft ist eine ganze Zahl, die den Datentyp der Eigenschaft angibt.  
  
-   Die [Wert](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft ist eine Variante, die die Einstellung der Eigenschaft enthält. **Wert** ist die Standardeigenschaft für eine **Eigenschaft** Objekt.  
  
-   Die [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) -Eigenschaft ist ein long-Wert, der Merkmale der Eigenschaft für den Anbieter spezifisch angibt.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
