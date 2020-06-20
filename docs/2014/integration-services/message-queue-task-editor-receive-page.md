---
title: Editor für den Task ' Nachrichten Warteschlange ' (Seite empfangen) Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.receive.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 7028756d-1dcc-480c-bbcd-e9654f0772a0
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b30a7863fe50843f4408931b2b766bcb520f3a2c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84950990"
---
# <a name="message-queue-task-editor-receive-page"></a>Editor für den Task 'Nachrichtenwarteschlange' (Seite Empfangen)
  Auf der Seite **Empfangen** des Dialogfelds **Editor für den Task „Nachrichtenwarteschlange“** können Sie den Task „Nachrichtenwarteschlange“ konfigurieren, um MSMQ-Nachrichten ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing) zu empfangen.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [Message Queue Task](control-flow/message-queue-task.md).  
  
## <a name="options"></a>Tastatur  
 **RemoveFromMessageQueue**  
 Geben Sie an, ob die Nachricht aus der Warteschlange entfernt werden soll, nachdem sie empfangen wurde. Standardmäßig ist dieser Wert auf `False` festgelegt.  
  
 **ErrorIfMessageTimeOut**  
 Geben Sie an, ob der Task fehlschlägt und eine Fehlermeldung angezeigt wird, wenn die Zeit für die Nachricht überschritten wird. Der Standardwert lautet `False`.  
  
 **TimeoutAfter**  
 Wenn eine Fehlermeldung beim Fehlschlagen des Tasks angezeigt werden soll, geben Sie hier die Wartezeit vor dem Anzeigen der Timeoutmeldung in Sekunden an.  
  
 **MessageType**  
 Wählen Sie den Nachrichtentyp aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**Data file message**|Die Nachricht wird in einer Datei gespeichert. Bei Auswahl dieses Wertes wird die dynamische Option **DataFileMessage**angezeigt.|  
|**Variable message**|Die Nachricht wird in einer Variable gespeichert. Bei Auswahl dieses Wertes wird die dynamische Option **VariableMessage**angezeigt.|  
|**String message**|Die Nachricht wird im Task 'Nachrichtenwarteschlange' gespeichert. Bei Auswahl dieses Wertes wird die dynamische Option **StringMessage**angezeigt.|  
|**String message to variable**|Die Nachricht wurde in einer Variablen gespeichert.<br /><br /> Bei Auswahl dieses Wertes wird die dynamische Option **StringMessage**angezeigt.|  
  
## <a name="messagetype-dynamic-options"></a>MessageType (dynamische Optionen)  
  
### <a name="messagetype--data-file-message"></a>MessageType = Data file message  
 **SaveFileAs**  
 Geben Sie den Pfad der zu verwendenden Datei an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(...)**, um nach der Datei zu suchen.  
  
 **Overwrite**  
 Geben Sie an, dass die Daten in einer vorhandenen Datei überschrieben werden sollen, wenn der Inhalt einer Datendateinachricht gespeichert wird. Der Standardwert lautet `False`.  
  
 **Filter**  
 Geben Sie an, ob auf die Nachricht ein Filter angewendet werden soll. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**Kein Filter**|Der Task filtert keine Nachrichten. Wenn Sie diesen Wert auswählen, wird die dynamische Option **IdentifierReadOnly**angezeigt.|  
|**Vom Paket**|Der Task empfängt nur Nachrichten von dem angegebenen Paket. Wenn Sie diesen Wert auswählen, wird die dynamische Option **Identifier**angezeigt.|  
  
### <a name="filter-dynamic-options"></a>Filter (dynamische Optionen)  
  
#### <a name="filter--no-filter"></a>Filter = No filter  
 **IdentifierReadOnly**  
 Diese Option ist schreibgeschützt. Sie kann leer sein oder die GUID eines Pakets enthalten, wenn die Eigenschaft Filter vorher festgelegt wurde.  
  
#### <a name="filter--from-package"></a>Filter = From package  
 **Bezeichner**  
 Wenn Sie einen Filter anwenden möchten, geben Sie den eindeutigen Bezeichner des Pakets ein, aus dem die Nachrichten empfangen werden können, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(...)**, und geben Sie das Paket an.  
  
 **Verwandte Themen:** [Paket auswählen](control-flow/select-a-package.md)  
  
