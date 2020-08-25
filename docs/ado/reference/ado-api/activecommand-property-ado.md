---
description: ActiveCommand-Eigenschaft (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e8c969c8e611c8e2bff76dc045a28a9c6d6ab96
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759940"
---
# <a name="activecommand-property-ado"></a>ActiveCommand-Eigenschaft (ADO)
Gibt das [Befehls](./command-object-ado.md) Objekt an, das das zugeordnete [Recordset](./recordset-object-ado.md) -Objekt erstellt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variante** zurück, die ein **Befehls** Objekt enthält. Der Standardwert ist ein NULL-Objekt Verweis.  
  
## <a name="remarks"></a>Hinweise  
 Die **ActiveCommand** -Eigenschaft ist schreibgeschützt.  
  
 Wenn kein **Befehls** Objekt zum Erstellen des aktuellen **Recordsets**verwendet wurde, wird ein **null** -Objekt Verweis zurückgegeben.  
  
 Verwenden Sie diese Eigenschaft, um das zugeordnete **Befehls** Objekt zu suchen, wenn Sie nur das resultierende **Recordset** -Objekt erhalten.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveCommand-Eigenschaft (VB)](./activecommand-property-example-vb.md)   
 [ActiveCommand-Eigenschafts Beispiel (JScript)](./activecommand-property-example-jscript.md)   
 [ActiveCommand-Eigenschafts Beispiel (VC + +)](./activecommand-property-example-vc.md)   
 [Command-Objekt (ADO)](./command-object-ado.md)