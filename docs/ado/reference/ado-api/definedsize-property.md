---
title: DefinedSize-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::DefinedSize
helpviewer_keywords:
- DefinedSize property [ADO]
ms.assetid: 3ee27314-a305-4fbc-8433-9ee9a909afd6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b80838ce47bdb74878efb2918fd79b057abce216
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718483"
---
# <a name="definedsize-property"></a>DefinedSize-Eigenschaft
Gibt die Datenkapazität von einem [Feld](../../../ado/reference/ado-api/field-object.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **lange** -Wert, der die definierte Größe eines Felds zu, die für den Datentyp des Felds Objekts abhängig ist wiedergeben, finden Sie unter [Typ](../../../ado/reference/ado-api/type-property-ado.md) für Weitere Informationen. Für ein Feld, das einen Datentyp mit fester Länge verwendet wird, ist der zurückgegebene Wert die Größe des Datentyps in Byte. Ein Feld, das einen Datentyp mit variabler Länge verwendet wird, ist dies eine der folgenden:  
  
1.  Die maximale Länge des Felds in Zeichen (für **AdVarChar** und **AdVarWChar**) oder in Byte (für **AdVarBinary**, und **AdVarNumeric**) Wenn das Feld definierte Länge verfügt. Z. B. **adVarChar(5)** Feld hat eine maximale Länge von 5.  
  
2.  Die maximale Länge des Datentyps in Zeichen (für **AdChar** und **AdWChar**) oder in Byte (für **AdBinary** und **Type**) Wenn die Feld besitzt keine definierte Länge.  
  
3.  ~ 0 (bitweiser der Wert ist 0; nicht alle Bits auf 1 festgelegt), wenn weder das Feld als auch der Datentyp eine definierte Maximallänge besitzt.  
  
4.  Datentypen, die nicht über eine Länge verfügen, dies ist so eingestellt ~ 0 (bitweiser der Wert ist 0; nicht alle Bits auf 1 festgelegt).  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **DefinedSize** Eigenschaft zum Ermitteln der Datenkapazität von einem **Feld** Objekt.  
  
 Die **DefinedSize** und [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) Eigenschaften unterschiedlich sind. Betrachten Sie beispielsweise eine **Feld** Objekt mit dem deklarierten Typ **AdVarChar** und **DefinedSize** Eigenschaftswert von 50 enthält ein einzelnes Zeichen. Die **ActualSize** Eigenschaftswert zurückgegeben wird, die Länge in Bytes des einzelnen Zeichens.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ActualSize und DefinedSize – Beispiel (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize und DefinedSize – Beispiel (VC++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [ActualSize-Eigenschaft (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)
