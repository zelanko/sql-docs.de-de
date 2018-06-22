---
title: Hinzufügen von Daten zu einem Bericht (Berichts-Generator und SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2e42303-e355-4c1f-bb3b-3338fbdd230d
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: aeae106d4ab76cb6ab04248126b4b32e1e4a160a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147623"
---
# <a name="add-data-to-a-report-report-builder-and-ssrs"></a>Hinzufügen von Daten zu einem Bericht (Berichts-Generator und SSRS)
  Um einem Bericht Daten hinzuzufügen, erstellen Sie Datasets. Jedes Dataset stellt das Resultset der Ausführung eines Abfragebefehls für eine Datenquelle dar. Die Spalten im Resultset sind die Feldauflistung. Die Zeilen im Resultset sind die Daten. Ein Dataset enthält nicht die tatsächlichen Daten. Es enthält die Informationen, die benötigt werden, um einen bestimmten Satz von Daten aus einer Datenquelle abzurufen.  
  
 Zwei Typen von Datasets werden unterschieden: eingebettet und freigegeben. Ein eingebettetes Dataset wird im Bericht definiert und nur von diesem Bericht verwendet. Ein freigegebenes Dataset wird auf dem Berichtsserver oder einer SharePoint-Website definiert und kann von mehreren Berichten verwendet werden. Im Berichts-Generator können Sie im Modus "Freigegebenes Dataset" freigegebene Datasets oder im Modus "Berichts-Designer" eingebettete Datasets erstellen. Im Berichts-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]können freigegebene Datasets als Teil eines Projekts oder eingebettete Datasets als Teil eines Berichts erstellt werden.  
  
-   **Eingebettete Datasets.** Anders als in Anwendungen wie [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel, in denen Sie direkt in einem Arbeitsblatt mit Daten arbeiten, arbeiten Sie im Berichts-Generator oder Berichts-Designer mit Metadaten, die die beim Verarbeiten des Berichts abgerufenen Daten darstellen. Um ein eingebettetes Dataset zu erstellen, wählen Sie die Quelle der Daten aus, und geben Sie eine Abfrage an. Nachdem Sie das Dataset erstellt haben, zeigen Sie im Berichtsdatenbereich die Feldauflistung an. Sie können Daten aus einem Dataset in einem Datenbereich wie einer Tabelle oder einem Diagramm anzeigen. In jedem Datenbereich können Sie die Daten gruppieren, filtern und sortieren, um sie zu organisieren. Nachdem Sie das Berichtslayout entworfen haben, führen Sie den Bericht aus, um die tatsächlichen Daten anzuzeigen.  
  
     In der folgenden Abbildung werden im Berichtsdatenbereich eine Datenquelle mit dem Namen [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)], ein Dataset namens "DataSet1" und fünf Felder in der Datasetfeldauflistung angezeigt. Im Layoutbereich wird eine Tabelle mit Spaltenüberschriften in der obersten Zeile und Tabellenzellen mit Text in der untersten Zeile angezeigt. Der Platzhaltertext [Name] stellt die Metadaten für das Namensfeld dar. Wenn der Bericht ausgeführt wird, wird der Platzhaltertext durch die tatsächlichen Datenwerte ersetzt. Die Tabelle wird entsprechend erweitert, um alle Daten anzuzeigen.  
  
     ![rs_DatendesignundVorschau](../media/rs-datadesignandpreview.gif "rs_DataDesignandPreview")  
  
