---
description: Dialect-Eigenschaft
title: Dialekt Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
author: rothja
ms.author: jroth
ms.openlocfilehash: e106c76b859f9ccdf1e977cfe3a0ac784cb78740
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444072"
---
# <a name="dialect-property"></a>Dialect-Eigenschaft
Gibt den Dialekt der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft oder der [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) -Eigenschaft an. Der Dialekt definiert die Syntax und die allgemeinen Regeln, die der Anbieter verwendet, um die Zeichenfolge oder den Stream zu analysieren.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Die **Dialekt** -Eigenschaft enthält eine gültige GUID, die den Dialekt des Befehls Texts oder-Streams darstellt. Der Standardwert für diese Eigenschaft ist {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}. Dies bedeutet, dass der Anbieter auswählen soll, wie der Befehls Text oder der Stream interpretiert werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 ADO fragt den Anbieter nicht ab, wenn der Benutzer den Wert dieser Eigenschaft liest. Sie gibt eine Zeichen folgen Darstellung des Werts zurück, der derzeit im [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt gespeichert ist.  
  
 Wenn der Benutzer die **Dialekt** Eigenschaft festlegt, überprüft ADO die GUID und löst einen Fehler aus, wenn der angegebene Wert keine gültige GUID ist. Weitere Informationen finden Sie in der Dokumentation für Ihren Anbieter, um die von der **Dialekt** Eigenschaft unterstützten GUID-Werte zu ermitteln  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Execute-Methode (ADO-Befehl)](../../../ado/reference/ado-api/execute-method-ado-command.md)
