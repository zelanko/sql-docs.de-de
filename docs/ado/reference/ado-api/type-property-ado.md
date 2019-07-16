---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ee1058299becb4a7a4234debc097516cb02dd41
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937869"
---
# <a name="type-property-ado"></a>Type-Eigenschaft (ADO)
Gibt an, die betriebliche Typ oder den Datentyp einer [Parameter](../../../ado/reference/ado-api/parameter-object.md), [Feld](../../../ado/reference/ado-api/field-object.md), oder [Eigenschaft](../../../ado/reference/ado-api/property-object-ado.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) Wert.  
  
## <a name="remarks"></a>Hinweise  
 Für **Parameter** Objekte, die **Typ** Eigenschaft schreibgeschützt ist. Für den neuen **Feld** Objekte, die angefügt wurden die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung von einer [Datensatz](../../../ado/reference/ado-api/record-object-ado.md), **Typ** ist Lese-/Schreibzugriff nur, nachdem die [ Wert](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft für die **Feld** angegeben wurde und der neue der Datenanbieter wurde erfolgreich hinzugefügt **Feld** durch Aufrufen der [aktualisieren](../../../ado/reference/ado-api/update-method.md)Methode der **Felder** Auflistung.  
  
 Für alle anderen Objekte die **Typ** Eigenschaft ist schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|[Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Type-Eigenschaft – Beispiel (Field) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Type-Eigenschaft – Beispiel (Eigenschaft) (VC++)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [RecordType-Eigenschaft (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type-Eigenschaft (ADO Stream)](../../../ado/reference/ado-api/type-property-ado-stream.md)
