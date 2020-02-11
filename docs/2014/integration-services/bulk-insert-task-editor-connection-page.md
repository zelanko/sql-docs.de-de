---
title: Massen Einfügungs Task-Editor (Seite Verbindung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b6834a2a4cd75e70de253419cc42ec5904ce0793
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66061218"
---
# <a name="bulk-insert-task-editor-connection-page"></a>Masseneinfügungstask-Editor (Seite Verbindung)
  Mithilfe der Seite **Verbindung** im Dialogfeld **Masseneinfügungstask-Editor** können Sie die Quelle und das Ziel des Masseneinfügevorgangs und das zu verwendende Format angeben.  
  
 Informationen zum Arbeiten mit Masseneinfügungen finden Sie unter [Masseneinfügungstask](control-flow/bulk-insert-task.md) und [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="options"></a>Tastatur  
 **Verbindung**  
 Wählen Sie einen OLE DB-Verbindungs-Manager in der Liste aus, oder klicken Sie auf \<**Neue Verbindung...**>, um eine neue Verbindung zu erstellen.  
  
 **Verwandte Themen:** [OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md), [Konfigurieren von OLE DB-Verbindungs-Manager](../../2014/integration-services/configure-ole-db-connection-manager.md)  
  
 **DestinationTable**  
 Geben Sie den Namen der Zieltabelle oder Zielsicht ein, oder wählen Sie aus der Liste eine Tabelle oder Sicht aus.  
  
 **Ges**  
 Wählen Sie die Quelle des Formats für die Masseneinfügung aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Datei verwenden**|Wählen Sie eine Datei mit Formatspezifikationen aus. Nach Auswahl dieser Option wird die dynamische Option **FormatFile**angezeigt.|  
|**Geben**|Geben Sie das Format an. Wenn Sie diese Option auswählen, werden `RowDelimiter` die dynamischen `ColumnDelimiter`Optionen und angezeigt.|  
  
 **Datei**  
 Wählen Sie einen Datei- oder Flatfileverbindungs-Manager in der Liste aus, oder klicken Sie auf \<**Neue Verbindung...**>, um eine neue Verbindung zu erstellen.  
  
 Der Speicherort ist relativ zur SQL Server-Datenbank-Engine, die im Verbindungs-Manager für diesen Task angegeben wurde. Die SQL Server-Datenbank-Engine muss auf die Textdatei zugreifen können, und zwar entweder auf einer lokalen Festplatte des Servers oder über eine Freigabe oder einem SQL Server zugeordneten Laufwerk. Auf die Datei wird nicht von der SSIS-Laufzeit zugegriffen.  
  
 Wenn Sie auf die Quelldatei mithilfe eines Flatfileverbindungs-Managers zugreifen, verwendet der Masseneinfügungstask nicht das im Flatfileverbindungs-Manager angegebene Format. Stattdessen verwendet der Masseneinfügungstask entweder das in einer Formatdatei angegebene Format oder die Werte der Eigenschaften RowDelimiter und ColumnDelimiter des Tasks.  
  
 **Verwandte Themen:** [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md), [Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md), [Verbindungs](connection-manager/flat-file-connection-manager.md)-Manager für Flatfiles, Verbindungs-Manager- [Editor für Flatfiles, &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md), [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Spalten&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md), [Verbindungs-&#40;Manager](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) -Editor für Flatfiles  
  
 **Tabellen aktualisieren**  
 Aktualisieren Sie die Liste der Tabellen und Sichten.  
  
## <a name="format-dynamic-options"></a>Format (dynamische Optionen)  
  
### <a name="format--use-file"></a>Format = Use File  
 **Format file**  
 Geben Sie den Pfad der Formatdatei ein, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**…**), um nach der Formatdatei zu suchen.  
  
### <a name="format--specify"></a>Format = Specify  
 `RowDelimiter`  
 Geben Sie das Zeilentrennzeichen in der Quelldatei an. Der Standardwert ist **{CR} {LF}**.  
  
 `ColumnDelimiter`  
 Geben Sie das Spaltentrennzeichen in der Quelldatei an. Der Standardwert ist **Tabstopp**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Massen Einfügungs Task-Editor &#40;Seite Allgemein&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md)   
 [Massen Einfügungs Task-Editor &#40;Options Seite&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Ablaufsteuerung](control-flow/control-flow.md)  
  
  
