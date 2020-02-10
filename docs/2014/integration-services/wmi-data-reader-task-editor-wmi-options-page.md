---
title: Editor für den Task ' WMI-Daten Leser ' (Seite WMI-Optionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8367f0ae57df5333808e4dfde25c5676a3bcf1d4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054357"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a>Editor für den Task 'WMI-Datenleser' (Seite WMI-Optionen)
  Auf der Seite **WMI-Optionen** des Dialogfelds **Editor für den Task „WMI-Datenleser“** können Sie die Quelle der WQL-Abfrage (Windows Management Instrumentation Query Language) und das Ziel des Abfrageergebnisses angeben.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [WMI Data Reader Task](control-flow/wmi-data-reader-task.md). Weitere Informationen zur WMI Query Language (WQL) finden Sie im Thema zur Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI), [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)(Abfragen mit WQL), in der MSDN Library.  
  
## <a name="static-options"></a>Statische Optionen  
 **Wmiconnectionname**  
 Wählen Sie einen vorhandenen WMI-Verbindungs-Manager aus der Liste aus, oder klicken Sie auf \<**Neue WMI-Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [WMI-Verbindungs-Manager](connection-manager/wmi-connection-manager.md), [WMI-Verbindungs-Manager-Editor](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Wählen Sie den Quelltyp der WQL-Abfrage aus, die von dem Task ausgeführt wird. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Direkte Eingabe**|Legen Sie die Quelle für eine WQL-Abfrage fest. Bei Auswahl dieses Werts wird die dynamische Option **WQLQuerySourceType**angezeigt.|  
|**Dateiverbindung**|Wählen Sie eine Datei aus, in der die WQL-Abfrage enthalten ist. Bei Auswahl dieses Werts wird die dynamische Option **WQLQuerySourceType**angezeigt.|  
|**Variable**|Legen Sie die Quelle für eine Variable fest, die die WQL-Abfrage definiert. Bei Auswahl dieses Werts wird die dynamische Option **WQLQuerySourceType**angezeigt.|  
  
 **OutputType**  
 Geben Sie an, ob es sich bei der Ausgabe um eine Datentabelle, einen Eigenschaftswert oder einen Eigenschaftsnamen und -wert handeln soll.  
  
 **OverwriteDestination**  
 Gibt an, ob die ursprünglichen Daten in der Zieldatei oder -variablen beibehalten, überschrieben oder an diese angefügt werden sollen.  
  
 **DestinationType**  
 Wählen Sie den Zieltyp der WQL-Abfrage aus, die von dem Task ausgeführt wird. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Dateiverbindung**|Wählen Sie eine Datei aus, um die Ergebnisse der WQL-Abfrage darin zu speichern. Bei Auswahl dieses Werts wird die dynamische Option **DestinationType**angezeigt.|  
|**Variable**|Legen Sie die Variable fest, um die Ergebnisse der WQL-Abfrage darin zu speichern. Bei Auswahl dieses Werts wird die dynamische Option **DestinationType**angezeigt.|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a>Dynamische Optionen von WQLQuerySourceType  
  
### <a name="wqlquerysourcetype--direct-input"></a>WQLQuerySourceType = Direct input  
 **WQLQuerySource (**  
 Stellen Sie eine Abfrage bereit, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), und geben Sie eine Abfrage mithilfe des Dialogfelds **WQL-Abfrage** ein.  
  
### <a name="wqlquerysourcetype--file-connection"></a>WQLQuerySourceType = File connection  
 **WQLQuerySource (**  
 Wählen Sie einen Dateiverbindungs-Manager aus der Liste \<aus, oder klicken Sie auf **neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md), [Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysourcetype--variable"></a>WQLQuerySourceType = Variable  
 **WQLQuerySource (**  
 Wählen Sie eine Variable aus der Liste aus, \<oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
## <a name="destinationtype-dynamic-options"></a>Dynamische Optionen von DestinationType  
  
### <a name="destinationtype--file-connection"></a>DestinationType = File connection  
 **Ziel**  
 Wählen Sie einen Dateiverbindungs-Manager aus der Liste \<aus, oder klicken Sie auf **neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md), [Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="destinationtype--variable"></a>DestinationType = Variable  
 **Ziel**  
 Wählen Sie eine Variable aus der Liste aus, \<oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task ' WMI-Daten Leser ' &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [WMI-Ereignisüberwachung (Task)](control-flow/wmi-event-watcher-task.md)  
  
  
