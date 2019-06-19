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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 556474c3b038f40e21467a4bbc945fc8f29fd5a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695988"
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout-Eigenschaft (ADO)
Gibt an, wie lange warten, während der Ausführung eines Befehls, bevor der Versuch beendet und ein Fehler generiert.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** hodnota ukazuje, in Sekunden an, wie lange warten, bis ein Befehl zum Ausführen. Standardwert ist 30.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **"CommandTimeout"** Eigenschaft für eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt oder [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt, das den Abbruch zu ermöglichen eine [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) Methode Rufen Sie aufgrund von Verzögerungen von Netzwerk-Datenverkehr oder hohem Server verwenden. Wenn das Intervall, in Festlegen der **"CommandTimeout"** Eigenschaft verstreicht, bevor der Befehl abgeschlossen ist Ausführung ein Fehler auftritt und ADO bricht den Befehl ab. Wenn Sie die Eigenschaft auf 0 (null) festlegen, wartet die ADO auf unbestimmte Zeit, bis die Ausführung abgeschlossen ist. Stellen Sie sicher, dass den Anbieter und der Datenquelle, dem Sie Unterstützung für Code schreiben, die **"CommandTimeout"** Funktionalität.  
  
 Die **"CommandTimeout"** festlegen auf eine **Verbindung** Objekt hat keine Auswirkungen auf die **"CommandTimeout"** festlegen auf einen **Befehl** -Objekt die gleiche **Verbindung**, d. h. die **Befehl** des Objekts **"CommandTimeout"** Eigenschaft erbt nicht den Wert des der **Verbindung** des Objekts **"CommandTimeout"** Wert.  
  
 Auf einer **Verbindung** -Objekt, das **"CommandTimeout"** Eigenschaft bleibt Lese-/Schreibzugriff nach der **Verbindung** wird geöffnet.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
