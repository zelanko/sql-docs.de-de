---
title: Verbindungs-Manager-Editor für Flatfiles (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.general.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 77296024-5c1a-4f6a-9665-0b50d45d744c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b378d7257ddd57e97407d82feb817aa70965f598
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058753"
---
# <a name="flat-file-connection-manager-editor-general-page"></a>Verbindungs-Manager-Editor für Flatfiles (Seite Allgemein)
  Auf der Seite **Allgemein** des Dialogfelds **Verbindungs-Manager-Editor für Flatfiles** wählen Sie eine Datei und ein Dateiformat aus. Eine Flatfileverbindung ermöglicht das Herstellen einer Verbindung von einem Paket zu einer Textdatei.  
  
 Weitere Informationen zum Verbindungs-Manager für Flatfiles finden Sie unter [Flat File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="options"></a>Tastatur  
 **Name des Verbindungs-Managers**  
 Geben Sie einen eindeutigen Namen für die Flatfileverbindung im Workflow an. Der angegebene Name wird im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer angezeigt.  
  
 **Beschreibung**  
 Beschreiben Sie die Verbindung. Die bewährte Methode ist hierbei, die Verbindung zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und leichter zu verwalten sind.  
  
 **Dateiname**  
 Geben Sie den Pfad und den Dateinamen ein, die für die Flatfileverbindung verwendet werden sollen.  
  
 **Durchsuchen**  
 Suchen Sie den Dateinamen, der für die Flatfileverbindung verwendet werden soll.  
  
 **Gebietsschema**  
 Gibt das Gebietsschema für die Bereitstellung sprachspezifischer Informationen für das Bestellen sowie für Datums- und Zeitformate an.  
  
 **Unicode-**  
 Gibt an, ob Unicode verwendet werden soll. Wenn Sie Unicode verwenden, können Sie keine Codepage angeben.  
  
 **Codepage**  
 Gibt die Codepage für Nicht-Unicode-Text an.  
  
 **Ges**  
 Gibt an, ob die Datei Formatierung mit Trennzeichen, fester Breite oder rechtem Flatterrand verwendet.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|Durch Trennzeichen getrennt|Die Trennung von Spalten erfolgt durch Trennzeichen. Welche Trennzeichen dies sind, wird auf der Seite **Spalten** angegeben.|  
|Feste Breite|Spalten haben eine feste Breite.|  
|Rechter Flatterrand|Bei Dateien mit rechtem Flatterrand haben die Spalten mit Ausnahme der letzten Spalte eine feste Breite. Die Trennung der letzten Spalte erfolgt mit einem Zeilentrennzeichen.|  
  
 **Textqualifizierer**  
 Gibt die zu verwendenden Textqualifizierer an. So können Sie beispielsweise angeben, dass Textfelder in Anführungszeichen eingeschlossen sind.  
  
> [!NOTE]  
>  Nachdem Sie einen Textqualifizierer ausgewählt haben, können Sie die Option **Keine** nicht erneut auswählen. Geben Sie **Keine** ein, um die Auswahl des Textqualifizierers aufzuheben.  
  
 **Header Zeilen Trennzeichen**  
 Wählen Sie aus einer Liste mit Trennzeichen für Kopfzeilen ein Trennzeichen aus, oder geben Sie den Trennzeichentext ein.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Programmiert Verlangt**|Als Trennzeichen für Kopfzeilen dient ein Wagenrücklauf in Kombination mit einem Zeilenvorschub.|  
|**Programmiert**|Als Trennzeichen für Kopfzeilen dient ein Wagenrücklauf.|  
|**Verlangt**|Als Trennzeichen für Kopfzeilen dient ein Zeilenvorschub.|  
|**Semikolon {;}**|Als Trennzeichen für Kopfzeilen dient ein Semikolon.|  
|**Doppelpunkt {:}**|Als Trennzeichen für Kopfzeilen dient ein Doppelpunkt.|  
|**Komma{,}**|Als Trennzeichen für Kopfzeilen dient ein Komma.|  
|**Tab {t}**|Als Trennzeichen für Kopfzeilen dient ein Tabulator.|  
|**Senkrechter Strich {&#124;}**|Als Trennzeichen für Kopfzeilen dient ein senkrechter Strich.|  
  
 **Zu über springende Header Zeilen**  
 Gibt an, wie viele Kopfzeilen bzw. erste Datenzeilen ggf. ausgelassen werden sollen.  
  
 **Spaltennamen in der ersten Daten Zeile**  
 Gibt an, ob in der ersten Datenzeile Spaltennamen erwartet werden bzw. bereitzustellen sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Spalten&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)   
 [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Erweiterte Seite&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)   
 [Verbindungs-Manager-Editor für Flatfiles &#40;Vorschau Seite&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
