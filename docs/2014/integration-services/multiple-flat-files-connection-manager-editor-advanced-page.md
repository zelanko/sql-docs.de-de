---
title: Verbindungs-Manager-Editor für mehrere Flatfiles (Seite erweitert) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.advanced.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: fc883131-c03d-4ab3-8220-b51cbe243a82
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: de238c1012a255ceb59086e542d5529b8b907915
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057549"
---
# <a name="multiple-flat-files-connection-manager-editor-advanced-page"></a>Verbindungs-Manager-Editor für mehrere Flatfiles (Seite Erweitert)
  Legen Sie mithilfe der Seite **Erweitert** im Dialogfeld **Verbindungs-Manager-Editor für mehrere Flatfiles** Eigenschaften wie den Datentyp und Trennzeichen für jede einzelne Spalte in den Textdateien fest, mit denen der Verbindungs-Manager für Flatfiles eine Verbindung herstellt.  
  
 Standardmäßig beträgt die Länge von Zeichenfolgenspalten 50 Zeichen. Sie können Beispieldaten auswerten und die Länge dieser Spalten automatisch ändern, um zu verhindern, dass Daten abgeschnitten werden oder extrem breite Spalten entstehen. Sie können darüber hinaus andere Metadaten aktualisieren, um Kompatibitlität mit Zielspalten zu aktivieren. Sie können beispielsweise den Datentyp einer Spalte, die nur ganzzahlige Daten enthält, in einen numerischen Datentyp ändern, z. B. DT_I2.  
  
 Weitere Informationen zum Verbindungs-Manager für mehrere Flatfiles finden Sie unter [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).  
  
## <a name="options"></a>Tastatur  
 **Name des Verbindungs-Managers**  
 Geben Sie einen eindeutigen Namen für den Verbindungs-Manager für mehrere Flatfiles im Workflow an. Der eingegebene Name wird im Bereich **Verbindungs-Manager** des [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designers angezeigt.  
  
 **Beschreibung**  
 Beschreiben Sie den Verbindungs-Manager. Die bewährte Methode ist hierbei, den Verbindungs-Manager zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und leichter zu verwalten sind.  
  
 **Konfigurieren Sie die Eigenschaften der einzelnen Spalten.**  
 Wählen Sie eine Spalte im linken Bereich, um im rechten Bereich ihre Eigenschaften anzuzeigen. In der folgenden Tabelle werden die Datentypeigenschaften beschrieben. Einige der aufgeführten Eigenschaften können nur für einige Flatfileformate konfiguriert werden.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|**ColumnType**|Gibt an, ob eine Spalte getrennt ist, eine feste Breite hat bzw. einen unregelmäßigen rechten Rand aufweist. Diese Eigenschaft ist schreibgeschützt. Bei Dateien mit rechtem Flatterrand weisen alle Spalten mit Ausnahme der letzten eine feste Breite auf. Die letzte Spalte wird durch das Zeilentrennzeichen abgeschlossen.|  
|**OutputColumnWidth**|Gibt an, welcher Wert als Anzahl von Bytes gespeichert werden soll; bei Unicode-Dateien wird dieser Wert als Zeichenanzahl angezeigt. Im Datenflusstask dient dieser Wert dem Festlegen der Breite der Ausgabespalte für die Flatfilequelle.<br /><br /> Hinweis: Im Objektmodell heißt diese Eigenschaft MaximumWidth.|  
|**DataType**|Wählen Sie eine Option aus der Liste der verfügbaren Datentypen aus. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).|  
|**Textqualified**|Gibt an, ob Textdaten mit einem Textqualifiziererzeichen gekennzeichnet werden. Gültige Werte sind:<br /><br /> **True**: die Textdaten in der Flatfile sind qualifiziert.<br /><br /> **False**: die Textdaten in der Flatfile sind nicht qualifiziert.|  
|**Name**|Geben Sie einen Spaltennamen an. Standardwert ist eine nummerierte Liste mit Spalten; Sie können jedoch einen eindeutigen, beschreibenden Namen auswählen.|  
|**Datascale**|Gibt die Skala numerischer Daten an. Skala heißt in diesem Fall die Anzahl der Dezimalstellen. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).|  
|**ColumnDelimiter**|Wählen Sie eine Option aus der Liste der verfügbaren Spaltentrennzeichen aus. Dabei sollten Sie Spaltentrennzeichen auswählen, deren Auftreten als Zeichen im Text unwahrscheinlich ist. Bei Spalten fester Breite wird dieser Wert ignoriert.<br /><br /> **{CR} {LF}** -als Trennzeichen für Spalten dient eine Kombination aus Wagen Rücklauf/Zeilenvorschub<br /><br /> **{CR}** -als Trennzeichen für Spalten dient ein Wagen Rücklauf.<br /><br /> **{LF}** -als Trennzeichen für Spalten dient ein Zeilenvorschub.<br /><br /> **Semikolon {;}** -als Trennzeichen für Spalten dient ein Semikolon.<br /><br /> **Doppelpunkt {:}** -als Trennzeichen für Spalten dient ein Doppelpunkt.<br /><br /> **Komma {,} ** -als Trennzeichen für Spalten dient ein Komma.<br /><br /> **Tabulator {t}** -als Trennzeichen für Spalten dient ein Tabulator.<br /><br /> **Vertikaler Strich {&#124;}** -als Trennzeichen für Spalten dient ein senkrechter Strich.|  
|**Datapresion**|Gibt die Präzision numerischer Daten an. Präzision heißt in diesem Fall die Anzahl der Stellen. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).|  
|**Inputcolumnwidth**|Gibt an, welcher Wert als Anzahl von Bytes gespeichert werden soll; bei Unicode-Dateien wird dieser Wert als Zeichenanzahl angezeigt. Bei mit Trennzeichen versehenen Spalten wird dieser Wert ignoriert.<br /><br /> **Hinweis** Im-Objektmodell lautet der Name dieser Eigenschaft ColumnWidth.|  
  
 **Neu**  
 Durch Klicken auf **Neu**fügen Sie eine neue Spalte hinzu. Die neue Spalten wird beim Klicken auf **Neu** standardmäßig am Ende der Liste hinzugefügt. Ferner sind für die Schaltfläche folgende, über die Dropdownliste auswählbare Optionen verfügbar.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Spalte hinzufügen**|Fügt am Ende der Liste eine neue Spalte hinzu.|  
|**Einfügen vor**|Fügt vor der ausgewählten Spalte eine neue Spalte ein.|  
|**Einfügen nach**|Fügt nach der ausgewählten Spalte eine neue Spalte ein.|  
  
 **Löschen**  
 Wählen Sie eine Spalte aus, und entfernen Sie sie dann, indem Sie auf **Löschen**klicken.  
  
 **Typen vorschlagen**  
 Im Dialogfeld **Spaltentypen vorschlagen** können Sie die Beispieldaten in der ersten ausgewählten Datei auswerten, um Vorschläge für den Datentyp und die -länge der einzelnen Spalten zu erhalten. Weitere Informationen finden Sie unter [Referenz zur Benutzeroberfläche des Dialogfelds „Spaltentypen vorschlagen“](connection-manager/suggest-column-types-dialog-box-ui-reference.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite Spalten&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)   
 [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Vorschau Seite&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
