---
title: Analysis Services-Verbindungstyp für MDX (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: bd2e7148-3124-4e07-9734-22333127c3be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6992356bc7a61287854d11fb5ed62067c5a14805
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59967866"
---
# <a name="analysis-services-connection-type-for-mdx-ssrs"></a>Analysis Services-Verbindungstyp für MDX (SSRS)
  Wenn Sie Daten aus einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Cube in den Bericht einschließen möchten, benötigen Sie ein Dataset, das auf einer Berichtsdatenquelle vom Typ " [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]" basiert. Dieser integrierte Datenquellentyp basiert auf der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenerweiterung. Sie können Metadaten über Dimensionen, Hierarchien, Ebenen, Key Performance Indicators (KPIs), Measures und Attribute zur Verwendung als Berichtsdaten aus einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Cube abrufen.  
  
 Diese Datenverarbeitungserweiterung unterstützt mehrwertige Parameter, Serveraggregate und getrennt von der Verbindungszeichenfolge verwaltete Anmeldeinformationen.  
  
 Verwenden Sie die Informationen in diesem Thema, um eine Datenquelle zu erstellen. Schrittweise Anweisungen finden Sie unter [hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Verbindungszeichenfolge  
 Wenn Sie eine Verbindung mit einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Cube herstellen, stellen Sie eine Verbindung mit dem Datenbankobjekt in einer Analysis Services-Instanz auf einem Server her. Die Datenbank kann mehrere Cubes enthalten. Sie geben den Cube beim Erstellen der Abfrage im Abfrage-Designer an. Das folgenden Beispiel zeigt eine Verbindungszeichenfolge:  
  
```  
data source=<server name>;initial catalog=<database name>  
```  
  
 Weitere Beispiele für Verbindungszeichenfolgen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
  
  
##  <a name="Credentials"></a> Anmeldeinformationen  
 Anmeldeinformationen sind erforderlich, um Abfragen auszuführen und den Bericht lokal oder vom Berichtsserver aus in der Vorschau anzuzeigen.  
  
 Nachdem Sie den Bericht veröffentlicht haben, müssen Sie eventuell die Anmeldeinformationen für die Datenquelle ändern, sodass die Berechtigungen zum Abrufen der Daten beim Ausführen des Berichts auf dem Berichtsserver gültig sind.  
  
 Auf einem Berichterstellungsclient sind die folgenden Optionen zum Angeben von Anmeldeinformationen verfügbar:  
  
-   Aktueller Windows-Benutzer (auch bekannt als integrierte Sicherheit).  
  
-   Verwendung eines gespeicherten Benutzernamens und eines gespeicherten Kennworts.  
  
-   Aufforderung zur Eingabe der Anmeldeinformationen. Diese Option unterstützt nur die integrierte Windows-Sicherheit.  
  
-   Anmeldeinformationen sind nicht erforderlich. Zur Verwendung dieser Option müssen Sie zuvor das Konto für die unbeaufsichtigte Ausführung auf dem Berichtsserver konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren des unbeaufsichtigten Ausführungskontos (SSRS-Konfigurations-Manager)](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in der [Reporting Services-Dokumentation](https://go.microsoft.com/fwlink/?linkid=121312) auf msdn.microsoft.com.  
  
 Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) oder [angeben von Anmeldeinformationen im Berichts-Generator](../specify-credentials-in-report-builder.md).  
  
  
  
##  <a name="Query"></a> Abfragen  
 Nachdem Sie eine Datenverbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenquelle hergestellt haben, erstellen Sie ein Dataset, und Sie definieren eine MDX-Abfrage (Multidimensional Expressions), die die aus dem Cube abzurufenden Daten angibt. Verwenden Sie den grafischen MDX-Abfrage-Designer, um die zugrunde liegenden Datenstrukturen der Datenquelle zu durchsuchen und auszuwählen.  
  
 Zum Angeben einer Abfrage stehen Ihnen folgende Methoden zur Auswahl:  
  
-   Erstellen Sie eine Abfrage interaktiv. Der Analysis Services-MDX-Abfrage-Designer unterstützt die folgenden Ansichten:  
  
    -   **Entwurfsansicht** Ziehen Sie Dimensionen, Elemente, Elementeigenschaften, Measures und KPIs aus dem Metadatenbrowser in den Bereich **Daten** , um eine MDX-Abfrage zu erstellen. Ziehen Sie berechnete Elemente aus dem Bereich „Berechnete Elemente“ in den Datenbereich, um zusätzliche Datasetfelder zu definieren.  
  
    -   **Abfrageansicht** Ziehen Sie Dimensionen, Elemente, Elementeigenschaften, Measures und KPIs aus dem Metadatenbrowser in den Bereich "Abfrage", um eine MDX-Abfrage zu erstellen. Sie können MDX-Text direkt im Abfragebereich bearbeiten. Ziehen Sie berechnete Elemente aus dem Bereich „Berechnete Elemente“ in den Abfragebereich, um zusätzliche Datasetfelder zu definieren.  
  
     Weitere Informationen finden Sie unter [Benutzeroberfläche des MDX-Abfrage-Designers für Analysis Services (Berichts-Generator)](../analysis-services-mdx-query-designer-user-interface-report-builder.md).  
  
-   Importieren Sie eine vorhandene MDX-Abfrage aus einem Bericht. Verwenden Sie die Schaltfläche **Abfrage importieren** , um eine RDL-Datei auszuwählen und eine Abfrage zu importieren. Sie können eine Abfrage aus einem Bericht importieren, der ein eingebettetes, auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenquelle beruhendes Dataset enthält. Das direkte Importieren einer MDX-Abfrage aus einer MDX-Datei wird nicht unterstützt.  
  
 Führen Sie die Abfrage zur Entwurfszeit aus, um ein Resultset anzuzeigen. Die Abfrageergebnisse werden automatisch als vereinfachtes Rowset abgerufen. Die Feldauflistung für ein Dataset wird mit den Spalten aus dem Resultset einer Abfrage aufgefüllt. Nachdem Sie die Abfrage erstellt haben, zeigen Sie die aus den Metadaten generierte Datasetfeldauflistung im Berichtsdatenbereich an. Bei der Ausführung des Berichts werden die tatsächlichen Daten aus der externen Datenquelle zurückgegeben.  
  
 Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenverarbeitungserweiterung unterstützt erweiterte Datasetfeldeigenschaften. Bei diesen Eigenschaften handelt es sich um Werte, die in der externen Datenquelle verfügbar sind, aber nicht im Berichtsdatenbereich angezeigt werden. Über die `Fields`-Auflistung können Sie in Ihrem Bericht erweiterte Feldeigenschaften verwenden, die von der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenverarbeitungserweiterung unterstützt werden. Für Eigenschaften, die Werte für die Datenquelle besitzen, können Sie auf vordefinierte Eigenschaftswerte wie `FormattedValue`, `Color` oder `UniqueName` zugreifen. Weitere Informationen finden Sie unter [Erweiterte Feldeigenschaften für eine Analysis Services-Datenbank &#40;SSRS&#41;](extended-field-properties-for-an-analysis-services-database-ssrs.md).  
  
  
  
##  <a name="Parameters"></a> Parameter  
 Erstellen Sie im Filterbereich des Abfrage-Designers einen Filter, und markieren Sie ihn als Parameter, um Abfrageparameter einzuschließen. Für jeden Filter wird automatisch ein Dataset erstellt, um die verfügbaren Werte bereitzustellen. Diese Datasets werden standardmäßig nicht im Berichtsdatenbereich angezeigt. Weitere Informationen finden Sie unter [Definieren von Parametern im MDX-Abfrage-Designer für Analysis Services (Berichts-Generator und SSRS)](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) und [Anzeigen von ausgeblendeten Datasets für Parameterwerte für mehrdimensionale Daten (Berichts-Generator und SSRS)](show-hidden-datasets-for-parameter-values-multidimensional-data.md).  
  
 Alle Berichtsparameter sind standardmäßig vom Datentyp **Text**. Die Standardwerte müssen möglicherweise nach dem Erstellen der Berichtsparameter geändert werden. Weitere Informationen finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)" basiert.  
  
  
  
##  <a name="Remarks"></a> Hinweise  
 Die Analysis Services-Datenerweiterung basiert auf dem XMLA-Protokoll (XML for Analysis). Resultsets von Cubes werden durch das XMLA-Protokoll als vereinfachtes Rowset abgerufen. Unregelmäßige Hierarchien werden nicht unterstützt. Weitere Informationen zu Hierarchien finden Sie unter [Unregelmäßige Hierarchien](../../analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md).  
  
 Sie können auch mit dem OLE DB-Datenquellentyp Daten aus einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Cube abrufen. Weitere Informationen finden Sie unter [OLE DB-Verbindungstyp &#40;SSRS&#41;](ole-db-connection-type-ssrs.md).  
  
 Weitere Informationen zur Versionsunterstützung finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Dokumentation der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-[Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312).  
  
  
  
##  <a name="Related"></a> Verwandte Abschnitte  
 Diese Abschnitte der Dokumentation enthalten umfassende grundlegende Informationen zu Berichtsdaten sowie Informationen zum Definieren, Anpassen und Verwenden der mit Daten zusammenhängenden Teile eines Berichts.  
  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)  
 Bietet eine Übersicht über den Zugriff auf Daten für den Bericht.  
  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Enthält Informationen zu Datenverbindungen und Datenquellen.  
  
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Enthält Informationen zu eingebetteten und freigegebenen Datasets.  
  
 [Datasetfelder-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Enthält Informationen zur von der Abfrage generierten Datasetfeldauflistung.  
  
 [Erweiterte Feldeigenschaften für eine Analysis Services-Datenbank &#40;SSRS&#41;](extended-field-properties-for-an-analysis-services-database-ssrs.md)  
 Enthält Informationen zu zusätzlichen Feldern, die über den XMLA-Datenanbieter zur Verfügung stehen.  
  
 [Von Reporting Services unterstützte Datenquellen (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md) in der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Dokumentation der [Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312) zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Enthält ausführliche Informationen zur Plattform- und Versionsunterstützung für die einzelnen Datenerweiterungen.  
  
  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
