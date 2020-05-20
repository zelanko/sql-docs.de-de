---
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
ms.openlocfilehash: b771c5b8dc54bb312893885aea9c9c151feef3e3
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760386"
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout-Eigenschaft (ADO)
Gibt an, wie lange beim Ausführen eines Befehls gewartet werden soll, bevor der Versuch beendet und ein Fehler erzeugt wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der angibt (in Sekunden), wie lange auf die Ausführung eines Befehls gewartet werden soll, oder gibt ihn zurück. Standard ist 30.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **CommandTimeout** -Eigenschaft für ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt oder ein [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt, um den Abbruch eines [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -Methoden Aufrufes aufgrund von Verzögerungen beim Netzwerkverkehr oder bei hoher Servernutzung zuzulassen. Wenn das in der **CommandTimeout** -Eigenschaft festgelegte Intervall abläuft, bevor die Ausführung des Befehls abgeschlossen ist, tritt ein Fehler auf, und der Befehl wird von ADO abgebrochen. Wenn Sie die-Eigenschaft auf 0 (null) festlegen, wartet ADO unbegrenzt, bis die Ausführung vollständig ist. Stellen Sie sicher, dass der Anbieter und die Datenquelle, für die Sie Code schreiben, die **CommandTimeout** -Funktionalität unterstützen.  
  
 Die **CommandTimeout** -Einstellung für ein **Verbindungs** Objekt hat keine Auswirkung auf die **CommandTimeout** -Einstellung eines **Befehls** Objekts auf derselben **Verbindung**. Das bedeutet, dass die **CommandTimeout** -Eigenschaft des **Befehls** Objekts den Wert des **CommandTimeout** -Werts des **Verbindungs** Objekts nicht erbt.  
  
 Bei einem **Verbindungs** Objekt bleibt die **CommandTimeout** -Eigenschaft nach dem Öffnen der **Verbindung** Lese-/Schreibzugriff.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
