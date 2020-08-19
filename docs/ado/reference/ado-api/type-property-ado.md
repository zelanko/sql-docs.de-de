---
description: Type-Eigenschaft (ADO)
title: Type-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Type
- Field20::Type
helpviewer_keywords:
- Type property [ADO]
ms.assetid: 8a4c079f-9f4f-4545-801d-85983b8db71e
author: rothja
ms.author: jroth
ms.openlocfilehash: de97e62a8152e7d14d1442cc1da9b5138ddc39fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441742"
---
# <a name="type-property-ado"></a>Type-Eigenschaft (ADO)
Gibt den Betriebs Typ oder den Datentyp eines [Parameters](../../../ado/reference/ado-api/parameter-object.md), [Felds](../../../ado/reference/ado-api/field-object.md)oder [Eigenschafts](../../../ado/reference/ado-api/property-object-ado.md) Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [datatyanum](../../../ado/reference/ado-api/datatypeenum.md) -Wert fest oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei **Parameter** Objekten ist die **Type** -Eigenschaft Lese-/Schreibzugriff. Bei neuen **Feld** Objekten, die an die [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung eines [Datensatzes](../../../ado/reference/ado-api/record-object-ado.md)angehängt wurden, ist der **Typ** Lese-/Schreibzugriff, wenn die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft für das **Feld** angegeben wurde und der Datenanbieter das neue **Feld** durch Aufrufen der [Update](../../../ado/reference/ado-api/update-method.md) -Methode der **Fields** -Auflistung erfolgreich hinzugefügt hat.  
  
 Für alle anderen Objekte ist die **Type** -Eigenschaft schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)  
    :::column-end:::
    :::column:::
        [Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Typeigenschaft (Feld) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Typeigenschafts Beispiel (Eigenschaft) (VC + +)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [RecordType-Eigenschaft (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type-Eigenschaft (ADO-Stream)](../../../ado/reference/ado-api/type-property-ado-stream.md)
