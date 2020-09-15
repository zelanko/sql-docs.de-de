---
title: Einführung in Berichtsdaten in SQL Server Reporting Services (SSRS)
description: Hier finden Sie einführende Informationen zu Berichtsdaten in den SQL Server Reporting Services (SSRS), z. B. dazu, wie Sie Datenquellen erstellen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.custom: seodec18
ms.date: 11/18/2019
ms.openlocfilehash: d9581fe8ae3f250d40eeaf21e76c4e1f373e12cd
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395341"
---
# <a name="intro-to-report-data-in-sql-server-reporting-services-ssrs"></a>Einführung in Berichtsdaten in SQL Server Reporting Services (SSRS)

  Berichtsdaten können aus mehreren Datenquellen in Ihrer Organisation stammen. Der erste Schritt beim Entwerfen eines Berichts ist das Erstellen von Datenquellen und Datasets, die die zugrunde liegenden Berichtsdaten darstellen. Jede Datenquelle enthält Datenverbindungsinformationen. Jedes Dataset enthält einen Abfragebefehl, der den Satz von Feldern definiert, der als Daten aus einer Datenquelle verwendet werden soll. Sie können die Daten jedes Datasets visuell darstellen, indem Sie einen Datenbereich hinzufügen, z. B. eine Tabelle, eine Matrix, ein Diagramm oder eine Karte. Wenn der Bericht verarbeitet wird, wird Datenquelle abgefragt, und jeder Datenbereich nach Bedarf erweitert, um die Abfrageergebnisse für das Dataset anzuzeigen.  

> [!NOTE]
> Die Integration von Reporting Services in SharePoint ist nach SQL Server 2016 nicht mehr möglich.

## <a name="data-in-ssrbnoversion"></a>Daten in [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]  
 ![rs_DataSourcesStory](../../reporting-services/report-data/media/rs-datasourcesstory.gif "rs_DataSourcesStory")  
  
1.  **Datenquellen im Berichtsdatenbereich:** Eine Datenquelle wird im Berichtsdatenbereich angezeigt, nachdem Sie eine eingebettete Datenquelle erstellt oder eine freigegebene Datenquelle hinzugefügt haben.  
  
2.  **Dialogfeld „Verbindung“:** Verwenden Sie das Dialogfeld „Verbindung“, um eine Verbindungszeichenfolge zu erstellen oder eine Verbindungszeichenfolge einzufügen.  
  
3.  **Datenverbindungsinformationen:** Die Verbindungszeichenfolge wird an die Datenerweiterung übergeben.  
  
4.  **Anmeldeinformationen:** Anmeldeinformationen werden getrennt von der Verbindungszeichenfolge verwaltet.  
  
5.  **Datenerweiterung/Datenanbieter:** Die Verbindung mit den Daten kann über mehrere Datenzugriffsebenen hergestellt werden.  
  
6.  **Externe Datenquellen:** Rufen Sie Daten aus relationalen Datenbanken, mehrdimensionalen Datenbanken, SharePoint-Listen oder Webdiensten ab.  


##  <a name="defining-terms"></a><a name="BkMk_ReportDataTerms"></a> Definieren von Begriffen  
  
- **Datenverbindung.** Wird auch als *Datenquelle*. Eine Datenverbindung umfasst einen Namen und Verbindungseigenschaften, die vom Verbindungstyp abhängen. Programmbedingt enthält eine Datenverbindung keine Anmeldeinformationen. Eine Datenverbindung gibt nicht an, welche Daten aus der externen Datenquelle abgerufen werden sollen. Geben Sie hierzu beim Erstellen eines Datasets eine Abfrage an.  
  
- **Datenquellendefinition.** Eine Datei, die die XML-Darstellung einer Berichtsdatenquelle enthält. Wenn Sie einen Bericht veröffentlichen, werden seine Datenquellen unabhängig von der Berichtsdefinition auf dem Berichtsserver oder der SharePoint-Website als Datenquellendefinitionen gespeichert. Ein Berichtsserveradministrator kann z. B. die Verbindungszeichenfolge oder die Anmeldeinformationen aktualisieren. Auf einem systemeigenen Berichtsserver lautet der Dateityp RDS. Auf einer SharePoint-Website lautet der Dateityp RSDS.  
  
