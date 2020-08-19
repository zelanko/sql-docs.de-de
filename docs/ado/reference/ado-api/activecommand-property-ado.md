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
ms.openlocfilehash: 38c0a0955e934b4f303937d978f739e00ac6c120
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451742"
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
