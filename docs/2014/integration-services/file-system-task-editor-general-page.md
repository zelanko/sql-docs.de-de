---
title: Dateisystem Aufgabe-Editor (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e6778bd585d84601d35846cafca3822a81a3bb60
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208750"
---
# <a name="file-system-task-editor-general-page"></a>Editor für den Task 'Dateisystem' (Seite Allgemein)
  Mithilfe der Seite **Allgemein** des Dialogfelds **Editor für den Task 'Dateisystem'** können Sie den Dateisystemvorgang konfigurieren, der durch den Task ausgeführt wird.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [File System Task](control-flow/file-system-task.md).  
  
 Sie müssen durch Festlegen der Eigenschaften SourceConnection und DestinationConnection einen Quell- und einen Zielverbindungs-Manager angeben. Sie können entweder die Namen von Dateiverbindungs-Managern bereitstellen, die auf die Dateien zeigen, die der Task als Quelle oder Ziel verwendet. Wenn die Pfade der Dateien in Variablen gespeichert sind, können Sie alternativ auch die Namen der Variablen bereitstellen. Wenn Sie Variablen zum Speichern der Dateipfade verwenden möchten, müssen Sie zuerst die Option IsSourcePathVariable für die Quellverbindung und die Option IsDestinationPathVariable für die Zielverbindung auf **True**festlegen. Sie können dann die vorhandenen System- oder benutzerdefinierten Variablen zur Verwendung auswählen oder neue Variablen erstellen. Im Dialogfeld **Variable hinzufügen** können Sie den Bereich der Variablen konfigurieren und angeben. Der Bereich muss der Task Dateisystem oder ein übergeordneter Container sein. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md) und [Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md).  
  
> [!NOTE]  
>  Zum Überschreiben Sie die Variablen für die Auswahl der `SourceConnection` und `DestinationConnection` Eigenschaften, geben Sie einen Ausdruck für die **Quelle** und **Ziel** Eigenschaften. Die Ausdrücke werden im **Editor für den Task 'Dateisystem'** auf der Seite **Ausdrücke**eingegeben. Wenn Sie beispielsweise den Pfad der Dateien, die vom Task verwendet werden, als Ziel festlegen möchten, kann in einigen Fällen die Variable A und in anderen die Variable B besser geeignet sein.  
  
> [!NOTE]  
>  Der Task Dateisystem wird in einer einzelnen Datei oder in einem einzelnen Verzeichnis ausgeführt. Daher unterstützt dieser Task nicht die Verwendung von Platzhalterzeichen, um denselben Vorgang in mehreren Dateien oder Verzeichnissen auszuführen. Damit der Task Dateisystem einen Vorgang in mehreren Dateien oder Verzeichnissen wiederholt, platzieren Sie den Task Dateisystem in einem Foreach-Schleifencontainer. Weitere Informationen finden Sie unter [File System Task](control-flow/file-system-task.md).  
  
 Sie können Ausdrücke verwenden, um verschiedene Variablen einzusetzen.  
  
## <a name="options"></a>Tastatur  
 **IsDestinationPathVariable**  
 Geben Sie an, ob der Zielpfad in einer Variablen gespeichert ist. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|Description|  
|-----------|-----------------|  
|**Wahr**|Der Zielpfad ist in einer Variablen gespeichert. Wenn Sie diesen Wert auswählen, wird die dynamische Option **DestinationVariable**angezeigt.|  
|**False**|Der Zielpfad wird in einem Dateiverbindungs-Manager angegeben. Bei Auswahl dieses Wertes wird die dynamische Option `DestinationConnection`.|  
  
 **OverwriteDestination**  
 Geben Sie an, ob der Vorgang Dateien im Zielverzeichnis überschreiben kann.  
  
 **Name**  
 Geben Sie einen eindeutigen Namen für den Task Dateisystem an. Dieser Name wird im Tasksymbol als Bezeichnung verwendet.  
  
> [!NOTE]  
>  Tasknamen müssen innerhalb eines Pakets eindeutig sein.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung des Tasks Dateisystem ein.  
  
 **Vorgang**  
 Wählen Sie den auszuführenden Dateisystemvorgang aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|Description|  
