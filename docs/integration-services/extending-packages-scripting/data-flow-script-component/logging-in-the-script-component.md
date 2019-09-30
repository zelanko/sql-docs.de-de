---
title: Protokollieren in der Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52f4c841d2022216480051576bb0b6da7bdb5d34
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71286460"
---
# <a name="logging-in-the-script-component"></a>Protokollieren in der Skriptkomponente

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Durch die Protokollierung in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Paketen können Sie detaillierte Informationen zum Fortschritt sowie über die Ergebnisse und Probleme der Ausführung speichern, indem Sie vordefinierte Ereignisse bzw. benutzerdefinierte Meldungen für die spätere Analyse erfassen. Die Skriptkomponente kann die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>-Methode der **ScriptMain**-Klasse verwenden, um benutzerdefinierte Daten zu protokollieren. Wenn die Protokollierung aktiviert ist und in der Registerkarte **Details** des Dialogfelds **SSIS-Protokolle konfigurieren** das Ereignis **ScriptComponentLogEntry** für die Protokollierung ausgewählt ist, dann speichert ein einzelner Aufruf der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>-Methode die Ereignisinformationen in allen Protokollanbietern, die für den Datenflusstask konfiguriert wurden.  
  
 Im Folgenden ein einfaches Beispiel für die Protokollierung:  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Obwohl Sie Protokollierungen direkt von der Skriptkomponente ausführen können, ist ggf. eine Implementierung von Ereignissen einer Protokollierung vorzuziehen. Bei der Verwendung von Ereignissen können Sie nicht nur die Protokollierung von Ereignismeldungen aktivieren, sondern auch auf das Ereignis mit standardmäßigen oder benutzerdefinierten Ereignishandlern reagieren.  
  
 Weitere Informationen zur Protokollierung finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Protokollierung &#40;SSIS&#41;](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
