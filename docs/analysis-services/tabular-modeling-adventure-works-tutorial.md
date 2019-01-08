---
title: Analysis Services-tabellarische Modellierung (Kompatibilitätsgrad 1200) | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43ef5c290e1234af4482f09f2ec7f01e2edbca99
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072177"
---
# <a name="tabular-modeling-1200-compatibility-level"></a>Tabellarische Modellierung (Kompatibilitätsgrad 1200)
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Dieses Lernprogramm enthält Lektionen zum Erstellen Sie eines tabellarischen Analysis Services-Modells mit den [Kompatibilitätsgrad 1200](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md) mit [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt), und Ihr Modell in einer Analysis Services bereitstellen. lokal oder in Azure.  
 
Wenn Sie SQL Server 2017 oder Azure Analysis Services verwenden, und Sie möchten Ihr Modell auf den Kompatibilitätsgrad 1400 Ebene erstellen, verwenden die [tabellarische Modellierung (Kompatibilitätsgrad 1400)](tutorial-tabular-1400/as-adventure-works-tutorial.md). Diese aktualisierte Version der moderne datenabruffeature zum Verbinden und Importieren von Daten verwendet, verwendet die M-Sprache zum Konfigurieren von Partitionen und umfasst zusätzliche ergänzende Lektionen.

> [!IMPORTANT]
> Sie sollten Ihren tabellarischen Modellen mit dem aktuellen, vom Server unterstützten Kompatibilitätsgrad erstellen. Weiter unten auf Kompatibilität-Modelle bieten verbesserte Leistung, weitere Features, und führen ein upgrade auf zukünftige Kompatibilitätsgraden zusammen.
 
  
## <a name="what-you-learn"></a>Ihre Lernziele   
  
-   Vorgehensweise: erstellen ein neuen tabellenmodellprojekts in SSDT.
  
-   Importieren von Daten von einer relationalen SQL Server-Datenbank in ein Tabellenmodellprojekt.  
  
-   Erstellen und Verwalten von Beziehungen zwischen Tabellen im Modell.  
  
-   Erstellen und Verwalten von Berechnungen, Measures und Key Performance Indicators, mit denen Benutzer Modelldaten analysieren können.  
  
-   So erstellen und Verwalten von Perspektiven und Hierarchien, die Benutzern, die weitere einfacher Modelldaten durchsuchen, durch die Bereitstellung von Geschäfts- und anwendungsspezifische Blickpunkte helfen.  
  
-   Gewusst wie: Erstellen Sie Partitionen Division Tabellendaten in kleinere logische Teile, die unabhängig von anderen Partitionen verarbeitet werden können.  
  
-   Sichern von Modellobjekten und -daten durch die Erstellung von Rollen mit Benutzerelementen.  
  
-   Ein tabellarisches Modell auf einem Analysis Services Server lokal oder in Azure bereitstellen  
  
## <a name="scenario"></a>Szenario  
In diesem Tutorial basiert auf Adventure Works Cycles, einem fiktiven Unternehmen. Adventure Works ist ein großes, multinationales Unternehmen, das Fahrräder, Teile und Zubehör für kommerzielle Märkte in Nordamerika, Europa und Asien produziert. Mit Hauptsitz in Bothell, Washington und das Unternehmen 500 Arbeiter beschäftigt. Zusätzlich beschäftigt Adventure Works mehrere regionale Vertriebsteams gesamte marktbasis.  
  
Um die Datenanalyseanforderungen von Verkaufs- und Marketingteams sowie des Senior Managements besser zu unterstützen, werden Sie damit beauftragt, ein Tabellenmodell für Benutzer zu erstellen, um Internetumsatzdaten in der AdventureWorksDW-Beispieldatenbank zu analysieren.  
  
Um das Lernprogramm und das Tabellenmodell für die Adventure Works-Internetverkäufe abzuschließen, ist eine Reihe von Lektionen auszuführen. In der jeweiligen Lektion ist eine Reihe von Aufgaben. Aufgaben nacheinander abschließen muss zum Abschließen der Lektion. Während in einer bestimmten Lektion gibt es möglicherweise mehrere Aufgaben, die einem ähnlichen Ergebnis zu erreichen, aber wie Sie jede Aufgabe etwas anders ist. So wird verdeutlicht, dass es häufig mehr als eine Möglichkeit, um eine bestimmte Aufgabe abzuschließen, und sollen Sie Fähigkeiten einsetzen, die in vorherigen Aufgaben haben Sie gelernt haben.  
  
