---
title: Hinzufügen von Daten aus externen Datenquellen (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 924a2ec3-150c-4bb2-83c9-4c7b440e8c03
caps.latest.revision: 10
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 22ec8f6785e33323931c5d1199b1c308285be088
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061552"
---
# <a name="add-data-from-external-data-sources-ssrs"></a>Hinzufügen von Daten aus externen Datenquellen (SSRS)
  Daten werden mithilfe einer Datenverbindung aus einer externen Datenquelle abgerufen. Datenverbindungsinformationen werden normalerweise vom Besitzer der externen Datenquelle bereitgestellt, der für das Gewähren der Berechtigungen und Festlegen der erforderlichen Anmeldeinformationstypen zuständig ist. Datenverbindungsinformationen werden als Berichtsdatenquelle gespeichert. Der Datenquellentyp bestimmt, welche Datenerweiterung zum Abrufen der Daten verwendet wird.  
  

  
##  <a name="DataAccess"></a> Grundlegendes zur Datenzugriffstechnologie  
 Zum Abrufen von Daten für ein Berichtsdataset sind mehrere Ebenen von Datenzugriffssoftware erforderlich. In der folgenden Liste wird die Verwendung von Datenzugriffstechnologien in Berichten kurz erläutert:  
  
-   **Anwendung und Benutzeroberfläche:** Die Anwendung Berichts-Generator dient zum Erstellen einer Datenquelle und zum Hinzufügen eines Verweises auf eine freigegebene Datenquelle, eines freigegebenes Datasets oder eines Berichtsteils, der die Datenquellen und die Datasets enthält, von denen er abhängt.  
  
-   **Berichtsdefinitionselemente:** Datenquellen und Datasets sind Teil der Berichtsdefinition. Nachdem ein Bericht auf einem Berichtsserver veröffentlicht wurde, werden freigegebene Datenquellen und freigegebene Datasets unabhängig von der Berichtsdefinition verwaltet.  
  
    -   **Datenquelle und freigegebene Datenquelle:** Dies ist der Teil einer Berichtsdefinition, der die Informationen zum Typ der Datenverarbeitungserweiterung sowie die Verbindungs- und Authentifizierungsinformationen enthält.  
  
    -   **Dataset und Feldauflistung:** Dies ist der Teil einer Berichtsdefinition, der die Abfrage, die Feldauflistung und die Felddatentypen enthält.  
  
-   **Reporting Services-Datenerweiterungen:** Diese integrierten Datenerweiterungen werden mit dem Berichts-Generator installiert. Eine Datenerweiterung stellt Funktionen zur Behandlung der Authentifizierung, von Serveraggregaten und mehrwertigen Parametern bereit.  
  
-   **Datenanbieter:** Diese Software verwaltet die Verbindung und den Abruf der Daten aus der externen Datenquelle. Der Datenanbieter definiert die Verbindungszeichenfolgensyntax. Die meisten Datenerweiterungen werden basierend auf einer Datenanbieterebene erstellt.  
  
-   **Externe Datenquelle:** Aus externen Datenquellen wie Datenbanken, Dateien, Cubes oder Webdiensten werden Berichtsdaten abgerufen.  
  
> [!NOTE]  
>  Wenn Sie nicht mit einem Berichtsserver verbunden sind, stehen Ihnen die mit Berichts-Generator installierten Datenerweiterungen zur Verfügung. Sie greifen im Einzelbenutzermodus von Ihrem Computer aus auf die Daten zu (mit Anmeldeinformationen). Wenn Sie mit einem Berichtsserver verbunden sind, können Sie die auf dem Berichtsserver installierten Datenerweiterungen auswählen. Der Zugriff auf die Daten erfolgt im Mehrbenutzermodus (der Bericht wird von mehreren Benutzern ausgeführt), und Sie verwenden Anmeldeinformationen für den Berichtsserver. Weitere Informationen finden Sie unter [Angeben von Anmeldeinformationen im Berichts-Generator](../specify-credentials-in-report-builder.md).  
  
##  <a name="ReportData"></a> Grundlegendes zu Berichtsdaten  
 In der einfachsten Form zeigt ein Bericht Daten aus einem Berichtsdataset in einem Datenbereich auf der Berichtsseite an, d. h. in nur einer Tabelle, einem Diagramm, einer Matrix oder einem anderen Berichtsdatenbereich. Die Daten in einem Berichtsdataset stammen aus dem ersten Resultset, das für einen mit schreibgeschütztem Zugriff in einer externen Datenquelle ausgeführten Abfragebefehl zurückgegeben wird. Jeder Datenbereich wird bei Bedarf erweitert, um alle Daten aus dem Dataset anzuzeigen.  
  
 Daten in einem Dataset sind im Wesentliche tabellarische Daten. Spalten sind die Felder aus der Datasetabfrage. Zeilen sind die Zeilen aus dem Resultset. Die folgenden verallgemeinerten Datentypen können in einem Bericht verwendet werden:  
  
-   Rechteckige Daten. Daten aus einem Resultset, das in jeder Zeile gleiche Anzahl von Spalten aufweist.  
  
-   Hierarchische Daten werden als vereinfachtes Rowset unterstützt.  
  
    -   Unregelmäßige Hierarchien mit einer unterschiedlichen Anzahl von Spalten für jede Datenzeile werden nicht unterstützt. Dies hat für einige Datenerweiterungen Auswirkungen.  
  
    -   Datenerweiterungen, die mit mehrdimensionalen Datenquellen arbeiten, verwenden das XML for Analysis-Protokoll und rufen Daten nicht als Cellset, sondern als vereinfachtes Rowset ab.  
  
    -   Die XML-Datenerweiterung vereinfacht XML-Daten automatisch zur Verwendung in einem Bericht. Wenn die erste Instanz eines XML-Elements nicht alle Attribute oder Unterelemente enthält, sind die Daten u. U. nicht als Berichtsdaten verfügbar.  
  
-   Rekursive Daten werden unterstützt. Ein Resultset mit einer rekursiven Datenhierarchie enthält alle Informationen zur Hierarchiestruktur in einem rechteckigen Resultset. Die Mitarbeiterstruktur in einem Unternehmen kann z. B. durch eine Tabelle mit zwei Spalten dargestellt werden: ein Mitarbeiter und ein Manager. Jeder Manager ist auch ein Mitarbeiter mit einem Manager. Der Manager auf der obersten Ebene enthält normalerweise NULL oder einen anderen Bezeichner, der angibt, dass dieser Mitarbeiter keinen Manager hat.  
  

  
##  <a name="DataTypes"></a> Arbeiten mit Datentypen  
 Beim Erstellen eines Datasets werden die Datentypen der Felder einer Teilmenge der CLR-Datentypen (Common Language Runtime) von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]zugeordnet. Datentypen, die nicht eindeutig zugeordnet werden können, werden als Zeichenfolgen zurückgegeben. Weitere Informationen zum Arbeiten mit Felddatentypen finden Sie unter [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md). Wenn Sie einen Parameter erstellen, muss es sich beim Datentyp um einen unterstützten Berichtsdefinitions-Datentyp handeln. Weitere Informationen zur Zuordnung von Datentypen des Datenanbieters zu einem Berichtsparameter finden Sie unter [Datentypen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md).  
  

  
