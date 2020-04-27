---
title: DMX-Abfrage-Editor (Analysis Services-Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.startpage.dmx.f1
ms.assetid: 7ac877a1-0f29-46b9-9a51-73b02172bef1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3be28b0a402743e4d9c26b346386202127c5f74d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081566"
---
# <a name="dmx-query-editor-analysis-services---data-mining"></a>DMX-Abfrage-Editor (Analysis Services &ndash; Data Mining)
  Mithilfe des DMX-Abfrage-Editors können Sie in der DMX-Sprache (Data Mining Extensions) geschriebene Anweisungen entwerfen und ausführen.  
  
## <a name="features"></a>Features  
  
-   Im Abfrage-Editorfenster des DMX-Abfrage-Editors können Sie Skripts eingeben.  
  
-   Um Skripts auszuführen, müssen Sie entweder **F5**drücken oder auf der Symbolleiste oder im Menü **Abfrage** auf **Ausführen** klicken. Wenn ein Teil des Codes ausgewählt ist, wird nur dieser Teil ausgeführt. Ist kein Code ausgewählt, wird der gesamte Inhalt des DMX-Abfrage-Editors ausgeführt.  
  
-   Im Metadatenbereich können Sie Metadaten für Cubes und andere Objekte einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank anzeigen.  
  
-   Um Hilfe zur DMX-Syntax zu erhalten, wählen Sie im DMX-Abfrage-Editor ein Schlüsselwort aus, und drücken Sie dann **F1**.  
  
-   Dynamische Hilfe zur DMX-Syntax erhalten Sie, indem Sie im Menü **Hilfe** auf **Dynamische Hilfe** klicken, um die Komponente „Dynamische Hilfe“ zu öffnen. Bei der dynamischen Hilfe werden die Hilfethemen im Fenster **Dynamische Hilfe** angezeigt, sobald Schlüsselwörter im Abfrage-Editor eingegeben werden.  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>SQL Server Analysis Services-Editoren (Symbolleiste)  
 Wenn der DMX-Abfrage-Editor geöffnet ist, wird die Symbolleiste **SQL Server Analysis Services-Editoren** mit den in der folgenden Tabelle aufgeführten Schaltflächen angezeigt.  
  
|Begriff|Definition|  
|----------|----------------|  
|**Herstellen einer Verbindung**|Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem eine Verbindung mit einer Instanz von Analysis Service hergestellt werden kann.|  
|**Verschluss**|Trennt die Verbindung zwischen dem DMX-Abfrage-Editor und einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Verbindung ändern**|Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem eine Verbindung mit einer anderen Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt werden kann.|  
|**Neue Abfrage mit aktueller Verbindung**|Öffnet ein neues DMX-Abfrage-Editorfenster mithilfe der Verbindungsinformationen des aktuellen DMX-Abfrage-Editorfensters.|  
|**Verfügbare Datenbanken**|Ändert die Verbindung zu einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank innerhalb derselben Instanz.|  
|**Auszuführen**|Führt den ausgewählten Code aus. Wenn kein Code ausgewählt ist, wird mit dieser Option der gesamte Code im DMX-Abfrage-Editor ausgeführt.|  
|**Parse**|Überprüft die Syntax des ausgewählten Codes. Wenn kein Code ausgewählt ist, wird mit dieser Option die Syntax des gesamten DMX-Abfrage-Editorfensters geprüft.|  
|**Ausführung der Abfrage abbrechen**|Sendet eine Abbruchsanforderung an den Server. Einige Abfragen können nicht sofort abgebrochen werden, sondern müssen auf angemessene Bedingungen für einen Abbruch warten. Bei einem Abbruch können Verzögerungen auftreten, während für die Transaktionen ein Rollback ausgeführt wird.|  
  
## <a name="dmx-query-editor-window"></a>DMX-Abfrage-Editorfenster  
 Im DMX-Abfrage-Editor stehen die in der folgenden Tabelle aufgelisteten Optionen zur Verfügung.  
  
|Begriff|Definition|  
|----------|----------------|  
|**Abfrage-Editorfenster**|Hier können Sie DMX-Anweisungen und -Skripts eingeben, die vom DMX-Abfrage-Editor ausgeführt werden sollen.<br /><br /> Das Kontextmenü des Abfrage-Editorfensters enthält die folgenden Optionen:<br /><br /> **Ausschneiden**: kopiert die aktuelle Auswahl in die Zwischenablage und entfernt die Auswahl aus dem Abfrage-Editor-Fenster.<br /><br /> **Kopieren:** Kopiert die aktuelle Auswahl in die Zwischenablage.<br /><br /> **Einfügen**: Fügt den Inhalt der Zwischenablage in die aktuelle Auswahl ein.<br /><br /> **Verbinden:** Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt werden kann.<br /><br /> **Trennen**: trennt die Verbindung zwischen dem aktuellen Abfrage- [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Editor und einer Instanz von.<br /><br /> **Alle Abfragen trennen**: trennt alle geöffneten Abfrage-Editoren.<br /><br /> **Verbindung ändern**: öffnet das Dialogfeld Verbindung **mit Server herstellen** , um eine Verbindung mit einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz herzustellen.<br /><br /> **Server in Objekt-Explorer öffnen**: öffnet die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz, mit der der aktuelle Abfrage-Editor in **Objekt-Explorer**verbunden ist.<br /><br /> **Execute**: führt den ausgewählten Code aus. Wenn kein Code ausgewählt ist, wird der gesamte Code im aktuellen Abfrage-Editor ausgeführt.<br /><br /> **Eigenschaften Fenster**: zeigt das Fenster **Eigenschaften** für [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] das aktuelle Abfragefenster an.<br /><br /> **Abfrage Optionen**: zeigt das Dialogfeld **Abfrage Optionen** an.|  
|**Fenster Metadaten**|Zeigt Metadaten für die aktuell verbundene [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank an.|  
|**Cube**|Wählen Sie einen Cube in der aktuell verbundenen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank aus, um die zugehörigen Metadaten des Cubes auf der Registerkarte **Metadaten** anzuzeigen.|  
|**Metadaten**|Zeigt die Metadaten für den unter **Cube**ausgewählten Cube an, einschließlich Measuregruppen und Measures, Key Performance Indicators, Dimensionen, Hierarchien, Ebenen, Elementen und Elementeigenschaften. Zum Abrufen des voll gekennzeichneten Schlüssels eines Objekts führen Sie einen der beiden folgenden Schritte aus:<br /><br /> Ziehen Sie das Objekt von der Registerkarte **Metadaten** in das Abfragefenster.<br /><br /> Oder:<br /><br /> Klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie **Kopieren**aus. Klicken Sie anschließend mit der rechten Maustaste in das Abfragefenster, und wählen Sie **Einfügen**aus.|  
|**Functions**|Zeigt die Metadaten für DMX-Funktionen an, die für die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank so verfügbar sind, wie sie aus DMSCHEMA_MINING_FUNCTIONS-Schemarowset abgerufen wurden.<br /><br /> Zum Abrufen der Syntax einer Funktion führen Sie einen der beiden folgenden Schritte aus:<br /><br /> Ziehen Sie das Objekt von der Registerkarte **Funktionen** in das Abfragefenster.<br /><br /> Oder:<br /><br /> Klicken Sie mit der rechten Maustaste auf die Funktion, und wählen Sie **Kopieren**aus. Klicken Sie anschließend mit der rechten Maustaste in das Abfragefenster, und wählen Sie **Einfügen**aus.|  
|**Ergebnisfenster**|Zeigt die Ergebnisse einer DMX-Anweisung in einem Raster an.|  
|**Meldungsfenster**|Zeigt Informationen zur Art der Ausführung einer DMX-Anweisung an. In diesem Fenster werden beispielsweise während der Ausführung alle auftretenden Fehler bzw. wird nach der Ausführung die Anzahl der abgerufenen Zellen angezeigt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](/sql/dmx/data-mining-extensions-dmx-reference)   
 [MDX-Abfrage-Editor &#40;Analysis Services Mehrdimensionale Daten&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [Der XMLA-Abfrage-Editor &#40;Analysis Services Mehrdimensionale Daten&#41;](xmla-query-editor-analysis-services-multidimensional-data.md)   
 [Abfrage-und Text-Editoren &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [SQL Server Management Studio Tastenkombinationen](../ssms/sql-server-management-studio-keyboard-shortcuts.md)   
 [Anpassen von Menüs und Tastenkombinationen](../ssms/customize-menus-and-shortcut-keys.md)   
 [Farbcodierung im Abfrage-Editor](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  
