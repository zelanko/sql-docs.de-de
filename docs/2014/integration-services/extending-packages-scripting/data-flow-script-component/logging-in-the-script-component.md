---
title: Protokollieren in der Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f44ec46f61e215fabe5c4ae2af78d898d7e35c64
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53356951"
---
# <a name="logging-in-the-script-component"></a>Protokollieren in der Skriptkomponente
  Durch die Protokollierung in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Paketen können Sie detaillierte Informationen zum Fortschritt sowie über die Ergebnisse und Probleme der Ausführung speichern, indem Sie vordefinierte Ereignisse bzw. benutzerdefinierte Meldungen für die spätere Analyse erfassen. Die Skriptkomponente kann die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>-Methode der `ScriptMain`-Klasse verwenden, um benutzerdefinierte Daten zu protokollieren. Wenn die Protokollierung aktiviert ist und in der Registerkarte **Details** des Dialogfelds **SSIS-Protokolle konfigurieren** das Ereignis **ScriptComponentLogEntry** für die Protokollierung ausgewählt ist, dann speichert ein einzelner Aufruf der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>-Methode die Ereignisinformationen in allen Protokollanbietern, die für den Datenflusstask konfiguriert wurden.  
  
 Im Folgenden ein einfaches Beispiel für die Protokollierung:  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Obwohl Sie Protokollierungen direkt von der Skriptkomponente ausführen können, ist ggf. eine Implementierung von Ereignissen einer Protokollierung vorzuziehen. Bei der Verwendung von Ereignissen können Sie nicht nur die Protokollierung von Ereignismeldungen aktivieren, sondern auch auf das Ereignis mit standardmäßigen oder benutzerdefinierten Ereignishandlern reagieren.  
  
 Weitere Informationen zur Protokollierung finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../../performance/integration-services-ssis-logging.md).  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Protokollierung &#40;SSIS&#41;](../../performance/integration-services-ssis-logging.md)  
  
  
