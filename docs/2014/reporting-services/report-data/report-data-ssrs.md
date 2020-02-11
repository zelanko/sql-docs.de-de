---
title: Berichtsdaten
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: be36e61a44a416283e77638f01005f1b3e16883b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67413059"
---
# <a name="report-data-in-sql-server-reporting-services-ssrs"></a>Berichtsdaten in SQL Server Reporting Services (SSRS)

  Berichtsdaten können aus mehreren Datenquellen in Ihrer Organisation stammen. Der erste Schritt beim Entwerfen eines Berichts ist das Erstellen von Datenquellen und Datasets, die die zugrunde liegenden Berichtsdaten darstellen. Jede Datenquelle enthält Datenverbindungsinformationen. Jedes Dataset enthält einen Abfragebefehl, der den Satz von Feldern definiert, der als Daten aus einer Datenquelle verwendet werden soll. Sie können die Daten jedes Datasets visuell darstellen, indem Sie einen Datenbereich hinzufügen, z. B. eine Tabelle, eine Matrix, ein Diagramm oder eine Karte. Wenn der Bericht verarbeitet wird, wird Datenquelle abgefragt, und jeder Datenbereich nach Bedarf erweitert, um die Abfrageergebnisse für das Dataset anzuzeigen.  
  
##  <a name="BkMk_ReportDataTerms"></a>Bedingungen

 Wenn Sie mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] den Konzepten nicht vertraut sind, überprüfen Sie die folgenden Begriffe in [Reporting Services Konzepten &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md): *Datenverbindung*, *eingebettete Datenquellen*, frei *gegebene Datenquellen*, *eingebettete Datasets*, frei *gegebene Datasets*, *Datasetabfragen*, *Berichts Teile*und *Daten Warnungen*.  
  
##  <a name="BkMk_ReportDataTips"></a>Tipps zum Angeben von Berichtsdaten

 Die folgenden Informationen helfen Ihnen beim Entwerfen Ihrer Berichtsdaten-Strategie.  
  
- **Datenquellen** Datenquellen können unabhängig von Berichten auf einem Berichts Server oder einer SharePoint-Website veröffentlicht und verwaltet werden. Für jede Datenquelle können Sie oder der Datenbankbesitzer Verbindungsinformationen an einem Ort verwalten. Anmeldeinformationen für Datenquellen werden sicher auf dem Berichtsserver gespeichert; Kennwörter werden nicht in die Verbindungszeichenfolge aufgenommen. Sie können eine Datenquelle von einem Testserver an einen Produktionsserver umleiten. Sie können eine Datenquelle deaktivieren, um alle Berichte anzuhalten, die sie verwenden. Eine Liste der unterstützten Datenquellen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)Zeichenfolgen in Reporting Services.  
  
- **DataSets** Datasets können unabhängig von Berichten oder freigegebenen Datenquellen, von denen Sie abhängen, veröffentlicht und verwaltet werden. Sie oder der Datenbankbesitzer können optimierte Abfragen zur Verfügung stellen, die die Berichtsautoren dann verwenden können. Wenn Sie die Abfrage ändern, verwenden alle Berichte, die das freigegebene Dataset nutzen, die aktualisierte Abfrage. Zur Steigerung der Leistung können Sie die Zwischenspeicherung von Datasets aktivieren. Sie können die Zwischenspeicherung von Abfragen für eine bestimmte Zeit planen oder einen freigegebenen Zeitplan verwenden.  
  
- **Daten, die von Berichts Teilen verwendet werden** Berichts Teile können die Daten enthalten, von denen Sie abhängen. Weitere Informationen zu Berichtsteilen finden Sie unter [Berichtsteile im Berichts-Designer (SSRS)](../report-design/report-parts-in-report-designer-ssrs.md).  
  
