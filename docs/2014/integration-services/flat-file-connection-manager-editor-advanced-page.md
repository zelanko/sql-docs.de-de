---
title: Flatfile-Verbindungs-Manager-Editor (Seite erweitert) | Microsoft Docs
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
- sql12.dts.designer.ffileconnection.columnproperties.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 58aa3dee-4774-4e0b-a956-96d199be4c3a
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3b2aa339c8f68d65bdb1566ff781facccf927358
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149927"
---
# <a name="flat-file-connection-manager-editor-advanced-page"></a>Verbindungs-Manager-Editor für Flatfiles (Seite Erweitert)
  Verwenden Sie im Dialogfeld **Verbindungs-Manager-Editor für Flatfiles** die Seite **Erweitert** , um die Eigenschaften festzulegen, mit denen angegeben wird, wie mit Integration Services Daten in Flatfiles gelesen und geschrieben werden. Sie können die Namen der Spalten in der Flatfile ändern und Eigenschaften festlegen. Zu den Eigenschaften zählen der Datentyp und die Trennzeichen für jede Spalte in der Datei.  
  
 Standardmäßig beträgt die Länge von Zeichenfolgenspalten 50 Zeichen. Sie können die Länge dieser Spalten ändern, um das Abschneiden von Daten und das Entstehen übermäßig breiter Spalten zu verhindern. Sie können darüber hinaus andere Metadaten aktualisieren, um Kompatibitlität mit Zielspalten zu aktivieren. Sie können beispielsweise den Datentyp einer Spalte, die nur ganzzahlige Daten enthält, in einen numerischen Datentyp ändern, z. B. DT_I2. Nehmen Sie diese Änderungen manuell vor, oder klicken Sie auf die Schaltfläche **Typen vorschlagen** , um mithilfe des Dialogfelds **Spaltentypen vorschlagen** Beispieldaten auszuwerten und einige dieser Änderungen automatisch vornehmen zu lassen.  
  
 Weitere Informationen zum Verbindungs-Manager für Flatfiles finden Sie unter [Flat File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="options"></a>Tastatur  
 **Name des Verbindungs-Managers**  
 Geben Sie einen eindeutigen Namen für den Verbindungs-Manager für Flatfiles im Workflow an. Der angegebene Name wird im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer angezeigt.  
  
 **Beschreibung**  
 Beschreiben Sie den Verbindungs-Manager. Die bewährte Methode ist hierbei, den Verbindungs-Manager zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und leichter zu verwalten sind.  
  
 **Konfigurieren Sie die Eigenschaften für jede Spalte.**  
 Wählen Sie eine Spalte im linken Bereich, um im rechten Bereich ihre Eigenschaften anzuzeigen. In der folgenden Tabelle werden die Datentypeigenschaften beschrieben. Einige der aufgeführten Eigenschaften können nur für einige Flatfileformate konfiguriert werden.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**ColumnType**|Gibt an, ob eine Spalte getrennt ist, eine feste Breite hat bzw. einen unregelmäßigen rechten Rand aufweist. Diese Eigenschaft ist schreibgeschützt. Bei Dateien mit rechtem Flatterrand haben die Spalten mit Ausnahme der letzten Spalte eine feste Breite. Die Trennung der letzten Spalte erfolgt mit einem Zeilentrennzeichen.|  
|**OutputColumnWidth**|Geben Sie einen Wert an, der als Anzahl von Bytes gespeichert werden soll; bei Unicode-Dateien entspricht dieser Wert einer Zeichenanzahl. Im Datenflusstask dient dieser Wert dem Festlegen der Breite der Ausgabespalte für die Flatfilequelle.<br /><br /> Hinweis: Im Objektmodell heißt diese Eigenschaft MaximumWidth.|  
|**DataType**|Wählen Sie eine Option aus der Liste der verfügbaren Datentypen aus. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).|  
|**TextQualified**|Gibt an, ob Textdaten Qualifizierer Textzeichen z. B. in Anführungszeichen eingeschlossen ist. Gültige Werte sind:<br /><br /> **True**: Die Textdaten in der Flatfile sind gekennzeichnet.<br /><br /> **False**: Die Textdaten in der Flatfile sind nicht gekennzeichnet.|  
|**Name**|Geben Sie einen beschreibenden Spaltennamen an. Wenn Sie keinen Namen eingeben, wird in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] automatisch ein Name im Format Spalte 0, Spalte 1 usw. erstellt.|  
|**DataScale**|Gibt die Skala numerischer Daten an. Skala heißt in diesem Fall die Anzahl der Dezimalstellen. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).|  
|**ColumnDelimiter**|Wählen Sie eine Option aus der Liste der verfügbaren Spaltentrennzeichen aus. Dabei sollten Sie Spaltentrennzeichen auswählen, deren Auftreten als Zeichen im Text unwahrscheinlich ist. Bei Spalten fester Breite wird dieser Wert ignoriert.<br /><br /> **{CR}{LF}**. Als Trennzeichen für Spalten dient ein Wagenrücklauf in Kombination mit einem Zeilenvorschub.<br /><br /> **{CR}**. Als Trennzeichen für Spalten dient ein Wagenrücklauf.<br /><br /> **{LF}**. Als Trennzeichen für Spalten dient ein Zeilenvorschub.<br /><br /> **Semikolon {;}**. Als Trennzeichen für Spalten dient ein Semikolon.<br /><br /> **Doppelpunkt {:}**. Als Trennzeichen für Spalten dient ein Doppelpunkt.<br /><br /> **Komma {,}**. Als Trennzeichen für Spalten dient ein Komma.<br /><br /> **Tabulator {t}**. Als Trennzeichen für Spalten dient ein Tabulator.<br /><br /> **Senkrechter Strich {&#124;}**. Als Trennzeichen für Spalten dient ein senkrechter Strich.|  
|**DataPrecision**|Gibt die Präzision numerischer Daten an. Präzision heißt in diesem Fall die Anzahl der Stellen. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).|  
|**InputColumnWidth**|Gibt an, welcher Wert als Anzahl von Bytes gespeichert werden soll; bei Unicode-Dateien wird dieser Wert als Zeichenanzahl angezeigt. Bei mit Trennzeichen versehenen Spalten wird dieser Wert ignoriert.<br /><br /> **Hinweis:** Im Objektmodell heißt diese Eigenschaft ColumnWidth.|  
  
 **Neu**  
 Durch Klicken auf **Neu**fügen Sie eine neue Spalte hinzu. Die neue Spalten wird beim Klicken auf **Neu** standardmäßig am Ende der Liste hinzugefügt. Ferner sind für die Schaltfläche folgende, über die Dropdownliste auswählbare Optionen verfügbar.  
  
|value|Description|  
|-----------|-----------------|  
|**Spalte hinzufügen**|Fügt am Ende der Liste eine neue Spalte hinzu.|  
|**Einfügen vor**|Fügt vor der ausgewählten Spalte eine neue Spalte ein.|  
|**Einfügen nach**|Fügt nach der ausgewählten Spalte eine neue Spalte ein.|  
  
 **Delete**  
 Wählen Sie eine Spalte aus, und entfernen Sie sie dann, indem Sie auf **Löschen**klicken.  
  
 **Typen vorschlagen**  
 Im Dialogfeld **Spaltentypen vorschlagen** können Sie die Beispieldaten in der Datei auswerten, um Vorschläge für den Datentyp und die -länge der einzelnen Spalten zu erhalten. Weitere Informationen finden Sie unter [Referenz zur Benutzeroberfläche des Dialogfelds „Spaltentypen vorschlagen“](connection-manager/suggest-column-types-dialog-box-ui-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Dateiverbindungs-Manager-Editor für Flatfiles &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Dateiverbindungs-Manager-Editor für Flatfiles &#40;Seite "Spalten"&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)   
 [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Vorschau&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  