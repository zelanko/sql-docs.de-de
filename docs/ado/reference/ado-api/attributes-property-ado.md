---
description: Attributes-Eigenschaft (ADO)
title: Attribute-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Attributes
- Field20::Attributes
- _Parameter::Attributes
helpviewer_keywords:
- Attributes property [ADO]
ms.assetid: acc15d40-68a6-4ba9-85bd-12d331aecaa6
author: rothja
ms.author: jroth
ms.openlocfilehash: ceb141b0ecdbc278e324f19f3bd4b3d7ed1b4eb6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975941"
---
# <a name="attributes-property-ado"></a>Attributes-Eigenschaft (ADO)
Gibt eine oder mehrere Eigenschaften eines Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest oder gibt ihn zurück.  
  
 Für ein [Verbindungs](./connection-object-ado.md) Objekt lautet die Eigenschaft **Attribute** Lese-/Schreibzugriff, und ihr Wert kann die Summe von einem oder mehreren [XactAttributeEnum](./xactattributeenum.md) -Werten sein. Der Standardwert ist null (0).  
  
 Bei einem [Parameter](./parameter-object.md) Objekt lautet die Eigenschaft **Attribute** Lese-/Schreibzugriff, und ihr Wert kann die Summe von einem oder mehreren [parameterattributesenum](./parameterattributesenum.md) -Werten sein. Der Standardwert ist **adparamsigned**.  
  
 Bei einem [Feld](./field-object.md) Objekt kann die Eigenschaft **Attribute** die Summe von einem oder mehreren [FieldAttributeEnum](./fieldattributeenum.md) -Werten sein. Normalerweise ist sie schreibgeschützt. Bei neuen **Feld** Objekten, die an die [Fields](./fields-collection-ado.md) -Auflistung eines [Datensatzes](./record-object-ado.md)angehängt wurden, werden **Attribute** nur dann gelesen/geschrieben, wenn die [value](./value-property-ado.md) -Eigenschaft für das **Feld** angegeben wurde und das neue **Feld** durch Aufrufen der [Update](./update-method.md) -Methode der **Fields** -Auflistung erfolgreich vom Datenanbieter hinzugefügt wurde.  
  
 Für ein [Property](./property-object-ado.md) -Objekt ist die **Attribute** -Eigenschaft schreibgeschützt, und ihr Wert kann die Summe von einem oder mehreren [propertyattributesenum](./propertyattributesenum.md) -Werten sein.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der Eigenschaft **Attribute** können Sie Merkmale von **Verbindungs** Objekten, **Parameter** Objekten, **Feld** Objekten oder **Eigenschafts** Objekten festlegen oder zurückgeben.  
  
 Wenn Sie mehrere Attribute festlegen, können Sie die entsprechenden Konstanten summieren. Wenn Sie den-Eigenschafts Wert auf eine Summe einschließlich nicht kompatibler Konstanten festlegen, tritt ein Fehler auf.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Diese Eigenschaft ist für ein Client seitiges **Verbindungs** Objekt nicht verfügbar.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Connection-Objekt (ADO)](./connection-object-ado.md)  
        [Field-Objekt](./field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter-Objekt](./parameter-object.md)  
        [Property-Objekt (ADO)](./property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Attribute und namens Eigenschaften (VB)](./attributes-and-name-properties-example-vb.md)   
 [Beispiel für Attribute und namens Eigenschaften (VC + +)](./attributes-and-name-properties-example-vc.md)   
 [AppendChunk-Methode (ADO)](./appendchunk-method-ado.md)   
 [BeginTrans-, CommitTrans-und RollbackTrans-Methode (ADO)](./begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [GetChunk-Methode (ADO)](./getchunk-method-ado.md)