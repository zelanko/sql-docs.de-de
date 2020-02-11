---
title: Designer für tabellarische Modelle (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.TOPLEVSEMMODUIENTRY.F1
ms.assetid: 45735c57-2a95-4e45-8994-7242df6c9c5f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 223a8a300a4f3000512f8d75dfb7595cb52abc08
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067828"
---
# <a name="tabular-model-designer-ssas-tabular"></a>Designer für tabellarische Modelle (SSAS – tabellarisch)
  Der Designer für tabellarische Modelle ist [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Bestandteil von, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integriert in Microsoft 2010 oder höher, mit zusätzlichen Projekttyp Vorlagen speziell für die Entwicklung professioneller tabellarischer Modelllösungen.  
  
 Abschnitte in diesem Thema:  
  
-   [Vorteile](#bkmk_benefits)  
  
-   [Projektvorlagen](#bkmk_proj_temp)  
  
-   [Fenster und Menüs](#bkmk_wind_men)  
  
-   [Visual Studio-Integration](#bkmk_vsint)  
  
##  <a name="bkmk_benefits"></a> Vorteile  
 Wenn Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] installieren, werden den verfügbaren Projekttypen neue Projektvorlagen zum Erstellen tabellarischer Modelle hinzugefügt. Nachdem ein neues Projekt für tabellarische Modelle auf der Grundlage einer der Vorlagen erstellt wurde, können Sie mit der Erstellung von Modellen beginnen. Dazu verwenden Sie die Designer-Tools und Assistenten für tabellarische Modelle.  
  
 Zusätzlich zu neuen Vorlagen und Tools zum Erstellen professioneller Projektmappen für mehrdimensionale und tabellarische Modelle stellt die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Umgebung Debugging- und Projektlebenszyklusfunktionen bereit, mit denen Sie immer die leistungsstärksten BI-Lösungen für Ihre Organisation erstellen können. Weitere Informationen zu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] finden Sie unter [Erste Schritte mit Visual Studio](https://go.microsoft.com/fwlink/?LinkId=206389).  
  
##  <a name="bkmk_proj_temp"></a>Projektvorlagen  
 Wenn Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] installieren, werden den Business Intelligence-Projekttypen die folgenden Projektvorlagen für tabellarische Modelle hinzugefügt:  
  
 **Analysis Services-Projekt für tabellarische Modelle**  
 Mit dieser Vorlage kann ein neues, leeres tabellarisches Modellprojekt erstellt werden.  
  
 **Von Server importieren (tabellarisch)**  
 Mit dieser Vorlage kann ein neues tabellarisches Modellprojekt erstellt werden, indem die Metadaten aus einem vorhandenen tabellarischen Modell in Analysis Services extrahiert werden.  
  
 **Aus PowerPivot importieren**  
 Mit dieser Vorlage wird ein neues tabellarisches Modellprojekt erstellt, indem die Metadaten und Daten aus einer [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] -Datei extrahiert werden.  
  
> [!NOTE]  
>  Projekte für tabellarische Modelle erfordern, dass eine sich im tabellarischen Modus befindliche Analysis Services-Serverinstanz lokal oder im Netzwerk ausgeführt wird.  
  
##  <a name="bkmk_wind_men"></a>Fenster und Menüs  
 Die [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]-Erstellungsumgebung für tabellarische Modelle schließt Folgendes ein:  
  
### <a name="designer-window"></a>Designerfenster  
 Das Designerfenster dient zur Erstellung tabellarischer Modelle, indem das Modell in einer visuellen Darstellung abgebildet wird. Wenn Sie die Datei Model.bim öffnen, wird das Modell im Designerfenster geöffnet. Zum Erstellen eines Modells im Designerfenster stehen zwei unterschiedliche Ansichtsmodi zur Verfügung:  
  
 **Datenansicht**  
 In der Datensicht werden Tabellen in einem tabellarischen Rasterformat angezeigt. Außerdem können Sie Measures mit dem Measureraster definieren, das für jede Tabelle ausschließlich in der Datensicht angezeigt werden kann.  
  
 **Diagramm Ansicht**  
 In der Diagrammsicht werden Tabellen mit den bestehenden Beziehungen in einem grafischen Format angezeigt. Spalten, Measures, Hierarchien und KPIs können gefiltert werden, und Sie können auswählen, ob das Modell mithilfe einer definierten Perspektive angezeigt wird.  
  
 Die meisten Modellerstellungsaufgaben können in einer beliebigen Ansicht ausgeführt werden.  
  
### <a name="solution-explorer"></a>Projektmappen-Explorer  
 Im Projektmappen-Explorer-Fenster wird die aktive Projektmappe als logischer Container für Projekte für tabellarische Modelle dargestellt und umfasst die dazugehörigen Elemente. Das Modellprojekt (.smproj) enthält gewöhnlich nur ein (leeres) References-Objekt und die Datei Model.bim. In dieser Ansicht können Sie Projektelemente zum Ändern öffnen und andere Verwaltungsaufgaben ausführen.  
  
 Projektmappen für tabellarische Modelle enthalten normalerweise nur ein Projekt. Dagegen kann eine Projektmappe weitere Projekte enthalten, z. B. ein Projekt für Integration Services oder Reporting Services. Sie können eine beliebige Anzahl von Dateien hinzufügen, sofern sie nicht den gleichen Typ aufweisen wie Projektdateien für tabellarische Modelle und ihre Buildvorgang-Eigenschaft nicht auf Kein bzw. ihre In Ausgabeverzeichnis kopieren-Eigenschaft nicht auf Nicht kopieren festgelegt ist.  
  
 Klicken Sie zum Anzeigen des Projektmappen-Explorers auf das Menü **Ansicht** und anschließend auf **Projektmappen-Explorer**.  
  
### <a name="properties-window"></a>Eigenschaftenfenster  
 Im Eigenschaftenfenster werden Eigenschaften des ausgewählten Objekts aufgelistet. Die folgenden Objekte verfügen über Eigenschaften, die im Eigenschaftenfenster angezeigt und bearbeitet werden können:  
  
-   Model.bim  
  
-   Tabelle  
  
-   Column  
  
-   "Measure"  
  
 Die Projekteigenschaften im Eigenschaftenfenster enthalten nur den Projektnamen und den Projektordner. Projekte verfügen außerdem über zusätzliche Einstellungen für Bereitstellungsoptionen und den Bereitstellungsserver, die Sie über ein Dialogfeld für modale Eigenschaften festlegen können. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend auf **Eigenschaften**, um diese Eigenschaften anzuzeigen.  
  
 In die Felder des Eigenschaftenfensters sind Steuerelemente eingebettet, die geöffnet werden, wenn Sie darauf klicken. Der Typ des Bearbeitungssteuerelements hängt von der bestimmten Eigenschaft ab. Die Steuerelemente umfassen Bearbeitungsfelder, Dropdownlisten und Links zu benutzerdefinierten Dialogfeldern. Die in grau angezeigten Eigenschaften sind schreibgeschützt.  
  
 Klicken Sie zum Anzeigen des Fensters **Eigenschaften** auf das Menü **Ansicht** und anschließend auf **Eigenschaftenfenster**.  
  
### <a name="error-list"></a>Fehlerliste  
 Das Fenster mit der Fehlerliste enthält Meldungen zum Modellstatus:  
  
-   Benachrichtigungen zu bewährten Sicherheitsmethoden.  
  
-   Anforderungen für die Datenverarbeitung.  
  
-   Informationen zu Semantikfehlern für berechnete Spalten, Measures und Zeilenfilter für Rollen. Bei berechneten Spalten können Sie auf die Fehlermeldung doppelklicken, um zur Fehlerquelle zu navigieren.  
  
-   DirectQuery-Überprüfungsfehler.  
  
 Die **Fehlerliste** wird standardmäßig erst angezeigt, nachdem ein Fehler zurückgegeben wurde. Sie können das Fenster **Fehlerliste** jedoch jederzeit anzeigen. Klicken Sie zum Anzeigen des Fensters **Fehlerliste** auf das Menü **Ansicht** und anschließend auf **Fehlerliste**.  
  
### <a name="output"></a>Output  
 Erstellungs- und Bereitstellungsinformationen werden (zusätzlich zum modalen Statusdialogfeld) im Fenster **Ausgabe** angezeigt. Klicken Sie zum Anzeigen des Ausgabefensters auf das Menü **Ansicht** und anschließend auf **Ausgabe**.  
  
### <a name="menu-items"></a>Menüelemente  
 Wenn Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] installieren, werden der Visual Studio-Menüleiste zusätzliche Menüelemente speziell für die Erstellung tabellarischer Modelle hinzugefügt. Das Menü **Modell** kann verwendet werden, um den Datenimport-Assistenten zu starten, vorhandene Verbindungen anzuzeigen, Arbeitsbereichsdaten zu verarbeiten und den Modellarbeitsbereich in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel zu durchsuchen. Das Menü **Tabelle** kann verwendet werden, um Beziehungen zwischen Tabellen zu erstellen und zu verwalten, Measures zu erstellen und zu verwalten sowie Datentabelleneinstellungen, Berechnungsoptionen und andere Tabelleneigenschaften anzugeben. Im Menü **Spalte** können Sie Spalten in einer Tabelle hinzufügen und löschen, Spalten aus- und einblenden und verschiedene Spalteneigenschaften angeben, z.B. Datentypen und Filter. Sie können Projektmappen für tabellarische Modelle über das Menü **Erstellen** anlegen und bereitstellen. Die Funktionen zum Kopieren bzw. Einfügen sind im Menü **Bearbeiten** enthalten.  
  
 Zusätzlich zu diesen Menüelementen werden die Analysis Services-Optionen um weitere Einstellungen ergänzt, die im Menü Extras verfügbar sind.  
  
### <a name="toolbar"></a>Symbolleiste  
 Die Analysis Services-Symbolleiste ermöglicht den schnellen und einfachen Zugriff auf die am häufigsten verwendeten Befehle für die Modellerstellung.  
  
##  <a name="bkmk_vsint"></a>Visual Studio-Integration  
 **Quell Code Verwaltung**  
 Analysis Services-Projekte werden mit dem ausgewählten Plug-In für die Quellcodeverwaltung integriert. Wenn Sie Visual Studio für die Verwendung der Quellcodeverwaltung konfiguriert haben, können Sie die Funktionen zum Ein-/Auschecken im Projektmappen-Explorer verwenden. Weitere Informationen zum Konfigurieren von Team Foundation Server finden Sie unter [Konfigurieren von Visual Studio für die Verwendung der Team Foundation-Versionskontrolle](https://msdn.microsoft.com/library/ms253064.aspx). Viele Drittanbieter-Plug-Ins für die Quellcodeverwaltung werden ebenfalls unterstützt.  
  
 **Schrift**  
 Tabellarische Modelle verwenden die Schriftart der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Umgebung, um die Schriftarten in der Anzeige zu steuern. Es kann erforderlich sein, diese Schriftart zu ändern, wenn die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Standardschriftart nicht über alle Unicode-Zeichen verfügt, die Sie für Ihre Sprache benötigen. Klicken Sie zum Ändern von Schriftarten auf das Menü **Extras** > **Optionen** und anschließend auf **Schriftarten und Farben**.  
  
 **Tastenkombinationen**  
 Die Analysis Services-Tastenkombinationen können über das Dialogfeld Tools->Optionen->Tastatur konfiguriert bzw. neu zugeordnet werden. Einige globale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Verknüpfungen, wie z.B. „Erstellen“, „Speichern“, „Debuggen“, „neues Projekt“ usw., werden im Kontext des Designers für tabellarische Modelle unterstützt. Andere spezifische Tastenkombinationen des Designers für tabellarische Modelle sind im Analysis Services-Kontext verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellarische Modellprojekte &#40;tabellarischen SSAS-&#41;](tabular-models/tabular-model-projects-ssas-tabular.md)   
 [Eigenschaften &#40;tabellarischen SSAS-&#41;](tabular-models/properties-ssas-tabular.md)  
  
  
