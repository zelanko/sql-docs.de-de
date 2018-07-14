---
title: Datamining-Client für Excel (SQL Server Data Mining-Add-ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Data Mining Client
- wizards
- getting started
ms.assetid: e075e2de-11cc-4f71-9603-0b161bca8a24
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 78a71f5fed5bfcc46742f8554ff69329c3a30b0d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257506"
---
# <a name="data-mining-client-for-excel-sql-server-data-mining-add-ins"></a>Data Mining-Client für Excel (SQL Server Data Mining-Add-Ins)
  Der Data Mining-Client für Excel umfasst eine Reihe von Tools, mit denen Sie häufige Data Mining-Aufgaben ausführen können – von der Datenbereinigung bis hin zur Modellerstellung und Vorhersageabfragen. Sie können Daten in Excel-Tabellen oder Bereichen verwenden oder auf externe Datenquellen zugreifen.  
  
 ![DM](media/dm-tabletools.gif "DM")  
  
-   [Arbeiten mit Daten](#bkmk_Data)  
  
     Laden Sie die Daten in Excel, bereinigen Sie die Daten, suchen Sie nach Ausreißern, und erstellen Sie statistische Zusammenfassungen. Sie können auch verschiedene Arten von Stichproben ausführen, Datenprofile erstellen und Modelle mithilfe externer Daten testen. Mit dem Data Mining-Client können Sie Daten einfach ohne komplexe Skripts oder ETL-Prozesse für die Analyse vorbereiten.  
  
-   [Erstellen von Modellen und analysieren](#bkmk_Model)  
  
     Diese Tools bieten Assistentenschnittstellen zu bekannten, empirisch getesteten Data Mining-Algorithmen, einschließlich Clustering (K-Means und EM), Zuordnungsanalyse, Zeitreihenanalyse und Entscheidungsstrukturen. Durch erweiterte Modellierungsoptionen für jeden Assistenten können Sie verschiedene Algorithmen auswählen (wie Naive Bayes oder neuronale Netzwerke) und das Verhalten anpassen (wie Cluster-Ausgangswert oder ursprüngliche Stichprobengröße).  
  
     Alle Data Mining-Algorithmen werden in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], sodass Ihnen das Erstellen komplexer Modelle erleichtert wird.  
  
-   [Testen, Abfragen und Validieren von Modellen](#bkmk_Validate)  
  
     Der Data Mining-Client stellt Tools nach Industriestandard zum Testen von Modellen bereit, einschließlich Prognosegütediagramme und Kreuzvalidierung. Die Assistenten, die bereitgestellt werden, vereinfachen das Testen der Gültigkeit des Datasets und seiner Genauigkeit. Der Abfrage-Assistent erstellt Abfragen, um die Modelle für Vorhersagen und Bewertungen zu verwenden.  
  
-   [Anzeigemodelle](#bkmk_ViewModels)  
  
     Diagramme, die von den meisten Tools generiert werden, können direkt in Excel gespeichert werden. Verwenden der [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41; ](browsing-models-in-excel-sql-server-data-mining-add-ins.md) Tool, um Modelle zu untersuchen.  
  
-   [Verwalten Sie, dokumentieren und bereitstellen](#bkmk_UsageMgmt)  
  
     Der Data Mining-Client für Excel verfügt über eine aktive Verbindung mit dem Server, sodass Sie das Data Mining-Modell auf dem Server speichern können, um es weiteren Tests zu unterziehen oder um es für größere Skalierbarkeit auf einem Produktionsserver bereitzustellen.  
  
##  <a name="bkmk_Data"></a> Arbeiten mit Daten  
 Die **Datenvorbereitung** Gruppe enthält die folgenden Assistenten, mit denen Sie überprüfen und Bereinigen von Daten als Vorbereitung für Datamining-Tasks. Darüber hinaus können Sie mit den meisten Assistenten Daten in Trainings- und Testsätze trennen.  
  
 [Durchsuchen von Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 Zum Erstellen und Speichern von Modellen unterstützen die Add-Ins die folgenden Datenverbindungen:  
  
-   Verbindung mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server zum Speichern und Verarbeiten der Modelle.  
  
-   Optionale Verbindungen mit externen Datenquellen. Sie können Ihr Modell mit einem beliebigen Typ von Daten erstellen, die als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle definiert werden können. Sie können jedoch auch einfach die Daten verwenden, die bereits in Excel enthalten sind.  
  
 [Durchsuchen von Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 Die **Stichprobenoptionen** Assistenten können Sie den Typ und die Menge der Daten in der Datentabelle, die anhand von Diagrammen, die Verteilung und Werte für die ausgewählten Spalten nacheinander zu verstehen.  
  
 [Beispieldaten &#40;SQL Server Data Mining-Add-ins&#41;](sample-data-sql-server-data-mining-add-ins.md)  
 Das Erstellen der richtigen Daten zum Trainieren und Testen Ihrer Modelle ist ein wichtiger Bestandteil beim Data Mining. Ohne die richtigen Tools kann diese Aufgabe jedoch mühsam sein. Die **Beispieldaten** Assistent erleichtert das Aufteilen die Daten, die für ein Modell in zwei Gruppen, für das Erstellen des Modells und eine zum Testen verwendet. Sie können zufällige Stichproben nehmen oder Überquotierung anwenden.  
  
 [Vorhersagerechner &#40;Tabellenanalysetools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Die **Ausreißerentfernungs** Assistent bietet mehrere Tools, um zu identifizieren und entsprechend behandeln von Ausreißern. Er zeigt die Verteilung der Werte sowie die Beziehung zwischen Ausreißern und anderen Daten auf. Sie können entscheiden, ob Ausreißer entfernt oder geändert werden sollen.  
  
 [Vorhersagerechner &#40;Tabellenanalysetools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Die **neu bezeichnen** Assistenten können Sie neue Bezeichnungen für Daten zu erleichtern, die Ergebnisse der Analyse übersichtlicher zu erstellen. Beispielsweise können Sie einem Datenbereich einen aussagekräftigeren Namen geben oder einen repräsentativen Wert aus der Liste auswählen.  
  
##  <a name="bkmk_Model"></a> Erstellen von Modellen und analysieren  
 Die Optionen auf der **Datenmodellierung** Abschnitt der Symbolleiste können Sie die Muster aus Daten ableiten, Gruppieren von Zeilen von Daten anhand von Attributen oder Zuordnungen durchsuchen. Die Assistenten auf diesem Menüband basieren auf den leistungsfähigen Data Mining-Algorithmen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Anders als mit den vergleichbaren Tabellenanalysetools für Excel können Sie mit diesen Assistenten das Verhalten der Algorithmen anpassen und eine Vielzahl von Datenquellen nutzen.  
  
 [Assistent zum Klassifizieren &#40;Data Mining-Add-ins für Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
 Die **klassifizieren** Assistenten können Sie ein klassifizierungsmodell auf Basis vorhandener Daten in einer Excel-Tabelle, einem Excel-Bereich oder einer externen Datenquelle zu erstellen. Mit einem Klassifizierungsmodell werden Muster in den Daten extrahiert, die auf Übereinstimmungen hinweisen. So können Sie Vorhersagen basierend auf Wertgruppen treffen. Ein Klassifizierungsmodell kann beispielsweise verwendet werden, um das Risiko auf der Grundlage von Einkommens- und Konsummustern vorherzusagen.  
  
 Die **klassifizieren** -Assistent unterstützt die Verwendung der folgenden Datamining-Algorithmen von Microsoft: Decision Trees-Algorithmus die logistische Regression, Naïve Bayes, neuronaler Netzwerke.  
  
 [Assistent zum Schätzen von &#40;Data Mining-Add-ins für Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
 Die **Schätzung** Assistenten können Sie ein schätzmodell zu erstellen. Ein Schätzmodell extrahiert Datenmuster und verwendet diese, um ein numerisches Ergebnis (z. B. eine Währung, einen Umsatz, ein Datum oder eine Uhrzeit) vorherzusagen.  
  
 Die **Schätzung** -Assistent verwendet diese Datamining-Algorithmen von Microsoft: Decision Trees, Linear Regression, logistische Regression und Neural Networks.  
  
 [Wichtige Einflussfaktoren analysieren &#40;Tabellenanalysetools für Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Der Cluster-Assistent unterstützt Sie beim Erstellen eines Clusteringmodells. Ein Clustermodell erkennt Gruppen von Zeilen mit ähnlichen Merkmalen. Dieser Assistent ist hilfreich beim Durchsuchen von Mustern in sämtlichen Daten.  
  
 Die **Cluster** -Assistent verwendet den Microsoft Clustering-Algorithmus, der sowohl K-Means und EM enthält.  
  
 [Zuordnungs-Assistent &#40;Datamining-Client für Excel&#41;](associate-wizard-data-mining-client-for-excel.md)  
 Die **zuordnen** Assistent hilft Ihnen beim Erstellen einer Datamining-Modell mithilfe des Microsoft Association Rules-Algorithmus, der häufig gemeinsam auftretende Elemente oder Ereignisse erkennt. Solche Zuordnungsmodelle sind besonders nützlich, wenn Sie Empfehlungen aussprechen möchten.  
  
 Die **zuordnen** -Assistent verwendet den Microsoft Association Rules-Algorithmus.  
  
 [Planungs-Assistent &#40;Data Mining-Add-ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
 Die **prognostizieren** Assistenten können Sie die Werte in einer Zeitreihe Vorhersagen. In der Regel enthalten in einer Vorhersage verwendete Daten eine Art von Zeitreihen, entweder einen Datumsstempel oder eine Sequenz ID, anhand derer Muster für die Vorhersage künftiger Werte abgeleitet werden.  
  
 Die **prognostizieren** -Assistent verwendet den Microsoft Time Series-Algorithmus.  
  
 [Erweiterte Modellierung &#40;Data Mining-Add-ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
 Sind Sie bereits vertraut mit dem Data Mining? Sie können die **erweitert** datenmodellierungsoptionen zum Erstellen benutzerdefinierte Datenstrukturen sowie Modelle mit Anpassungen, die nicht in den anderen Tools und Assistenten enthalten.  
  
##  <a name="bkmk_Validate"></a> Testen, Abfragen und Validieren von Modellen  
 Mithilfe der Assistenten auf der **Genauigkeit und Überprüfung** Symbolleiste branchenüblichen Tests zum Überprüfen der Genauigkeit Ihrer Modelle und für die Bewertung der Bewertung des Datasets zum Erstellen von Modellen verwendet.  
  
 [Wichtige Einflussfaktoren analysieren &#40;Tabellenanalysetools für Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Bewertet die Leistung eines Data Mining-Modells durch Erstellen eines Liftdiagramms oder Punktdiagramms.  
  
 [Klassifikationsmatrix &#40;SQL Server Data Mining-Add-ins&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
 Hilft beim Überprüfen der Leistung eines Klassifizierungsmodells durch Erstellen eines Diagramms, das genaue und ungenaue Vorhersagen des Modells zusammenfasst.  
  
 [Gewinndiagramm &#40;SQL Server Data Mining-Add-ins&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
 Hilft beim Einschätzen der Auswirkungen eines Data Mining-Modells, indem die Genauigkeit der Vorhersagen zusammen mit den Kosten und Vorteilen der daraufhin erfolgenden Maßnahmen analysiert werden.  
  
 [Übergreifende Überprüfung &#40;SQL Server Data Mining-Add-ins&#41;](cross-validation-sql-server-data-mining-add-ins.md)  
 Erstellt einen Bericht, der die Genauigkeit des Modells über viele Teilmengen eines Datasets hinweg zusammenfasst, sodass Sie die Stabilität des Modells beurteilen können.  
  
 Sie können Daten in einer Excel-Tabelle auch in einer Vorhersageabfrage für ein Miningmodell verwenden, das auf dem Server gespeichert ist.  
  
 [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md)  
 Die **Abfrage** Assistenten können Sie Vorhersagen für ein vorhandenes Datamining-Modell zu erstellen.  
  
 [Erweiterter Data Mining-Abfrage-Editor](advanced-data-mining-query-editor.md)  
 Für fortgeschrittene Benutzer bietet das Tool eine Drag & Drop-Schnittstelle zu DMX. Sie können auf einfache Weise Vorhersageabfragen oder neue Modelle erstellen, ohne dass Sie sich Gedanken über die Syntax machen müssen.  
  
##  <a name="bkmk_ViewModels"></a> Anzeigemodelle  
 Modelle, die Sie erstellen, werden zum Durchsuchen automatisch geöffnet. Sie können Modelle trotzdem auch auf dem Server durchsuchen und neue Visualisierungen generieren. Verwenden der [Visio-Shapes](viewing-data-mining-models-in-visio-data-mining-add-ins.md) um Modelldiagramme in einen anpassbaren Zeichenbereich zu exportieren.  
  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
 Zeigen Sie die erstellten Modelle mit interaktiven Diagrammen an, die für jeden Modelltyp angepasst sind.  
  
 [Dokumentieren von Miningmodellen &#40;Data Mining-Add-ins für Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)  
 Dieser Assistent erstellt Berichte mit einer statistischen Zusammenfassung des Datasets und Metadaten zum Modell, die die Untersuchung und Interpretation erleichtern.  
  
##  <a name="bkmk_UsageMgmt"></a> Verwalten Sie, dokumentieren und bereitstellen  
 Mithilfe dieser Tools können Sie eine Verbindung mit einem Data Mining-Server herstellen. Zudem ermöglichen sie das Verwalten und Exportieren von Modellen sowie das Überwachen von Data Mining-Aktivitäten.  
  
 [Verwalten von Modellen &#40;SQL Server Data Mining-Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md)  
 Wenn Sie über die erforderlichen Berechtigungen verfügen, können Sie vorhandene Miningmodelle und -strukturen löschen, ändern, umbenennen oder verarbeiten, ohne dazu Excel verlassen zu müssen.  
  
 [Ablaufverfolgung &#40;Datamining-Client für Excel&#41;](trace-data-mining-client-for-excel.md)  
 Klicken Sie auf **Ablaufverfolgung** an eine laufende Aufzeichnung der Interaktion zwischen dem Excel-Client und dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Server. Alle Aktivitäten werden als DMX- oder XMLA-Anweisungen gespeichert, sodass Sie Probleme in Ihrer Data Mining-Sitzung behandeln oder die Informationen zur späteren Verwendung speichern können.  
  
 [Herstellen einer Verbindung mit einem Data Mining-Server](connect-to-a-data-mining-server.md)  
 Wenn Sie Excel als Client für das Data Mining verwenden möchten, müssen Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen. Mithilfe der Verbindung können Sie auf die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Engine zugreifen. Mit den entsprechenden Berechtigungen lassen sich über die Verbindung alle entdeckten Muster speichern sowie vorhandene Data Mining-Objekte ändern.  
  
 Die **Verbindungen** Symbolleiste stellt Assistenten zum Verwalten von Verbindungen mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Sie müssen eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] definieren, um die Data Mining-Tools und -Algorithmen zu verwenden. Sie können die Verbindung beim Installieren des Add-Ins erstellen oder später hinzufügen.  
  
 **Erste Schritte**  
 Klicken Sie auf die **Einstieg** Schaltfläche, um einen Konfigurations-Assistenten zu starten, das Sie durch den Prozess zum Herstellen eine Verbindung mit einer Instanz von führt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], und die Berechtigungen, die erforderlichen Datamining zu arbeiten.  
  
 **Hilfe**  
 Die **Hilfe** Dropdown-Menü enthält Links zu Onlinehilfe, Websites und einen Konfigurations-Assistenten, die Ihnen helfen, einrichten und Starten von Datamining.  
  
 Die Hilfeseite bietet zudem Links zu Onlineressourcen (u. a. zur Hilfe für das Add-In) sowie zusätzliche Videos, Demos und Beispiele.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)   
 [Problembehandlung für Data Mining-Diagramme in Visio &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
