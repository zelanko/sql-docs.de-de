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
manager: jroth
ms.openlocfilehash: 59bfebe5885d0f18811b6b6c8df0f12634ed316f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703248"
---
# <a name="precision-property-ado"></a>Precision-Eigenschaft (ADO)
Gibt den Grad an Genauigkeit für numerische Werte in einer [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt oder für numerische [Feld](../../../ado/reference/ado-api/field-object.md) Objekte.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Byte** Wert, der die maximale Anzahl von Ziffern zur Darstellung von Werten angibt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Genauigkeit** Eigenschaft, um zu bestimmen, die maximale Anzahl von Ziffern für die Werte für eine numerische Darstellung **Parameter** oder **Feld** Objekt.  
  
 Der Wert ist Lese-/Schreibzugriff auf eine **Parameter** Objekt.  
  
 Für eine **Feld**Objekt **Genauigkeit** normalerweise schreibgeschützt ist. Jedoch für den neuen **Feld** Objekte, die angefügt wurden die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung von einer [Datensatz](../../../ado/reference/ado-api/record-object-ado.md), **Genauigkeit** Lese-und Schreibzugriff nur Nachdem die [Wert](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft für die **Feld** angegeben wurde und der neue der Datenanbieter wurde erfolgreich hinzugefügt **Feld** durch Aufrufen der [Update](../../../ado/reference/ado-api/update-method.md) Methode der **Felder** Auflistung.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [NumericScale- und Precision-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale- und Precision-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [NumericScale-Eigenschaft (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