-   **Freigegebene Datasets.** Erstellen Sie ein freigegebenes Dataset, wenn Sie ein Dataset in mehreren Berichten verwenden möchten. In der Entwurfsansicht für freigegebene Datasets des Berichts-Generators können Sie ein freigegebenes Dataset erstellen und auf einem Berichtsserver oder auf einer SharePoint-Website speichern. Um ein freigegebenes Dataset als Teil eines Projekts zu erstellen, das auf einem Server oder einer Website bereitgestellt werden kann, verwenden Sie den Berichts-Designer.  
  
     Die folgende Abbildung zeigt die Entwurfsansicht für freigegebene Datasets im Berichts-Generator. Sie können die Datenverbindung, die Dataseteigenschaften, die Abfrage und Filter auswählen bzw. ändern, Filter optional als Parameter markieren und die Abfrageergebnisse anzeigen. Anschließend speichern Sie die Änderungen auf dem Server oder der Website.  
  
     ![rs_FreigegebenesDatasetEntwurfsmodus](../media/rs-shareddatasetdesignmode.gif "rs_SharedDatasetDesignMode")  
  
 Weitere Informationen finden Sie unter [Eingebettete und freigegebene Datasets &#40;Berichts-Generator und SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md) und [Eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).  
  
 Sie können einem Bericht auch Datasets hinzufügen, indem Sie Berichtsteile mit den Datasets hinzufügen, von denen sie abhängig sind. [!INCLUDE[ssRBrptparts](../../../includes/ssrbrptparts-md.md)]  
  
 Eine Anleitung zum Erstellen eines Berichts, der Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank anzeigt, finden Sie unter [Tutorial: Erstellen eines einfachen Tabellenberichts (Berichts-Generator)](../tutorial-creating-a-basic-table-report-report-builder.md). Informationen zum Erstellen eines Berichts, der seine eigenen Daten enthält, finden Sie unter [Tutorial: Erstellen eines Quick-Diagrammberichts offline &#40;Berichts-Generator&#41;](../report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="Methods"></a> Hinzufügen von Berichtsdaten  
 Im Berichts-Generator stehen Ihnen folgende Möglichkeiten zum Hinzufügen von Berichtsdaten zur Verfügung.  
  
-   Fügen Sie dem Bericht Berichtsteile von einem Berichtsserver hinzu. Jeder Berichtsteil ist in sich abgeschlossen und schließt abhängige Datasets ein. Die Datasets sind vordefiniert.  
  
-   Verwenden Sie die Assistenten für Tabellen/Matrizen, Diagramme und Karten. Mithilfe der Assistenten können Sie freigegebene Datenquellen und freigegebene Datasets auswählen oder neue Datsets erstellen und mit dem Entwurf des Berichts beginnen.  
  
-   Fügen Sie freigegebene Datasets von einem Berichtsserver hinzu. Freigegebene Datasets sind vordefiniert und geben an, welche Daten aus einer vordefinierten Datenquelle verwendet werden sollen. Wenn Sie dem Bericht ein freigegebenes Dataset hinzufügen, fügen Sie einen Datasetverweis hinzu, der auf die Definition des freigegebenen Datasets verweist.  
  
 Im Berichts-Generator oder Berichts-Designer stehen Ihnen folgende Möglichkeiten zum Hinzufügen von Daten zur Verfügung.  
  
-   Fügen Sie eingebettete Datasets hinzu, die auf freigegebenen Datenquellen basieren.  
  
-   Fügen Sie eingebettete Datasets hinzu, die auf eingebetteten Datenquellen basieren.  
  
> [!NOTE]  
>  Auf einem Berichtsserver werden freigegebene Elemente einzeln oder durch Vererbung der Berechtigungen des Ordners, in dem sie veröffentlicht werden, gesichert. Damit andere Benutzer auf die von Ihnen gespeicherten freigegebenen Datasets zugreifen können, müssen Sie verstehen, wie Berechtigungen gewährt werden. Weitere Informationen finden Sie unter [Sicherheit (Berichts-Generator)](../report-builder/security-report-builder.md) oder [Sichern von freigegebenen Datasetelementen](../security/secure-shared-dataset-items.md).  
  
 Nachdem Sie einem Bericht Daten hinzugefügt haben, können Sie die Daten auf der Berichtsseite anhand von Datenbereichen organisieren, Berichtsteile ändern und diese Änderungen für andere freigeben sowie Benutzern das Einschränken oder Sortieren der im Bericht angezeigten Daten ermöglichen. Weitere Informationen finden Sie in folgenden verwandten Themen:  
  
-   [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
-   [Diagramme &#40;Berichts-Generator und SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md)  
  
-   [Sparklines und Datenbalken &#40;Berichts-Generator und SSRS&#41;](../report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
-   [Indikatoren &#40;Berichts-Generator und SSRS&#41;](../report-design/indicators-report-builder-and-ssrs.md)  
  
-   [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)  
  
-   [Berichtsteile &#40;Berichts-Generator und SSRS&#41;](../report-parts-report-builder-and-ssrs.md)  
  
-   [Filtern, gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
##  <a name="QuickStart"></a> Hinzufügen von Daten mit Berichtsteilen  
 Berichtsteile enthalten die Datasets, von denen sie abhängen. Diese Datasets werden basierend auf freigegebenen Datenquellen erstellt, die auf dem Berichtsserver verfügbar sind. Wenn Sie dem Bericht im Berichts-Generator einen Berichtsteil hinzufügen, werden die abhängigen Datasets dem Bericht hinzugefügt (ähnlich wie beim manuellen Hinzufügen). Ein vordefiniertes Diagramm enthält z.B. ein Dataset. Zeigen Sie eine Vorschau des Berichts an, um die Daten anzuzeigen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBrptparts](../../../includes/ssrbrptparts-md.md)]  
  
 Berichtsteile, freigegebene Datenquellen und freigegebene Datasets werden vorab definiert und auf einem Berichtsserver gespeichert. Für den Zugriff auf diese Elemente müssen Sie den Berichts-Generator im Servermodus öffnen, indem Sie eine Verbindung mit dem Berichtsserver herstellen. Sie können eigene neue Versionen erstellen, wenn Sie über Schreibberechtigungen für den Berichtsserver verfügen.  
  
-   Weitere Informationen finden Sie unter [Berichtsteile &#40;Berichts-Generator und SSRS&#41;](../report-parts-report-builder-and-ssrs.md) und [Berichtsteile im Berichts-Designer &#40;SSRS&#41;](../report-design/report-parts-in-report-designer-ssrs.md).  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
##  <a name="Queries"></a> Abfragen und Abfrage-Designer  
 Zum Angeben der Daten, die Sie aus einer Datenquelle abrufen möchten, erstellen Sie einen Abfragebefehl. Jeder Datenquellentyp stellt einen zugehörigen *Abfrage-Designer* bereit, mit dessen Hilfe Sie die Abfrage erstellen können. Der Abfrage-Designer kann grafisch oder textbasiert sein. In einem grafischen Abfrage-Designer zeigen Sie Metadaten an, die die Daten in der externen Datenquelle darstellen, und erstellen durch Ziehen von Feldern oder Entitäten in die Abfrageentwurfsoberfläche interaktiv eine Abfrage. In einem textbasierten Abfrage-Designer schreiben oder importieren Sie Abfragen in der Abfragesyntax, die von der externen Datenquelle unterstützt wird.  
  
 Im Abfrage-Designer können Sie die Abfrage ausführen, um Beispieldaten anzuzeigen und die Abfragebefehlssyntax zu überprüfen. Spaltennamen im Resultset werden die Feldnamen, die im Berichtsdatenbereich angezeigt werden. Das Resultset muss ein einzelner Satz von Zeilen und Spalten sein, der die gleiche Anzahl von Werten für jede Datenzeile aufweist. Mehrere Resultsets aus einer einzelnen Abfrage werden nicht unterstützt. Unregelmäßige Hierarchien, die keine konstante Anzahl von Spalten enthalten und für jede Zeile eine andere Anzahl von Datenwerten erzeugen können, werden nicht unterstützt.  
  
 Sie benötigen Entwurfszeitanmeldeinformationen, um eine Abfrage auszuführen. Weitere Informationen finden Sie unter [Geben Sie Anmeldeinformationen im Berichts-Generator](../specify-credentials-in-report-builder.md) und [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 Die Kommunikation zwischen einer Datenerweiterung und der externen Datenquelle wird von Datenanbietern behandelt. Die Unterstützung der Abfragebefehlssyntax, Abfrageparameter und Datentypen für Werte im Resultset wird von den einzelnen Datenanbietern bestimmt. Weitere Informationen finden Sie im Thema zum jeweiligen Datenerweiterungstyp und unter [Abfrage-Designer &#40;Berichts-Generator&#41;](../query-designers-report-builder.md).  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
##  <a name="HowTo"></a> Themen zur Vorgehensweise  
 [Hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Hinzufügen, Bearbeiten und Aktualisieren von Feldern im Berichtsdatenbereich &#40;Berichts-Generator und SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)  
  
 [Erstellen einer Abfrage im relationalen Abfrage-Designer &#40;Berichts-Generator und SSRS&#41;](build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)  
  
 [Anzeigen von ausgeblendeten Datasets für Parameterwerte für mehrdimensionale Daten &#40;Berichts-Generator und SSRS&#41;](show-hidden-datasets-for-parameter-values-multidimensional-data.md)  
  
 [Hinzufügen eines Filters zu einem Dataset &#40;Berichts-Generator und SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 [Festlegen eine Meldung über fehlende Daten für einen Datenbereich &#40;Berichts-Generator und SSRS&#41;](set-a-no-data-message-for-a-data-region-report-builder-and-ssrs.md)  
  
 [Zuordnen eines Abfrageparameters zu einem Berichtsparameter &#40;Berichts-Generator und SSRS&#41;](associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs.md)  
  
 [Definieren von Parametern im MDX-Abfrage-Designer für Analysis Services &#40;Berichts-Generator und SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md)  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
##  <a name="Section"></a> In diesem Abschnitt  
 [Report Parts and Datasets in Report Builder (Berichtsteile und Datasets in Berichts-Generator)](report-parts-and-datasets-in-report-builder.md)  
  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
 [Angeben von Anmeldeinformationen im Berichts-Generator](../specify-credentials-in-report-builder.md)  
  
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
 [Datasetfelder-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsentwurfsansicht &#40;Berichts-Generator&#41;](../report-builder/report-design-view-report-builder.md)   
 [Konzepte zum Erstellen von Berichten &#40;Berichts-Generator und SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)  
  
  