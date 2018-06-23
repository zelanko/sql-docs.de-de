---
title: Editor für die WMI-Ereignisüberwachung-Task (Seite "WMI-Optionen") | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0163cc6fdc1af42031886c4b0dc47889df85d0a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162294"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a>Editor für den Task 'WMI-Ereignisüberwachung' (Seite WMI-Optionen)
  Auf der Seite **WMI-Optionen** des Dialogfelds **Editor für den Task „WMI-Ereignisüberwachung“** können Sie die Quelle der WQL-Abfrage (Windows Management Instrumentation Query Language) und das Verhalten angeben, mit dem der Task „WMI-Ereignisüberwachung“ auf WMI-Ereignisse (Microsoft Windows Instrumentation) antwortet.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md). Weitere Informationen zur WMI Query Language finden Sie im WMI-Thema [Querying with WQL](http://go.microsoft.com/fwlink/?LinkId=79045)(Abfragen mit WQL), in der MSDN Library.  
  
## <a name="static-options"></a>Statische Optionen  
 **WMIConnectionName**  
 Wählen Sie einen vorhandenen WMI-Verbindungs-Manager aus der Liste aus, oder klicken Sie auf \<**Neue WMI-Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [WMI-Verbindungs-Manager](connection-manager/wmi-connection-manager.md), [WMI-Verbindungs-Manager-Editor](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Wählen Sie den Quelltyp der WQL-Abfrage aus, die von dem Task ausgeführt wird. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|Description|  
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
 Stellen Sie eine Abfrage bereit, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (…), und geben Sie im Dialogfeld **WQL-Abfrage** eine Abfrage ein.  
  
### <a name="wqlquerysource--file-connection"></a>WQLQuerySource = File connection  
 **WQLQuerySource**  
 Wählen Sie in der Liste einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysource--variable"></a>WQLQuerySource = Variable  
 **WQLQuerySource**  
 Wählen Sie in der Liste eine Variable aus, oder klicken Sie auf \<**Neue Variable…**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Task-Editor für WMI-Ereignisüberwachung &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [WMI-Datenleser (Task)](control-flow/wmi-data-reader-task.md)  
  
  