|-----------|-----------------|  
|**Verzeichnis kopieren**|Kopieren Sie ein Verzeichnis. Bei Auswahl dieses Wertes werden die dynamischen Optionen für eine Quelle und ein Ziel angezeigt.|  
|**Datei kopieren**|Kopieren Sie eine Datei. Bei Auswahl dieses Wertes werden die dynamischen Optionen für eine Quelle und ein Ziel angezeigt.|  
|**Verzeichnis erstellen**|Erstellen Sie ein Verzeichnis. Bei Auswahl dieses Wertes werden die dynamischen Optionen für ein Quell- und ein Zielverzeichnis angezeigt.|  
|**Verzeichnis löschen**|Löschen Sie ein Verzeichnis. Bei Auswahl dieses Wertes werden die dynamischen Optionen für eine Quelle angezeigt.|  
|**Verzeichnisinhalt löschen**|Löschen Sie den Inhalt eines Verzeichnisses. Bei Auswahl dieses Wertes werden die dynamischen Optionen für eine Quelle angezeigt.|  
|**Datei löschen**|Löschen Sie eine Datei. Bei Auswahl dieses Wertes werden die dynamischen Optionen für eine Quelle angezeigt.|  
|**Verzeichnis verschieben**|Verschieben Sie ein Verzeichnis. Bei Auswahl dieses Wertes werden die dynamischen Optionen für eine Quelle und ein Ziel angezeigt.|  
|**Datei verschieben**|Verschieben Sie eine Datei. Bei Auswahl dieses Wertes werden die dynamischen Optionen für eine Quelle und ein Ziel angezeigt.<br /><br /> Hinweis: Wenn Sie eine Datei zu verschieben, enthalten Sie keinen Dateinamen in den Verzeichnispfad ein, dem Sie als Ziel angeben.|  
|**Datei umbenennen**|Benennen Sie eine Datei um. Bei Auswahl dieses Wertes werden die dynamischen Optionen für eine Quelle und ein Ziel angezeigt.<br /><br /> Hinweis: Beim Umbenennen einer Datei enthalten Sie den neuen Dateinamen in den Verzeichnispfad an, dem Sie für das Ziel bereitstellen.|  
|**Attribute festlegen**|Legen Sie die Attribute einer Datei oder eines Verzeichnisses fest. Bei Auswahl dieses Wertes werden die dynamischen Optionen für eine Quelle und einen Vorgang angezeigt.|  
  
 `IsSourcePathVariable`  
 Geben Sie an, ob der Zielpfad in einer Variablen gespeichert ist. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value||  
|-----------|-|  
|**True**|Der Zielpfad ist in einer Variablen gespeichert. Bei Auswahl dieses Wertes wird die dynamische Option **SourceVariable**angezeigt.|  
|**False**|Der Zielpfad wird in einem Dateiverbindungs-Manager angegeben. Wenn Sie diesen Wert auswählen, wird die dynamische Option **DestinationVariable**angezeigt.|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a>IsDestinationPathVariable (dynamische Optionen)  
  
### <a name="isdestinationpathvariable--true"></a>IsDestinationPathVariable = True  
 **DestinationVariable**  
 Wählen Sie den Variablennamen aus der Liste aus, oder klicken Sie auf \<**Neue Variable…**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md)  
  
### <a name="isdestinationpathvariable--false"></a>IsDestinationPathVariable = False  
 `DestinationConnection`  
 Wählen Sie in der Liste einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="issourcepathvariable-dynamic-options"></a>IsSourcePathVariable (dynamische Optionen)  
  
### <a name="issourcepathvariable--true"></a>IsSourcePathVariable = True  
 **SourceVariable**  
 Wählen Sie den Variablennamen aus der Liste aus, oder klicken Sie auf \<**Neue Variable…**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md)  
  
### <a name="issourcepathvariable--false"></a>IsSourcePathVariable = False  
 `SourceConnection`  
 Wählen Sie in der Liste einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="operation-dynamic-options"></a>Operation (dynamische Optionen)  
  
### <a name="operation--set-attributes"></a>Operation = Set Attributes  
 **Hidden**  
 Geben Sie an, ob die Datei oder das Verzeichnis angezeigt wird.  
  
 **ReadOnly**  
 Geben Sie an, ob die Datei schreibgeschützt ist.  
  
 **Archive**  
 Geben Sie an, ob die Datei oder das Verzeichnis archiviert werden kann.  
  
 **System**  
 Geben Sie an, ob die Datei eine Betriebssystemdatei ist.  
  
### <a name="operation--create-directory"></a>Operation = Create directory  
 `UseDirectoryIfExists`  
 Gibt an, ob der Vorgang **Verzeichnis erstellen** ein vorhandenes Verzeichnis mit dem angegebenen Namen verwendet, statt ein neues Verzeichnis zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)  
  
  
