---
title: Editor für die WMI-Ereignisüberwachung-Task (Seite "WMI-Optionen") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8c3286d1246efb8b5ae2e17cf8df5d38d865a9f9
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374178"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a>Editor für den Task 'WMI-Ereignisüberwachung' (Seite WMI-Optionen)
  Auf der Seite **WMI-Optionen** des Dialogfelds **Editor für den Task „WMI-Ereignisüberwachung“** können Sie die Quelle der WQL-Abfrage (Windows Management Instrumentation Query Language) und das Verhalten angeben, mit dem der Task „WMI-Ereignisüberwachung“ auf WMI-Ereignisse (Microsoft Windows Instrumentation) antwortet.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md). Weitere Informationen zur WMI Query Language finden Sie im WMI-Thema [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)(Abfragen mit WQL), in der MSDN Library.  
  
## <a name="static-options"></a>Statische Optionen  
 **WMIConnectionName**  
 Wählen Sie einen vorhandenen WMI-Verbindungs-Manager aus der Liste aus, oder klicken Sie auf \<**Neue WMI-Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [WMI-Verbindungs-Manager](connection-manager/wmi-connection-manager.md), [WMI-Verbindungs-Manager-Editor](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Wählen Sie den Quelltyp der WQL-Abfrage aus, die von dem Task ausgeführt wird. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Direct input**|Legen Sie die Quelle für eine WQL-Abfrage fest. Bei Auswahl dieses Wertes wird die dynamische Option **WQLQuerySource**angezeigt.|  
|**File connection**|Wählen Sie eine Datei aus, in der die WQL-Abfrage enthalten ist. Bei Auswahl dieses Wertes wird die dynamische Option **WQLQuerySource**angezeigt.|  
|**Variable**|Legen Sie die Quelle für eine Variable fest, die die WQL-Abfrage definiert. Bei Auswahl dieses Wertes wird die dynamische Option **WQLQuerySource**angezeigt.|  
  
 **ActionAtEvent**  
 Geben Sie an, ob das WMI-Ereignis das Ereignis protokolliert und eine [!INCLUDE[ssIS](../includes/ssis-md.md)] -Aktion initiiert oder nur das Ereignis protokolliert.  
  
 **AfterEvent**  
 Gibt an, ob der Task nach dem Empfangen des WMI-Ereignisses erfolgreich ausgeführt wird oder fehlschlägt, oder ob die Überwachung des Auftretens dieses Ereignisses durch den Task fortgesetzt wird.  
  
 **ActionAtTimeout**  
 Gibt an, ob ein WMI-Abfragetimeout durch den Task protokolliert und als Antwort ein [!INCLUDE[ssIS](../includes/ssis-md.md)] -Ereignis ausgelöst wird, oder ob nur der Timeout protokolliert wird.  
  
 **AfterTimeout**  
 Gibt an, ob der Task als Antwort auf einen Timeout erfolgreich ausgeführt wird oder fehlschlägt, oder ob der Task die Überwachung fortsetzt, bis ein weiterer Timeout auftritt.  
  
 **NumberOfEvents**  
 Gibt die Anzahl der zu überwachenden Ereignisse an.  
  
 **Timeout**  
 Gibt die Zeit in Sekunden an, in der auf das Auftreten des Ereignisses gewartet wird. Der Wert 0 bedeutet, dass kein Timeout aktiviert ist.  
  
## <a name="wqlquerysource-dynamic-options"></a>WQLQuerySource (dynamische Optionen)  
  
### <a name="wqlquerysource--direct-input"></a>WQLQuerySource = Direct input  
 **WQLQuerySource**  
 Stellen Sie eine Abfrage bereit, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), und geben Sie eine Abfrage mithilfe des Dialogfelds **WQL-Abfrage** ein.  
  
### <a name="wqlquerysource--file-connection"></a>WQLQuerySource = File connection  
 **WQLQuerySource**  
 Wählen Sie in der Liste einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md), [Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysource--variable"></a>WQLQuerySource = Variable  
 **WQLQuerySource**  
 Wählen Sie in der Liste eine Variable aus, oder klicken Sie auf \<**Neue Variable…**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integrationsdienste &#40;SSIS&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task „WMI-Ereignisüberwachung“ &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [WMI-Datenleser (Task)](control-flow/wmi-data-reader-task.md)  
  
  