##  <a name="HowTo"></a> Themen zur Vorgehensweise  
 Dieser Abschnitt enthält schrittweise Anweisungen zum Arbeiten mit Datenverbindungen, Datenquellen und Datasets.  
  
 [Hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Hinzufügen eines Filters zu einem Dataset &#40;Berichts-Generator und SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  

  
##  <a name="InThisSection"></a> In diesem Abschnitt  
 Die folgenden Themen enthalten Informationen zu jeder integrierten Datenerweiterung.  
  
|Thema|Datenquellentyp|  
|-----------|----------------------|  
|[SQL Server-Verbindungstyp &#40;SSRS&#41;](sql-server-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|[Analysis Services-Verbindungstyp für MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|  
|[PowerPivot-Verbindungstyp &#40;SSRS&#41;](power-pivot-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|  
|[SharePoint-Listenverbindungstyp &#40;SSRS&#41;](sharepoint-list-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint-Liste|  
|[SQL Azure-Verbindungstyp &#40;SSRS&#41;](sql-azure-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
|[SQL Server Parallel Data Warehouse-Verbindungstyp &#40;SSRS&#41;](sql-server-parallel-data-warehouse-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDWfull](../../includes/ssdwfull-md.md)]|  
|[SAP NetWeaver BI-Verbindungstyp &#40;SSRS&#41;](sap-netweaver-bi-connection-type-ssrs.md)|SAP NetWeaver BI|  
|[Hyperion Essbase-Verbindungstyp &#40;SSRS&#41;](hyperion-essbase-connection-type-ssrs.md)|Hyperion Essbase|  
|[OLE DB-Verbindungstyp &#40;SSRS&#41;](ole-db-connection-type-ssrs.md)|OLE DB|  
|[ODBC-Verbindungstyp &#40;SSRS&#41;](odbc-connection-type-ssrs.md)|ODBC|  
|[XML-Verbindungstyp &#40;SSRS&#41;](xml-connection-type-ssrs.md)|XML|  
|[Berichtsmodellverbindung &#40;SSRS&#41;](report-model-connection-ssrs.md)|SMDL-Modell|  
  

  
##  <a name="Related"></a> Verwandte Abschnitte  
 Diese Abschnitte der Dokumentation enthalten umfassende grundlegende Informationen zu Berichtsdaten sowie Informationen zum Definieren, Anpassen und Verwenden der mit Daten zusammenhängenden Teile eines Berichts.  
  
|Thema|Description|  
|-----------|-----------------|  
|[Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)|Bietet eine Übersicht über den Zugriff auf Daten für den Bericht.|  
|[Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md)|Enthält Informationen zu Datenverbindungen und Datenquellen.|  
|[Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)|Enthält Informationen zu eingebetteten und freigegebenen Datasets.|  
|[Datasetfelder-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)|Enthält Informationen zur von der Abfrage generierten Datasetfeldauflistung.|  
|[Von Reporting Services unterstützte Datenquellen (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md) in der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Dokumentation der [Onlinedokumentation](http://go.microsoft.com/fwlink/?linkid=121312) zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Enthält ausführliche Informationen zur Plattform- und Versionsunterstützung für die einzelnen Datenerweiterungen.|  
|[Übersicht über Datenverarbeitungserweiterungen](../extensions/data-processing/data-processing-extensions-overview.md) in der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Dokumentation der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Onlinedokumentation](http://go.microsoft.com/fwlink/?linkid=121312).|Enthält ausführliche Informationen zu Datenerweiterungen für erfahrene Benutzer.|  
  

  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)   
 [Abfrage-Designer &#40;Berichts-Generator&#41;](../query-designers-report-builder.md)  
  
  