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
manager: craigg
ms.openlocfilehash: 4dfdb60f9a394fa4d11e9b66ffb1f4b205881293
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705538"
---
# <a name="activecommand-property-ado"></a>ActiveCommand-Eigenschaft (ADO)
Gibt an, die [Befehl](../../../ado/reference/ado-api/command-object-ado.md) -Objekt, das zugeordnete erstellt [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variant** , enthält eine **Befehl** Objekt. Standardwert ist ein null-Objektverweis.  
  
## <a name="remarks"></a>Hinweise  
 Die **ActiveCommand** Eigenschaft ist schreibgeschützt.  
  
 Wenn eine **Befehl** Objekt nicht verwendet, um das aktuelle **Recordset**, und klicken Sie dann eine **Null** Objektverweis wird zurückgegeben.  
  
 Mithilfe dieser Eigenschaft finden Sie die zugeordnete **Befehl** Objekt, wenn Sie nur die resultierende erhalten **Recordset** Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveCommand-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [ActiveCommand-Eigenschaft – Beispiel (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [ActiveCommand-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
