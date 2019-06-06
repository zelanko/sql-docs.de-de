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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 39650433fb8b88fb45d38347440d2d612481fb21
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719180"
---
# <a name="numericscale-property-ado"></a>NumericScale-Eigenschaft (ADO)
Gibt an, die Dezimalstellen der numerischen Werte in einer [Parameter](../../../ado/reference/ado-api/parameter-object.md) oder [Feld](../../../ado/reference/ado-api/field-object.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Byte** Wert, der die Anzahl der Dezimalstellen der numerischen Werte angibt, wird aufgelöst werden.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **NumericScale** Eigenschaft, um zu bestimmen, wie viele Ziffern rechts vom Dezimaltrennzeichen verwendet werden, zur Darstellung von Werten für einen numerischen **Parameter** oder **Feld** Objekt.  
  
 Für **Parameter** Objekte, die **NumericScale** Eigenschaft schreibgeschützt ist.  
  
 Für eine **Feld**Objekt **NumericScale** normalerweise schreibgeschützt ist. Jedoch für den neuen **Feld** Objekte, die angefügt wurden die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung von einem [Datensatz](../../../ado/reference/ado-api/record-object-ado.md), **NumericScale** Lese-und Schreibzugriff erst nach der [Wert](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft für die **Feld** angegeben wurde und der neue der Datenanbieter wurde erfolgreich hinzugefügt **Feld** durch Aufrufen der [ Update](../../../ado/reference/ado-api/update-method.md) Methode der [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [NumericScale- und Precision-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale- und Precision-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Precision-Eigenschaft (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
