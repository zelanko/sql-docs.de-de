---
title: Konzepte von Reporting Services (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 934b199c-9918-4e6b-83f4-5862b94fc904
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5baa02220a0dc2488e81153fd6b2a26f82dfa4e3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177154"
---
# <a name="reporting-services-concepts-ssrs"></a>Konzepte von Reporting Services (SSRS)
  In diesem Artikel werden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Konzepte zusammengefasst.

||
|-|
|**[!INCLUDE[applies](../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus &#124; [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Einheitlicher Modus|

 **In diesem Thema:**

-   [Berichtsserverkonzepte](#bkmk_ReportServerConcepts)

-   [Berichte und verwandte Elementkonzepte](#bkmk_ReportsandRelatedItemConcepts)

-   [Berichtstypen](#bkmk_TypesofReports)

-   [Phasen der Berichtsentwicklung](#bkmk_StagesofReports)

##  <a name="report-server-concepts"></a><a name="bkmk_ReportServerConcepts"></a>Berichts Server Konzepte
 Ein Berichtsserver ist ein Computer, auf dem eine Instanz von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installiert ist. Ein Berichtsserver speichert intern Elemente, wie z. B. Berichte, berichtsbezogene Elemente und Ressourcen, Zeitpläne und Abonnements. Ein Berichtsserver kann als eigenständiger einzelner Server oder als skalierbare Farm konfiguriert werden, oder er kann in SharePoint Server integriert werden. Sie interagieren durch den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Webdienst, WMI-Anbieter, URL-Zugriff oder programmgesteuert durch Skripts mit Berichtsserverelementen. Die Art und Weise, in der Sie mit einem Berichtsserver interagieren, hängt von der Bereitstellungstopologie und der Konfiguration ab.

 **Ein Berichts Server** im einheitlichen Modus Ein im einheitlichen Modus konfigurierter Berichts Server ist ein Computer, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] auf dem als eigenständiger Server installiert und konfiguriert ist. Sie interagieren mit dem Berichtsserver, mit Berichten und verwandten Elemente mithilfe eines Browsers mit Berichts-Manager oder URL-Zugriffsbefehlen, SQL Server Management Studio oder programmgesteuert durch Skripts. Weitere Informationen finden Sie unter [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](report-server/reporting-services-report-server-native-mode.md).

 **Berichtsserver im SharePoint-Modus** Ein in SharePoint integrierter Berichtsserver hat zwei mögliche Konfigurationen. In [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]ist [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] mit SharePoint Server als freigegebener SharePoint-Dienst installiert. In früheren Versionen war der Berichtsserver durch das Installieren des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Add-Ins in SharePoint Server integriert. In beiden Fällen interagieren Sie mit dem Berichtsserver, mit Berichten und verwandten Elementen mithilfe von Anwendungsseiten auf der SharePoint-Website. Sie verwenden die SharePoint-Dokumentbibliothek und andere Bibliotheken, die Sie erstellen, um die auf Berichte bezogenen Inhaltstypen zu speichern. Weitere Informationen finden Sie unter [Reporting Services-Berichtsserver &#40;SharePoint-Modus&#41;](../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md).

 **Berichtsserverelemente** Berichtsserverelemente include reports, models, shared data sources, shared datasets, and other items that you can publish, upload, or save to a report server. Organisieren Sie Elemente in der hierarchischen Berichtsserver-Ordnerstruktur auf einem systemeigenen Berichtsserver oder in SharePoint-Inhaltsbibliotheken auf einer SharePoint-Website. Weitere Informationen finden Sie unter [Verwalten von Berichtsserverinhalten (einheitlicher SSRS-Modus)](report-server/report-server-content-management-ssrs-native-mode.md).

 **Ordner** Auf einem systemeigenen Berichtsserver stellen Ordner die hierarchische Navigationsstruktur und den Pfad aller auf einem Berichtsserver gespeicherter adressierbaren Elemente bereit. Sie verwenden die Ordnerhierarchie und die Website- und Ordnerberechtigungen, um den Zugriff auf Berichtsserverelemente, die als *Sicherheit auf Elementebene*bezeichnet werden, zu steuern. Standardmäßig werden Rollenzuweisungen, die Sie für bestimmte Ordner definieren, von untergeordneten Ordnern in der Ordnerhierarchie geerbt. Wenn Sie einem Ordner bestimmte Rollen zuweisen, gelten die Vererbungsregeln nicht mehr. Die Ordnerstruktur besteht aus einem Stammordner namens **Home**und reservierten Ordnern, die die optionale Funktion **Meine Berichte** unterstützen. In einem Browser ist der Stammknoten der Name des virtuellen Berichtsserververzeichnisses, z.B. http://myreportserver/reports. Weitere Informationen finden Sie unter [Folders](report-server/report-server-content-management-ssrs-native-mode.md#bkmk_Folders).

 Verwenden Sie SharePoint-Ordner in Dokumentbibliotheken und Inhaltsbibliotheken auf einer SharePoint-Website, um Elemente zu organisieren.

 **Rollen und Berechtigungen** Auf einem systemeigenen Berichtsserver verwaltet der Systemadministrator Zugriffsberechtigungen, konfiguriert den Berichtsserver, um Berichtsanforderungen zu verarbeiten, Momentaufnahmehierarchien beizubehalten und Berechtigungen für Berichte, Datenquellen, Datasets und Abonnements zu verwalten. Ein veröffentlichter Bericht wird beispielsweise über Rollenzuweisungen gesichert, die das rollenbasierte Sicherheitsmodell von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] verwenden. Weitere Informationen finden Sie unter [Rollen und Berechtigungen &#40;Reporting Services&#41;](security/roles-and-permissions-reporting-services.md).

 Verwenden Sie die SharePoint-Websiteadministratorseite auf einer SharePoint-Website, um Zugriffsberechtigungen für Berichte und berichtsbezogene Websiteinhalte zu verwalten.

 **Zeitpläne** Auf einem systemeigenen Berichts Server können Sie Berichte, freigegebene Datasets und Abonnements zum Abrufen von Daten und Übermitteln von Berichten und Datasetabfragen zu bestimmten Zeitpunkten oder außerhalb der Spitzenzeiten planen. Zeitpläne können einmal oder kontinuierlich in stündlichen, täglichen, wöchentlichen oder monatlichen Intervallen ausgeführt werden. Weitere Informationen finden Sie unter [Schedules](subscriptions/schedules.md).

 **Abonnements und Übermittlung** Ein Abonnement ist eine Anforderung zur Übermittlung eines Berichts zu einem bestimmten Zeitpunkt oder als Reaktion auf ein Ereignis in dem im Abonnement angegebenen Anwendungsdateiformat. Abonnements stellen eine Alternative zum Ausführen eines Berichts bei Bedarf bereit. Jedes Mal, wenn Sie einen bedarfsgesteuerten Bericht anzeigen möchten, müssen Sie den Bericht aktiv auswählen. Im Gegensatz dazu können Abonnements dazu verwendet werden, die Übermittlung eines Berichts zu planen und zu automatisieren. Sie können Berichte an einen E-Mail-Posteingang oder eine Dateifreigabe übermitteln. Weitere Informationen finden Sie unter [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md).

 **Erweiterungen** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] stellt eine erweiterbare Architektur bereit, mit der Sie Berichtslösungen anpassen können. Der Berichtsserver unterstützt benutzerdefinierte Authentifizierungserweiterungen, Datenverarbeitungserweiterungen, Berichtsverarbeitungserweiterungen, Renderingerweiterungen und Übermittlungserweiterungen, und die Erweiterungen, die den Benutzern zur Verfügung stehen, sind in der Konfigurationsdatei "RSReportServer.config" konfigurierbar. Sie können z. B. die Exportformate, die der Berichts-Viewer verwenden darf, einschränken. Übermittlungserweiterungen und Berichtsverarbeitungserweiterungen sind zwar optional, jedoch erforderlich, wenn Sie die Berichtsverteilung oder benutzerdefinierte Steuerelemente unterstützen möchten. Weitere Informationen finden Sie unter [Erweiterungen &#40;SSRS&#41;](extensions-ssrs.md).

 **Berichts Zugriff** Der Bedarfs gesteuerte Zugriff ermöglicht es Benutzern, die Berichte aus einem Bericht Anzeige Tool auszuwählen. Je nach Berichtsserverkonfiguration können Sie den Berichts-Manager, einen [!INCLUDE[msCoName](../includes/msconame-md.md)] SharePoint 2.0-Webpart, eine SharePoint-Bibliothek (sofern [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im integrierten SharePoint-Modus installiert ist), ein eingebettetes ReportViewer-Steuerelement oder einen Browser verwenden. Weitere Informationen zum bedarfsgesteuerten Zugriff auf Berichte finden Sie unter [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS)](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md).

 Abonnements stellen eine Alternative zum Ausführen eines Berichts bei Bedarf bereit. Weitere Informationen finden Sie unter [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md).

 Die Liste der Tools für die Interaktion mit dem Berichtsserver finden Sie unter [Reporting Services-Tools](tools/reporting-services-tools.md).

##  <a name="reports-and-related-item-concepts"></a><a name="bkmk_ReportsandRelatedItemConcepts"></a>Konzepte für Berichte und verwandte Elemente
 **Berichte und Berichtsdefinitionen** **RDL.** Eine Berichtsdefinition ist eine XML-Datei, die einer XML-Grammatik entspricht, der so genannten Berichtsdefinitionssprache (RDL, Report Definition Language). In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]erstellen Sie eine Berichtsdefinition in einem Tool, zum Beispiel im Berichts-Generator oder im Berichts-Designer. Es enthält Elemente, die Datenquellenverbindungen, Abfragen zum Abrufen von Daten, Ausdrücken, Parametern, Bildern, Textfeldern, Tabellen und einem beliebigen anderen Entwurfszeitlayout definieren. Weitere Informationen finden Sie unter [Berichtsdefinitionssprache (Report Definition Language, RDL) &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).

 **RDLX.** Eine Berichtsdefinition in RDLX ist eine RDL-Datei mit internen Erweiterungen, die die [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] -Visualisierungserfahrung ermöglichen. Weitere Informationen finden Sie unter [Power View Übersicht](https://support.office.com/article/power-view-explore-visualize-and-present-your-data-98268d31-97e2-42aa-a52b-a68cf460472e#__toc328127684).

 **RDLC.** Der Visual Studio-Berichts-Designer erzeugt Clientberichtsdefinitionsdateien (Dateierweiterung .rdlc) im XML-Format zur Verwendung mit dem ReportViewer-Steuerelement.

 **Berichtsdatenverbindungen und Datenquellen** Berichte rufen Daten für einen Bericht mithilfe von Datenverbindungen ab, wenn eine Abfrage ausgeführt oder der Bericht verarbeitet wird. In einer Berichtsdefinition ist eine Datenverbindung mit einer Datenquelle identisch. Sie können aus einer Liste integrierter Datenverbindungstypen auswählen, um eine Verbindung mit einer relationalen Datenbank, einer mehrdimensionalen Datenbank, einem Webdienst oder einer anderen Datenquelle herzustellen. Beim Beschreiben von Datenverbindungen werden die folgenden Begriffe verwendet.

-   **Datenverbindung.** Wird auch als *Datenquelle*. Eine Datenverbindung umfasst einen Namen und Verbindungseigenschaften, die vom Verbindungstyp abhängen. Programmbedingt enthält eine Datenverbindung keine Anmeldeinformationen. Eine Datenverbindung gibt nicht an, welche Daten aus der externen Datenquelle abgerufen werden sollen. Geben Sie hierzu beim Erstellen eines Datasets eine Abfrage an.

-   **Datenquellendefinition.** Eine Datei, die die XML-Darstellung einer Berichtsdatenquelle enthält. Wenn ein Bericht veröffentlicht wird, werden seine Datenquellen unabhängig von der Berichtsdefinition auf dem Berichtsserver oder der SharePoint-Website als Datenquellendefinitionen gespeichert. Ein Berichtsserveradministrator kann z. B. die Verbindungszeichenfolge oder die Anmeldeinformationen aktualisieren. Auf einem systemeigenen Berichtsserver lautet der Dateityp RDS. Auf einer SharePoint-Website lautet der Dateityp RSDS.

-   **Verbindungs Zeichenfolge.** Eine Verbindungszeichenfolge ist eine Zeichenfolgenversion der Verbindungseigenschaften, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind. Verbindungseigenschaften unterscheiden sich je nach Datenverbindungstyp.

-   **Freigegebene Datenquelle.** Eine auf einem Berichtsserver oder einer SharePoint-Website verfügbare Datenquelle, die von mehreren Berichten verwendet wird.

     Freigegebene Datenquellen sind hilfreich für Datenquellen, die Sie häufig verwenden. Es wird empfohlen, dass Sie so oft wie möglich freigegebene Datenquellen verwenden. Mit ihnen können Berichte und der Berichtszugriff einfacher verwaltet und Berichte und die Datenquellen, auf die sie zugreifen, sicherer gemacht werden. Wenn Sie eine freigegebene Datenquelle benötigen, wenden Sie sich an den Systemadministrator. Er erstellt eine freigegebene Datenquelle für Sie.

     Freigegebene Datenquellen können nicht in Berichts-Generator erstellt werden. Sie können zum Berichtsserver wechseln und dort eine freigegebene Datenquelle auswählen.

     In Berichts-Designer können Sie nicht zu einer freigegebenen Datenquelle auf dem Berichtsserver wechseln. Sie können freigegebene Datenquellen als Teil eines Projekts im Projektmappen-Explorer erstellen und auswählen, ob sie auf einem Berichtsserver bereitgestellt werden sollen. Sie können festlegen, sie wegen Unterschiede in vom Computer oder dem Berichtsserver erforderlichen Anmeldeinformationen nur lokal zu verwenden.

-   **Eingebettete Datenquelle.** Wird auch als *berichtsspezifische Datenquelle*bezeichnet. Eine eingebettete Datenquelle wird in einem Bericht definiert und wird nur von diesem Bericht verwendet.

     Eine eingebettete Datenquellenverbindung ist eine Datenverbindung, die in der Berichtsdefinition gespeichert wird. Eingebettete Informationen für eine Datenquellenverbindung können nur in dem Bericht verwendet werden, in den die Informationen eingebettet wurden.

-   **Daten.** Anmeldeinformationen sind die Authentifizierungsinformationen, die für den Zugriff auf externe Daten bereitgestellt werden müssen.

     Anmeldeinformationen werden beim Erstellen einer eingebetteten Datenquelle, beim Ausführen einer Abfrage oder beim Abrufen von Daten während der Berichtsverarbeitung verwendet. Der Besitzer der Datenquelle legt den für den Zugriff auf die Daten erforderlichen Anmeldeinformationstyp fest. Anmeldeinformationen werden unabhängig von der Datenverbindung auf einem Berichtsserver, einer SharePoint-Website oder auf einem lokalen Computer in einer Berichterstellungsumgebung verwaltet. Abhängig vom Datenquellentyp können Anmeldeinformationen gespeichert werden, um Aufforderungen zu vermeiden, oder so konfiguriert werden, dass jeder Benutzer zur Eingabe aufgefordert wird. Die erforderlichen Anmeldeinformationen können sich unterscheiden, je nachdem, ob Sie die Verbindung mit der Datenquelle von Ihrem Computer oder vom Berichtsserver herstellen. Weitere Informationen finden Sie unter [Angeben von Anmeldeinformationen im Berichts-Generator](../../2014/reporting-services/specify-credentials-in-report-builder.md).

 **Berichtsdatasets** In einem Bericht stellt ein Dataset Berichtsdaten dar, die als Ergebnis der Ausführung einer Abfrage für eine externe Datenquelle zurückgegeben werden. Das Dataset hängt von der Datenverbindung ab, die Informationen zur externen Datenquelle enthält. Die Daten selbst sind nicht in der Berichtsdefinition enthalten. Das Dataset enthält einen Abfragebefehl, eine Feldauflistung, Parameter, Filter und Datenoptionen, mit denen die Groß- und Kleinschreibung berücksichtigt und eine Sortierung vorgenommen werden kann. Die folgenden beiden Datasettypen stehen zur Verfügung:

-   **Freigegebene Datasets.** Ein freigegebenes Dataset wird auf einem Berichtsserver veröffentlicht und kann in mehreren Berichten verwendet werden. Ein freigegebenes Dataset muss auf einer freigegebenen Datenquelle basieren. Ein freigegebenes Dataset kann zwischengespeichert und durch Erstellen eines Cacheaktualisierungsplans geplant werden.

-   **Eingebettete Datasets.** Eingebettete Datasets werden in nur einem Bericht definiert und verwendet.

 Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).

 **Berichtsparameter** Berichtsparameter are a part of a report definition. Sie können einem Bericht Parameter hinzufügen, um verknüpfte Berichte zu verknüpfen, die Berichtsdarstellung zu steuern, Berichtsdaten zu filtern oder den Bereich eines Berichts auf bestimmte Benutzer oder Orte einzugrenzen. Wenn ein Bericht auf einem systemeigenen Berichtsserver oder einer SharePoint-Website veröffentlicht wird, werden Berichtsparameter als separates Berichtsserverelement gespeichert. Parameter können unabhängig von der Berichtsdefinition verwaltet werden. Um mehrere Sätze mit Parametern für den gleichen Bericht zu erstellen, erstellen Sie *verknüpfte Berichte*.

 **Berichtselemente** Ein Berichtselement ist ein internes, aber grundlegendes Konzept in einer Berichtsdefinition. Eigenschaften eines Berichtselements gelten für Datenbereiche, Karten, Textfelder, Bilder und andere Entwurfselemente, die Sie einem Bericht hinzufügen. Das Verstehen der Eigenschaften eines Berichtselements kann Ihnen dabei helfen, angepasste Berichtsinhalte und -darstellungen zu entwerfen. Alle Berichtselemente haben z. B. eine "Hidden"-Eigenschaft, um die Sichtbarkeit zu steuern.

 **Datenbereiche und Karten** Ein Datenbereich ist ein Layoutelement, das Daten aus einem einzelnen Dataset anzeigt. Datenbereichstypen sind beispielsweise Tablix, Diagramm, Leiste und Indikator. "Karte" ist ein besonderer Typ des Datenbereichs, da er Daten aus zwei Datasets anzeigen kann: ein Dataset mit räumlichen Daten und eins mit analytischen Daten.

 Aktivieren Sie allgemeine Datenvisualisierungen mithilfe von Datenbereichen: Zahlen und Text in einer Tabelle, Matrix oder Liste; grafische Anzeigen in einem Diagramm oder einer Leiste; und geografische Anzeigen in einer Karte. Tabellen, Matrizen und Listen basieren auf dem Tablix-Datenbereich, der bei Bedarf erweitert wird, um alle Daten aus dem Dataset anzuzeigen. Ein Tablix-Datenbereich unterstützt mehrere Zeilen- und Spaltengruppen mit statischen und dynamischen Zeilen und Spalten. In einem Diagramm werden mehrere Reihen und Kategoriegruppen in einer Vielzahl von Diagrammformaten angezeigt. In einem Messgerät wird ein einzelner Wert oder ein aggregierter Wert für ein Dataset angezeigt. In einer Karte werden räumliche Daten in Form von Kartenelementen angezeigt, deren Darstellung abhängig von den aggregierten Daten aus einem Dataset variieren kann.

-   **Glaub.** Eine Tabelle ist ein Datenbereich, in dem die Daten zeilenweise dargestellt werden. Tabellenspalten sind statisch: Sie bestimmen die Anzahl von Spalten, wenn Sie den Bericht entwerfen. Tabellenzeilen sind dynamisch: sie werden nach unten erweitert, um die Daten aufzunehmen. Sie können zu den Tabellen Gruppen hinzufügen, die die Daten nach ausgewählten Feldern oder Ausdrücken zusammenfassen. Weitere Informationen finden Sie unter [Tabellen &#40;Berichts-Generator und SSRS&#41;](report-design/tables-report-builder-and-ssrs.md).

-   **Matrix** Eine Matrix wird auch als Kreuztabelle bezeichnet. Ein Matrixdatenbereich enthält dynamische Zeilen und Spalten: sie werden zur Aufnahme der Daten erweitert. Eine Matrix kann dynamische Spalten und Zeilen und statische Spalten und Zeilen enthalten. Spalten oder Zeilen können in anderen Spalten oder Zeilen enthalten sein, die zur Gruppierung von Daten verwendet werden können. Weitere Informationen finden Sie unter [Matrices &#40;Berichts-Generator und SSRS&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md).

-   **List.** Eine Liste ist ein Datenbereich, in dem Daten frei angeordnet dargestellt werden. Sie können Berichtselemente zu einem Formular anordnen, indem Sie Textfelder, Bilder und andere Datenbereiche beliebig in der Liste platzieren. Weitere Informationen finden Sie unter [Listen &#40;Berichts-Generator und SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).

-   **Fluss.** Ein Diagramm stellt Daten grafisch dar. Beispiele für Diagramme sind Balken-, Kreis- und Liniendiagramme, es werden jedoch weit mehr Arten unterstützt. Weitere Informationen finden Sie unter [Diagramme &#40;Berichts-Generator und SSRS&#41;](report-design/charts-report-builder-and-ssrs.md).

-   **Mess Gerät.** Ein Messgerät präsentiert Daten als Bereich mit einem Indikator, der auf einen bestimmten Wert innerhalb des Bereichs zeigt. Messgeräte werden verwendet, um Key Performance Indicators (KPIs) und andere Daten anzuzeigen. Beispiele für Messgeräte umfassen lineare und runde Ausführungen. Weitere Informationen finden Sie unter [Messgeräte &#40;Berichts-Generator und SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md).

-   **Bilden.** Mit einer Karte können Daten vor einem geografischen Hintergrund präsentiert werden. Kartendaten können räumliche Daten aus einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Abfrage, einer ESRI-Shape-Datei oder aus [!INCLUDE[msCoName](../includes/msconame-md.md)] Bing-Kartenkacheln sein. Räumliche Daten bestehen aus Sätzen von Koordinaten zur Definition von Polygonen, die Formen oder Bereiche darstellen, von Linien, die Routen oder Pfade darstellen, und von Punkten, die durch Marker dargestellt werden. Sie können aggregierte Daten Kartenelementen zuordnen, um deren Farbe und Größe automatisch zu verändern. So kann der Markertyp für ein Geschäft auf Grundlage der Umsätze oder die Farbe für eine Straße auf Grundlage der Geschwindigkeitsbegrenzung variieren. Weitere Informationen finden Sie unter [Karten &#40;Berichts-Generator und SSRS&#41;](report-design/maps-report-builder-and-ssrs.md).

 Sie können auch Werte aus Datasets einschließen, die nicht mit dem Datenbereich verknüpft sind, indem Sie folgendermaßen vorgehen:

-   Ausdrücke, die Aufrufe zu Aggregatfunktionen einschließen, die ein anderes Dataset als Bereichsparameter angeben, z. B. `=Max(Fields!Sales.Value, "AnnualSales")`.

-   Verwenden Sie die Funktion `Lookup`, um Werte von Name-Wert-Paaren in einem anderen Dataset nachzuschlagen.

 **Berichts Teile** Eine Berichts Teil Definition (. RSC) ist ein Berichts Server Element, bei dem es sich um ein XML-Fragment einer Berichts Definitionsdatei handelt. Sie erstellen Berichtsteile, indem Sie eine Berichtsdefinition erstellen und dann Berichtselemente im Bericht auswählen, die als Berichtsteile getrennt veröffentlicht werden sollen. Berichtsteile umfassen Datenbereiche, Rechtecke und enthaltene Elemente sowie Bilder. Sie können einen Berichtsteil mit seinen abhängigen Datasets und freigegebenen Datenquellenverweisen speichern, damit er in anderen Berichten wiederverwendet werden kann. Weitere Informationen finden Sie unter [Berichtsteile im Berichts-Designer &#40;SSRS&#41;](report-design/report-parts-in-report-designer-ssrs.md).

 **Datenwarnungen** Eine Datenwarnung ist ein in einer Warnungsdatenbank intern gespeichertes Element. Eine Datenwarnungsdefinition umfasst die Information, welche Daten aus vorhandenen Berichtsdatenfeeds verwendet werden sollen, welche Bedingungen erfüllt werden müssen, einen Zeitplan und Empfänger für die Warnung. Datenwarnungen sind nur in Berichten verfügbar, die auf einem in SharePoint Server integrierten Berichtsserver veröffentlicht wurden. Datenwarnungen sind auf einer systemeigenen Berichtsserverinstallation nicht verfügbar. Weitere Informationen finden Sie unter [Reporting Services-Datenwarnungen](../ssms/agent/alerts.md).

##  <a name="types-of-reports"></a><a name="bkmk_TypesofReports"></a>Berichts Typen
 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]kann der Begriff *Bericht* für einen bestimmten Typ von Berichtsserverelement, für einen Layoutentwurf oder einen Lösungsentwurf gelten. Ein einzelner Bericht kann Eigenschaften von mehr als einem Typ haben; z. B. kann ein Bericht gleichzeitig ein eigenständiger Bericht, ein von einem Hauptbericht referenzierter Unterbericht, das Ziel eines Drillthroughberichts in einem anderen Hauptbericht und ein verknüpfter Bericht sein.

 **Drilldownberichte** Ein Drilldownbericht ist ein Layoutentwurf, der zunächst Komplexität ausblendet und es dem Benutzer ermöglicht, bedingt ausgeblendete Berichtselemente umzuschalten, um die Detailliertheit der Anzeige steuern zu können. Für Drilldownberichte müssen alle möglichen Daten abgerufen werden, die im Bericht angezeigt werden können. Erwägen Sie bei Berichten mit großen Datenmengen stattdessen die Verwendung von Drillthroughberichten. Weitere Informationen finden Sie unter [Drilldownaktion &#40;Berichts-Generator und SSRS&#41;](report-design/drilldown-action-report-builder-and-ssrs.md).

 **Unterberichte** Ein Unterbericht ist ein Berichtselement, das Sie einem Bericht als Layoutelement hinzufügen. Ein Unterbericht zeigt auf einen anderen Bericht und wird innerhalb eines Hauptberichts als Unterberichtsinstanz angezeigt. In einem Unterbericht können andere Datenquellen verwendet werden als im Hauptbericht. Zwar kann ein Unterbericht innerhalb von Datenbereichen wiederholt werden, indem die Daten in den einzelnen Instanzen des Unterberichts mithilfe eines Parameters gefiltert werden, doch werden Unterberichte meist mit einem Hauptbericht als "Lagebesprechungsprotokoll" oder Container für eine Auflistung miteinander verknüpfter Berichte verwendet. Jede Instanz eines Unterberichts wechselt den Kontext für die Berichtsverarbeitung zwischen dem Hauptbericht und dem Unterbericht. Erwägen Sie bei Berichten mit vielen Instanzen von Unterberichten stattdessen die Verwendung von Drillthroughberichten. Weitere Informationen finden Sie unter [Unterberichte (Berichts-Generator und SSRS)](report-design/subreports-report-builder-and-ssrs.md).

 **Haupt-/Detailberichte und Drillthrough-Berichte** Eine Haupt-/Detail Berichtslösung schließt einen Hauptbericht ein, der Zusammenfassungs Informationen mit Links zu einem oder mehreren Berichten anzeigt, in denen ausführliche Informationen angezeigt werden.  Der Detailbericht wird nur ausgeführt, wenn ein Berichtsleser auf einen entsprechenden Link klickt. Der Drillthroughbericht wird getrennt im Hauptbericht geöffnet. Ein Link kann für beliebige Berichtselemente definiert werden, die über eine Action-Eigenschaft verfügen, z. B. Textfeld, Platzhaltertext oder Diagrammreihe. Weitere Informationen finden Sie unter [Drillthroughberichte (Berichts-Generator und SSRS)](report-design/drillthrough-reports-report-builder-and-ssrs.md).

 **Linked reports** Ein verknüpfter Bericht ist ein Berichtsserverelement, das einen Zeiger auf die Berichtsdefinition enthält, aber einen eigenen Satz von Berichtseigenschaften und -einstellungen aufweist. Dazu gehören Sicherheit, Parameter, Speicherort, Abonnements und Zeitpläne. Da Parameter auf dem Server unabhängig verwaltet werden, werden durch das erneute Veröffentlichen eines Hauptberichts, der neue Parametereinstellungen verwendet, weder im Hauptbericht noch im verknüpften Bericht vorhandene Parametereinstellungen überschrieben.

 Weitere Informationen finden Sie unter [Erstellen eines verknüpften Berichts](reports/create-a-linked-report.md).

 **Verlaufsberichte** Der Berichtsverlauf ist eine Auflistung von Berichtsmomentaufnahmen. Mithilfe des Berichtsverlaufs können Sie eine Aufzeichnung eines Berichts für einen bestimmten Zeitraum verwalten. Der Berichtsverlauf ist nicht für Berichte mit vertraulichen oder persönlichen Daten gedacht. Aus diesem Grund kann der Berichtsverlauf nur die Berichte einschließen, die eine Datenquelle mithilfe eines einzelnen Satzes von Anmeldeinformationen abfragen. Alternativ können Sie einen Verlauf eines Berichts erstellen, indem Sie einen Zeitplan und ein Abonnement definieren, um den Bericht in einem exportierten Dateiformat an eine Dateifreigabe zu übermitteln. Weitere Informationen finden Sie unter [Leistung, Momentaufnahmen, Zwischenspeichern &#40;Reporting Services&#41;](report-server/performance-snapshots-caching-reporting-services.md).

 **Zwischengespeicherte Berichte** Ein zwischengespeicherter Bericht ist eine gespeicherte Kopie eines kompilierten Berichts und der Berichtsdaten. Zwischengespeicherte Berichte werden verwendet, um die Leistung zu verbessern, indem die Anzahl der Verarbeitungsanforderungen an den Berichtsprozessor und die zum Abrufen großer Berichtsdatasets erforderliche Verarbeitungszeit verringert wird. Sie verfügen über einen obligatorischen Ablaufzeitraum, der normalerweise in Minuten definiert wird. Weitere Informationen zur Verwendung dieser Berichte finden Sie unter [Zwischenspeichern von Berichten (SSRS)](report-server/caching-reports-ssrs.md).

 Sie können die Abfrageergebnisse für ein freigegebenes Dataset auch zwischenspeichern. Weitere Informationen finden Sie unter [Zwischenspeichern von freigegebenen Datasets (SSRS)](report-server/cache-shared-datasets-ssrs.md).

 **Momentaufnahmen** Ein Berichtsmomentaufnahme ist ein Bericht, der Layoutinformationen und Abfrageergebnisse enthält, die zu einem bestimmten Zeitpunkt abgerufen wurden. Im Gegensatz zu bedarfsgesteuerten Berichten nach, die aktuelle Abfrageergebnisse abrufen, wenn Sie den Bericht anzeigen, ruft der Berichtsserver den kompilierten Bericht und die Berichtsdaten ab, die für den Bericht zur Zeit der Momentaufnahmeerstellung aktuell waren. Berichtsmomentaufnahmen werden in keinem speziellen Renderingformat gespeichert. Stattdessen werden Berichtsmomentaufnahmen erst dann in einem endgültigen Anzeigeformat (wie HTML) gerendert, wenn sie von einem Benutzer oder einer Anwendung angefordert werden. Weitere Informationen finden Sie unter [Leistung, Momentaufnahmen, Zwischenspeichern &#40;Reporting Services&#41;](report-server/performance-snapshots-caching-reporting-services.md).

 **Modellberichte und Berichte mit Durchklicken**
 -   **Berichts Modell.** Ein Berichtsmodell ist eine benutzerfreundliche Beschreibung einer zugrunde liegenden Datenbank mit im Voraus festgelegten Datenbeziehungen und automatisch generierten Abfragen. Berichtsmodelle können als Datenquellen für Berichte verwendet werden, die Sie im Berichts-Designer und Berichts-Generator erstellen.

-   **Bericht mit Durchklicken.** Ein Bericht mit Durchklicken zeigt verknüpfte Daten aus einem Berichtsmodell an, wenn Sie auf die interaktiven Daten klicken, die im modellbasierten Bericht enthalten sind. Berichte mit Durchklicken werden automatisch erzeugt. Weitere Informationen finden Sie unter [Berichte mit Durchklicken &#40;SSRS&#41;](reports/clickthrough-reports-ssrs.md).

 Weitere Informationen zu SMDL-Modellen finden Sie unter [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).

 **Gespeicherte Berichte** Ein gespeicherter Bericht ist eine Berichts Definitionsdatei (RDL-Datei). Eine Berichtsdefinition kann lokal gespeichert oder auf einen Berichtsserver hochgeladen werden. Wenn Sie eine Berichtsdefinition hochladen, statt sie zu veröffentlichen, tritt keine Versionsüberprüfung oder Ausdrucksüberprüfung auf. Fehler werden erst bei der Ausführung des Berichts angezeigt. Weitere Informationen finden Sie unter [Save and Deploy](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md#bkmk_SaveandDeploy).

 **Veröffentlichte Berichte** Ein veröffentlichter Bericht ist ein Berichtsserverelement, das Sie auf einem Berichtsserver von einem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Tool aus veröffentlichen. Auf einem systemeigenen Berichtsserver veröffentlichen Sie den Bericht in einem Ordner, für den Sie Berechtigungen haben. Auf einem SharePoint-Berichtsserver können Sie den Bericht in einer Dokumentbibliothek veröffentlichen, die für den Berichtsinhaltstyp aktiviert ist. Um den Bericht für andere Benutzer freizugeben, müssen diese Benutzer die Berechtigung zum Anzeigen des Berichts haben. Weitere Informationen finden Sie unter [Save and Deploy](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md#bkmk_SaveandDeploy).

 **Aktualisierte Berichte** Ein aktualisierter Bericht ist eine veröffentlichte Berichtsdefinition, die in ein neueres Schema konvertiert wird, wenn ein Berichtsserver von einer Version von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] auf eine neuere Version aktualisiert wird. Die ursprüngliche Berichtsdefinition wird beibehalten. Der Bericht wird im Arbeitsspeicher aktualisiert, kompiliert, und die kompilierte Version wird intern gespeichert. Weitere Informationen finden Sie unter [Upgrade Reports](install-windows/upgrade-reports.md).

##  <a name="stages-of-report-development"></a><a name="bkmk_StagesofReports"></a>Phasen der Berichts Entwicklung
 Eine Berichtsdefinition kann erstellt, veröffentlicht oder gespeichert, kompiliert, verarbeitet, zwischengespeichert, gerendert, angezeigt, exportiert und als Verlauf gespeichert werden. Wenn Sie einen Bericht ausführen, verarbeitet der Berichtsserver den Bericht in drei Schritten. Zu diesen Schritten gehört die Berichtsverarbeitung, die Datenverarbeitung und das Rendering. Daten- und Berichtsverarbeitung werden in einer Berichtsdefinition ausgeführt. Die Ergebnisse liegen in einem internen Zwischenformat vor. Berichte im Zwischenformat werden nachfolgend in einem bestimmten Anzeigeformat gerendert. Das folgende Diagramm zeigt die Phasen und Elemente der Berichtsverarbeitung.

 ![Berichts Verarbeitungs Diagramm](media/report-execution.gif "Diagramm für die Berichtsverarbeitung") Berichts Verarbeitungs Diagramm

 **Berichtsdefinition** Die auf einem Berichts Server gespeicherte Berichts Definitionsdatei (RDL). Weitere Informationen finden Sie unter [Berichtsdefinitionssprache (Report Definition Language, RDL) &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).

 **Kompilierter Bericht und Zwischenberichtsformat** Der Bericht, der ausgewertete Ausdrücke, Parameter und Parametereigenschaften verwendet.

 **Momentaufnahmen- oder Berichtsverlauf** Eine Momentaufnahme ist der Satz von Berichtsdaten zu einem bestimmten Zeitpunkt plus dem Zwischenformat, das Berichtslayoutinformationen enthält. Weitere Informationen finden Sie unter [Leistung, Momentaufnahmen, Zwischenspeichern &#40;Reporting Services&#41;](report-server/performance-snapshots-caching-reporting-services.md).

 **Verarbeiteter Bericht** Ein vollständig verarbeiteter Bericht, der Daten und Layoutinformationen enthält.

 **Gerenderter Bericht** Ein vollständig verarbeiteter Bericht wird an einen Berichtsrenderer gesendet, um die Daten und das Layout auf den einzelnen Seiten des beabsichtigten Renderingformat zu kombinieren. Renderingerweiterungen können vom Benutzer angepasst und erweitert werden. Das Standardrenderingformat für einen Bericht ist HTML 4.0. Weitere Informationen finden Sie unter [Seitenlayout und Rendering (Berichts-Generator und SSRS)](report-design/page-layout-and-rendering-report-builder-and-ssrs.md) und [Erweiterungen (SSRS)](extensions-ssrs.md).

 **Exportierter Bericht** Ein exportierter Bericht ist ein vollständig ausgelagerter und in einem bestimmten Dateiformat gespeicherter Bericht. Exportformate hängen von installierten Renderingerweiterungen ab und können angepasst werden. Standardmäßig schließen Exportformate Excel, Word, XML, PDF, TIFF und CSV ein. Weitere Informationen finden Sie unter [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md).

## <a name="see-also"></a>Weitere Informationen
 [Reporting Services Features und Aufgaben &#40;SSRS&#41;](reporting-services-features-and-tasks-ssrs.md) [Technische Referenz &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md) Reporting Services &#40;[SSRS](create-deploy-and-manage-mobile-and-paginated-reports.md)&#41;


