---
title: DMX-Abfrage-Editor (Analysis Services – Datamining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.startpage.dmx.f1
ms.assetid: 7ac877a1-0f29-46b9-9a51-73b02172bef1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 063e78a15a4bd365c4eb061cc54454fb6e6637c9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153240"
---
# <a name="dmx-query-editor-analysis-services---data-mining"></a>DMX-Abfrage-Editor (Analysis Services &ndash; Data Mining)
  Mithilfe des DMX-Abfrage-Editors können Sie in der DMX-Sprache (Data Mining Extensions) geschriebene Anweisungen entwerfen und ausführen.  
  
## <a name="features"></a>Funktionen  
  
-   Im Abfrage-Editorfenster des DMX-Abfrage-Editors können Sie Skripts eingeben.  
  
-   Um Skripts auszuführen, müssen Sie entweder **F5**drücken oder auf der Symbolleiste oder im Menü **Abfrage** auf **Ausführen** klicken. Wenn ein Teil des Codes ausgewählt ist, wird nur dieser Teil ausgeführt. Ist kein Code ausgewählt, wird der gesamte Inhalt des DMX-Abfrage-Editors ausgeführt.  
  
-   Im Metadatenbereich können Sie Metadaten für Cubes und andere Objekte einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank anzeigen.  
  
-   Um Hilfe zur DMX-Syntax zu erhalten, wählen Sie im DMX-Abfrage-Editor ein Schlüsselwort aus, und drücken Sie dann **F1**.  
  
-   Dynamische Hilfe zur DMX-Syntax erhalten Sie, indem Sie im Menü **Hilfe** auf **Dynamische Hilfe** klicken, um die Komponente „Dynamische Hilfe“ zu öffnen. Bei der dynamischen Hilfe werden die Hilfethemen im Fenster **Dynamische Hilfe** angezeigt, sobald Schlüsselwörter im Abfrage-Editor eingegeben werden.  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>SQL Server Analysis Services-Editoren (Symbolleiste)  
 Wenn der DMX-Abfrage-Editor geöffnet ist, wird die Symbolleiste **SQL Server Analysis Services-Editoren** mit den in der folgenden Tabelle aufgeführten Schaltflächen angezeigt.  
  
|Begriff|Definition|  
|----------|----------------|  
|**Verbinden**|Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem eine Verbindung mit einer Instanz von Analysis Service hergestellt werden kann.|  
|**Trennen**|Trennt die Verbindung zwischen dem DMX-Abfrage-Editor und einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|**Verbindung ändern**|Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem eine Verbindung mit einer anderen Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt werden kann.|  
|**Neue Abfrage mit aktueller Verbindung**|Öffnet ein neues DMX-Abfrage-Editorfenster mithilfe der Verbindungsinformationen des aktuellen DMX-Abfrage-Editorfensters.|  
|**Verfügbare Datenbanken**|Ändert die Verbindung zu einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank innerhalb derselben Instanz.|  
|**Ausführen**|Führt den ausgewählten Code aus. Wenn kein Code ausgewählt ist, wird mit dieser Option der gesamte Code im DMX-Abfrage-Editor ausgeführt.|  
|**Analysieren**|Überprüft die Syntax des ausgewählten Codes. Wenn kein Code ausgewählt ist, wird mit dieser Option die Syntax des gesamten DMX-Abfrage-Editorfensters geprüft.|  
|**Ausführung der Abfrage abbrechen**|Sendet eine Abbruchsanforderung an den Server. Einige Abfragen können nicht sofort abgebrochen werden, sondern müssen auf angemessene Bedingungen für einen Abbruch warten. Bei einem Abbruch können Verzögerungen auftreten, während für die Transaktionen ein Rollback ausgeführt wird.|  
  
## <a name="dmx-query-editor-window"></a>DMX-Abfrage-Editorfenster  
 Im DMX-Abfrage-Editor stehen die in der folgenden Tabelle aufgelisteten Optionen zur Verfügung.  
  
|Begriff|Definition|  
|----------|----------------|  
|**Abfrage-Editor-Fenster**|Hier können Sie DMX-Anweisungen und -Skripts eingeben, die vom DMX-Abfrage-Editor ausgeführt werden sollen.<br /><br /> Das Kontextmenü des Abfrage-Editorfensters enthält die folgenden Optionen:<br /><br /> **Ausschneiden**: kopiert die aktuelle Auswahl in die Zwischenablage und entfernt Sie aus dem Abfrage-Editorfenster.<br /><br /> **Kopieren:** Kopiert die aktuelle Auswahl in die Zwischenablage.<br /><br /> **Fügen Sie**: Fügt den Inhalt der Zwischenablage in die aktuelle Auswahl.<br /><br /> **Verbinden:** Öffnet das Dialogfeld **Verbindung mit Server herstellen**, in dem eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt werden kann.<br /><br /> **Trennen Sie**: trennt die Verbindung der aktuellen Abfrage-Editor aus einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz.<br /><br /> **Alle Abfragen trennen**: trennt die Verbindung aller geöffneten Abfrage-Editoren.<br /><br /> **Verbindung ändern**: Öffnet die **Herstellen einer Verbindung mit Server** im Dialogfeld zum Herstellen einer Verbindung zu einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz.<br /><br /> **Öffnen Sie im Objekt-Explorer den Server**: Öffnet die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz, die mit der aktuellen Abfrage-Editor, in verbunden ist **Objekt-Explorer**.<br /><br /> **Führen Sie**: führt den ausgewählten Code aus, oder wenn kein Code ausgewählt ist, der gesamte Code in der aktuellen Abfrage-Editor ausgeführt.<br /><br /> **Fenster "Eigenschaften"**: Zeigt die **Eigenschaften** -Fensters im [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] für das aktuelle Abfragefenster.<br /><br /> **Abfrageoptionen**: Zeigt die **Abfrageoptionen** Dialogfeld.|  
|**Fenster Metadaten**|Zeigt Metadaten für die aktuell verbundene [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank an.|  
|**Cube**|Wählen Sie einen Cube in der aktuell verbundenen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank aus, um die zugehörigen Metadaten des Cubes auf der Registerkarte **Metadaten** anzuzeigen.|  
|**Metadaten**|Zeigt die Metadaten für den unter **Cube**ausgewählten Cube an, einschließlich Measuregruppen und Measures, Key Performance Indicators, Dimensionen, Hierarchien, Ebenen, Elementen und Elementeigenschaften. Zum Abrufen des voll gekennzeichneten Schlüssels eines Objekts führen Sie einen der beiden folgenden Schritte aus:<br /><br /> Ziehen Sie das Objekt von der Registerkarte **Metadaten** in das Abfragefenster.<br /><br /> Oder:<br /><br /> Klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie **Kopieren**aus. Klicken Sie anschließend mit der rechten Maustaste in das Abfragefenster, und wählen Sie **Einfügen**aus.|  
|**Funktionen**|Zeigt die Metadaten für DMX-Funktionen an, die für die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank so verfügbar sind, wie sie aus DMSCHEMA_MINING_FUNCTIONS-Schemarowset abgerufen wurden.<br /><br /> Zum Abrufen der Syntax einer Funktion führen Sie einen der beiden folgenden Schritte aus:<br /><br /> Ziehen Sie das Objekt von der Registerkarte **Funktionen** in das Abfragefenster.<br /><br /> Oder:<br /><br /> Klicken Sie mit der rechten Maustaste auf die Funktion, und wählen Sie **Kopieren**aus. Klicken Sie anschließend mit der rechten Maustaste in das Abfragefenster, und wählen Sie **Einfügen**aus.|  
|**Fenster "Ergebnisse"**|Zeigt die Ergebnisse einer DMX-Anweisung in einem Raster an.|  
|**Meldungsfenster**|Zeigt Informationen zur Art der Ausführung einer DMX-Anweisung an. In diesem Fenster werden beispielsweise während der Ausführung alle auftretenden Fehler bzw. wird nach der Ausführung die Anzahl der abgerufenen Zellen angezeigt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Verweis](/sql/dmx/data-mining-extensions-dmx-reference)   
 [MDX-Abfrage-Editor &#40;Analysis Services – mehrdimensionale Daten&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [XMLA-Abfrage-Editor &#40;Analysis Services – mehrdimensionale Daten&#41;](xmla-query-editor-analysis-services-multidimensional-data.md)   
 [Abfrage- und Text-Editoren &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [Tastenkombinationen für SQL Server Management Studio](../ssms/sql-server-management-studio-keyboard-shortcuts.md)   
 [Anpassen von Menüs und Tastenkombinationen](../ssms/customize-menus-and-shortcut-keys.md)   
 [Farbcodierung im Abfrage-Editor](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  
