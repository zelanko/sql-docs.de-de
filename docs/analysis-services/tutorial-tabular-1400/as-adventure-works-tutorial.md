---
title: Analysis Services Adventure Works Internet Sales-Tutorial (1400) | Microsoft-Dokumentation
ms.date: 05/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 39d4c0e19d89438aa08ff2f7ead24184196d5412
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65503277"
---
# <a name="adventure-works-internet-sales-tutorial-1400"></a>Adventure Works Internet Sales-Tutorial (1400)

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dieses Lernprogramm enthält Lektionen zum Erstellen und Bereitstellen eines tabellarischen Modells mit dem [Kompatibilitätsgrad 1400](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md). Wenn Sie mit Analysis Services und tabellarischer Modellierung noch nicht vertraut sind, ist dieses Tutorial am schnellsten erfahren Sie, wie zum Erstellen und Bereitstellen eines einfachen tabellarischen Modells mithilfe von Visual Studio. Nachdem Sie die erforderlichen Komponenten haben direkte, sollten sie zwei bis drei Stunden in Anspruch nehmen.  
  
## <a name="what-you-learn"></a>Ihre Lernziele   
  
-   Vorgehensweise: Erstellen Sie ein neues tabellarisches Modellprojekt auf das **Kompatibilitätsgrad 1400** in Visual Studio mit SSDT.
  
-   Importieren von Daten aus einer relationalen Datenbank in eine arbeitsbereichsdatenbank für tabellarische Modelle-Projekt.  
  
-   Erstellen und Verwalten von Beziehungen zwischen Tabellen im Modell.  
  
-   Vorgehensweise: Erstellen von berechneten Spalten, Measures und Key Performance Indicators, mit denen Benutzer kritische Geschäftsmetrik zu analysieren.  
  
-   So erstellen und Verwalten von Perspektiven und Hierarchien, die Benutzern, die weitere einfacher Modelldaten durchsuchen, durch die Bereitstellung von Geschäfts- und anwendungsspezifische Blickpunkte helfen.  
  
-   Erstellen von Partitionen, mit denen sich Tabellendaten in kleinere logische Teile aufteilen lassen, die unabhängig von anderen Partitionen verarbeitet werden können.  
  
-   Sichern von Modellobjekten und -daten durch die Erstellung von Rollen mit Benutzerelementen.  
  
-   Gewusst wie: Bereitstellen ein tabellarisches Modells zu einer **Azure Analysis Services** Server oder **SQL Server 2017 Analysis Services** Server mithilfe von SSDT.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Um dieses Tutorial abzuschließen, müssen wie folgt vor:  
  