### <a name="messagetype--variable-message"></a>MessageType = Variable message  
 **Filter**  
 Geben Sie an, ob auf Nachrichten ein Filter angewendet werden soll. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**Kein Filter**|Der Task filtert keine Nachrichten. Wenn Sie diesen Wert auswählen, wird die dynamische Option **IdentifierReadOnly**angezeigt.|  
|**Vom Paket**|Der Task empfängt nur Nachrichten von dem angegebenen Paket. Wenn Sie diesen Wert auswählen, wird die dynamische Option **Identifier**angezeigt.|  
  
 **Variable**  
 Geben Sie den Variablennamen ein, oder klicken Sie auf, \<**New variable...**> und konfigurieren Sie dann eine neue Variable.  
  
 **Verwandte Themen:** [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
### <a name="filter-dynamic-options"></a>Filter (dynamische Optionen)  
  
#### <a name="filter--no-filter"></a>Filter = No filter  
 **IdentifierReadOnly**  
 Diese Option ist leer.  
  
#### <a name="filter--from-package"></a>Filter = From package  
 **Bezeichner**  
 Wenn Sie einen Filter anwenden möchten, geben Sie den eindeutigen Bezeichner des Pakets ein, aus dem die Nachrichten empfangen werden können, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(...)**, und geben Sie das Paket an.  
  
 **Verwandte Themen:** [Paket auswählen](control-flow/select-a-package.md)  
  
### <a name="messagetype--string-message"></a>MessageType = Zeichenfolgennachricht  
 **Vergleich**  
 Geben Sie an, ob auf Nachrichten ein Filter angewendet werden soll. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Value|BESCHREIBUNG|  
|-----------|-----------------|  
|**None**|Die Nachrichten werden nicht verglichen.|  
|**Genaue Übereinstimmung**|Die Nachrichten müssen genau mit der Zeichenfolge in der Option **CompareString** übereinstimmen.|  
|**Groß-/Kleinschreibung ignorieren**|Die Nachricht muss mit der Zeichenfolge in der Option **CompareString** übereinstimmen, aber beim Vergleichen wird nicht zwischen Groß- und Kleinschreibung unterschieden.|  
|**Mit Inhalt**|Die Nachrichten müssen die Zeichenfolge in der Option **CompareString** enthalten.|  
  
 **CompareString**  
 Geben Sie hier die Zeichenfolge an, mit der die Nachricht verglichen wird, wenn die Option **Vergleichen** nicht auf **Keine**festgelegt ist.  
  
### <a name="messagetype--string-message-to-variable"></a>MessageType = String message to variable  
 **Vergleich**  
 Geben Sie an, ob auf Nachrichten ein Filter angewendet werden soll. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Value|BESCHREIBUNG|  
|-----------|-----------------|  
|**None**|Die Nachrichten werden nicht verglichen.|  
|**Genaue Übereinstimmung**|Die Nachricht muss genau mit der Zeichenfolge in der Option **CompareString** übereinstimmen.|  
|**Groß-/Kleinschreibung ignorieren**|Die Nachricht muss mit der Zeichenfolge in der Option **CompareString** übereinstimmen, aber beim Vergleichen wird nicht zwischen Groß- und Kleinschreibung unterschieden.|  
|**Mit Inhalt**|Die Nachricht muss die Zeichenfolge in der Option **CompareString** enthalten.|  
  
 **CompareString**  
 Geben Sie hier die Zeichenfolge an, mit der die Nachricht verglichen wird, wenn die Option **Vergleichen** nicht auf **Keine**festgelegt ist.  
  
 **Variable**  
 Geben Sie den Namen der Variablen ein, die die empfangene Nachricht enthalten soll, oder klicken Sie auf, \<**New variable...**> und konfigurieren Sie dann eine neue Variable.  
  
 **Verwandte Themen:** [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task Nachrichten Warteschlange &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor für den Task Nachrichten Warteschlange &#40;&#41;Seite senden](../../2014/integration-services/message-queue-task-editor-send-page.md)   
 [Ausdrucks Seite](expressions/expressions-page.md)   
 [Nachrichtenwarteschlange (Task)](control-flow/message-queue-task.md)  
  
  
