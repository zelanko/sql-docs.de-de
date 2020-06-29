---
title: Verbindungs-Manager-Editor für mehrere Flatfiles (Seite Spalten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.columns.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: ad0cb668-0df2-4d4e-9a20-d20692a0b67a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 207c6e9837f2a828316c91c642d7397b72c4ddc3
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440167"
---
# <a name="multiple-flat-files-connection-manager-editor-columns-page"></a>Verbindungs-Manager-Editor für mehrere Flatfiles (Seite Spalten)
  Verwenden Sie den Knoten **Spalten** im Dialogfeld **Verbindungs-Manager-Editor für mehrere Flatfiles** , um die Zeilen- und Spalteninformationen anzugeben und eine Vorschau der ersten ausgewählten Datei anzuzeigen.  
  
 Weitere Informationen zum Verbindungs-Manager für mehrere Flatfiles finden Sie unter [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Name des Verbindungs-Managers**  
 Geben Sie einen eindeutigen Namen für die Verbindung für mehrere Flatfiles im Workflow an. Der angegebene Name wird im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer angezeigt.  
  
 **Beschreibung**  
 Beschreiben Sie die Verbindung. Es ist eine bewährte Methode, die Verbindung zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und einfacher zu verwalten sind.  
  
## <a name="flat-file-format-dynamic-options"></a>Flatfileformat (dynamische Optionen)  
  
### <a name="format--delimited"></a>Format = Mit Trennzeichen  
 **Zeilentrennzeichen**  
 Wählen Sie aus der Liste verfügbarer Zeilentrennzeichen ein Trennzeichen aus, oder geben Sie den Trennzeichentext ein.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**{CR}{LF}**|Als Trennzeichen für Zeilen dient ein Wagenrücklauf in Kombination mit einem Zeilenvorschub.|  
|**Programmiert**|Als Trennzeichen für Zeilen dient ein Wagenrücklauf.|  
|**{LF}**|Als Trennzeichen für Zeilen dient ein Zeilenvorschub.|  
|**Semikolon {;}**|Als Trennzeichen für Zeilen dient ein Semikolon.|  
|**Doppelpunkt {:}**|Als Trennzeichen für Zeilen dient ein Doppelpunkt.|  
|**Komma{,}**|Als Trennzeichen für Zeilen dient ein Komma.|  
|**Tabulator {t}**|Als Trennzeichen für Zeilen dient ein Tabulator.|  
|**Senkrechter Strich {&#124;}**|Als Trennzeichen für Zeilen dient ein senkrechter Strich.|  
  
 **Spaltentrennzeichen**  
 Wählen Sie aus der Liste verfügbarer Spaltentrennzeichen ein Trennzeichen aus, oder geben Sie den Trennzeichentext ein.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**{CR}{LF}**|Als Trennzeichen für Spalten dient ein Wagenrücklauf in Kombination mit einem Zeilenvorschub.|  
|**Programmiert**|Als Trennzeichen für Spalten dient ein Wagenrücklauf.|  
|**{LF}**|Als Trennzeichen für Spalten dient ein Zeilenvorschub.|  
|**Semikolon {;}**|Als Trennzeichen für Spalten dient ein Semikolon.|  
|**Doppelpunkt {:}**|Als Trennzeichen für Spalten dient ein Doppelpunkt.|  
|**Komma{,}**|Als Trennzeichen für Spalten dient ein Komma.|  
|**Tabulator {t}**|Als Trennzeichen für Spalten dient ein Tabulator.|  
|**Senkrechter Strich {&#124;}**|Als Trennzeichen für Spalten dient ein senkrechter Strich.|  
  
 **Spalten zurücksetzen**  
 Entfernt alle bis auf die ursprünglichen Spalten, wenn Sie auf **Spalten zurücksetzen**klicken.  
  
### <a name="format--fixed-width"></a>Format = Feste Breite  
 **Schriftart**  
 Wählen Sie die Schriftart aus, in der die Vorschaudaten angezeigt werden sollen.  
  
 **Quelldatenspalten**  
 Passen Sie die Zeilenbreite an, indem Sie die vertikale Zeilenmarkierungslinie verschieben, und passen Sie die Spaltenbreite an, indem Sie auf das Lineal am oberen Rand des Vorschaufensters klicken.  
  
 **Zeilenbreite**  
 Geben Sie erst die Länge der Zeile an, bevor Sie einzelnen Spalten Trennzeichen hinzufügen. Sie können auch die vertikale Linie im Vorschaufenster verschieben, um das Zeilenende zu kennzeichnen. Der Wert der Zeilenbreite wird automatisch aktualisiert.  
  
 **Spalten zurücksetzen**  
 Entfernt alle bis auf die ursprünglichen Spalten, wenn Sie auf **Spalten zurücksetzen**klicken.  
  
### <a name="format--ragged-right"></a>Format = Rechter Flatterrand  
  
> [!NOTE]  
>  Bei Dateien mit rechtem Flatterrand haben die Spalten mit Ausnahme der letzten Spalte eine feste Breite. Die Trennung der letzten Spalte erfolgt mit einem Zeilentrennzeichen.  
  
 **Schriftart**  
 Wählen Sie die Schriftart aus, in der die Vorschaudaten angezeigt werden sollen.  
  
 **Quelldatenspalten**  
 Passen Sie die Zeilenbreite an, indem Sie die vertikale Zeilenmarkierungslinie verschieben, und passen Sie die Spaltenbreite an, indem Sie auf das Lineal am oberen Rand des Vorschaufensters klicken.  
  
 **Zeilentrennzeichen**  
 Wählen Sie aus der Liste verfügbarer Zeilentrennzeichen ein Trennzeichen aus, oder geben Sie den Trennzeichentext ein.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**{CR}{LF}**|Als Trennzeichen für Zeilen dient ein Wagenrücklauf in Kombination mit einem Zeilenvorschub.|  
|**Programmiert**|Als Trennzeichen für Zeilen dient ein Wagenrücklauf.|  
|**{LF}**|Als Trennzeichen für Zeilen dient ein Zeilenvorschub.|  
|**Semikolon {;}**|Als Trennzeichen für Zeilen dient ein Semikolon.|  
|**Doppelpunkt {:}**|Als Trennzeichen für Zeilen dient ein Doppelpunkt.|  
|**Komma{,}**|Als Trennzeichen für Zeilen dient ein Komma.|  
|**Tabulator {t}**|Als Trennzeichen für Zeilen dient ein Tabulator.|  
|**Senkrechter Strich {&#124;}**|Als Trennzeichen für Zeilen dient ein senkrechter Strich.|  
  
 **Spalten zurücksetzen**  
 Entfernt alle bis auf die ursprünglichen Spalten, wenn Sie auf **Spalten zurücksetzen**klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite "Erweitert"&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)   
 [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Vorschau“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
