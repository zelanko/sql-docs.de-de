---
title: NumericScale-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::PutNumericScale
- _Column::GetNumericScale
- _Column::NumericScale
- _Column::put_NumericScale
- _Column::get_NumericScale
helpviewer_keywords:
- NumericScale property [ADOX]
ms.assetid: 573ee5d1-57c7-4a27-be79-a0e12944ad9b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ba72974f9531d328a40244d4ec4ee736ab162fa0
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66706268"
---
# <a name="numericscale-property-adox"></a>NumericScale-Eigenschaft (ADOX)
Gibt die Dezimalstellen eines numerischen Werts in der Spalte an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest, und gibt eine **Byte** -Wert, der die Skalierung der Datenwerte in der Spalte ist bei der [Typ](../../../ado/reference/adox-api/type-property-column-adox.md) -Eigenschaft ist **Type** oder **AdDecimal**. **NumericScale** wird für alle anderen Datentypen ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Der Standardwert ist 0 (null).  
  
 **NumericScale** ist schreibgeschützt und für [Spalte](../../../ado/reference/adox-api/column-object-adox.md) Objekte, die bereits an eine Auflistung angefügt.  
  
## <a name="applies-to"></a>Gilt für  
 [Column-Objekt (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ADOX-Codebeispiel: NumericScale- und Precision-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type-Eigenschaft (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
