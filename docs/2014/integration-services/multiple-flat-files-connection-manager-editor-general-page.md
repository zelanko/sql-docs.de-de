---
title: Verbindungs-Manager-Editor (Seite Allgemein) für mehrere Flatfiles | Microsoft Docs
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
- sql12.dts.designer.multifile.general.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: 00129d43-2772-413b-bdf8-ac5de81cf4a5
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 200a1ea8334c1347597f2364e624881c74a0e499
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058087"
---
# <a name="multiple-flat-files-connection-manager-editor-general-page"></a>Verbindungs-Manager-Editor für mehrere Flatfiles (Seite Allgemein)
  Um eine Gruppe von Dateien im selben Datenformat auszuwählen und das entsprechende Datenformat anzugeben, verwenden Sie im Dialogfeld **Verbindungs-Manager-Editor für mehrere Flatfiles** die Seite **Allgemein** . Durch eine Verbindung für mehrere Flatfiles kann von einem Paket eine Verbindung zu einer Gruppe von Textdateien im selben Format hergestellt werden.  
  
 Weitere Informationen zum Verbindungs-Manager für mehrere Flatfiles finden Sie unter [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).  
  
## <a name="options"></a>Tastatur  
 **Name des Verbindungs-Managers**  
 Geben Sie einen eindeutigen Namen für die Verbindung für mehrere Flatfiles im Workflow an. Der angegebene Name wird im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer angezeigt.  
  
 **Beschreibung**  
 Beschreiben Sie die Verbindung. Die bewährte Methode ist hierbei, die Verbindung zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und leichter zu verwalten sind.  
  
 **Dateinamen**  
 Geben Sie den Pfad und den Dateinamen ein, die für die Verbindung für mehrere Flatfiles verwendet werden sollen. Verwenden Sie zum Angeben mehrerer Dateien Platzhalterzeichen, wie in „C:\\\*.txt“, oder verwenden Sie den senkrechten Strich (|), um die verschiedenen angegebenen Dateinamen voneinander zu trennen. Alle Dateien müssen dasselbe Datenformat aufweisen.  
  
 **Durchsuchen**  
 Wechseln Sie in das Verzeichnis mit den Dateinamen, die bei der Verbindung für mehrere Flatfiles verwendet werden sollen. Sie können mehrere Dateien auswählen. Alle Dateien müssen dasselbe Datenformat aufweisen.  
  
 **Gebietsschema**  
 Geben Sie den Ort an, um Informationen zu Bestellungen und zur Datums- und Zeitkonvertierung bereitzustellen.  
  
 **Unicode**  
 Gibt an, ob Unicode verwendet werden soll. Bei Verwendung von Unicode wird keine Codepage angegeben.  
  
 **Codepage**  
 Gibt die Codepage für Nicht-Unicode-Text an.  
  
 **Format**  
 Gibt an, ob die Datei Formatierung mit Trennzeichen, fester Breite oder rechtem Flatterrand verwendet. Alle Dateien müssen dasselbe Datenformat aufweisen.  
  
|value|Description|  
|-----------|-----------------|  
|Mit Trennzeichen|Die Trennung von Spalten erfolgt durch Trennzeichen. Welche Trennzeichen dies sind, wird auf der Seite **Spalten** angegeben.|  
|Feste Breite|Die Spalten weisen eine feste Breite auf, die auf der Seite **Spalten** durch Ziehen der Markierungslinien angegeben wird.|  
|Rechter Flatterrand|Bei Dateien mit rechtem Flatterrand weisen alle Spalten mit Ausnahme der letzten eine feste Breite auf. Die letzte Spalte wird durch das auf der Seite **Spalten** angegebene Zeilentrennzeichen begrenzt.|  
  
 **Textqualifizierer**  
 Gibt die zu verwendenden Textqualifizierer an. Sie können beispielsweise angeben, dass Text in Anführungszeichen eingeschlossen werden soll.  
  
 **Kopfzeilentrennzeichen**  
 Wählen Sie aus einer Liste mit Trennzeichen für Kopfzeilen ein Trennzeichen aus, oder geben Sie den Trennzeichentext ein.  
  
|value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Als Trennzeichen für Kopfzeilen dient ein Wagenrücklauf in Kombination mit einem Zeilenvorschub.|  
|**{CR}**|Als Trennzeichen für Kopfzeilen dient ein Wagenrücklauf.|  
|**{LF}**|Als Trennzeichen für Kopfzeilen dient ein Zeilenvorschub.|  
|**Semikolon {;}**|Als Trennzeichen für Kopfzeilen dient ein Semikolon.|  
|**Doppelpunkt {:}**|Als Trennzeichen für Kopfzeilen dient ein Doppelpunkt.|  
|**Komma {,}**|Als Trennzeichen für Kopfzeilen dient ein Komma.|  
|**Tabulator {t}**|Als Trennzeichen für Kopfzeilen dient ein Tabulator.|  
|**Senkrechter Strich {&#124;}**|Als Trennzeichen für Kopfzeilen dient ein senkrechter Strich.|  
  
 **Auszulassende Kopfzeilen**  
 Geben Sie nach Möglichkeit die Anzahl der auszulassenden Kopfzeilen an.  
  
 **Spaltennamen in der ersten Datenzeile**  
 Gibt an, ob in der ersten Datenzeile Spaltennamen erwartet werden bzw. bereitzustellen sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite "Spalten"&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)   
 [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite "Erweitert"&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)   
 [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite in der Vorschau anzeigen&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  