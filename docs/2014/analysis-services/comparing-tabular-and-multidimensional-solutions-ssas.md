---
title: Vergleichen von tabellarischen und mehrdimensionalen Lösungen (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 76ee5e96-6a04-49af-a88e-cb5fe29f2e9a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1da4224387e70ccc76e069aa3ce411dddb79b805
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087773"
---
# <a name="comparing-tabular-and-multidimensional-solutions-ssas"></a>Vergleichen von tabellarischen und mehrdimensionalen Lösungen (SSAS)
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]bietet zwei unterschiedliche Ansätze für die Datenmodellierung: tabellarisch und mehrdimensional. Zwar gibt es erhebliche Überschneidungen, aber auch wichtige Unterschiede, die Ihre Entscheidung zur weiteren Vorgehensweise beeinflussen. In diesem Thema werden verschiedene Funktionen verglichen und erklärt, wie jeder Ansatz allgemeine Projektanforderungen erfüllt. Spielt beispielsweise die Unterstützung einer bestimmten Datenquelle eine wichtige Rolle, kann der Abschnitt zu Datenquellen bei der Entscheidung über den geeigneten Modellierungsansatz hilfreich sein.  
  
 Dieses Thema enthält die folgenden Abschnitte:  
  
-   [Übersicht über die Modellierung in Analysis Services](#bkmk_overview)  
  
-   [Datenquellenunterstützung nach Lösungstyp](#bkmk_ds)  
  
-   [Modell Funktionen](#bkmk_models)  
  
-   [Modellgröße](#bkmk_modelsize)  
  
-   [Programmierbarkeit und Möglichkeiten für Entwickler](#bkmk_ext)  
  
-   [Unterstützung für Abfrage und Skriptsprache](#bkmk_lang)  
  
-   [Unterstützung für Sicherheitsfunktionen](#bkmk_sec)  
  
-   [Entwurfs Tools](#bkmk_designer)  
  
-   [Client- und Berichterstellungsanwendungen](#bkmk_client)  
  
-   [Hostingplattformen](#bkmk_sharePoint)  
  
-   [Serverbereitstellungsmodi für mehrdimensionale und tabellarische Lösungen](#bkmk_deploymentmode)  
  
-   [Nächster Schritt: Erstellen einer Lösung](#bkmk_Next)  
  
 Weitere Informationen finden Sie im folgenden Fachartikel auf MSDN: [Auswählen einer tabellarischen oder mehrdimensionalen Modellierungserfahrung in SQL Server 2012 Analysis Service](https://go.microsoft.com/fwlink/?LinkId=251588).  
  
##  <a name="overview-of-modeling-in-analysis-services"></a><a name="bkmk_overview"></a>Übersicht über die Modellierung in Analysis Services  
 Analysis Services bietet sowohl eine Modellentwicklungsumgebung als auch die Modellbereitstellung über Datenbankhosting auf einer Analysis Services-Instanz. Es gibt tabellarische und mehrdimensionale Modelltypen. Wie zu erwarten, unterstützt Datenbankhosting die tabellarischen und mehrdimensionalen Lösungen, die Sie erstellen, aber es enthält auch PowerPivot für SharePoint.  
  
 PowerPivot für SharePoint ist *Analysis Services im SharePoint-Modus*. Dabei fungiert Analysis Services als zusätzlicher Dienst für SharePoint, der zum Hosten und Verwalten von Excel-Datenmodellen beiträgt, die zuvor in Excel erstellt und anschließend in SharePoint gespeichert wurden. Die Rolle von Analysis Services in diesem Kontext besteht darin, das Datenmodell in den Arbeitsspeicher zu laden, Daten aus externen Datenquellen zu aktualisieren und Abfragen für das Modell auszuführen. In dieser Konfiguration arbeitet Analysis Services im Hintergrund. Alle Verbindungen und Anforderungen für Analysis Services werden von SharePoint ausgeführt und zwar nur, wenn eine Excel-Arbeitsmappe ein Datenmodell enthält (Datenmodelle sind in Excel-Arbeitsmappen optional). Wenn Sie ein Datenmodell in Excel entwickeln und in SharePoint Hosting, richtet sich nach den Projektanforderungen. Weitere Informationen finden Sie unter [Power Pivot: leistungsstarke Datenanalyse und Datenmodellierung in Excel](https://support.office.com/en-ie/article/Power-Pivot-Powerful-data-analysis-and-data-modeling-in-Excel-d7b119ed-1b3b-4f23-b634-445ab141b59b) und [PowerPivot für SharePoint &#40;SSAS-&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md) .  
  
> [!NOTE]  
>  Excel-Datenmodelle und tabellarische Modelle sind architektonisch ähnlich. Sie können ein Excel-Datenmodell in ein tabellarisches Modell importieren, wenn Sie größere Datenmengen unterstützen oder andere Modellfunktionen verwenden müssen, die in Excel nicht zur Verfügung stehen.  
  
 Tabellarische und mehrdimensionale Lösungen werden mit [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] erstellt und sind für BI-Unternehmensprojekte bestimmt, die auf einer eigenständigen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz ausgeführt werden. Beide Lösungen stellen hochleistungsfähige analytische Datenbanken bereit, die einfach mit Excel, Reporting Services-Berichten und andere BI-Anwendungen von Microsoft und Drittanbietern integriert werden können. Beide Lösungen führen zu eigenständigen Datenbanken, die von allen Clientanwendungen verwendet werden können, die Analysis Services unterstützen.  
  
 Die Unterschiede zwischen tabellarischen und mehrdimensionalen Modellen können auf allgemeiner Ebene wie folgt beschrieben werden:  
  
-   Mehrdimensionale und Data Mining-Lösungen verwenden OLAP-Modellierungskonstrukte (Cubes und Dimensionen) und MOLAP-, ROLAP- oder HOLAP-Speicherung, die die Festplatte als primären Datenspeicher für vorab aggregierte Daten verwenden.  
  
-   Tabellarische Lösungen basieren auf relationalen Modellierungskonstrukten wie Tabellen und Beziehungen zur Datenmodellierung sowie auf der Engine für die Datenanalyse im Arbeitsspeicher, die zum Speichern und Berechnen von Daten eingesetzt wird. Das Modell wird zum größten Teil oder ganz im Arbeitsspeicher gespeichert und ist oft schneller als sein mehrdimensionales Gegenstück.  
  
 Bei neuen Projekten sollten Sie zuerst das tabellarische Modell in Betracht ziehen. Es bietet schnellere Entwicklung, Testverfahren und Bereitstellung und arbeitet reibungsloser mit den neuesten Self-Service-BI-Anwendungen von Microsoft zusammen.  
  
##  <a name="data-source-support-by-solution-type"></a><a name="bkmk_ds"></a>Datenquellen Unterstützung nach Lösungstyp  
 Mehrdimensionale und tabellarische Modelle verwenden importierte Daten aus externen Quellen. Die meisten Entwickler verwenden ein Data Warehouse, das Berichtsdatenstrukturen unterstützen soll, als primäre Datenquelle für ein Modell. Das Data Warehouse basiert häufig auf einem Stern- oder Schneeflockenschema, und Daten werden mithilfe von SSIS aus OLTP-Lösungen in das Data Warehouse geladen. Die Modellierung ist einfacher, wenn Sie ein Data Warehouse als Back-End-Datenquelle verwenden.  
  
|**Link**|**Zusammenfassung der unterstützten Optionen**|  
|--------------|--------------------------------------|  
|[Unterstützte Datenquellen &#40;mehrdimensionalen SSAS-&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md)|Mehrdimensionale Modelle verwenden Daten aus relationalen Datenquellen.|  
|[Unterstützte Datenquellen &#40;SSAS – tabellarisch&#41;](tabular-models/data-sources-supported-ssas-tabular.md)|Tabellarische Modelle unterstützen eine breitere Palette von Datenquellen, einschließlich Flatfiles, Datenfeeds und Datenquellen, auf die über ODBC-Datenanbieter zugegriffen wird.|  
  
 Bei beiden Modellierungsansätzen können Daten aus mehreren Datenquellen im gleichen Modell verwendet werden.  
  
 Wenn Ihre Lösung das Speichern von Modelldaten außerhalb des Modells in der relationalen Datenbank erfordert (diese Methode wird verwendet, wenn sehr umfangreiche Daten erforderlich sind), muss es sich bei der Datenquelle um eine relationale SQL Server-Datenbank handeln. Sowohl die ROLAP-Speicherung für mehrdimensionale Modelle als auch DirectQuery für tabellarische Modelle haben diese Anforderung.  
  
 **Datengröße**  
  
 Sowohl tabellarische als auch mehrdimensionale Lösungen verwenden die Datenkomprimierung, durch die die Größe der Analysis Services-Datenbank relativ zum Data Warehouse verringert wird, aus dem Sie Daten importieren. Da sich der tatsächliche Komprimierungsgrad nach den Eigenschaften der zugrunde liegenden Daten richtet, lässt sich nicht genau vorhersagen, wie viel Datenträger- und Arbeitsspeicherkapazität von einer Lösung benötigt wird, nachdem die Daten verarbeitet und in Abfragen verwendet wurden. Eine Faustregel, die von vielen Analysis Services-Entwicklern angewendet wird, besagt, dass der primäre Speicher einer mehrdimensionalen Datenbank ein Drittel der ursprünglichen Daten ausmachen sollte.  
  
 Tabellarische Datenbanken können manchmal einen höheren Komprimierungsgrad von etwa einem Zehntel der Größe erzielen. Dies gilt insbesondere dann, wenn die meisten Daten aus Faktentabellen importiert werden. Bei tabellarischen Lösungen sind die Arbeitsspeicheranforderungen im Vergleich zu der auf dem Datenträger benötigten Datenkapazität höher. Das liegt an den zusätzlichen Datenstrukturen, die beim Laden der tabellarischen Datenbank in den Arbeitsspeicher erstellt werden. Unter Belastung ist davon auszugehen, dass die Kapazitätsanforderungen sowohl an den Datenträger als auch an den Arbeitsspeicher steigen, weil Daten von Analysis Services zwischengespeichert, gespeichert, durchsucht und abgefragt werden.  
  
 Bei einigen Projekten können die Datenanforderungen so hoch sein, dass sie bei der Wahl des Modelltyps ins Gewicht fallen. Wenn sich der Umfang der zu ladenden Daten in der Größenordnung von mehreren Terabytes bewegt, erfüllt eine tabellarische Lösung die Anforderungen möglicherweise nicht, wenn der Arbeitsspeicher die Daten nicht aufnehmen kann. Auch wenn eine Auslagerungsoption dafür sorgt, dass Arbeitsspeicherdaten auf den Datenträger ausgelagert werden, sind mehrdimensionale Lösungen bei sehr großen Datenmengen zweckmäßiger. Die größten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Produktionsdatenbanken sind heute mehrdimensional. Weitere Informationen zu Speicherauslagerungsoptionen für tabellarische Lösungen finden Sie unter [Memory Properties](server-properties/memory-properties.md). Weitere Informationen zum Skalieren einer mehrdimensionalen Lösung finden Sie unter [Horizontale Skalierung bei Abfragen für Analysis Services mit schreibgeschützten Datenbanken](https://go.microsoft.com/fwlink/?LinkId=251711).  
  
##  <a name="model-features"></a><a name="bkmk_models"></a> Modellfunktionen  
 In der folgenden Tabelle wird die Funktionsverfügbarkeit auf der Modellebene zusammengefasst. Wenn Sie Analysis Services bereits installiert haben, können Sie die Funktionen des installierten Servermodus mithilfe dieser Informationen verstehen. Wenn Sie bereits in Analysis Services mit Modellfunktionen vertraut sind und die Geschäftsanforderungen eine oder mehrere dieser Funktionen einschließen, können Sie diese Liste überprüfen, um sicherzustellen, dass die zu verwendende Funktion im zu erstellenden Modelltyp verfügbar ist.  
  
 Eine Gegenüberstellung der Funktionen nach Modellierungsansatz finden Sie im technischen Artikel [Auswählen der tabellarischen oder mehrdimensionalen Modellierung in SQL Server 2012 Analysis Services](https://go.microsoft.com/fwlink/?LinkId=251588) auf MSDN.  
  
> [!NOTE]  
>  Die tabellarische Modellierung wird in bestimmten Editionen von SQL Server unterstützt. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
||||  
|-|-|-|  
||**Multidimensional**|**Arisches**|  
|Aktionen|[Ja](multidimensional-models/actions-in-multidimensional-models.md)|Nein|  
|Aggregationsobjekte|[Ja](multidimensional-models/designing-aggregations-analysis-services-multidimensional.md)|Nein|  
|Berechnete Measures|[Ja](multidimensional-models/create-calculated-members.md)|Ja|  
|Benutzerdefinierte Assemblys|[Ja](multidimensional-models/multidimensional-model-assemblies-management.md)|Nein|  
|Benutzerdefinierte Rollups|Ja|Nein |  
|Distinct Count|[Ja](multidimensional-models/use-aggregate-functions.md)|Ja (über DAX) *|  
|Drillthrough ausführen|[Ja](multidimensional-models/actions-in-multidimensional-models.md)|Ja|  
|Hierarchien|[Ja](multidimensional-models/user-defined-hierarchies-create.md)|Ja|  
|KPIs (Key Performance Indicators)|[Ja](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)|Ja|  
|Verknüpfte Measuregruppen|[Ja](multidimensional-models/linked-measure-groups.md)|Nein|  
|m:n-Beziehungen|[Ja](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)|Nein|  
|Über- und untergeordnete Hierarchien|[Ja](multidimensional-models/parent-child-dimension.md)|Ja (über DAX)|  
|Partitionen|[Ja](tabular-models/partitions-ssas-tabular.md)|  
|Perspektiven|[Ja](multidimensional-models/perspectives-in-multidimensional-models.md)|[Ja](tabular-models/partitions-ssas-tabular.md)|  
|Semiadditive Measures|[Ja](multidimensional-models/define-semiadditive-behavior.md)|Ja (über DAX)|  
|Translations|[Ja](multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|Nein|  
|Benutzerdefinierte Hierarchien|[Ja](multidimensional-models/user-defined-hierarchies-create.md)|Ja|  
|Rückschreiben|[Ja](multidimensional-models/set-partition-writeback.md)|Nein|  
  
 * Wenn Ihre Lösung eine sehr große Anzahl von unterschiedlichen Anzahlen (z. b. viele Millionen von Kunden-IDs) unterstützen muss, sollten Sie zuerst die tabellarische Tabelle Sie ist in diesem Szenario voraussichtlich leistungsfähiger. Weitere Informationen finden Sie im Abschnitt über Distinct Counts im Whitepaper [Analysis Services-Fallstudie: Verwenden von tabellarischen Modellen in umfangreichen kommerziellen Lösungen](https://msdn.microsoft.com/library/dn751533.aspx).  
  
##  <a name="model-size"></a><a name="bkmk_modelsize"></a>Modell Größe  
 Die Gesamtanzahl der Objekte wirkt sich bei den verschiedenen Lösungstypen nicht auf die Modellgröße aus. Allerdings sind die Entwurfstools, die zum Erstellen der einzelnen Lösungen eingesetzt werden, unterschiedlich gut zum Umgang mit einer großen Anzahl von Objekten geeignet. Ein umfangreicheres Modell ist in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] etwas einfacher zu erstellen, da diese Umgebung mehr Möglichkeiten für die Abbildung und Auflistung nach Objekttypen im Objekt-Explorer und Projektmappen-Explorer bietet.  
  
 Sehr große Modelle, die aus vielen Hunderten Tabellen oder Dimensionen bestehen, werden häufig programmgesteuert in Visual Studio erstellt und nicht mithilfe von Entwurfstools. Weitere Informationen zur maximalen Anzahl von Objekten in einem Modell finden Sie unter [Spezifikationen der maximalen Kapazität &#40;Analysis Services&#41;](multidimensional-models/olap-physical/maximum-capacity-specifications-analysis-services.md).  
  
##  <a name="programmability-and-developer-experience"></a><a name="bkmk_ext"></a>Programmierbarkeit und Entwickler Freundlichkeit  
 Für tabellarische und mehrdimensionale Modelle gibt es ein für beide Modalitäten freigegebenes Objektmodell. AMO und ADOMD.NET unterstützen beide Modi. Auch die Clientbibliothek wurde nicht auf tabellarische Konstrukte umgestellt. Sie müssen sich also vergegenwärtigen, wie sich mehrdimensionale und tabellarische Konstrukte und Benennungskonventionen aufeinander beziehen. Als erstes befassen Sie sich mit dem Programmierbeispiel, das Analysis Management Objects (AMO) in ein tabellarisches Modell überführt, um die AMO-Programmierung im Kontext tabellarischer Modellierung zu erlernen. Um weitere Informationen zu erhalten, laden Sie das Beispiel von der [Codeplex-Website](https://go.microsoft.com/fwlink/?LinkID=221036)herunter.  
  
 Tabellarische Lösungen unterstützen nur eine model.bim-Datei pro Lösung. Das bedeutet, dass die gesamte Arbeit in einer einzelnen Datei erledigt werden muss. Entwicklungsteams, die daran gewöhnt sind, mit mehreren Projekten in einer einzelnen Lösung zu arbeiten, müssen ihre Arbeitsweise bei der Erstellung einer freigegebenen tabellarischen Lösung möglicherweise überdenken.  
  
##  <a name="query-and-scripting-language-support"></a><a name="bkmk_lang"></a>Unterstützung von Abfrage-und Skriptsprache  
 Analysis Services schließen MDX, DMX, DAX, XML/A und ASSL ein. Unterstützung für diese Sprachen variiert leicht nach Modelltyp. Wenn Anforderungen für die Abfrage und Skriptsprache in Betracht kommen, überprüfen Sie die folgende Liste.  
  
-   Tabellarische Modelldatenbanken unterstützen DAX-Berechnungen, DAX-Abfragen und MDX-Abfragen.  
  
-   Mehrdimensionale Modelldatenbanken unterstützen MDX-Berechnungen und MDX-Abfragen sowie ASSL.  
  
-   Data Mining-Modelle unterstützen DMX und ASSL.  
  
-   Analysis Services PowerShell wird für die Server- und Datenbankverwaltung unterstützt. Der Modelltyp (oder der Servermodus) ist kein Faktor bei der Verwendung von PowerShell-Cmdlets.  
  
 Alle Datenbanken unterstützen XML/A.  
  
##  <a name="security-feature-support"></a><a name="bkmk_sec"></a>Unterstützung von Sicherheitsfunktionen  
 Alle Analysis Services-Projektmappen können auf Datenbankebene gesichert werden. Präzisere Sicherheitsoptionen variieren je nach Modus. Wenn präzise Sicherheitseinstellungen für die Projektmappe erforderlich sind, überprüfen Sie die folgende Liste, um sicherzustellen, dass die Sicherheitsstufe, die Sie möchten, für den zu erstellenden Projektmappentyp unterstützt wird:  
  
-   Für tabellarische Modelldatenbanken kann Sicherheit auf Zeilenebene mit rollenbasierten Berechtigungen in Analysis Services verwendet werden.  
  
-   Für mehrdimensionale Modelldatenbanken kann Sicherheit auf Dimensions- und Zellenebene verwendet werden, wobei rollenbasierte Berechtigungen in Analysis Services verwendet werden.  
  
 Excel-Datenmodelle können auf einem Server im tabellarischen Modus wiederhergestellt werden. Nachdem die Datei wiederhergestellt wurde, wird diese von SharePoint entkoppelt (sofern Sie sie von einem SharePoint-Speicherort wiederhergestellt haben), und Sie können fast alle tabellarischen Modellierungsfunktionen verwenden, einschließlich Sicherheit auf Zeilenebene. Die einzige Funktion der tabellarischen Modellierung, das für wiederhergestellte Arbeitsmappen nicht unterstützt wird, sind verknüpfte Tabellen.  
  
##  <a name="design-tools"></a><a name="bkmk_designer"></a> -Entwurftools  
 Fähigkeiten zur Datenmodellierung und technische Kenntnisse können unter Benutzern, die mit dem Erstellen von analytischen Modellen beauftragt sind, stark variieren. Wenn die Vertrautheit mit dem Tool oder Anwender-Know-How eine für die Projektmappe in Betracht kommt, vergleichen Sie die folgenden Erfahrungen für die Modellerstellung.  
  
|**Modellierungstool**|**Verwendung**|  
|-----------------------|------------------|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|Verwenden Sie diese, um tabellarische, mehrdimensionale und Data Mining-Projektmappen zu erstellen. Diese Erstellungsumgebung stellt Arbeitsbereiche, Eigenschaftenbereiche und Objektnavigation mithilfe von Visual Studio Shell bereit. Technisch versierte Benutzer, die bereits Visual Studio verwenden, ziehen höchstwahrscheinlich dieses Tool zum Erstellen von Business Intelligence-Anwendungen vor. Einzelheiten dazu finden Sie unter [Tools and applications used in Analysis Services](tools-and-applications-used-in-analysis-services.md) .|  
|Excel 2013 und höher, mit dem Add-In PowerPivot für Excel|PowerPivot für Excel ist ein Tool zum Bearbeiten und Erweitern eines Excel-Datenmodells. Es verfügt über einen separaten Anwendungsarbeitsbereich, der über Excel geöffnet wird, aber die gleichen visuellen Metaphern (Seiten im Registerkartenformat, Rasterlayout und Bearbeitungsleiste) wie Excel verwendet. Benutzer, die in Excel versiert sind, ziehen dieses Tool normalerweise [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]vor. Weitere Informationen finden Sie unter [Power Pivot: Leistungsstarke Datenanalyse und Datenmodellierung in Excel](https://support.office.com/en-ie/article/Power-Pivot-Powerful-data-analysis-and-data-modeling-in-Excel-d7b119ed-1b3b-4f23-b634-445ab141b59b).|  
  
##  <a name="client-and-reporting-applications"></a><a name="bkmk_client"></a>Client-und Bericht Erstellungs Anwendungen  
 In früheren Versionen wirkte sich die Auswahl des Modelltyps auf die verfügbaren Clientanwendungen aus. Der Unterschied hat sich jedoch im Lauf der Zeit verringert. Tabellarische und mehrdimensionale Modelle unterstützen größtenteils die gleichen Clientanwendungen zur Herstellung einer Verbindung mit Analysis Services-Daten. Die folgende Tabelle enthält eine Liste der Microsoft-Clientanwendungen, die mit Analysis Services-Datenmodellen verwendet werden können.  
  
|**Application**|**Beschreibung**|  
|---------------------|---------------------|  
|Excel PivotTable-Berichte|Die Excel-Funktionalität ist für tabellarische und mehrdimensionale Modelle identisch, obwohl Rückschreiben (eine Analysis Services-Funktion, die von Excel implementiert wird) nur für mehrdimensionale unterstützt wird.|  
|Reporting Services-RDL-Berichte|Im Berichts-Generator oder Berichts-Designer erstellte RDL-Berichte können beliebige Analysis Services-Modelle sowie Excel-Datenmodelle, die in PowerPivot für SharePoint gehostet werden, verwenden.|  
|PerformancePoint-Dashboards|In SharePoint können PerformancePoint-Dashboards mit allen Analysis Services-Datenbanken, einschließlich Excel-Datenmodellen, eine Verbindung herstellen. Weitere Informationen finden Sie unter [Erstellen von Datenverbindungen (PerformancePoint Services)](https://go.microsoft.com/fwlink/?linkdID=218155).|  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]in Office 365 oder Power BI Websites|Nur tabellarische Modelle.|  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] in lokalem SharePoint|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], eine ClickOnce-Anwendung von SharePoint, kann entweder einen Analysis Services-Cube oder ein Tabellenmodell verwenden.|  
  
##  <a name="server-deployment-modes-for-multidimensional-and-tabular-solutions"></a><a name="bkmk_deploymentmode"></a>Server Bereitstellungs Modi für mehrdimensionale und tabellarische Lösungen  
 Eine Analysis Services-Instanz ist in einem der drei Modi installiert, die den operativen Kontext des Servers festlegen. Der Servermodus, den Sie installieren, bestimmt den Typ von Projektmappen, die auf diesem Server bereitgestellt werden können. Die Speicher- und Arbeitsspeicherarchitektur sind die primären Unterschiede zwischen den Modi, zusätzliche Unterschiede sind jedoch vorhanden. Die drei Servermodi werden in der folgenden Tabelle kurz beschrieben. Weitere Informationen finden Sie unter [Bestimmen des Servermodus einer Analysis Services-Instanz](instances/determine-the-server-mode-of-an-analysis-services-instance.md).  
  
|Bereitstellungsmodus|Beschreibung|  
|---------------------|-----------------|  
|0 - Mehrdimensionaler Modus und Data Mining-Modus|Ausführung mehrdimensionaler Lösungen und Data Mining-Lösungen, die Sie auf einer Standardinstanz von Analysis Services bereitstellen. Der Bereitstellungsmodus 0 ist der Standardmodus für eine Analysis Services-Installation. Weitere Informationen finden Sie unter [Install Analysis Services in Multidimensional and Data Mining Mode](../../2014/sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md).|  
|1 - PowerPivot für SharePoint|Analysis Services ist eine interne Komponente von SharePoint für den Zugriff auf Excel-Datenmodelle. Analysis Services wird im Bereitstellungsmodus 1 installiert und akzeptiert nur Anforderungen von Excel Services in einer SharePoint-Umgebung. Weitere Informationen finden Sie unter [PowerPivot for SharePoint 2010 Installation](../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md).|  
|2 - Tabellarischer Modus|Ausführung tabellarischer Lösungen auf einer eigenständigen Analysis Services-Instanz, die für den Bereitstellungsmodus 2 konfiguriert wurde. Weitere Informationen finden Sie unter [Install Analysis Services in Tabular Mode](instances/install-windows/install-analysis-services.md).|  
  
 Beachten Sie, dass Servermodelle nicht austauschbar sind. Bei der Installation wählen Sie einen Modus für den Betrieb des Servers aus. Sie sollten mehrere Instanzen installieren, eine für jeden Servermodus, um alle Arbeitsauslastungen zu unterstützen.  
  
##  <a name="hosting-platforms"></a><a name="bkmk_sharePoint"></a>Hostingplattformen  
 Microsoft bietet mehrere Methoden zum Hosten von Daten, Anwendungen, Berichten und Zusammenarbeit. In diesem Abschnitt wird die Interoperabilität von Analysis Services im Hinblick auf die einzelnen Hostingplattformen behandelt.  
  
|**Plattform**|**Beschreibung**|  
|------------------|---------------------|  
|Microsoft Azure|Sie können jede unterstützte Version und Edition von Analysis Services auf einem virtuellen Azure-Computer ausführen. Im Gegensatz zu Azure SQL-Datenbank, einem Dienst in Azure mit großteils derselben Funktionalität wie eine lokale relationale Datenbank-Engine, gibt es kein Analysis Services-Äquivalent in Azure. Das Installieren, Konfigurieren und Ausführen von Analysis Services in einer Azure-VM ist unsere einzige Azure-basierte Option.|  
|Office 365|Excel Online in Office 365 unterstützt Remoteverbindungen mit tabellarischen und mehrdimensionalen Modellen, die lokal ausgeführt werden.|  
|Power BI-Websites in Office 365|Auf einer Power BI-Website können Power View-Berichte Verbindungen mit tabellarischen Datenmodellen herstellen, die lokal ausgeführt werden.|  
|Lokale Server (SharePoint- und SQL Server-Instanzen)|Ein lokaler Datenbankserver (d. h. eine SQL Server-Instanz, auf der Analysis Services installiert ist) ist immer noch das primäre Mittel zum Bereitstellen von Analysis Services-Daten für Berichte und Clientanwendungen. Tabellarische, mehrdimensionale und Data Mining-Lösungen können auf Analysis Services-Instanzen in einem Netzwerk ausgeführt werden, ohne dass eine SharePoint-Abhängigkeit besteht.<br /><br /> SQL Server wird mit SharePoint integriert, indem Unterstützung für PowerPivot-Datenzugriff und den Zugriff auf tabellarische Daten hinzugefügt wird. Die Investitionskosten einer integrierten SharePoint- und SQL Server-Lösung sind umso höher, je mehr Funktionen für die einzelnen Produkte verfügbar sind. Wenn Sie über SharePoint verfügen, können Sie SQL Server PowerPivot für SharePoint installieren, um den PowerPivot-Datenzugriff zu ermöglichen und die BISM-Verbindungsdateien von PowerPivot zu nutzen. Diese werden für den Zugriff auf tabellarische Datenbanken verwendet, die auf einer externen Analysis Services-Instanz auf einem Netzwerkserver ausgeführt werden.<br /><br /> Wenn Sie über SharePoint und SQL Server verfügen, können Sie die folgende Kombination von Diensten und Anwendungen unterstützen:<br /><br /> Analysis Services-Modelle (tabellarische oder mehrdimensionale)<br /><br /> SharePoint-Dienste der mittleren Ebene (Excel Services, Reporting Services in SharePoint und PerformancePoint-Dienste)<br /><br /> Browser-Clients oder Rich Clients (Excel) für tiefer gehende Datenanalyse und -erkundung.|  
  
##  <a name="next-step-build-a-solution"></a><a name="bkmk_Next"></a> Nächster Schritt: Erstellen einer Lösung  
 Nachdem Sie jetzt ein grundlegendes Verständnis der Unterschiede zwischen den Lösungen gewonnen haben, können Sie die folgenden Lernprogramme ausführen, um sich mit den Schritten zur Erstellung der einzelnen Lösungen vertraut zu machen. Über die folgenden Links gelangen Sie zu den Lernprogrammen, in denen die Schritte erklärt sind.  
  
-   Erstellen eines tabellarischen Modells mit dem [Tabellenmodellierung &#40;Adventure Works-Tutorial&#41;](tabular-modeling-adventure-works-tutorial.md).  
  
-   Erstellen eines mehrdimensionalen Modells mit dem [Mehrdimensionale Modellierung &#40;Adventure Works-Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md).  
  
-   Erstellen eines Data Mining-Modells mit dem [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
-   Erstellen eines PowerPivot-Modells mit dem [PowerPivot für Excel-Lernprogramm](https://go.microsoft.com/fwlink/?LinkId=251135).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Instanzverwaltung](instances/analysis-services-instance-management.md)   
 [Neues in Analysis Services und Business Intelligence](what-s-new-in-analysis-services.md)   
 [Neues &#40;Reporting Services&#41;](../../2014/reporting-services/what-s-new-reporting-services.md)   
 [Neues in Power Pivot](https://go.microsoft.com/fwlink/?LinkId=238141)   
 [Power Pivot-Hilfe für SQL Server 2012](https://go.microsoft.com/fwlink/?LinkID=220946)   
 [Power Pivot BI-Semantik Modell Verbindung &#40;. bism-&#41;](power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)   
 [Erstellen und Verwalten von freigegebenen Datenquellen &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)  
  
  
