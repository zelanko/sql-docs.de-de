---
description: Precision-Eigenschaft (ADO)
title: Precision-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Precision
- Field20::Precision
helpviewer_keywords:
- Precision property [ADO]
ms.assetid: 1fa38e78-6b5b-414d-ba0a-3dd26b29b766
author: rothja
ms.author: jroth
ms.openlocfilehash: 4be9c3ae7e9f4cc8ac7f90b78b80ee96b64eaf5d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442702"
---
# <a name="precision-property-ado"></a>Precision-Eigenschaft (ADO)
Gibt den Genauigkeits Grad für numerische Werte in einem [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt oder numerischen [Feld](../../../ado/reference/ado-api/field-object.md) Objekten an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Bytewert** fest, der die maximale Anzahl von Ziffern angibt, die zum Darstellen von Werten verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der Eigenschaft **Genauigkeit** können Sie die maximale Anzahl von Ziffern ermitteln, die zum Darstellen von Werten für einen numerischen **Parameter** oder **Feld** Objekt verwendet werden.  
  
 Der Wert ist Lese-/Schreibzugriff auf ein **Parameter** Objekt.  
  
 Bei einem **Feld**Objekt ist die **Genauigkeit** normalerweise schreibgeschützt. Bei neuen **Feld** Objekten, die an die [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung eines [Datensatzes](../../../ado/reference/ado-api/record-object-ado.md)angefügt wurden, ist die **Genauigkeit** jedoch nur mit Lese-/Schreibzugriff, nachdem die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft für das **Feld** angegeben wurde und der Datenanbieter das neue **Feld** durch Aufrufen der [Update](../../../ado/reference/ado-api/update-method.md) -Methode der **Fields** -Auflistung erfolgreich hinzugefügt hat.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für NumericScale und Precision Properties (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Beispiel für NumericScale und Precision Properties (VC + +)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [NumericScale-Eigenschaft (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
