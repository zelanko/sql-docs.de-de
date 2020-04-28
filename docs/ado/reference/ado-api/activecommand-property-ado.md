---
title: ActiveCommand-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::ActiveCommand
helpviewer_keywords:
- ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d2a2f23360cf3ce032d14af7ca475d5c2c3ea638
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921676"
---
# <a name="activecommand-property-ado"></a>ActiveCommand-Eigenschaft (ADO)
Gibt das [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt an, das das zugeordnete [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt erstellt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variante** zurück, die ein **Befehls** Objekt enthält. Der Standardwert ist ein NULL-Objekt Verweis.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **ActiveCommand** -Eigenschaft ist schreibgeschützt.  
  
 Wenn kein **Befehls** Objekt zum Erstellen des aktuellen **Recordsets**verwendet wurde, wird ein **null** -Objekt Verweis zurückgegeben.  
  
 Verwenden Sie diese Eigenschaft, um das zugeordnete **Befehls** Objekt zu suchen, wenn Sie nur das resultierende **Recordset** -Objekt erhalten.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveCommand-Eigenschaft (VB)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [ActiveCommand-Eigenschafts Beispiel (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [ActiveCommand-Eigenschafts Beispiel (VC + +)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