Der Zweck der Lektionen wird durch ein einfaches tabellarisches Modell im In-Memory-Modus ausgeführt wird, mithilfe von vielen in SSDT beinhalteten erstellen. Da jede Lektion auf der jeweils vorherigen Lektion aufbaut, sollten Sie die Lektionen in der entsprechenden Reihenfolge bearbeiten. Nachdem Sie alle Lektionen abgeschlossen haben, haben Sie erstellt und das beispieltabellenmodell von Adventure Works-Internetverkäufe auf einem Analysis Services-Server bereitgestellt.  
  
Dieses Lernprogramm enthält keine Lektionen oder Informationen zum Verwalten einer Datenbank für Tabellenmodelle unter Verwendung von SQL Server Management Studio oder das Verwenden einer Berichterstellungs-Clientanwendung zur Herstellung einer Verbindung mit einem bereitgestellten Modell zum Durchsuchen von Modelldaten.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Um dieses Tutorial abzuschließen, benötigen Sie Folgendes ein:  
  
-   Die neueste Version des [SSDT](../ssdt/download-sql-server-data-tools-ssdt.md).

-   Die neueste Version von SQL Server Management Studio. [Abrufen der neuesten Version](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 
  
-   Eine Clientanwendung wie z. B. [Power BI Desktop](https://powerbi.microsoft.com/desktop/) oder Excel.    
  
-   SQL Server-Instanz mit der Adventure Works DW-Beispieldatenbank. Diese Beispieldatenbank beinhaltet die für das Abschließen des Lernprogramms notwendigen Daten. [Abrufen der neuesten Version](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  

-   Ein Azure Analysis Services oder SQL Server 2016 oder höher Analysis Services-Instanz an Ihr Modell bereitstellen. [Melden Sie sich für eine kostenlose Testversion von Azure Analysis Services](https://azure.microsoft.com/services/analysis-services/).
  
## <a name="lessons"></a>Lektionen  
Dieses Tutorial umfasst die folgenden Lektionen:  
  
|Lektion|Für den Abschluss voraussichtlich benötigte Zeit|  
|----------|------------------------------|  
|[Lektion 1: Erstellen eines neuen tabellarischen Modellprojekts](../analysis-services/lesson-1-create-a-new-tabular-model-project.md)|10 Minuten|  
|[Lektion 2: Hinzufügen von Daten](../analysis-services/lesson-2-add-data.md)|20 Minuten|  
|[Lektion 3: Markieren als Datumstabelle](../analysis-services/lesson-3-mark-as-date-table.md)|3 Minuten|  
|[Lektion 4: Erstellen von Beziehungen](../analysis-services/lesson-4-create-relationships.md)|10 Minuten|  
|[Lektion 5: Erstellen von berechneten Spalten](../analysis-services/lesson-5-create-calculated-columns.md)|15 Minuten|
|[Lektion 6: Erstellen von Measures](../analysis-services/lesson-6-create-measures.md)|30 Minuten|  
|[Lektion 7: Erstellen von Key Performance Indicators](../analysis-services/lesson-7-create-key-performance-indicators.md)|15 Minuten|  
|[Lektion 8: Erstellen von Perspektiven](../analysis-services/lesson-8-create-perspectives.md)|5 Minuten|  
|[Lektion 9: Erstellen von Hierarchien](../analysis-services/lesson-9-create-hierarchies.md)|20 Minuten|  
|[Lektion 10: Erstellen von Partitionen](../analysis-services/lesson-10-create-partitions.md)|15 Minuten|  
|[Lektion 11: Erstellen von Rollen](../analysis-services/lesson-11-create-roles.md)|15 Minuten|  
|[Lektion 12: In Excel analysieren](../analysis-services/lesson-12-analyze-in-excel.md)|20 Minuten| 
|[Lektion 13: Bereitstellen](../analysis-services/lesson-13-deploy.md)|5 Minuten|  
  
## <a name="supplemental-lessons"></a>Ergänzende Lektionen  
Dieses Tutorial umfasst außerdem [ergänzende Lektionen](http://msdn.microsoft.com/library/2018456f-b4a6-496c-89fb-043c62d8b82e). Die Themen in diesem Abschnitt sind nicht erforderlich, um das Lernprogramm abzuschließen, aber sie können das Verständnis der erweiterten Funktionen zum Erstellen eines Tabellenmodells erleichtern.  
  
|Lektion|Für den Abschluss voraussichtlich benötigte Zeit|  
|----------|------------------------------|  
|[Implementieren von dynamischer Sicherheit mithilfe von Zeilenfiltern](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md)|30 Minuten|  

  
## <a name="next-step"></a>Nächster Schritt  
Um das Lernprogramm zu starten, fahren Sie mit der ersten Lektion fort: [Lektion 1: Erstellen ein neuen tabellarischen Modellprojekts](../analysis-services/lesson-1-create-a-new-tabular-model-project.md).  
  
  
  