- **Filtern von Daten** Berichtsdaten können in der Abfrage oder im Bericht gefiltert werden. Sie können kaskadierende Parameter mithilfe von Datasets und Abfragevariablen erstellen und so den Benutzern die Möglichkeit geben, die Auswahl von Tausenden von Möglichkeiten auf eine überschaubare Zahl einzugrenzen. Sie können Daten in einer Tabelle oder in einem Diagramm auf Grundlage von Parameterwerten oder anderen Werten, die Sie angeben, filtern.  
  
- **Parameter** Datasetabfragebefehle, die Abfrage Variablen einschließen, erstellen automatisch übereinstimmende Berichts Parameter. Parameter können aber auch manuell erstellt werden. Wenn Sie einen Bericht anzeigen, zeigt die Berichtssymbolleiste die Parameter an. Benutzer können Werte auswählen, um Berichtsdaten zu überprüfen oder deren Auftreten zu melden. Sie können Berichtsdaten für bestimmte Zielgruppen anpassen, indem Sie Sätze von Berichtsparametern mit anderen Standardwerten erstellen, die mit derselben Berichtsdefinition verknüpft sind, oder das integrierte `UserID`-Feld verwenden. Weitere Informationen finden Sie unter [Berichtsparameter (Berichts-Generator und Berichts-Designer)](../report-design/report-parameters-report-builder-and-report-designer.md) und [Integrierte Sammlungen in Ausdrücken (Berichts-Generator und SSRS)](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
- **Daten Warnungen** Nachdem ein Bericht veröffentlicht wurde, können Sie Warnungen auf der Grundlage von Berichtsdaten erstellen und e-Mail-Nachrichten empfangen, wenn er die von Ihnen angegebenen Regeln erfüllt.  
  
- **Gruppieren und Aggregieren von Daten** Berichtsdaten können in der Abfrage oder im Bericht gruppiert und aggregiert werden. Wenn Sie Werte in der Abfrage aggregieren, können Sie weiterhin im Rahmen des Sinnvollen Werte im Bericht kombinieren.  Weitere Informationen finden Sie unter [Filtern, Gruppieren und Sortieren von Daten (Berichts-Generator und SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) und [Aggregate-Funktion (Berichts-Generator und SSRS)](../report-design/report-builder-functions-aggregate-function.md).  
  
- **Sortieren von Daten** Berichtsdaten können in der Abfrage oder im Bericht sortiert werden. In Tabellen können Sie zudem eine interaktive Sortierschaltfläche hinzufügen, mit der die Benutzer selbst über die Sortierreihenfolge entscheiden können.  
  
- **Ausdrucks basierte Daten** Da die meisten Berichts Eigenschaften Ausdrucks basiert sein können und Ausdrücke Verweise auf Datasetfelder und Berichts Parameter enthalten können, können Sie leistungsstarke Ausdrücke schreiben, um die Berichtsdaten und die Darstellung zu steuern. Sie können einem Benutzer die Möglichkeit geben, die Datenanzeige durch Definieren von Parametern zu steuern.  
  
- **Anzeigen von Daten aus einem DataSet** Daten aus einem Dataset werden in der Regel in einem oder mehreren Daten Bereichen angezeigt, z. b. in einer Tabelle und einem Diagramm.  
  
- **Anzeigen von Daten aus mehreren Datasets**  Sie können Ausdrücke in einem Datenbereich auf Grundlage eines Datasets schreiben, das nach Werten oder Aggregaten in anderen Datasets sucht. Sie können Unterberichte auf Grundlage eines Datasets in eine Tabelle aufnehmen, um Daten aus einer anderen Datenquelle anzuzeigen.  
  
## <a name="data-connections-data-sources-and-datasets"></a>Datenverbindungen, Datenquellen und Datensets

 Die folgende Liste kann Ihnen dabei helfen, die Quellen von Daten für einen Bericht zu definieren.  
  
- Dabei müssen Sie sich entscheiden, ob Sie eingebettete oder freigegebene Datenquellen und Datasets verwenden möchten. Arbeiten Sie mit Besitzern der Datenquellen zusammen, um eine Authentifizierungs- und Autorisierungstechnologie zu implementieren und zu verwenden, die für Ihre Organisation geeignet ist.  
  
- Beachten Sie dabei bitte die Architektur der Softwaredatenschichten Ihrer Organisation und die potenziellen Probleme, die sich aus Datentypen ergeben können. Achten Sie darauf, wie sich Datenerweiterungen und Datenverarbeitungserweiterungen auf Abfrageergebnisse auswirken können. Je nach Datenquelle, Datenanbieter und den in der Berichtsdefinitionsdatei (.rdl) gespeicherten Datentypen stehen unterschiedliche Datentypen zur Verfügung.  
  
- Achten Sie auf die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Client/Server-Architekturen und -Tools. Im Berichts-Designer erstellen Sie z. B. Berichte auf einem Clientcomputer, der integrierte Datenquellentypen verwendet. Wenn Sie einen Bericht veröffentlichen, müssen der Berichtsserver oder die SharePoint-Website die Datenquellentypen unterstützen.  Weitere Informationen finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
- Datenquellen und Datasets werden in einem Bericht erstellt und von einem Clienterstellungstool auf einem Berichtsserver oder einer SharePoint-Website veröffentlicht. Datenquellen können auf dem Berichtsserver direkt erstellt werden. Nach der Veröffentlichung können Sie Anmeldeinformationen und andere Eigenschaften auf dem Berichtsserver konfigurieren. Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) Zeichenfolgen in Reporting Services und [Reporting Services Tools](../tools/reporting-services-tools.md).  
  
- Die verfügbaren Datenquellen hängen davon ab, welche [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenerweiterungen installiert sind. Je nach Clienterstellungstool, Berichtsserverversion und Berichtsserverplattform kann sich die Unterstützung für Datenquellen unterscheiden. Weitere Informationen finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
- Die Anmeldeinformationen für Datenquellen sind unterschiedlich je nach Datenquellentyp und je nachdem, ob Sie die Berichte auf Ihrem Client, auf dem Berichtsserver oder auf einer SharePoint-Website anzeigen. Weitere Informationen finden Sie unter [Festlegen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website (Reporting Services im integrierten SharePoint-Modus)](../security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) und [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../../integration-services/connection-manager/data-sources.md). Spezifische Anmeldeinformationen zu den Tools finden Sie unter [Reporting Services-Tools](../tools/reporting-services-tools.md).  
  
## <a name="related-tasks"></a>Related Tasks

 Auf das Erstellen von Datenverbindungen bezogene Tasks, die Daten aus externen Quellen, Datasets und Abfragen hinzufügen.  
  
|||  
|-|-|  
|**Allgemeine Aufgaben**|**Links**|  
|Erstellen von Datenverbindungen|[Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)|  
|Erstellen von Datasets und Abfragen|[Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)|  
|Verwalten von Datenquellen nach der Veröffentlichung|[Verwalten von Berichtsdatenquellen](manage-report-data-sources.md)|  
|Verwalten von freigegebenen Datasets nach der Veröffentlichung|[Verwalten von freigegebenen Datasets](manage-shared-datasets.md)|  
|Erstellen und Verwalten von Datenwarnungen|[Reporting Services-Datenwarnungen](../tutorial-creating-a-basic-table-report-report-builder.md)|  
|Zwischenspeichern von freigegebenen Datasets|[Zwischenspeichern von freigegebenen Datasets &#40;SSRS&#41;](../report-server/cache-shared-datasets-ssrs.md)|  
|Festlegen des Zeitpunkts für das Vorladen des Caches mit freigegebenen Datasets|[Zeitpläne](../subscriptions/schedules.md)|  
|Hinzufügen von Datenerweiterungen|[Implementieren von Datenverarbeitungserweiterungen](../extensions/data-processing/implementing-a-data-processing-extension.md)|