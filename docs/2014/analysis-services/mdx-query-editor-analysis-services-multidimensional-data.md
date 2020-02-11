---
title: MDX-Abfrage-Editor (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.startpage.mdx.f1
helpviewer_keywords:
- Query Editor [MDX]
- MDX Query Editor
ms.assetid: 777f2c23-1c1c-4b72-9d19-48a4866551f8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 579af162998ffaa7c9483a6e6d29a87f98e96fac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077880"
---
# <a name="mdx-query-editor-analysis-services---multidimensional-data"></a>MDX-Abfrage-Editor (Analysis Services – Mehrdimensionale Daten)
  Mithilfe von MDX-Abfrage-Editor können Sie in MDX-Sprache verfasste Anweisungen und Skripts erstellen und ausführen.  
  
## <a name="features"></a>Features  
  
-   Im Abfrage-Editorfenster des MDX-Abfrage-Editors können Sie Skripts eingeben.  
  
-   Um Skripts auszuführen, müssen Sie entweder **F5**drücken oder auf der Symbolleiste auf **Ausführen** klicken oder im Menü **Abfrage** die Option **Ausführen**auswählen. Wenn ein Teil des Codes ausgewählt ist, wird nur dieser Teil ausgeführt. Ist kein Code ausgewählt, wird der gesamte Inhalt des MDX-Abfrage-Editors ausgeführt.  
  
-   Im Metadatenbereich können Sie Metadaten für Cubes und andere Objekte der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank anzeigen.  
  
-   Um Hilfe zur MDX-Syntax zu erhalten, wählen Sie im MDX-Abfrage-Editor ein Schlüsselwort aus, und klicken Sie dann auf **F1**.  
  
-   Dynamische Hilfe zur MDX-Syntax erhalten Sie, indem Sie im Menü **Hilfe** auf **Dynamische Hilfe**klicken, um die Komponente der dynamischen Hilfe zu öffnen. Bei der dynamischen Hilfe werden die Hilfethemen im Fenster **Dynamische Hilfe** angezeigt, sobald Schlüsselwörter im Abfrage-Editor eingegeben werden.  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>SQL Server Analysis Services-Editoren (Symbolleiste)  
 Wenn der MDX-Abfrage-Editor geöffnet ist, wird die Symbolleiste der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Editoren mit den in der folgenden Tabelle aufgelisteten Schaltflächen angezeigt.  
  
|Begriff|Definition|  
|----------|----------------|  
|**Herstellen einer Verbindung**|Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt werden kann.|  
|**Verschluss**|Trennt die Verbindung zwischen dem MDX-Abfrage-Editor und einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Verbindung ändern**|Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem eine Verbindung mit einer anderen Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt werden kann.|  
|**Neue Abfrage mit aktueller Verbindung**|Öffnet ein neues MDX-Abfrage-Editorfenster mithilfe der Verbindungsinformationen des aktuellen MDX-Abfrage-Editorfensters.|  
|**Verfügbare Datenbanken**|Wechselt die Verbindung zu einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank innerhalb derselben Instanz.|  
|**Auszuführen**|Führt den ausgewählten Code aus. Wenn kein Code ausgewählt ist, wird der gesamte Code im MDX-Abfrage-Editor ausgeführt.|  
|**Analysieren**|Überprüft die Syntax des ausgewählten Codes. Wenn kein Code ausgewählt ist, wird die Syntax des gesamten MDX-Abfrage-Editorfensters geprüft.|  
|**Ausführung der Abfrage abbrechen**|Sendet eine Abbruchsanforderung an den Server. Einige Abfragen können nicht sofort abgebrochen werden, sondern müssen auf angemessene Bedingungen für einen Abbruch warten. Beim Abbruch von Abfragen können Verzögerungen auftreten, während für die Transaktionen ein Rollback ausgeführt wird.|  
  
## <a name="mdx-query-editor-window"></a>MDX-Abfrage-Editorfenster  
 Im MDX-Abfrage-Editor stehen die in der folgenden Tabelle aufgelisteten Optionen zur Verfügung.  
  
|Begriff|Definition|  
|----------|----------------|  
|**Abfrage-Editorfenster**|Hier können Sie MDX-Anweisungen und -Skripts eingeben, die vom MDX-Abfrage-Editor ausgeführt werden sollen.<br /><br /> Das Kontextmenü des Abfrage-Editorfensters enthält die folgenden Optionen:<br /><br /> **Ausschneiden**: kopiert die aktuelle Auswahl in die Zwischenablage und entfernt die Auswahl aus dem Abfrage-Editor-Fenster.<br /><br /> **Kopieren**: kopiert die aktuelle Auswahl in die Zwischenablage.<br /><br /> **Einfügen**: Fügt den Inhalt der Zwischenablage in die aktuelle Auswahl ein.<br /><br /> **Verbinden**: öffnet das Dialogfeld **Verbindung mit Server herstellen** , um eine Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz herzustellen.<br /><br /> **Trennen**: trennt die Verbindung zwischen dem aktuellen Abfrage- [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Editor und einer Instanz von.<br /><br /> **Alle Abfragen trennen**: trennt die Verbindung aller aktuell geöffneten Abfrage-Editoren.<br /><br /> **Verbindung ändern**: öffnet das Dialogfeld Verbindung **mit Server herstellen** , um eine Verbindung mit einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz herzustellen.<br /><br /> **Server in Objekt-Explorer öffnen**: öffnet die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz, mit der der aktuelle Abfrage-Editor in **Objekt-Explorer**verbunden ist.<br /><br /> **Execute**: führt den ausgewählten Code aus. Wenn kein Code ausgewählt ist, wird der gesamte Code im aktuellen Abfrage-Editor ausgeführt.<br /><br /> **Eigenschaften Fenster**: zeigt das Fenster **Eigenschaften** für [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] das aktuelle Abfragefenster an.<br /><br /> **Abfrage Optionen**: zeigt das Dialogfeld **Abfrage Optionen** an.|  
|**Fenster Metadaten**|Zeigt Metadaten für die aktuell verbundene [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank an.|  
|**Cube**|Wählen Sie einen Cube in der aktuell verbundenen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank aus, um die zugehörigen Metadaten des Cubes auf der Registerkarte **Metadaten** anzuzeigen.|  
|**Metadaten**|Zeigt die Metadaten für den unter **Cube**ausgewählten Cube an, einschließlich Measuregruppen und Measures, Key Performance Indicators, Dimensionen, Hierarchien, Ebenen, Elementen und Elementeigenschaften. Zum Abrufen des voll gekennzeichneten Schlüssels eines Objekts führen Sie einen der beiden folgenden Schritte aus:<br /><br /> Ziehen Sie das Objekt von der Registerkarte **Metadaten** in das Abfragefenster.<br /><br /> Klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie **Kopieren** aus. Klicken Sie anschließend mit der rechten Maustaste in das Abfragefenster, und wählen Sie **Einfügen** aus.|  
|**Funktionen**|Zeigt die Metadaten für MDX-Funktionen an, die für die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank so verfügbar sind, wie sie aus MDSCHEMA_FUNCTIONS-Schemarowset abgerufen wurden. Zum Abrufen der Syntax einer Funktion führen Sie einen der beiden folgenden Schritte aus:<br /><br /> Ziehen Sie das Objekt von der Registerkarte **Funktionen** in das Abfragefenster.<br /><br /> Klicken Sie mit der rechten Maustaste auf die Funktion, und wählen Sie **Kopieren** aus. Klicken Sie anschließend mit der rechten Maustaste in das Abfragefenster, und wählen Sie **Einfügen** aus.|  
|**Ergebnisfenster**|Zeigt die Ergebnisse einer MDX-Anweisung bzw. eines MDX-Skripts in einem Raster an.|  
|**Meldungsfenster**|Zeigt Informationen zum Ausführen einer MDX-Anweisung bzw. eines MDX-Skripts an. In diesem Fenster werden beispielsweise während der Ausführung alle auftretenden Fehler bzw. wird nach der Ausführung die Anzahl der abgerufenen Zellen angezeigt.|  
  
  
