---
title: XMLA-Abfrage-Editor (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.editor.xmla.f1
helpviewer_keywords:
- XMLA Query Editor
- Query Editor [XMLA]
ms.assetid: 14623019-7839-4038-9d12-2f8953d2ec04
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d324657c6a405d090913909a7e5aaa756970734
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101540"
---
# <a name="xmla-query-editor-analysis-services---multidimensional-data"></a>XMLA-Abfrage-Editor (Analysis Services – Mehrdimensionale Daten)
  Mithilfe von XMLA-Abfrage-Editor können Sie in XMLA-Sprache verfasste Anweisungen und Skripts erstellen und ausführen.  
  
## <a name="features"></a>Funktionen  
  
-   Im Abfrage-Editorfenster des XMLA-Abfrage-Editors können Sie Skripts eingeben.  
  
-   Um Skripts auszuführen, müssen Sie entweder **F5**drücken oder auf der Symbolleiste auf **Ausführen** klicken oder im Menü **Abfrage** die Option **Ausführen**auswählen. Wenn ein Teil des Codes ausgewählt ist, wird nur dieser Teil ausgeführt. Ist kein Code ausgewählt, wird der gesamte Inhalt des XMLA-Abfrage-Editors ausgeführt.  
  
-   Im Metadatenbereich können Sie Metadaten für Cubes und andere Objekte der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank anzeigen.  
  
-   Um Hilfe zur XMLA-Syntax zu erhalten, wählen Sie im XMLA-Abfrage-Editor ein Schlüsselwort aus, und klicken Sie dann auf **F1**.  
  
-   Dynamische Hilfe zur XMLA-Syntax erhalten Sie, indem Sie im Menü **Hilfe** auf **Dynamische Hilfe** klicken, um die Komponente Dynamische Hilfe zu öffnen. Bei der dynamischen Hilfe werden die Hilfethemen im Fenster **Dynamische Hilfe** angezeigt, sobald Schlüsselwörter im Abfrage-Editor eingegeben werden.  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>SQL Server Analysis Services-Editoren (Symbolleiste)  
 Wenn der XMLA-Abfrage-Editor geöffnet ist, wird die Symbolleiste **SQL Server Analysis Services-Editoren** mit den folgenden Schaltflächen angezeigt.  
  
|Begriff|Definition|  
|----------|----------------|  
|**Verbinden**|Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt werden kann.|  
|**Trennen**|Trennt die Verbindung zwischen dem XMLA-Abfrage-Editor und einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Verbindung ändern**|Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem eine Verbindung mit einer anderen Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt werden kann.|  
|**Neue Abfrage mit aktueller Verbindung**|Öffnet ein neues XMLA-Abfrage-Editorfenster mithilfe der Verbindungsinformationen des aktuellen XMLA-Abfrage-Editorfensters.|  
|**Verfügbare Datenbanken**|Ändert die Verbindung zu einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank innerhalb derselben Instanz.|  
|**Ausführen**|Führt den ausgewählten Code aus. Wenn kein Code ausgewählt ist, wird mit dieser Option der gesamte Code im XMLA-Abfrage-Editor ausgeführt.|  
|**Analysieren**|Überprüft die Syntax des ausgewählten Codes. Wenn kein Code ausgewählt ist, wird mit dieser Option die Syntax des gesamten XMLA-Abfrage-Editorfensters geprüft.|  
|**Ausführung der Abfrage abbrechen**|Sendet eine Abbruchsanforderung an den Server. Einige Abfragen können nicht sofort abgebrochen werden, sondern müssen auf angemessene Bedingungen für einen Abbruch warten. Beim Abbruch von Abfragen können Verzögerungen auftreten, während für die Transaktionen ein Rollback ausgeführt wird.|  
  
## <a name="xmla-query-editor-window"></a>XMLA-Abfrage-Editorfenster  
 Im XMLA-Abfrage-Editor sind die folgenden Optionen verfügbar:  
  
|Begriff|Definition|  
|----------|----------------|  
|**Abfrage-Editor-Fenster**|Hier können Sie XMLA-Anweisungen und -Skripts eingeben, die vom XMLA-Abfrage-Editor ausgeführt werden sollen.<br /><br /> Das Kontextmenü des Abfrage-Editorfensters enthält die folgenden Optionen:<br /><br /> **Ausschneiden**: kopiert die aktuelle Auswahl in die Zwischenablage und entfernt Sie aus dem Abfrage-Editorfenster.<br />**Kopieren:** Kopiert die aktuelle Auswahl in die Zwischenablage.<br />**Fügen Sie**: Fügt den Inhalt der Zwischenablage in die aktuelle Auswahl.<br />**Verbinden:** Öffnet das Dialogfeld **Verbindung mit Server herstellen**, in dem eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt werden kann.<br />**Trennen Sie**: trennt die Verbindung der aktuellen Abfrage-Editor aus einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz.<br />**Alle Abfragen trennen**: trennt die Verbindung aller geöffneten Abfrage-Editoren.<br />**Verbindung ändern**: Öffnet die **Herstellen einer Verbindung mit Server** im Dialogfeld zum Herstellen einer Verbindung zu einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz.<br />**Öffnen Sie im Objekt-Explorer den Server**: Öffnet die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz, die mit der aktuellen Abfrage-Editor, in verbunden ist **Objekt-Explorer**.<br />**Führen Sie**: führt den ausgewählten Code aus, oder wenn kein Code ausgewählt ist, der gesamte Code in der aktuellen Abfrage-Editor ausgeführt.<br />**Fenster "Eigenschaften"**: Zeigt die **Eigenschaften** -Fensters im [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] für das aktuelle Abfragefenster.<br />**Abfrageoptionen**: Zeigt die **Abfrageoptionen** Dialogfeld.|  
|**Fenster "Ergebnisse"**|Zeigt die Ergebnisse einer XMLA-Anweisung bzw. eines MDX-Skripts als Text an.|  
|**Meldungsfenster**|Zeigt Informationen zum Ausführen einer XMLA-Anweisung bzw. eines MDX-Skripts an. In diesem Fenster werden beispielsweise während der Ausführung alle auftretenden Fehler bzw. wird nach der Ausführung die Anzahl der abgerufenen Zellen angezeigt.|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Abfrage-Editor &#40;Analysis Services – mehrdimensionale Daten&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [DMX-Abfrage-Editor &#40;Analysis Services – Datamining&#41;](dmx-query-editor-analysis-services-data-mining.md)   
 [Abfrage- und Text-Editoren &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [Tastenkombinationen für SQL Server Management Studio](../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  
