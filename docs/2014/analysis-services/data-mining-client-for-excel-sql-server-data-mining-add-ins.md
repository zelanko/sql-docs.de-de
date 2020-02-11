---
title: Data Mining-Client für Excel (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Data Mining Client
- wizards
- getting started
ms.assetid: e075e2de-11cc-4f71-9603-0b161bca8a24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9c2f11ecbdf90aeeb5e0e5a3ef097152898042d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086431"
---
# <a name="data-mining-client-for-excel-sql-server-data-mining-add-ins"></a>Data Mining-Client für Excel (SQL Server Data Mining-Add-Ins)
  Der Data Mining-Client für Excel umfasst eine Reihe von Tools, mit denen Sie häufige Data Mining-Aufgaben ausführen können – von der Datenbereinigung bis hin zur Modellerstellung und Vorhersageabfragen. Sie können Daten in Excel-Tabellen oder Bereichen verwenden oder auf externe Datenquellen zugreifen.  
  
 ![DM](media/dm-tabletools.gif "DM")  
  
-   [Arbeiten mit Daten](#bkmk_Data)  
  
     Laden Sie die Daten in Excel, bereinigen Sie die Daten, suchen Sie nach Ausreißern, und erstellen Sie statistische Zusammenfassungen. Sie können auch verschiedene Arten von Stichproben ausführen, Datenprofile erstellen und Modelle mithilfe externer Daten testen. Mit dem Data Mining-Client können Sie Daten einfach ohne komplexe Skripts oder ETL-Prozesse für die Analyse vorbereiten.  
  
-   [Erstellen von Modellen und Analysieren](#bkmk_Model)  
  
     Diese Tools bieten Assistentenschnittstellen zu bekannten, empirisch getesteten Data Mining-Algorithmen, einschließlich Clustering (K-Means und EM), Zuordnungsanalyse, Zeitreihenanalyse und Entscheidungsstrukturen. Durch erweiterte Modellierungsoptionen für jeden Assistenten können Sie verschiedene Algorithmen auswählen (wie Naive Bayes oder neuronale Netzwerke) und das Verhalten anpassen (wie Cluster-Ausgangswert oder ursprüngliche Stichprobengröße).  
  
     Alle Data Mining-Algorithmen werden in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], sodass Ihnen das Erstellen komplexer Modelle erleichtert wird.  
  
-   [Testen, Abfragen und Überprüfen von Modellen](#bkmk_Validate)  
  
     Der Data Mining-Client stellt Tools nach Industriestandard zum Testen von Modellen bereit, einschließlich Prognosegütediagramme und Kreuzvalidierung. Die Assistenten, die bereitgestellt werden, vereinfachen das Testen der Gültigkeit des Datasets und seiner Genauigkeit. Der Abfrage-Assistent erstellt Abfragen, um die Modelle für Vorhersagen und Bewertungen zu verwenden.  
  
-   [Modelle anzeigen](#bkmk_ViewModels)  
  
     Diagramme, die von den meisten Tools generiert werden, können direkt in Excel gespeichert werden. Verwenden Sie die [Browser Modelle in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) Tool, um die Modelle zu untersuchen.  
  
-   [Verwalten, Dokumentieren und Bereitstellen](#bkmk_UsageMgmt)  
  
     Der Data Mining-Client für Excel verfügt über eine aktive Verbindung mit dem Server, sodass Sie das Data Mining-Modell auf dem Server speichern können, um es weiteren Tests zu unterziehen oder um es für größere Skalierbarkeit auf einem Produktionsserver bereitzustellen.  
  
##  <a name="bkmk_Data"></a>Arbeiten mit Daten  
 Die Gruppe **Daten Vorbereitung** enthält die folgenden Assistenten, mit denen Sie Daten in Vorbereitung auf Data Mining Aufgaben überprüfen und bereinigen. Darüber hinaus können Sie mit den meisten Assistenten Daten in Trainings- und Testsätze trennen.  
  
 [Durchsuchen von Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 Zum Erstellen und Speichern von Modellen unterstützen die Add-Ins die folgenden Datenverbindungen:  
  
-   Verbindung mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server zum Speichern und Verarbeiten der Modelle.  
  
-   Optionale Verbindungen mit externen Datenquellen. Sie können Ihr Modell mit einem beliebigen Typ von Daten erstellen, die als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle definiert werden können. Sie können jedoch auch einfach die Daten verwenden, die bereits in Excel enthalten sind.  
  
 [Durchsuchen von Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 Der Assistent zum durch **Suchen von Daten** unterstützt Sie dabei, den Typ und die Menge der Daten in der Datentabelle zu verstehen, indem die Verteilung und die Werte für die ausgewählten Spalten nacheinander grafisch dargestellt werden.  
  
 [Beispiel Daten &#40;SQL Server Data Mining-Add-ins&#41;](sample-data-sql-server-data-mining-add-ins.md)  
 Das Erstellen der richtigen Daten zum Trainieren und Testen Ihrer Modelle ist ein wichtiger Bestandteil beim Data Mining. Ohne die richtigen Tools kann diese Aufgabe jedoch mühsam sein. Der Assistent für **Beispiel Daten** vereinfacht das Aufteilen der für ein Modell verwendeten Daten in zwei Gruppen, eine zum Entwickeln des Modells und eine zum Testen. Sie können zufällige Stichproben nehmen oder Überquotierung anwenden.  
  
 [Vorhersagerechner &#40;Tabellenanalyse Tools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Der **ausreißerentfernungs** -Assistent bietet mehrere Tools, mit denen Sie Ausreißer identifizieren und entsprechend behandeln können. Er zeigt die Verteilung der Werte sowie die Beziehung zwischen Ausreißern und anderen Daten auf. Sie können entscheiden, ob Ausreißer entfernt oder geändert werden sollen.  
  
 [Vorhersagerechner &#40;Tabellenanalyse Tools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Der **Assistent zum** neubezeichnen von Daten unterstützt Sie beim Erstellen neuer Bezeichnungen für Daten, damit die Ergebnisse der Analyse leichter verständlich werden. Beispielsweise können Sie einem Datenbereich einen aussagekräftigeren Namen geben oder einen repräsentativen Wert aus der Liste auswählen.  
  
##  <a name="bkmk_Model"></a>Erstellen von Modellen und analysieren  
 Mithilfe der Optionen im Abschnitt " **Datenmodellierung** " der Symbolleiste können Sie Muster aus Daten ableiten. Gruppieren Sie Daten Zeilen basierend auf Attributen, oder untersuchen Sie Zuordnungen. Die Assistenten auf diesem Menüband basieren auf den leistungsfähigen Data Mining-Algorithmen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Anders als mit den vergleichbaren Tabellenanalysetools für Excel können Sie mit diesen Assistenten das Verhalten der Algorithmen anpassen und eine Vielzahl von Datenquellen nutzen.  
  
 [Assistent zum Klassifizieren &#40;Data Mining-Add-Ins für Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
 Der Assistent zum **klassifizieren** unterstützt Sie beim Erstellen eines Klassifizierungs Modells auf der Grundlage vorhandener Daten in einer Excel-Tabelle, eines Excel-Bereichs oder einer externen Datenquelle. Mit einem Klassifizierungsmodell werden Muster in den Daten extrahiert, die auf Übereinstimmungen hinweisen. So können Sie Vorhersagen basierend auf Wertgruppen treffen. Ein Klassifizierungsmodell kann beispielsweise verwendet werden, um das Risiko auf der Grundlage von Einkommens- und Konsummustern vorherzusagen.  
  
 Der Assistent zum **klassifizieren** unterstützt die Verwendung dieser Microsoft Data Mining-Algorithmen: Decision Trees-Algorithmus, logistische Regression, Naive Bayes, neuronale Netzwerke.  
  
 [Assistent zum Schätzen von Daten &#40;Data Mining-Add-Ins für Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
 Der Assistent für die **Schätzung** unterstützt Sie beim Erstellen eines Schätz Modells. Ein Schätzmodell extrahiert Datenmuster und verwendet diese, um ein numerisches Ergebnis (z. B. eine Währung, einen Umsatz, ein Datum oder eine Uhrzeit) vorherzusagen.  
  
 Der Assistent für die **Schätzung** verwendet diese Microsoft Data Mining-Algorithmen: Entscheidungsbäume, lineare Regression, logistische Regression und neuronale Netzwerke.  
  
 [Wichtige Einflussfaktoren &#40;Tabellenanalyse Tools für Excel analysieren&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Der Cluster-Assistent unterstützt Sie beim Erstellen eines Clusteringmodells. Ein Clustermodell erkennt Gruppen von Zeilen mit ähnlichen Merkmalen. Dieser Assistent ist hilfreich beim Durchsuchen von Mustern in sämtlichen Daten.  
  
 Der **Cluster** -Assistent verwendet den Microsoft Clustering-Algorithmus, der sowohl K-Means als auch EM enthält.  
  
 [Assistenten &#40;Data Mining-Client für Excel zuordnen&#41;](associate-wizard-data-mining-client-for-excel.md)  
 Der Zuordnungs **-Assistent unterstützt Sie beim Erstellen** eines Data Mining Modells mithilfe des Microsoft Association Rules-Algorithmus, der häufig zusammen auftretende Elemente oder Ereignisse erkennt. Solche Zuordnungsmodelle sind besonders nützlich, wenn Sie Empfehlungen aussprechen möchten.  
  
 Der Zuordnungs **-Assistent verwendet den Microsoft** Association Rules-Algorithmus.  
  
 [Planungs-Assistent &#40;Data Mining-Add-Ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
 Der Planungs-Assistent unterstützt Sie bei der **Vorhersage von** Werten in einer Zeitreihe. In der Regel enthalten in einer Vorhersage verwendete Daten eine Art von Zeitreihen, entweder einen Datumsstempel oder eine Sequenz ID, anhand derer Muster für die Vorhersage künftiger Werte abgeleitet werden.  
  
 Der Planungs **-Assistent verwendet den Microsoft** Time Series-Algorithmus.  
  
 [Erweiterte Modellierung &#40;Data Mining-Add-Ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
 Sind Sie bereits vertraut mit dem Data Mining? Mithilfe der **erweiterten** Daten Modellierungs Optionen können Sie benutzerdefinierte Datenstrukturen erstellen und Modelle mithilfe von Anpassungen erstellen, die nicht in den anderen Tools und Assistenten enthalten sind.  
  
##  <a name="bkmk_Validate"></a>Testen, Abfragen und Validieren von Modellen  
 Verwenden Sie die Assistenten auf der Symbolleiste " **Genauigkeit und Validierung** ", um nach Industriestandard Tests zum Überprüfen der Genauigkeit ihrer Modelle und zur Bewertung der Daten Fähigkeit des Datasets zum Erstellen von Modellen zu verwenden.  
  
 [Wichtige Einflussfaktoren &#40;Tabellenanalyse Tools für Excel analysieren&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Bewertet die Leistung eines Data Mining-Modells durch Erstellen eines Liftdiagramms oder Punktdiagramms.  
  
 [Klassifizierungs Matrix &#40;SQL Server Data Mining-Add-ins&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
 Hilft beim Überprüfen der Leistung eines Klassifizierungsmodells durch Erstellen eines Diagramms, das genaue und ungenaue Vorhersagen des Modells zusammenfasst.  
  
 [Gewinn Diagramm &#40;SQL Server Data Mining-Add-ins&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
 Hilft beim Einschätzen der Auswirkungen eines Data Mining-Modells, indem die Genauigkeit der Vorhersagen zusammen mit den Kosten und Vorteilen der daraufhin erfolgenden Maßnahmen analysiert werden.  
  
 [&#40;SQL Server Data Mining-Add-ins&#41;der Kreuz Validierung](cross-validation-sql-server-data-mining-add-ins.md)  
 Erstellt einen Bericht, der die Genauigkeit des Modells über viele Teilmengen eines Datasets hinweg zusammenfasst, sodass Sie die Stabilität des Modells beurteilen können.  
  
 Sie können Daten in einer Excel-Tabelle auch in einer Vorhersageabfrage für ein Miningmodell verwenden, das auf dem Server gespeichert ist.  
  
 [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md)  
 Der **Abfrage** -Assistent unterstützt Sie beim Erstellen von Vorhersagen für ein vorhandenes Data Mining Modell.  
  
 [Erweiterter Data Mining-Abfrage-Editor](advanced-data-mining-query-editor.md)  
 Für fortgeschrittene Benutzer bietet das Tool eine Drag &amp; Drop-Schnittstelle zu DMX. Sie können auf einfache Weise Vorhersageabfragen oder neue Modelle erstellen, ohne dass Sie sich Gedanken über die Syntax machen müssen.  
  
##  <a name="bkmk_ViewModels"></a>Modelle anzeigen  
 Modelle, die Sie erstellen, werden zum Durchsuchen automatisch geöffnet. Sie können Modelle trotzdem auch auf dem Server durchsuchen und neue Visualisierungen generieren. Verwenden Sie die [Visio-Formen](viewing-data-mining-models-in-visio-data-mining-add-ins.md) , um Modell Diagramme in eine anpassbare Canvas zu exportieren.  
  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
 Zeigen Sie die erstellten Modelle mit interaktiven Diagrammen an, die für jeden Modelltyp angepasst sind.  
  
 [Dokumentieren von Mining Modellen &#40;Data Mining-Add-Ins für Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)  
 Dieser Assistent erstellt Berichte mit einer statistischen Zusammenfassung des Datasets und Metadaten zum Modell, die die Untersuchung und Interpretation erleichtern.  
  
##  <a name="bkmk_UsageMgmt"></a>Verwalten, dokumentieren und bereitstellen  
 Mithilfe dieser Tools können Sie eine Verbindung mit einem Data Mining-Server herstellen. Zudem ermöglichen sie das Verwalten und Exportieren von Modellen sowie das Überwachen von Data Mining-Aktivitäten.  
  
 [Verwalten von Modellen &#40;SQL Server Data Mining-Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md)  
 Wenn Sie über die erforderlichen Berechtigungen verfügen, können Sie vorhandene Miningmodelle und -strukturen löschen, ändern, umbenennen oder verarbeiten, ohne dazu Excel verlassen zu müssen.  
  
 [Ablauf Verfolgung &#40;Data Mining-Client für Excel&#41;](trace-data-mining-client-for-excel.md)  
 Klicken Sie auf Ablauf **Verfolgung** , um eine fortlaufende Erfassung der Interaktion zwischen dem Excel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Client und dem-Server anzuzeigen. Alle Aktivitäten werden als DMX- oder XMLA-Anweisungen gespeichert, sodass Sie Probleme in Ihrer Data Mining-Sitzung behandeln oder die Informationen zur späteren Verwendung speichern können.  
  
 [Herstellen einer Verbindung mit einem Data Mining-Server](connect-to-a-data-mining-server.md)  
 Wenn Sie Excel als Client für das Data Mining verwenden möchten, müssen Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen. Mithilfe der Verbindung können Sie auf die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Engine zugreifen. Mit den entsprechenden Berechtigungen lassen sich über die Verbindung alle entdeckten Muster speichern sowie vorhandene Data Mining-Objekte ändern.  
  
 Die Symbolleiste **Verbindungen** stellt Assistenten zum Verwalten von Verbindungen mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Instanz von bereit. Sie müssen eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] definieren, um die Data Mining-Tools und -Algorithmen zu verwenden. Sie können die Verbindung beim Installieren des Add-Ins erstellen oder später hinzufügen.  
  
 **Erste Schritte**  
 Klicken Sie **auf die Schalt** Fläche erste Schritte, um einen Konfigurations-Assistenten zu starten, der Sie durch die Erstellung einer Verbindung [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]mit einer Instanz von führt und die Berechtigungen erhält, die für die Data Mining erforderlich sind.  
  
 **Hilfe**  
 Das Dropdown Menü **Hilfe** enthält Links zu Online Hilfe, Websites und einen Konfigurations-Assistenten, mit dem Sie das Setup ausführen und Data Mining starten können.  
  
 Die Hilfeseite bietet zudem Links zu Onlineressourcen (u. a. zur Hilfe für das Add-In) sowie zusätzliche Videos, Demos und Beispiele.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenanalyse Tools für Excel](table-analysis-tools-for-excel.md)   
 [Problembehandlung bei Visio Data Mining-Diagrammen &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
