---
description: Property-Objekt (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8901f4b0f5372063b8aff88a47a7fddae13e66d7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442622"
---
# <a name="property-object-ado"></a>Property-Objekt (ADO)
Stellt eine dynamische Eigenschaft eines ADO-Objekts dar, das vom Anbieter definiert wird.  
  
## <a name="remarks"></a>Bemerkungen  
 ADO-Objekte verfügen über zwei Arten von Eigenschaften: integrierte und dynamische Eigenschaften.  
  
 Integrierte Eigenschaften sind die Eigenschaften, die in ADO implementiert werden und für jedes neue Objekt sofort verfügbar sind. dabei wird die- `MyObject.Property` Syntax verwendet. Sie werden nicht als **Eigenschafts** Objekte in der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung eines Objekts angezeigt, sodass Sie Ihre Werte ändern können, wenn Sie Ihre Werte ändern können.  
  
 Dynamische Eigenschaften werden vom zugrunde liegenden Datenanbieter definiert und in der **Properties** -Auflistung für das entsprechende ADO-Objekt angezeigt. Beispielsweise kann eine spezifische Eigenschaft für den Anbieter angeben, ob ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt Transaktionen oder Aktualisierungen unterstützt. Diese zusätzlichen Eigenschaften werden in der **Properties** -Auflistung des **Recordset** -Objekts als **Eigenschafts** Objekte angezeigt. Auf dynamische Eigenschaften kann nur mithilfe der-oder-Syntax über die-Auflistung verwiesen werden `MyObject.Properties(0)` `MyObject.Properties("Name")` .  
  
 Beide Arten von Eigenschaften können nicht gelöscht werden.  
  
 Ein dynamisches **Eigenschafts** Objekt verfügt über vier eigenständig integrierte Eigenschaften:  
  
-   Die [Name](../../../ado/reference/ado-api/name-property-ado.md) -Eigenschaft ist eine Zeichenfolge, die die-Eigenschaft bezeichnet.  
  
-   Die [Type](../../../ado/reference/ado-api/type-property-ado.md) -Eigenschaft ist eine ganze Zahl, die den Eigenschafts Datentyp angibt.  
  
-   Die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft ist eine Variante, die die Eigenschafts Einstellung enthält. **Value** ist die Standard Eigenschaft für ein **Property** -Objekt.  
  
-   Die [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) -Eigenschaft ist ein langer Wert, der die Merkmale der Eigenschaft angibt, die für den Anbieter spezifisch sind.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschafts Objekteigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
