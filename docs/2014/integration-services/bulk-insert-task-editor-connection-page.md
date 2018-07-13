---
title: Massenimport von Insert-Task-Editor (Verbindungsseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
caps.latest.revision: 30
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed6ab27e4c60aa398cafe1be0d4bbcb19ce3bb3d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201810"
---
# <a name="bulk-insert-task-editor-connection-page"></a>Masseneinfügungstask-Editor (Seite Verbindung)
  Mithilfe der Seite **Verbindung** im Dialogfeld **Masseneinfügungstask-Editor** können Sie die Quelle und das Ziel des Masseneinfügevorgangs und das zu verwendende Format angeben.  
  
 Informationen zum Arbeiten mit Masseneinfügungen finden Sie unter [Masseneinfügungstask](control-flow/bulk-insert-task.md) und [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="options"></a>Tastatur  
 **Verbindung**  
 Wählen Sie einen OLE DB-Verbindungs-Manager in der Liste aus, oder klicken Sie auf \<**Neue Verbindung...**>, um eine neue Verbindung zu erstellen.  
  
 **Verwandte Themen:** [OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md), [OLE DB-Verbindungs-Manager konfigurieren](../../2014/integration-services/configure-ole-db-connection-manager.md)  
  
 **DestinationTable**  
 Geben Sie den Namen der Zieltabelle oder Zielsicht ein, oder wählen Sie aus der Liste eine Tabelle oder Sicht aus.  
  
 **Format**  
 Wählen Sie die Quelle des Formats für die Masseneinfügung aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|Description|  
|-----------|-----------------|  
|**Use File**|Wählen Sie eine Datei mit Formatspezifikationen aus. Nach Auswahl dieser Option wird die dynamische Option **FormatFile**angezeigt.|  
|**Specify**|Geben Sie das Format an. Nach Auswahl dieser Option werden die dynamischen Optionen `RowDelimiter` und `ColumnDelimiter`.|  
  
 **File**  
 Wählen Sie einen Datei- oder Flatfileverbindungs-Manager in der Liste aus, oder klicken Sie auf \<**Neue Verbindung...**>, um eine neue Verbindung zu erstellen.  
  
 Der Speicherort ist relativ zur SQL Server-Datenbank-Engine, die im Verbindungs-Manager für diesen Task angegeben wurde. Die SQL Server-Datenbank-Engine muss auf die Textdatei zugreifen können, und zwar entweder auf einer lokalen Festplatte des Servers oder über eine Freigabe oder einem SQL Server zugeordneten Laufwerk. Auf die Datei wird nicht von der SSIS-Laufzeit zugegriffen.  
  
 Wenn Sie auf die Quelldatei mithilfe eines Flatfileverbindungs-Managers zugreifen, verwendet der Masseneinfügungstask nicht das im Flatfileverbindungs-Manager angegebene Format. Stattdessen verwendet der Masseneinfügungstask entweder das in einer Formatdatei angegebene Format oder die Werte der Eigenschaften RowDelimiter und ColumnDelimiter des Tasks.  
  
 **Verwandte Themen:** [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md), [Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md), [Verbindungs-Manager für Flatfiles](connection-manager/flat-file-connection-manager.md), [Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md), [Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Spalten“&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md), [Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Erweitert“&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)  
  
 **Tabellen aktualisieren**  
 Aktualisieren Sie die Liste der Tabellen und Sichten.  
  
## <a name="format-dynamic-options"></a>Format (dynamische Optionen)  
  
### <a name="format--use-file"></a>Format = Use File  
 **FormatFile**  
 Geben Sie den Pfad der Formatdatei ein, oder klicken Sie auf die Schaltfläche mit den drei Punkten ( **…** ), um nach der Formatdatei zu suchen.  
  
### <a name="format--specify"></a>Format = Specify  
 `RowDelimiter`  
 Geben Sie das Zeilentrennzeichen in der Quelldatei an. Der Standardwert ist **{CR}{LF}**.  
  
 `ColumnDelimiter`  
 Geben Sie das Spaltentrennzeichen in der Quelldatei an. Der Standardwert ist **Tabstopp**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Massenimport von Insert-Task-Editor &#40;Seite "Allgemein"&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md)   
 [Massenimport von Insert-Task-Editor &#40;Seite "Optionen"&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Ablaufsteuerung](control-flow/control-flow.md)  
  
  
