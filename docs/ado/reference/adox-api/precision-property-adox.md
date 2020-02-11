---
title: Precision-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::put_Precision
- _Column::PutPrecision
- _Column::GetPrecision
- _Column::get_Precision
- _Column::Precision
helpviewer_keywords:
- Precision property [ADOX]
ms.assetid: 0e0ecbbf-d7de-49d4-a128-5a519ecd54ba
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d1416842f3c122e9e5e5e28b8a14310b679697cd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965560"
---
# <a name="precision-property-adox"></a>Precision-Eigenschaft (ADOX)
Gibt die maximale Genauigkeit der Datenwerte in der [Spalte](../../../ado/reference/adox-api/column-object-adox.md)an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der die maximale Genauigkeit der Datenwerte in der Spalte angibt, wenn die [Type](../../../ado/reference/adox-api/type-property-column-adox.md) -Eigenschaft ein numerischer Typ ist, und gibt diesen zurück. Die **Genauigkeit** wird für alle anderen Datentypen ignoriert.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Standardwert ist **0** (null).  
  
 Diese Eigenschaft ist für [Spalten](../../../ado/reference/adox-api/column-object-adox.md) Objekte, die bereits an eine Auflistung angehängt wurden, schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  
 [Column-Objekt (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADOX-Code Beispiel: Beispiel für NumericScale und Precision Properties (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type-Eigenschaft (Spalte) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)   
 [Column-Objekt (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
