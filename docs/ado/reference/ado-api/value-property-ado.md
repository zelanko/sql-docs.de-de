---
title: Value-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::Value
- _Parameter::Value
helpviewer_keywords:
- Value property [ADO]
ms.assetid: 48919c74-86d4-462e-99b9-8854ceb8d683
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 68bde5e78c746579bcb34166469569fb594c129f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710276"
---
# <a name="value-property-ado"></a>Value-Eigenschaft (ADO)

Gibt den zugewiesenen Wert einen [Feld](../../../ado/reference/ado-api/field-object.md), [Parameter](../../../ado/reference/ado-api/parameter-object.md), oder [Eigenschaft](../../../ado/reference/ado-api/property-object-ado.md) Objekt.
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte

Legt fest oder gibt einen **Variant** Wert, der den Wert des Objekts angibt. Standardmäßig ist der Wert hängt von der [Typ](../../../ado/reference/ado-api/type-property-ado.md) Eigenschaft.
  
## <a name="remarks"></a>Hinweise

Verwenden der **Wert** Eigenschaft so festlegen oder Zurückgeben von Daten aus **Feld** -Objekten zum Festlegen oder Zurückgeben der Parameterwerte mit **Parameter** Objekte oder zum Festlegen oder zurückgeben eigenschafteneinstellungen mit **Eigenschaft** Objekte. Ob die **Wert** Eigenschaft Lese-/Schreibzugriff oder schreibgeschützten hängt von zahlreichen Faktoren ab. Finden Sie unter den jeweiligen Objektthemen Weitere Informationen.

ADO ermöglicht das Festlegen und Zurückgeben von lange Binärdaten mit dem **Wert** Eigenschaft.
  
> [!NOTE]
> Für **Parameter** Objekte, die ADO-Lesevorgänge der **Wert** Eigenschaft nur einmal vom Anbieter. Enthält ein Befehl ein **Parameter** , deren **Wert** -Eigenschaft ist leer, und Sie erstellen eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) aus den Befehl aus, stellen Sie sicher, dass Sie zuerst schließen die  **Recordset** vor dem Abrufen der **Wert** Eigenschaft. Einige Anbieter, ansonsten die **Wert** Eigenschaft kann leer sein und wird nicht den richtigen Wert enthalten.
> 
> Für den neuen **Feld** Objekte, die angefügt wurden die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung von eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekt, das **Wert** Eigenschaft muss festgelegt werden vor allen anderen **Feld** Eigenschaften können angegeben werden. Zuerst, einen bestimmten Wert für die **Wert** Eigenschaft zugewiesen und [Update](../../../ado/reference/ado-api/update-method.md) auf die **Felder** Sammlung mit dem Namen. Klicken Sie dann auf andere Eigenschaften wie z. B. [Typ](../../../ado/reference/ado-api/type-property-ado.md) oder [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) zugegriffen werden kann.
  
## <a name="applies-to"></a>Gilt für
  
||||  
|-|-|-|  
|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|[Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|
  
## <a name="see-also"></a>Siehe auch

[Wert der Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/value-property-example-vb.md)
[Wert der Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/value-property-example-vc.md) 
