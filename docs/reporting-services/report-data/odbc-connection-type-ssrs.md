---
title: ODBC-Verbindungstyp (SSRS) | Microsoft-Dokumentation
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 24163866-f37a-4c38-982e-c3d79bf64d4c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 11e1f8b080d76dce34b621e79e28a0771431f61c
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73593978"
---
# <a name="odbc-connection-type-ssrs"></a>OBDC-Verbindungstyp (SSRS)
  Wenn Sie Daten von einem ODBC-Datenanbieter einschließen möchten, benötigen Sie ein Dataset, das auf einer Berichtsdatenquelle vom Typ "ODBC" basiert. Dieser integrierte Datenquellentyp basiert auf der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -ODBC-Datenverarbeitungserweiterung.  
  
 Verwenden Sie die Informationen in diesem Thema, um eine Datenquelle zu erstellen. Eine Schritt-für-Schritt-Anleitung finden Sie unter [Hinzufügen und Prüfen einer Datenverbindung &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Verbindungszeichenfolge  
 Die Verbindungszeichenfolge für die ODBC-Datenverarbeitungserweiterung hängt vom gewünschten ODBC-Treiber ab. Eine typische Verbindungszeichenfolge enthält Name-Wert-Paare, die vom Treiber unterstützt werden. Die folgende Verbindungszeichenfolge gibt z. B. den ODBC-Treiber für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client und die AdventureWorks-Datenbank an:  
  
```  
Driver={SQL Server Native Client 10.0};Server=server;Database=AdventureWorks;Trusted_Connection=yes;  
```  
  
  
##  <a name="Credentials"></a> Anmeldeinformationen  
 Anmeldeinformationen sind erforderlich, um Abfragen auszuführen und den Bericht lokal oder vom Berichtsserver aus in der Vorschau anzuzeigen.  
  
 Nachdem Sie den Bericht veröffentlicht haben, müssen Sie eventuell die Anmeldeinformationen für die Datenquelle ändern, sodass die Berechtigungen zum Abrufen der Daten beim Ausführen des Berichts auf dem Berichtsserver gültig sind.  
  
 Wenn Sie die ODBC-Datenquelle so konfigurieren, dass ein Kennwort angegeben werden muss oder das Kennwort in der Verbindungszeichenfolge enthalten ist, und Benutzer das Kennwort mit Sonderzeichen (z. B. Satzzeichen) eingeben, können einige zugrunde liegende Datenquellentreiber die Sonderzeichen nicht überprüfen. Beim Verarbeiten des Berichts kann die Meldung "Kein zulässiges Kennwort" auf dieses Problem hinweisen. Wenn das Kennwort nicht geändert werden kann, können Sie mit Ihrem Datenbankadministrator Maßnahmen ergreifen, damit die entsprechenden Anmeldeinformationen auf dem Berichtsserver als Teil eines ODBC-Datenquellennamens des Systems (Data Source Name oder DSN) gespeichert werden. Weitere Informationen finden Sie unter "OdbcConnection.ConnectionString" in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK-Dokumentation.  
  
> [!NOTE]  
>  Es wird empfohlen, der Verbindungszeichenfolge keine Anmeldeinformationen (z. B. Kennwörter) hinzuzufügen. Der Berichts-Generator enthält eine separate Registerkarte im Dialogfeld **Datenquelle** , auf der Sie Anmeldeinformationen eingeben können.  
  
 Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen &#40;Berichts-Generator und SSRS&#41; ](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) oder [Angeben von Anmelde Informationen und Verbindungsinformationen für Berichtsdaten Quellen](specify-credential-and-connection-information-for-report-data-sources.md).  
  
  
##  <a name="Remarks"></a> Hinweise  
 ODBC ist eine frühe Datenzugriffstechnologie, die OLEDB vorausgegangen ist. ODBC unterstützt nur relationale Datenquellen. ODBC-Datenanbieter werden als *Treiber*bezeichnet. ODBC-Treiber werden von Microsoft und Drittanbietern bereitgestellt. Microsoft Office installiert z. B. ODBC-Treiber, die eine Verbindung mit Office-Dateiformaten herstellen.  
  
 Bevor Sie eine ODBC-Verbindungszeichenfolge erstellen können, müssen Sie ODBC-Treiber installieren und einen Computer- oder System-DSN erstellen. Zum erfolgreichen Abrufen der gewünschten Daten muss eine vom Treiber unterstützte Abfragesyntax angegeben werden. Die Parameterunterstützung variiert abhängig vom Treiber. Weitere Informationen finden Sie in den spezifischen Themen für den ausgewählten Treiber, z.B. [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md).  
  
###### <a name="platform-and-version-information"></a>Plattform- und Versionsinformationen  
 Weitere Informationen zu bestimmten ODBC-Datenanbietern finden Sie [unter von Reporting Services &#40;SSRS&#41;unterstützte Datenquellen](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).
  
  
##  <a name="HowTo"></a> Themen zur Vorgehensweise  
 Dieser Abschnitt enthält schrittweise Anweisungen zum Arbeiten mit Datenverbindungen, Datenquellen und Datasets.  
  
 [Hinzufügen und Prüfen einer Datenverbindung &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Hinzufügen eines Filters zu einem Dataset &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="Related"></a> Verwandte Abschnitte  
 Diese Abschnitte der Dokumentation enthalten umfassende grundlegende Informationen zu Berichtsdaten sowie Informationen zum Definieren, Anpassen und Verwenden der mit Daten zusammenhängenden Teile eines Berichts.  
  
 [Berichtsdatasets &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Bietet eine Übersicht über den Zugriff auf Daten für den Bericht.  
  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
 Enthält Informationen zu Datenverbindungen und Datenquellen.  
  
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Enthält Informationen zu eingebetteten und freigegebenen Datasets.  
  
 [Datasetfelder-Sammlung &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Enthält Informationen zur von der Abfrage generierten Datasetfeldauflistung.  
  
 [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) Enthält ausführliche Informationen zur Plattform- und Versionsunterstützung für die einzelnen Datenerweiterungen.  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
