---
description: Property-Objekt (ADOX)
title: Property-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a836b5b0778aea77732036d1951db81aa790198
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439602"
---
# <a name="property-object-adox"></a>Property-Objekt (ADOX)
Stellt ein Merkmal eines ADOX-Objekts dar.  
  
## <a name="remarks"></a>Bemerkungen  
 ADOX-Objekte verfügen über zwei Arten von Eigenschaften: integrierte und dynamische Eigenschaften.  
  
 Integrierte Eigenschaften sind die Eigenschaften, die für jedes neue Objekt sofort verfügbar sind. dabei wird die Syntax MyObject. Property verwendet. Sie werden nicht als Eigenschafts Objekte in der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md)-Auflistung eines Objekts angezeigt, sodass Sie Ihre Werte ändern können, wenn Sie Ihre Werte ändern können.  
  
 Dynamische Eigenschaften werden vom zugrunde liegenden Datenanbieter definiert und in der Properties-Auflistung für das entsprechende ADOX-Objekt angezeigt.  Auf dynamische Eigenschaften kann nur über die Auflistung verwiesen werden, wobei die Syntax MyObject. Properties (0) oder MyObject. Properties ("Name") verwendet wird.  
  
 Beide Arten von Eigenschaften können nicht gelöscht werden.  
  
 Ein dynamisches Eigenschafts Objekt verfügt über vier eigenständig integrierte Eigenschaften:  
  
 Die [Name](../../../ado/reference/ado-api/name-property-ado.md) -Eigenschaft ist eine Zeichenfolge, die die-Eigenschaft bezeichnet.  
  
 Die [Type](../../../ado/reference/ado-api/type-property-ado.md) -Eigenschaft ist eine ganze Zahl, die den Eigenschafts Datentyp angibt.  
  
 Die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft ist eine Variante, die die Eigenschafts Einstellung enthält. Value ist die Standard Eigenschaft für ein Property-Objekt.  
  
 Die [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) -Eigenschaft ist ein langer Wert, der die Merkmale der Eigenschaft angibt, die für den Anbieter spezifisch sind.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [ADOX-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