- **Verbindungszeichenfolge.** Eine Verbindungszeichenfolge ist eine Zeichenfolgenversion der Verbindungseigenschaften, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind. Verbindungseigenschaften unterscheiden sich je nach Datenverbindungstyp. Beispiele finden Sie unter [Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
- **Freigegebene Datenquelle.** Eine auf einem Berichtsserver oder einer SharePoint-Website verfügbare Datenquelle, die von mehreren Berichten verwendet wird.  
  
- **Eingebettete Datenquelle.** Wird auch als *berichtsspezifische Datenquelle*bezeichnet. Eine Datenquelle, die in einem Bericht definiert und nur von diesem Bericht verwendet wird.  
  
- **Anmeldeinformationen.** Anmeldeinformationen sind die Authentifizierungsinformationen, die für den Zugriff auf externe Daten bereitgestellt werden müssen.  
  
##  <a name="tips-for-specifying-report-data"></a><a name="BkMk_ReportDataTips"></a> Tipps zum Angeben von Berichtsdaten

 Die folgenden Informationen helfen Ihnen beim Entwerfen Ihrer Berichtsdaten-Strategie.  
  
- **Datenquellen** Datenquellen können veröffentlicht werden und unabhängig von Berichten auf einem Berichtsserver oder einer SharePoint-Website verwaltet werden. Für jede Datenquelle können Sie oder der Datenbankbesitzer Verbindungsinformationen an einem Ort verwalten. Anmeldeinformationen für Datenquellen werden sicher auf dem Berichtsserver gespeichert; Kennwörter werden nicht in die Verbindungszeichenfolge aufgenommen. Sie können eine Datenquelle von einem Testserver an einen Produktionsserver umleiten. Sie können eine Datenquelle deaktivieren, um alle Berichte anzuhalten, die sie verwenden.  
  
- **Datasets** Datasets können veröffentlicht werden und unabhängig von Berichten oder den freigegebenen Datenquellen, von denen sie abhängen, verwaltet werden. Sie oder der Datenbankbesitzer können optimierte Abfragen zur Verfügung stellen, die die Berichtsautoren dann verwenden können. Wenn Sie die Abfrage ändern, verwenden alle Berichte, die das freigegebene Dataset nutzen, die aktualisierte Abfrage. Zur Steigerung der Leistung können Sie die Zwischenspeicherung von Datasets aktivieren. Sie können die Zwischenspeicherung von Abfragen für eine bestimmte Zeit planen oder einen freigegebenen Zeitplan verwenden.  
  
- **Daten, die von Berichtsteilen verwendet werden** Berichtsteile können Daten einbeziehen, von denen sie abhängen. Weitere Informationen zu Berichtsteilen finden Sie unter [Berichtsteile im Berichts-Designer (SSRS)](../../reporting-services/report-design/report-parts-in-report-designer-ssrs.md).  
  
- **Filtern von Daten** Berichtsdaten können in der Abfrage oder im Bericht gefiltert werden. Sie können Datasets und Abfragevariablen verwenden, um kaskadierende Parameter zu erstellen. Mit kaskadierenden Parametern können Benutzer die Entscheidungen tausender Auswahlen auf eine besser zu verwaltende Anzahl eingrenzen. Sie können Daten in einer Tabelle oder in einem Diagramm auf Grundlage von Parameterwerten oder anderen Werten, die Sie angeben, filtern.  
  
- **Parameter** Dataset-Abfragebefehle, die Abfragevariablen einschließen, erstellen automatisch übereinstimmende Berichtsparameter. Parameter können aber auch manuell erstellt werden. Wenn Sie einen Bericht anzeigen, zeigt die Berichtssymbolleiste die Parameter an. Benutzer können Werte auswählen, um Berichtsdaten zu überprüfen oder deren Auftreten zu melden. Sie können Berichtsdaten für bestimmte Zielgruppen anpassen, indem Sie Sätze von Berichtsparametern mit anderen Standardwerten erstellen, die mit derselben Berichtsdefinition verknüpft sind. Sie können auch das integrierte **UserID**-Feld verwenden, um Daten für verschiedene Zielgruppen anzupassen. Weitere Informationen finden Sie unter [Berichtsparameter (Berichts-Generator und Berichts-Designer)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md) und [Integrierte Sammlungen in Ausdrücken (Berichts-Generator und SSRS)](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
- **Datenwarnungen** Nachdem Sie einen Bericht veröffentlicht haben, können Sie basierend auf Berichtsdaten Warnungen erstellen. Anschließend erhalten Sie E-Mail-Nachrichten, wenn die von Ihnen angegebenen Regeln erfüllt werden.  
  
- **Daten gruppieren und aggregieren** Berichtsdaten können in der Abfrage oder im Bericht gruppiert oder aggregiert werden. Wenn Sie Werte in der Abfrage aggregieren, können Sie weiterhin im Rahmen des Sinnvollen Werte im Bericht kombinieren.  Weitere Informationen finden Sie unter [Filtern, Gruppieren und Sortieren von Daten (Berichts-Generator und SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) und [Aggregate-Funktion (Berichts-Generator und SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-function.md).  
  
- **Daten sortieren** Berichtsdaten können in der Abfrage oder im Bericht sortiert werden. In Tabellen können Sie zudem eine interaktive Sortierschaltfläche hinzufügen, mit der die Benutzer selbst über die Sortierreihenfolge entscheiden können.  
  
- **Ausdrucksbasierte Daten:** Da die meisten Berichtseigenschaften ausdrucksbasiert sein und Ausdrücke Verweise auf Datasetfelder und Berichtsparameter enthalten können, können Sie leistungsstarke Ausdrücke schreiben, um die Berichtsdaten und ihre Darstellung zu steuern. Sie können einem Benutzer die Möglichkeit geben, die Datenanzeige durch Definieren von Parametern zu steuern.  
  
- **Daten aus einem Dataset anzeigen** Daten aus einem Dataset werden in der Regel in einem oder mehreren Datenbereichen angezeigt, z. B. einer Tabelle und einem Diagramm.  
  
- **Daten aus mehreren Datasets anzeigen**  . Sie können Ausdrücke in einem Datenbereich auf Grundlage eines Datasets schreiben, die nach Werten oder Aggregaten in anderen Datasets suchen. Sie können Unterberichte auf Grundlage eines Datasets in eine Tabelle aufnehmen, um Daten aus einer anderen Datenquelle anzuzeigen.  
  
 Die folgende Liste kann Ihnen dabei helfen, die Quellen von Daten für einen Bericht zu definieren.  
  
- Dabei müssen Sie sich entscheiden, ob Sie eingebettete oder freigegebene Datenquellen und Datasets verwenden möchten. Arbeiten Sie mit Besitzern der Datenquellen zusammen, um eine Authentifizierungs- und Autorisierungstechnologie zu implementieren und zu verwenden, die für Ihre Organisation geeignet ist.  
  
- Beachten Sie dabei bitte die Architektur der Softwaredatenschichten Ihrer Organisation und die potenziellen Probleme, die sich aus Datentypen ergeben können. Achten Sie darauf, wie sich Datenerweiterungen und Datenverarbeitungserweiterungen auf Abfrageergebnisse auswirken können. Je nach Datenquelle, Datenanbieter und den in der Berichtsdefinitionsdatei (.rdl) gespeicherten Datentypen stehen unterschiedliche Datentypen zur Verfügung.  
  
- Achten Sie auf die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Client/Server-Architekturen und -Tools. Im Berichts-Designer erstellen Sie z. B. Berichte auf einem Clientcomputer, der integrierte Datenquellentypen verwendet. Wenn Sie einen Bericht veröffentlichen, müssen der Berichtsserver oder die SharePoint-Website die Datenquellentypen unterstützen.  Weitere Informationen finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
- Datenquellen und Datasets werden in einem Bericht erstellt und von einem Clienterstellungstool auf einem Berichtsserver oder einer SharePoint-Website veröffentlicht. Datenquellen können auf dem Berichtsserver direkt erstellt werden. Nach der Veröffentlichung können Sie Anmeldeinformationen und andere Eigenschaften auf dem Berichtsserver konfigurieren. Weitere Informationen finden Sie unter [Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) und [Reporting Services-Tools](../../reporting-services/tools/reporting-services-tools.md).  
  
- Die verfügbaren Datenquellen hängen davon ab, welche [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenerweiterungen installiert sind. Je nach Clienterstellungstool, Berichtsserverversion und Berichtsserverplattform kann sich die Unterstützung für Datenquellen unterscheiden. Weitere Informationen finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
- Die Anmeldeinformationen für Datenquellen sind unterschiedlich je nach Datenquellentyp und je nachdem, ob Sie die Berichte auf Ihrem Client, auf dem Berichtsserver oder auf einer SharePoint-Website anzeigen. Weitere Informationen finden Sie unter [Festlegen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website (Reporting Services im integrierten SharePoint-Modus)](../../reporting-services/security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) und [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md). Spezifische Anmeldeinformationen zu den Tools finden Sie unter [Reporting Services-Tools](../../reporting-services/tools/reporting-services-tools.md).  
  
## <a name="related-tasks"></a>Related Tasks

 Auf das Erstellen von Datenverbindungen bezogene Tasks, die Daten aus externen Quellen, Datasets und Abfragen hinzufügen.  
  
|Allgemeine Aufgaben|Links|  
|-|-|  
|Erstellen von Datenverbindungen|[Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)|  
|Erstellen von Datasets und Abfragen|[Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)|  
|Verwalten von Datenquellen nach der Veröffentlichung|[Verwalten von Berichtsdatenquellen](../../reporting-services/report-data/manage-report-data-sources.md)|  
|Verwalten von freigegebenen Datasets nach der Veröffentlichung|[Verwalten von freigegebenen Datasets](../../reporting-services/report-data/manage-shared-datasets.md)|  
|Erstellen und Verwalten von Datenwarnungen|[Reporting Services-Datenwarnungen](../../reporting-services/reporting-services-data-alerts.md)|  
|Zwischenspeichern von freigegebenen Datasets|[Zwischenspeichern von freigegebenen Datasets &#40;SSRS&#41;](../../reporting-services/report-server/cache-shared-datasets-ssrs.md)|  
|Festlegen des Zeitpunkts für das Vorladen des Caches mit freigegebenen Datasets|[Zeitpläne](../../reporting-services/subscriptions/schedules.md)|  
|Hinzufügen von Datenerweiterungen|[Implementing a Data Processing Extension (Implementieren von Datenverarbeitungserweiterungen)](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)|