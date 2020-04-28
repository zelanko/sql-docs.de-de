---
title: Attribute-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b40b71dee32608756721d84a2e13f5f54f7bcbfa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920544"
---
# <a name="attributes-property-ado"></a>Attributes-Eigenschaft (ADO)
Gibt eine oder mehrere Eigenschaften eines Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest oder gibt ihn zurück.  
  
 Für ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt lautet die Eigenschaft **Attribute** Lese-/Schreibzugriff, und ihr Wert kann die Summe von einem oder mehreren [XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md) -Werten sein. Der Standardwert ist null (0).  
  
 Bei einem [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt lautet die Eigenschaft **Attribute** Lese-/Schreibzugriff, und ihr Wert kann die Summe von einem oder mehreren [parameterattributesenum](../../../ado/reference/ado-api/parameterattributesenum.md) -Werten sein. Der Standardwert ist **adparamsigned**.  
  
 Bei einem [Feld](../../../ado/reference/ado-api/field-object.md) Objekt kann die Eigenschaft **Attribute** die Summe von einem oder mehreren [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) -Werten sein. Normalerweise ist sie schreibgeschützt. Bei neuen **Feld** Objekten, die an die [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung eines [Datensatzes](../../../ado/reference/ado-api/record-object-ado.md)angehängt wurden, werden **Attribute** nur dann gelesen/geschrieben, wenn die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft für das **Feld** angegeben wurde und das neue **Feld** durch Aufrufen der [Update](../../../ado/reference/ado-api/update-method.md) -Methode der **Fields** -Auflistung erfolgreich vom Datenanbieter hinzugefügt wurde.  
  
 Für ein [Property](../../../ado/reference/ado-api/property-object-ado.md) -Objekt ist die **Attribute** -Eigenschaft schreibgeschützt, und ihr Wert kann die Summe von einem oder mehreren [propertyattributesenum](../../../ado/reference/ado-api/propertyattributesenum.md) -Werten sein.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der Eigenschaft **Attribute** können Sie Merkmale von **Verbindungs** Objekten, **Parameter** Objekten, **Feld** Objekten oder **Eigenschafts** Objekten festlegen oder zurückgeben.  
  
 Wenn Sie mehrere Attribute festlegen, können Sie die entsprechenden Konstanten summieren. Wenn Sie den-Eigenschafts Wert auf eine Summe einschließlich nicht kompatibler Konstanten festlegen, tritt ein Fehler auf.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Diese Eigenschaft ist für ein Client seitiges **Verbindungs** Objekt nicht verfügbar.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|  
|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|[Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Attribute und namens Eigenschaften (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Beispiel für Attribute und namens Eigenschaften (VC + +)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
 [AppendChunk-Methode (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [BeginTrans-, CommitTrans-und RollbackTrans-Methode (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [GetChunk-Methode (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
