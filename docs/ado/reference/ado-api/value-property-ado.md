---
description: Value-Eigenschaft (ADO)
title: Value-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: bc7ea2b5f571429d05b8201d8e23dc594bb896e8
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987991"
---
# <a name="value-property-ado"></a>Value-Eigenschaft (ADO)

Gibt den Wert an, der einem [Feld](./field-object.md), einem [Parameter](./parameter-object.md)oder einem [Eigenschafts](./property-object-ado.md) Objekt zugewiesen ist.
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte

Legt einen **Variant** -Wert fest, der den Wert des-Objekts angibt, oder gibt diesen zurück. Der Standardwert hängt von der [Type](./type-property-ado.md) -Eigenschaft ab.
  
## <a name="remarks"></a>Bemerkungen

Verwenden Sie die **value** -Eigenschaft zum Festlegen oder Zurückgeben von Daten aus **Feld** Objekten, zum Festlegen oder Zurückgeben von Parameterwerten mit **Parameter** Objekten oder zum Festlegen oder Zurückgeben von Eigenschafts Einstellungen mit **Eigenschafts** Objekten. Ob die **value** -Eigenschaft Lese-/Schreibzugriff hat oder schreibgeschützt ist, hängt von zahlreichen Faktoren ab. Weitere Informationen finden Sie in den jeweiligen Objekt Themen.

ADO ermöglicht das Festlegen und Zurückgeben von langen Binärdaten mit der **value** -Eigenschaft.
  
> [!NOTE]
> Bei **Parameter** Objekten liest ADO die **value** -Eigenschaft nur einmal vom Anbieter. Wenn ein Befehl einen **Parameter** enthält, dessen **value** -Eigenschaft leer ist, und Sie ein [Recordset](./recordset-object-ado.md) mit dem Befehl erstellen, müssen Sie zuerst das **Recordset** schließen, bevor Sie die **value** -Eigenschaft abrufen. Andernfalls ist für einige Anbieter die **value** -Eigenschaft möglicherweise leer und enthält nicht den richtigen Wert.
> 
> Bei neuen **Feld** Objekten, die an die [Fields](./fields-collection-ado.md) -Auflistung eines [Datensatz](./record-object-ado.md) -Objekts angehängt wurden, muss die **value** -Eigenschaft festgelegt werden, bevor andere **Feld** Eigenschaften angegeben werden können. Zuerst muss ein bestimmter Wert für die **value** -Eigenschaft zugewiesen und in der **Fields** -Auflistung mit dem Namen [aktualisiert](./update-method.md) werden. Anschließend können Sie auf andere Eigenschaften, z. b. den [Typ](./type-property-ado.md) oder die [Attribute](./attributes-property-ado.md) , zugreifen.
  
## <a name="applies-to"></a>Gilt für

:::row:::
    :::column:::
        [Field-Objekt](./field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter-Objekt](./parameter-object.md)  
    :::column-end:::
    :::column:::
        [Property-Objekt (ADO)](./property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen

[Beispiel für Wert Eigenschaft (VB)](./value-property-example-vb.md) 
 [Beispiel für Wert Eigenschaft (VC + +)](./value-property-example-vc.md)