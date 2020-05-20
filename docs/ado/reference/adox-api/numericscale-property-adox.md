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
author: rothja
ms.author: jroth
ms.openlocfilehash: a0a0090a24207e6faad1b14aa3cb5afd6091bc87
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763811"
---
# <a name="numericscale-property-adox"></a>NumericScale-Eigenschaft (ADOX)
Gibt die Skala eines numerischen Werts in der Spalte an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Bytewert** fest, der die Skala der Datenwerte in der Spalte ist, wenn die [Type](../../../ado/reference/adox-api/type-property-column-adox.md) -Eigenschaft **adNumeric** oder **addecimal**ist, und gibt diesen zurück. **NumericScale** wird für alle anderen Datentypen ignoriert.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Standardwert ist 0 (null).  
  
 **NumericScale** ist für [Spalten](../../../ado/reference/adox-api/column-object-adox.md) Objekte, die bereits an eine Auflistung angehängt wurden, schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  
 [Column-Objekt (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADOX-Code Beispiel: Beispiel für NumericScale und Precision Properties (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type-Eigenschaft (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
