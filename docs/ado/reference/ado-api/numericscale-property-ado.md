---
title: NumericScale-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
author: rothja
ms.author: jroth
ms.openlocfilehash: 3970ab8d8f446c4269e4b79c306d2dd9d2cf0426
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762329"
---
# <a name="numericscale-property-ado"></a>NumericScale-Eigenschaft (ADO)
Gibt die Skala numerischer Werte in einem [Parameter](../../../ado/reference/ado-api/parameter-object.md) -oder [Feld](../../../ado/reference/ado-api/field-object.md) Objekt an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Bytewert** fest, der die Anzahl der Dezimalstellen angibt, auf die numerische Werte aufgelöst werden, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **NumericScale** -Eigenschaft, um zu bestimmen, wie viele Ziffern rechts vom Dezimaltrennzeichen verwendet werden, um Werte für einen numerischen **Parameter** oder **Feld** Objekt darzustellen.  
  
 Bei **Parameter** Objekten ist die **NumericScale** -Eigenschaft Lese-/Schreibzugriff.  
  
 Für ein **Feld**Objekt ist **NumericScale** normalerweise schreibgeschützt. Bei neuen **Feld** Objekten, die an die [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung eines [Datensatzes](../../../ado/reference/ado-api/record-object-ado.md)angehängt wurden, ist **NumericScale** jedoch nur Lese-/Schreibzugriff, nachdem die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft für das **Feld** angegeben wurde und der Datenanbieter das neue **Feld** erfolgreich hinzugefügt hat, indem die [Update](../../../ado/reference/ado-api/update-method.md) -Methode der [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung aufgerufen wurde.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für NumericScale und Precision Properties (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Beispiel für NumericScale und Precision Properties (VC + +)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Precision-Eigenschaft (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
