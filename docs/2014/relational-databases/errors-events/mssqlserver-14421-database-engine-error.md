---
title: MSSQLSERVER_14421 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14421 (Database Engine error)
ms.assetid: 03e76d4a-d463-4673-8843-08e4ecaefe27
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a6db88a8bb5e44090e5201220fee36a432b69767
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62869875"
---
# <a name="mssqlserver14421"></a>MSSQLSERVER_14421
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14421|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum14421|  
|Meldungstext|Die sekundäre Datenbank für den Protokollversand, %s.%s, weist eine Wiederherstellungsschwelle von %d Minuten auf und ist nicht mehr synchronisiert. Während %d Minuten wurde keine Wiederherstellung ausgeführt. Die Wiederherstellungslatenzzeit beträgt %d Minuten. Überprüfen Sie das Agentprotokoll und die Informationen des Protokollversandmonitors.|  
  
## <a name="explanation"></a>Erklärung  
 Mit dieser Meldung wird angegeben, dass der Protokollversand außerhalb der Wiederherstellungsschwelle nicht mehr synchronisiert ist. Bei der Wiederherstellungsschwelle handelt es sich um eine Zeit in Minuten, die zwischen den Wiederherstellungsvorgängen vergehen kann, bevor eine Meldung erzeugt wird.  
  
### <a name="possible-causes"></a>Mögliche Ursachen  
 Mit dieser Meldung wird nicht unbedingt ein Problem beim Protokollversand angegeben. Stattdessen wird mit dieser Meldung eines der folgenden Probleme angegeben:  
  
-   Der Wiederherstellungsauftrag wird nicht ausgeführt.  
  
     Folgende mögliche Ursachen können vorliegen, dass der Auftrag nicht ausgeführt wird: Der SQL Server-Agent-Dienst in der sekundären Serverinstanz wird nicht ausgeführt, der Auftrag wurde deaktiviert, oder der Zeitplan für den Auftrag wurde geändert.  
  
-   Fehler beim Wiederherstellungsauftrag.  
  
     Folgende mögliche Ursachen können für den Fehler beim Auftrag vorliegen: Der Pfad des Wiederherstellungsordners ist nicht gültig, der Datenträger ist voll, oder es liegt ein anderer Grund vor, wonach ein Fehler bei der RESTORE-Anweisung auftritt.  
  
## <a name="user-action"></a>Benutzeraktion  
 So beheben Sie das mit dieser Meldung angegebene Problem:  
  
-   Stellen Sie sicher, dass der SQL Server-Agent-Dienst in der sekundären Serverinstanz ausgeführt wird, dass der Wiederherstellungsauftrag für diese sekundäre Datenbank aktiviert ist und dass er so geplant ist, dass er in der entsprechenden Häufigkeit ausgeführt wird.  
  
-   Möglicherweise tritt beim Wiederherstellungsauftrag auf dem sekundären Server ein Fehler auf. Überprüfen Sie in diesem Fall den Auftragsverlauf für den Wiederherstellungsauftrag, und suchen Sie nach der Ursache.  
  
-   Für den in der sekundären Serverinstanz ausgeführten Wiederherstellungsauftrag des Protokollversands kann möglicherweise keine Verbindung mit der Überwachungsserverinstanz hergestellt werden, um die **log_shipping_monitor_secondary**-Tabelle zu aktualisieren. Dies beruht möglicherweise auf einem Authentifizierungsproblem zwischen der Überwachungsserverinstanz und der sekundären Serverinstanz.  
  
-   Die Sicherungswarnschwelle weist möglicherweise einen falschen Wert auf. Im Idealfall ist dieser Wert auf den dreifachen Wert der Häufigkeit festgelegt, mit der der Wiederherstellungsauftrag ausgeführt wird. Wenn Sie die Häufigkeit für den Wiederherstellungsauftrag ändern, nachdem der Protokollversand konfiguriert und ausgeführt wurde, müssen Sie den Wert für die Sicherungswarnschwelle entsprechend aktualisieren.  
  
-   Wenn die Überwachungsserverinstanz offline geschaltet und anschließend wieder online geschaltet wird, wird die **log_shipping_monitor_secondary**-Tabelle erst dann mit den aktuellen Werten aktualisiert, wenn der Warnmeldungsauftrag ausgeführt wurde. Der Fehler 14421 kann ausgelöst werden, wenn ein Wiederherstellungsauftrag mit folgender Meldung erfolgreich ausgeführt wurde: "Für die sekundäre Datenbank wurde keine anwendbare Protokollsicherungsdatei gefunden." Wenn dieser Fehler auftritt, wird der Speicherzeitpunkt nicht aktualisiert. Möglicherweise beruht der Fehler in diesem Fall auf einem Problem mit dem Kopierauftrag.  
  
     Wenn Sie die Überwachungstabellen mit den neuesten Daten für die sekundäre Datenbank aktualisieren möchten, führen Sie **sp_refresh_log_shipping_monitor** in der sekundären Serverinstanz aus.  
  
-   Das Datum oder die Uhrzeit in der sekundären Serverinstanz oder in der Überwachungsserverinstanz ist nicht richtig. Dadurch werden möglicherweise Warnmeldungen generiert. Möglicherweise wurde das Systemdatum oder die Systemuhrzeit für eine der Instanzen geändert.  
  
    > [!NOTE]  
    >  Unterschiedliche Zeitzonen für die beiden Serverinstanzen sollten kein Problem darstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)   
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_help_log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)   
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
