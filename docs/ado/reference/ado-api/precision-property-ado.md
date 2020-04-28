---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 26da0367e494bd74253b904393a2dad62308a608
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931636"
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
  
|||  
|-|-|  
|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für NumericScale und Precision Properties (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Beispiel für NumericScale und Precision Properties (VC + +)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [NumericScale-Eigenschaft (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
