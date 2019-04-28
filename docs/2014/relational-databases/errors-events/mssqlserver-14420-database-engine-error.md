---
title: MSSQLSERVER_14420 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14420 (Database Engine error)
ms.assetid: 4a1d72b1-ab1b-4119-a11b-a8a05c6fdb45
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5c2818c322749672c514cd9d392b61b580d40e88
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869902"
---
# <a name="mssqlserver14420"></a>MSSQLSERVER_14420
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14420|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum14420|  
|Meldungstext|Die primäre Datenbank für den Protokollversand, %s.%s, weist eine Sicherungsschwelle von %d Minuten auf und hat während %d Minuten keinen Vorgang zur Sicherung des Protokolls ausgeführt. Überprüfen Sie das Agentprotokoll und die Informationen des Protokollversandmonitors.|  
  
## <a name="explanation"></a>Erklärung  
 Der Protokollversand wird bei Überschreitung des Sicherungsschwellenwerts nicht mehr synchronisiert. Bei der Sicherungsschwelle handelt es sich um eine Zeit in Minuten, die zwischen den Sicherungsaufträgen für den Protokollversand vergehen kann, bevor eine Warnmeldung generiert wird. Mit dieser Meldung wird nicht unbedingt ein Problem beim Protokollversand angegeben. Stattdessen wird mit dieser Meldung eines der folgenden Probleme angegeben:  
  
-   Der Sicherungsauftrag wird nicht ausgeführt. Hierfür können folgende mögliche Ursachen vorliegen: Der SQL Server-Agent-Dienst in der primären Serverinstanz wird nicht ausgeführt, der Auftrag ist deaktiviert, oder der Zeitplan für diesen Auftrag wurde geändert.  
  
-   Fehler beim Sicherungsauftrag. Hierfür können folgende mögliche Ursachen vorliegen: Der Pfad des Sicherungsordners ist nicht gültig, der Datenträger ist voll, oder es liegt ein anderer Grund vor, wonach ein Fehler bei der BACKUP-Anweisung auftritt.  
  
## <a name="user-action"></a>Benutzeraktion  
 So beheben Sie das mit dieser Meldung angegebene Problem:  
  
-   Stellen Sie sicher, dass der SQL Server-Agent-Dienst in der primären Serverinstanz ausgeführt wird, dass der Sicherungsauftrag für diese primäre Datenbank aktiviert ist und dass er so geplant ist, dass er in der entsprechenden Häufigkeit ausgeführt wird.  
  
-   Möglicherweise tritt beim Sicherungsauftrag auf dem primären Server ein Fehler auf. Überprüfen Sie in diesem Fall den Auftragsverlauf für den Sicherungsauftrag, und suchen Sie nach der Ursache.  
  
-   Für den in der primären Serverinstanz ausgeführten Sicherungsauftrag des Protokollversands kann möglicherweise keine Verbindung mit der Überwachungsserverinstanz hergestellt werden, um die **log_shipping_monitor_primary**-Tabelle zu aktualisieren. Dies beruht möglicherweise auf einem Authentifizierungsproblem zwischen der Überwachungsserverinstanz und der primären Serverinstanz.  
  
-   Die Sicherungswarnschwelle weist möglicherweise einen falschen Wert auf. Im Idealfall ist dieser Wert auf den dreifachen Wert der Häufigkeit festgelegt, mit der der Sicherungsauftrag ausgeführt wird. Wenn Sie die Häufigkeit für den Sicherungsauftrag ändern, nachdem der Protokollversand konfiguriert und ausgeführt wurde, müssen Sie den Wert für die Sicherungswarnschwelle entsprechend aktualisieren.  
  
-   Wenn die Überwachungsserverinstanz offline geschaltet und anschließend wieder online geschaltet wird, wird die **log_shipping_monitor_primary**-Tabelle erst dann mit den aktuellen Werten aktualisiert, wenn der Warnmeldungsauftrag ausgeführt wurde. Wenn Sie die Überwachungstabellen mit den neuesten Daten für die primäre Datenbank aktualisieren möchten, führen Sie **sp_refresh_log_shipping_monitor** in der primären Serverinstanz aus.  
  
-   Das Datum oder die Uhrzeit in der primären Serverinstanz oder in der Überwachungsserverinstanz ist nicht richtig. Dadurch werden möglicherweise Warnmeldungen generiert. Möglicherweise wurde das Systemdatum oder die Systemuhrzeit für eine der Instanzen geändert.  
  
    > [!NOTE]  
    >  Unterschiedliche Zeitzonen für die beiden Serverinstanzen sollten kein Problem darstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)   
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_help_log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)   
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
