---
description: NumericScale-Eigenschaft (ADO)
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
ms.openlocfilehash: 57375b89595c6ed3e5c377692709deacd8f0ff28
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773969"
---
# <a name="numericscale-property-ado"></a>NumericScale-Eigenschaft (ADO)
Gibt die Skala numerischer Werte in einem [Parameter](./parameter-object.md) -oder [Feld](./field-object.md) Objekt an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Bytewert** fest, der die Anzahl der Dezimalstellen angibt, auf die numerische Werte aufgelöst werden, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die **NumericScale** -Eigenschaft, um zu bestimmen, wie viele Ziffern rechts vom Dezimaltrennzeichen verwendet werden, um Werte für einen numerischen **Parameter** oder **Feld** Objekt darzustellen.  
  
 Bei **Parameter** Objekten ist die **NumericScale** -Eigenschaft Lese-/Schreibzugriff.  
  
 Für ein **Feld**Objekt ist **NumericScale** normalerweise schreibgeschützt. Bei neuen **Feld** Objekten, die an die [Fields](./fields-collection-ado.md) -Auflistung eines [Datensatzes](./record-object-ado.md)angehängt wurden, ist **NumericScale** jedoch nur Lese-/Schreibzugriff, nachdem die [value](./value-property-ado.md) -Eigenschaft für das **Feld** angegeben wurde und der Datenanbieter das neue **Feld** erfolgreich hinzugefügt hat, indem die [Update](./update-method.md) -Methode der [Fields](./fields-collection-ado.md) -Auflistung aufgerufen wurde.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Field-Objekt](./field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter-Objekt](./parameter-object.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für NumericScale und Precision Properties (VB)](./numericscale-and-precision-properties-example-vb.md)   
 [Beispiel für NumericScale und Precision Properties (VC + +)](./numericscale-and-precision-properties-example-vc.md)   
 [Precision-Eigenschaft (ADO)](./precision-property-ado.md)