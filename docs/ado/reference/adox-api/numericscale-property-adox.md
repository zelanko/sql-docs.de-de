---
description: NumericScale-Eigenschaft (ADOX)
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
ms.openlocfilehash: 3420a3e3d1e6ee06eaa63926604f3688b3f0590b
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769909"
---
# <a name="numericscale-property-adox"></a>NumericScale-Eigenschaft (ADOX)
Gibt die Skala eines numerischen Werts in der Spalte an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Bytewert** fest, der die Skala der Datenwerte in der Spalte ist, wenn die [Type](./type-property-column-adox.md) -Eigenschaft **adNumeric** oder **addecimal**ist, und gibt diesen zurück. **NumericScale** wird für alle anderen Datentypen ignoriert.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Standardwert ist 0 (null).  
  
 **NumericScale** ist für [Spalten](./column-object-adox.md) Objekte, die bereits an eine Auflistung angehängt wurden, schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  
 [Column-Objekt (ADOX)](./column-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADOX-Code Beispiel: Beispiel für NumericScale und Precision Properties (VB)](./adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type-Eigenschaft (Spalte) (ADOX)](./type-property-column-adox.md)