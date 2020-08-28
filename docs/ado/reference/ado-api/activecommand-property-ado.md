---
description: ActiveCommand-Eigenschaft (ADO)
title: ActiveCommand-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: df737543e8cc09735c7da413b89406b6f2385079
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977152"
---
# <a name="activecommand-property-ado"></a>ActiveCommand-Eigenschaft (ADO)
Gibt das [Befehls](./command-object-ado.md) Objekt an, das das zugeordnete [Recordset](./recordset-object-ado.md) -Objekt erstellt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variante** zurück, die ein **Befehls** Objekt enthält. Der Standardwert ist ein NULL-Objekt Verweis.  
  
## <a name="remarks"></a>Bemerkungen  
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