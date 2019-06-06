---
title: Prepared-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::Prepared
helpviewer_keywords:
- Prepared property [ADO]
ms.assetid: 11ca8825-765e-4bb4-a6ce-3f6564ad8755
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c762de42fd12509a56fcc22584b4afa57be2eaa5
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703139"
---
# <a name="prepared-property-ado"></a>Prepared-Eigenschaft (ADO)
Gibt an, ob eine kompilierte Version des speichern eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) vor der Ausführung.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **booleschen** -Wert, wenn auf festgelegt **"true"** , gibt an, dass der Befehl vorbereitet werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Prepared** Eigenschaft so, dass den Anbieter, speichern Sie eine vorbereitete (oder kompilierte) Version der Abfrage angegeben der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) Eigenschaft, bevor eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) des Objekts erste Ausführung. Dies kann sich dies negativ erste Ausführung des Befehls, aber sobald der Anbieter einen Befehl kompiliert wird, verwendet des Anbieters die kompilierte Version des Befehls für jede nachfolgenden Ausführungen, was zu einer leistungsverbesserung führt.  
  
 Wenn die Eigenschaft **"false"** , der Anbieter führt die **Befehl** Objekt direkt, ohne eine kompilierte Version erstellt.  
  
 Wenn der Anbieter die befehlsvorbereitung nicht unterstützt, kann es einen Fehler zurück, wenn diese Eigenschaft, um festgelegt wird **"true"** . Wenn der Anbieter keine Fehler zurückgegeben wird, ignoriert er einfach die Anforderung zum Vorbereiten der Befehl und legt die **Prepared** Eigenschaft **"false"** .  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Prepared-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/prepared-property-example-vb.md)   
 [Prepared-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/prepared-property-example-vc.md)   
