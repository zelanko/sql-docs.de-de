---
title: OLE DB-Verbindungstyp (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d00cb13b-e1c2-4300-a195-3da1430a2df1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d79ef7ae57894470f58701fd51a1d9ddd1b7126
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68891992"
---
# <a name="ole-db-connection-type-ssrs"></a>OLE-Datenbank-Verbindungstyp (SSRS)
  Wenn Sie Daten von einem OLE DB-Datenanbieter einschließen möchten, benötigen Sie ein Dataset, das auf einer Berichtsdatenquelle vom Typ "OLE DB" basiert. Dieser integrierte Datenquellentyp basiert auf der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-OLE DB-Datenverarbeitungserweiterung.  
  
 OLE DB ist eine Datenzugriffstechnologie, die es Clients ermöglicht, eine Verbindung mit einer Vielzahl von Datenanbietern herzustellen. Nachdem Sie den Datenquellentyp OLE DB ausgewählt haben, müssen Sie einen bestimmten Datenanbieter auswählen. Die Unterstützung für Funktionen wie Parameter und Anmeldeinformationen hängt vom ausgewählten Datenanbieter ab.  
  
 Verwenden Sie die Informationen in diesem Thema, um eine Datenquelle zu erstellen. Schritt-für-Schritt-Anweisungen finden [Sie unter Hinzufügen und Überprüfen einer Datenverbindung oder einer Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="connection-string"></a><a name="Connection"></a> Verbindungszeichenfolge  
 Die Verbindungszeichenfolge für die OLE DB-Datenverarbeitungserweiterung hängt vom gewünschten Datenanbieter ab. Eine typische Verbindungszeichenfolge enthält Name-Wert-Paare, die vom Datenanbieter unterstützt werden. Die folgende Verbindungszeichenfolge gibt z. B. den OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client und die AdventureWorks-Datenbank an:  
  
```  
Provider=SQLNCLI10.1;Data Source=server; Initial Catalog=AdventureWorks  
```  
  
 Die verwendete Verbindungszeichenfolge hängt von der externen Datenquelle ab, mit der Sie eine Verbindung herstellen. Wenn Sie die für einen Datenanbieter spezifischen Verbindungszeichenfolgen-Eigenschaften festlegen möchten, klicken Sie im Dialogfeld **Datenquelleneigenschaften** auf der Registerkarte **Allgemein** auf die Schaltfläche **Erstellen** , um das Dialogfeld **Verbindungseigenschaften** zu öffnen. Legen Sie erweiterte Datenquelleneigenschaften im Dialogfeld **Datenlinkeigenschaften** fest.  
  
 Weitere Beispiele für Verbindungszeichenfolgen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> Anmeldeinformationen  
 Anmeldeinformationen sind erforderlich, um Abfragen auszuführen und den Bericht lokal oder vom Berichtsserver aus in der Vorschau anzuzeigen.  
  
 Nachdem Sie den Bericht veröffentlicht haben, müssen Sie eventuell die Anmeldeinformationen für die Datenquelle ändern, sodass die Berechtigungen zum Abrufen der Daten beim Ausführen des Berichts auf dem Berichtsserver gültig sind.  
  
 Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) Zeichenfolgen in Reporting Services oder [Angeben von Anmelde Informationen in Berichts-Generator](../specify-credentials-in-report-builder.md).  
  
###### <a name="special-characters-in-a-password"></a>Sonderzeichen in Kennwörtern  
 Wenn Sie die OLE DB-Datenquelle so konfigurieren, dass ein Kennwort angegeben werden muss oder das Kennwort in der Verbindungszeichenfolge enthalten ist, und Benutzer das Kennwort mit Sonderzeichen (z. B. Satzzeichen) eingeben, können einige zugrunde liegende Datenquellentreiber die Sonderzeichen nicht überprüfen. Wenn Sie den Bericht verarbeiten, ist die Meldung "Kein zulässiges Kennwort" möglicherweise ein Anzeichen für dieses Problem.  
  
> [!NOTE]  
>  Es wird empfohlen, der Verbindungszeichenfolge keine Anmeldeinformationen (z. B. Kennwörter) hinzuzufügen. Der Berichts-Generator enthält eine separate Registerkarte im Dialogfeld **Datenquelle** , auf der Sie Anmeldeinformationen eingeben können.  
  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> Parameter  
 Einige OLE DB-Anbieter unterstützen unbenannte Parameter und nicht benannte Parameter. Parameter werden anhand der Position übergeben, indem in der Abfrage ein Platzhalter verwendet wird. Das Platzhalterzeichen hängt von der vom Datenanbieter unterstützten Syntax ab.  
  
 
  
##  <a name="remarks"></a><a name="Remarks"></a> Hinweise  
 OLE DB ist eine systemeigene Technologie zum Erstellen von Datenanbietern für bestimmte Datenquellen. OLE DB basiert auf COM-Schnittstellen (Component Object Model). Die OLE DB-Technologie wurde nach ODBC- und vor ADO.NET-Datenanbietern entwickelt. OLE DB-Datenanbieter werden wie andere COM-Komponenten im Betriebssystem registriert. OLE DB-Datenanbieter sind von Microsoft und Drittanbietern verfügbar. Microsoft stellt auch MSDASQL bereit, einen OLE DB-Datenanbieter, der die Kommunikation mit ODBC-Treibern überbrückt. Weitere Informationen finden Sie unter [ODBC-Verbindungstyp (SSRS)](odbc-connection-type-ssrs.md).  
  
 Zum erfolgreichen Abrufen der gewünschten Daten muss eine vom Datenanbieter unterstützte Abfragesyntax angegeben werden. Die Parameterunterstützung variiert abhängig vom Datenanbieter. Weitere Informationen finden Sie in den spezifischen Themen für den ausgewählten Datenanbieter. Beispiel:  
  
-   [OLE DB-Anbieter für Analysis Services &#40;Analysis Services – mehrdimensionale Daten&#41;](../../analysis-services/dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md)  
  
-   [Verwenden des .NET Framework-Datenanbieters für Oracle](https://go.microsoft.com/fwlink/?LinkId=112314)  
  
-   [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
 Weitere Informationen zu bestimmten OLE DB-Datenanbietern finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dokumentation der -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312).  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a>Themen zur Vorgehensweise  
 Dieser Abschnitt enthält schrittweise Anweisungen zum Arbeiten mit Datenverbindungen, Datenquellen und Datasets.  
  
 [Hinzufügen und Überprüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Hinzufügen eines Filters zu einem Dataset &#40;Berichts-Generator und SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="related-sections"></a><a name="Related"></a> Verwandte Abschnitte  
 Diese Abschnitte der Dokumentation enthalten umfassende grundlegende Informationen zu Berichtsdaten sowie Informationen zum Definieren, Anpassen und Verwenden der mit Daten zusammenhängenden Teile eines Berichts.  
  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)  
 Bietet eine Übersicht über den Zugriff auf Daten für den Bericht.  
  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Enthält Informationen zu Datenverbindungen und Datenquellen.  
  
 [Melden Sie eingebettete Datasets und freigegebene Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Enthält Informationen zu eingebetteten und freigegebenen Datasets.  
  
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Enthält Informationen zur von der Abfrage generierten Datasetfeldauflistung.  
  
 [Von Reporting Services unterstützte Datenquellen (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md) in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dokumentation der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312) zu .  
 Enthält ausführliche Informationen zur Plattform- und Versionsunterstützung für die einzelnen Datenerweiterungen.  
  
 
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts Parameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtern, gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
