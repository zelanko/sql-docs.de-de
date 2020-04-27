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
ms.openlocfilehash: e35dd93e6d90a81934d8f272ea79c5eb7c8a97c2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67913924"
---
# <a name="value-property-ado"></a>Value-Eigenschaft (ADO)

Gibt den Wert an, der einem [Feld](../../../ado/reference/ado-api/field-object.md), einem [Parameter](../../../ado/reference/ado-api/parameter-object.md)oder einem [Eigenschafts](../../../ado/reference/ado-api/property-object-ado.md) Objekt zugewiesen ist.
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte

Legt einen **Variant** -Wert fest, der den Wert des-Objekts angibt, oder gibt diesen zurück. Der Standardwert hängt von der [Type](../../../ado/reference/ado-api/type-property-ado.md) -Eigenschaft ab.
  
## <a name="remarks"></a>Hinweise

Verwenden Sie die **value** -Eigenschaft zum Festlegen oder Zurückgeben von Daten aus **Feld** Objekten, zum Festlegen oder Zurückgeben von Parameterwerten mit **Parameter** Objekten oder zum Festlegen oder Zurückgeben von Eigenschafts Einstellungen mit **Eigenschafts** Objekten. Ob die **value** -Eigenschaft Lese-/Schreibzugriff hat oder schreibgeschützt ist, hängt von zahlreichen Faktoren ab. Weitere Informationen finden Sie in den jeweiligen Objekt Themen.

ADO ermöglicht das Festlegen und Zurückgeben von langen Binärdaten mit der **value** -Eigenschaft.
  
> [!NOTE]
> Bei **Parameter** Objekten liest ADO die **value** -Eigenschaft nur einmal vom Anbieter. Wenn ein Befehl einen **Parameter** enthält, dessen **value** -Eigenschaft leer ist, und Sie ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) mit dem Befehl erstellen, müssen Sie zuerst das **Recordset** schließen, bevor Sie die **value** -Eigenschaft abrufen. Andernfalls ist für einige Anbieter die **value** -Eigenschaft möglicherweise leer und enthält nicht den richtigen Wert.
> 
> Bei neuen **Feld** Objekten, die an die [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung eines [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekts angehängt wurden, muss die **value** -Eigenschaft festgelegt werden, bevor andere **Feld** Eigenschaften angegeben werden können. Zuerst muss ein bestimmter Wert für die **value** -Eigenschaft zugewiesen und in der **Fields** -Auflistung mit dem Namen [aktualisiert](../../../ado/reference/ado-api/update-method.md) werden. Anschließend können Sie auf andere Eigenschaften, z. b. den [Typ](../../../ado/reference/ado-api/type-property-ado.md) oder die [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) , zugreifen.
  
## <a name="applies-to"></a>Gilt für
  
||||  
|-|-|-|  
|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|[Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|
  
## <a name="see-also"></a>Weitere Informationen

[Beispiel für Wert Eigenschaft (VB)](../../../ado/reference/ado-api/value-property-example-vb.md)
[Wert Eigenschaft (VC + +)](../../../ado/reference/ado-api/value-property-example-vc.md) 
