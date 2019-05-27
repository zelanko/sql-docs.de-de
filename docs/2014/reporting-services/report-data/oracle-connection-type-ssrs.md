---
title: Oracle-Verbindungstyp (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0021f77134075e18bcae4f3caeea92c1cbcdae73
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66107197"
---
# <a name="oracle-connection-type-ssrs"></a>Oracle-Verbindungstyp (SSRS)
  Wenn Sie Daten aus einer Oracle-Datenbank im Bericht verwenden möchten, benötigen Sie ein Dataset, das auf einer Berichtsdatenquelle vom Typ "Oracle" basiert. Dieser integrierte Datenquellentyp basiert auf dem verwalteten .NET Framework-Anbieter für Oracle und erfordert eine Oracle-Clientsoftwarekomponente.  
  
 Verwenden Sie die Informationen in diesem Thema, um eine Datenquelle zu erstellen. Schrittweise Anweisungen finden Sie unter [hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Verbindungszeichenfolge  
 Erfragen Sie bei Ihrem Datenbankadministrator die Verbindungsinformationen und die Anmeldeinformationen, die verwendet werden sollen, um eine Verbindung mit der Datenquelle herzustellen. In der Verbindungszeichenfolge im folgenden Beispiel wird eine Oracle-Datenbank auf dem Server "Oracle9" mithilfe von Unicode angegeben. Der Servername muss mit dem in der Konfigurationsdatei "Tnsnames.ora" definierten Oracle-Serverinstanzname übereinstimmen.  
  
```  
Data Source="Oracle9"; Unicode="True"  
```  
  
 Weitere Informationen zu Beispielen für Verbindungszeichenfolgen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
##  <a name="Credentials"></a> Anmeldeinformationen  
 Anmeldeinformationen sind erforderlich, um Abfragen auszuführen und den Bericht lokal oder vom Berichtsserver aus in der Vorschau anzuzeigen.  
  
 Nachdem Sie den Bericht veröffentlicht haben, müssen Sie eventuell die Anmeldeinformationen für die Datenquelle ändern, sodass die Berechtigungen zum Abrufen der Daten beim Ausführen des Berichts auf dem Berichtsserver gültig sind.  
  
 Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) oder [angeben von Anmeldeinformationen im Berichts-Generator](../specify-credentials-in-report-builder.md).  
  

  
##  <a name="Query"></a> Abfragen  
 Sie können ein Dataset erstellen, indem Sie in einer Dropdownliste eine gespeicherte Prozedur auswählen oder eine SQL-Abfrage erstellen. Zum Erstellen einer Abfrage muss der textbasierte Abfrage-Designer verwendet werden. Weitere Informationen finden Sie unter [Benutzeroberfläche des textbasierten Abfrage-Designers (Berichts-Generator)](text-based-query-designer-user-interface-report-builder.md).  
  
 Sie können gespeicherte Prozeduren angeben, die nur ein Resultset zurückgeben. Cursorbasierte Abfragen werden nicht unterstützt.  
  
##  <a name="Parameters"></a> Parameter  
 Wenn die Abfrage Abfragevariablen enthält, werden automatisch entsprechende Berichtsparameter generiert. Benannte Parameter werden von dieser Erweiterung unterstützt. Oracle Version 9 oder höher unterstützt mehrwertige Parameter.  
  
 Berichtsparameter werden mit Standardeigenschaftswerten erstellt, die Sie ggf. ändern müssen. Jeder Berichtsparameter ist z. B. vom Datentyp **Text**. Die Standardwerte müssen möglicherweise nach dem Erstellen der Berichtsparameter geändert werden. Weitere Informationen finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)" basiert.  
  

  
##  <a name="Remarks"></a> Hinweise  
 Bevor Sie eine Verbindung mit einer Oracle-Datenquelle herstellen können, muss der Systemadministrator die Version des .NET-Datenanbieters für Oracle installieren, die das Abrufen von Daten aus der Oracle-Datenbank unterstützt. Dieser Datenanbieter muss auf dem gleichen Computer wie der Berichts-Generator und auf dem Berichtsserver installiert werden.  
  
 Weitere Informationen finden Sie unter den folgenden Links:  
  
-   [Verwenden des .NET Framework-Datenanbieters für Oracle](https://go.microsoft.com/fwlink/?LinkId=112314) bei msdn.microsoft.com  
  
-   [Verwenden von Reporting Services zum Konfigurieren und Zugreifen auf eine Oracle-Datenquelle](https://support.microsoft.com/kb/834305)  
  
-   [Hinzufügen von Berechtigungen für den NETZWERKDIENST-Sicherheitsprinzipal](https://support.microsoft.com/kb/870668)  
  
###### <a name="alternate-data-extensions"></a>Alternative Datenerweiterungen  
 Sie können Daten auch mit einem OLE DB-Datenquellentyp aus einer Oracle-Datenbank abrufen. Weitere Informationen finden Sie unter [OLE DB-Verbindungstyp &#40;SSRS&#41;](ole-db-connection-type-ssrs.md).  
  
###### <a name="report-models"></a>Berichtsmodelle  
 Sie können auch auf einer Oracle-Datenbank basierende Modelle erstellen.  
  
###### <a name="platform-and-version-information"></a>Plattform- und Versionsinformationen  
 Weitere Informationen zur Unterstützung einzelner Plattformen und Versionen finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Dokumentation der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-[Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312).  
  

  
##  <a name="HowTo"></a> Themen zur Vorgehensweise  
 Dieser Abschnitt enthält schrittweise Anweisungen zum Arbeiten mit Datenverbindungen, Datenquellen und Datasets.  
  
 [Hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Hinzufügen eines Filters zu einem Dataset &#40;Berichts-Generator und SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 
  
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
  
 [Von Reporting Services unterstützte Datenquellen (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md) in der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Dokumentation der [Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312) zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
 Enthält ausführliche Informationen zur Plattform- und Versionsunterstützung für die einzelnen Datenerweiterungen.  
  

  
## <a name="see-also"></a>Siehe auch  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
