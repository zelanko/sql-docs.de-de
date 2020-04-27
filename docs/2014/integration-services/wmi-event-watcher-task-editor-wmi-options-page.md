---
title: Editor für den Task "WMI-Ereignisüberwachung" (Seite WMI-Optionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 52ca90b38975c8db762ec0937b265a91b03c5cb2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054383"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a>Editor für den Task 'WMI-Ereignisüberwachung' (Seite WMI-Optionen)
  Auf der Seite **WMI-Optionen** des Dialogfelds **Editor für den Task „WMI-Ereignisüberwachung“** können Sie die Quelle der WQL-Abfrage (Windows Management Instrumentation Query Language) und das Verhalten angeben, mit dem der Task „WMI-Ereignisüberwachung“ auf WMI-Ereignisse (Microsoft Windows Instrumentation) antwortet.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md). Weitere Informationen zur WMI Query Language (WQL) finden Sie im Thema zur Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) unter [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)(Abfragen mit WQL) in der MSDN Library.  
  
## <a name="static-options"></a>Statische Optionen  
 **WMIConnectionName**  
 Wählen Sie einen WMI-Verbindungs-Manager aus der Liste \<aus, oder klicken Sie auf **neue WMI-Verbindung**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [WMI-Verbindungs-Manager](connection-manager/wmi-connection-manager.md), [WMI-Verbindungs-Manager-Editor](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Wählen Sie den Quelltyp der WQL-Abfrage aus, die von dem Task ausgeführt wird. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
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
 Stellen Sie eine Abfrage bereit, oder klicken Sie auf die Schaltfläche mit den Auslassungs Punkten (...), und geben Sie im Dialogfeld **WQL-Abfrage** eine Abfrage  
  
### <a name="wqlquerysource--file-connection"></a>WQLQuerySource = File connection  
 **WQLQuerySource**  
 Wählen Sie einen Dateiverbindungs-Manager aus der Liste \<aus, oder klicken Sie auf **neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysource--variable"></a>WQLQuerySource = Variable  
 **WQLQuerySource**  
 Wählen Sie eine Variable aus der Liste aus, \<oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task ' WMI-Ereignisüberwachung ' &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Ausdrucks Seite](expressions/expressions-page.md)   
 [WMI-Datenleser (Task)](control-flow/wmi-data-reader-task.md)  
  
  
