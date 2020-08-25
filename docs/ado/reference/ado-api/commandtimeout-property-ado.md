---
description: CommandTimeout-Eigenschaft (ADO)
title: CommandTimeout-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
author: rothja
ms.author: jroth
ms.openlocfilehash: eaa3f7aace505092b147fc3d15c2890de50c5958
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776109"
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout-Eigenschaft (ADO)
Gibt an, wie lange beim Ausführen eines Befehls gewartet werden soll, bevor der Versuch beendet und ein Fehler erzeugt wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der angibt (in Sekunden), wie lange auf die Ausführung eines Befehls gewartet werden soll, oder gibt ihn zurück. Der Standardwert ist 30.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **CommandTimeout** -Eigenschaft für ein [Verbindungs](./connection-object-ado.md) Objekt oder ein [Befehls](./command-object-ado.md) Objekt, um den Abbruch eines [Execute](./execute-method-ado-command.md) -Methoden Aufrufes aufgrund von Verzögerungen beim Netzwerkverkehr oder bei hoher Servernutzung zuzulassen. Wenn das in der **CommandTimeout** -Eigenschaft festgelegte Intervall abläuft, bevor die Ausführung des Befehls abgeschlossen ist, tritt ein Fehler auf, und der Befehl wird von ADO abgebrochen. Wenn Sie die-Eigenschaft auf 0 (null) festlegen, wartet ADO unbegrenzt, bis die Ausführung vollständig ist. Stellen Sie sicher, dass der Anbieter und die Datenquelle, für die Sie Code schreiben, die **CommandTimeout** -Funktionalität unterstützen.  
  
 Die **CommandTimeout** -Einstellung für ein **Verbindungs** Objekt hat keine Auswirkung auf die **CommandTimeout** -Einstellung eines **Befehls** Objekts auf derselben **Verbindung**. Das bedeutet, dass die **CommandTimeout** -Eigenschaft des **Befehls** Objekts den Wert des **CommandTimeout** -Werts des **Verbindungs** Objekts nicht erbt.  
  
 Bei einem **Verbindungs** Objekt bleibt die **CommandTimeout** -Eigenschaft nach dem Öffnen der **Verbindung** Lese-/Schreibzugriff.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Command-Objekt (ADO)](./command-object-ado.md)  
    :::column-end:::
    :::column:::
        [Connection-Objekt (ADO)](./connection-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VB)](./activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VC + +)](./activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (JScript)](./activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout-Eigenschaft (ADO)](./connectiontimeout-property-ado.md)