-   Azure Analysis Services-Servers oder einer SQL Server 2017 Analysis Services-Server im tabellarischen Modus. Melden Sie sich für ein kostenloses [Azure Analysis Services-Testversion](https://azure.microsoft.com/services/analysis-services/) und [erstellen Sie einen Server](https://docs.microsoft.com/azure/analysis-services/analysis-services-create-server) oder Herunterladen einer kostenlosen [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).

-   Ein [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/create-data-warehouse-portal) mit der **AdventureWorksDW-Beispieldatenbank**, oder eine lokale SQL Server Data Warehouse mit einer [Beispieldatenbank "AdventureWorksDW"](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Bei der Installation einer Datenbank "AdventureWorksDW" zu einer lokalen SQL Server-Data Warehouse. verwenden Sie die Version der Beispiel-Datenbank, die entspricht mit Ihrer Version des Servers. 

    **Wichtig:** Wenn Sie die Beispieldatenbank auf einer lokalen SQL Server-Data Warehouse installieren und Ihres Modells mit einem Azure Analysis Services-Server bereitstellen eine [On-Premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) ist erforderlich.

-   Die neueste Version des [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx). Oder, wenn Sie bereits Visual Studio 2017 verfügen, können Sie herunterladen und installieren [Microsoft Analysis Services-Projekten](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) -Paket (VSIX). In diesem Tutorial werden die Verweise auf SSDT und Visual Studio synonym verwendet. 

-   Die neueste Version des [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).    

-   Eine Clientanwendung wie z. B. [Power BI Desktop](https://powerbi.microsoft.com/desktop/) oder Excel. 

## <a name="scenario"></a>Szenario  

In diesem Tutorial basiert auf Adventure Works Cycles, einem fiktiven Unternehmen. Adventure Works ist ein großes, multinationales Fertigungsunternehmen, die produziert und vertreibt Fahrräder, Teile und Zubehör für kommerzielle Märkte in Nordamerika, Europa und Asien. Das Unternehmen beschäftigt 500 Arbeiter. Zusätzlich beschäftigt Adventure Works mehrere regionale Vertriebsteams gesamte marktbasis. Ihr Projekt ist, erstellen Sie ein tabellarisches Modell für Benutzer Vertriebs- und Marketingteams internetverkaufsdaten in der AdventureWorksDW-Datenbank zu analysieren.  
  
Um das Tutorial abschließen zu können, müssen Sie verschiedene Lektionen abschließen. In der jeweiligen Lektion gibt es Aufgaben. Aufgaben nacheinander abschließen muss zum Abschließen der Lektion. Während in einer bestimmten Lektion gibt es möglicherweise mehrere Aufgaben, die einem ähnlichen Ergebnis zu erreichen, aber wie Sie jede Aufgabe etwas anders ist. Diese Methode zeigt, dass es oft mehr als eine Möglichkeit zum Abschluss einer Aufgabe, und sollen Sie Fähigkeiten einsetzen, die Sie in vorherigen Lektionen und Aufgaben gelernt haben.  
  
Der Zweck der Lektionen werden Sie schrittweise durch das Erstellen eines einfachen tabellarischen Modells mithilfe von vielen in SSDT beinhalteten. Da jede Lektion auf der jeweils vorherigen Lektion aufbaut, sollten Sie die Lektionen in der entsprechenden Reihenfolge bearbeiten.
  
Dieses Tutorial bietet keine Lektionen zur Verwaltung eines Servers im Azure-Portal Verwalten von einem Server oder Datenbank mit SSMS oder mithilfe einer Clientanwendung auf um Modelldaten zu durchsuchen. 


## <a name="lessons"></a>Lektionen  

Dieses Tutorial umfasst die folgenden Lektionen:  
  
|Lektion|Für den Abschluss voraussichtlich benötigte Zeit|  
|----------|------------------------------|  
|[1: Erstellen eines neuen tabellarischen modellprojekts](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)|10 Minuten|  
|[2: Get Data](../tutorial-tabular-1400/as-lesson-2-get-data.md)|10 Minuten|  
|[3: Als Datumstabelle markieren](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md)|3 Minuten|  
|[4: Beziehungen erstellen](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)|10 Minuten|  
|[5: Erstellen von berechneten Spalten](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md)|15 Minuten|
|[6: Erstellen von Measures](../tutorial-tabular-1400/as-lesson-6-create-measures.md)|30 Minuten|  
|[7: Erstellen von Key Performance Indicators (KPI)](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md)|15 Minuten|  
|[8: Erstellen von Perspektiven](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md)|5 Minuten|  
|[9: Erstellen von Hierarchien](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)|20 Minuten|  
|[10: Erstellen von Partitionen](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)|15 Minuten|  
|[11: Erstellen von Rollen](../tutorial-tabular-1400/as-lesson-11-create-roles.md)|15 Minuten|  
|[12: Analysieren in Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)|5 Minuten| 
|[13: Bereitstellen](../tutorial-tabular-1400/as-lesson-13-deploy.md)|5 Minuten|  
  
## <a name="supplemental-lessons"></a>Ergänzende Lektionen  

Diese Lektionen sind nicht erforderlich, um das Lernprogramm abzuschließen, aber bei der besseren Verständnis erweiterte Erstellung tabellarischer Modelle Funktionen hilfreich sein können.  
  
|Lektion|Für den Abschluss voraussichtlich benötigte Zeit|  
|----------|------------------------------|  
|[Detailzeilen](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)|10 Minuten|
|[Dynamische Sicherheit](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)|30 Minuten|
|[Unregelmäßige Hierarchien](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)|20 Minuten| 

  
## <a name="next-steps"></a>Nächste Schritte  

Informationen zum Einstieg finden Sie unter [Lektion 1: Erstellen ein neuen tabellarischen modellprojekts](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md).  
  
  
  

