---
title: Oracle-Verbindungstyp (Berichts-Generator und Power BI-Berichtsserver) | Microsoft-Dokumentation
ms.date: 02/26/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 216ab9a4d5dcfe18fe6346eadeec8778415cdeb4
ms.sourcegitcommit: 1035d11c9fb7905a012429ee80dd5b9d00d9b03c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634839"
---
# <a name="oracle-connection-type-report-builder--power-bi-report-server--microsoft-docs"></a>Oracle-Verbindungstyp ((Berichts-Generator und Power BI-Berichtsserver) | Microsoft-Dokumentation)

Wenn Sie Daten aus einer Oracle-Datenbank im Bericht verwenden möchten, benötigen Sie ein Dataset, das auf einer Berichtsdatenquelle vom Typ "Oracle" basiert. Dieser integrierte Datenquellentyp verwendet direkt den Oracle-Datenanbieter und erfordert eine Oracle-Clientsoftwarekomponente. Dieser Artikel erläutert, wie Sie Treiber für Reporting Services, den Power BI-Berichtsserver und den Berichts-Generator herunterladen.

## <a name="64-bit-drivers-for-the-report-servers"></a>64-Bit-Treiber für die Berichtsserver

Der Power BI-Berichtsserver sowie SQL Server Reporting Services 2016 und 2017 verwenden Managed ODP.NET. Die folgenden Schritte sind nur erforderlich, wenn Sie die neuesten 18x-Treiber verwenden. Es wird angenommen, dass die Dateien in „c:\oracle64“ installiert wurden.

1. Installieren Sie den [Oracle 64-Bit ODAC Oracle Universal Installer (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdeploy-4242173.html) von der Oracle-Downloadwebsite. 
2. Registrieren Sie ODP.NET Managed Client bei GAC:  C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. Fügen Sie ODP.NET Managed Client-Einträge zu „machine.config“ hinzu:  C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /productversion:4.122.18.3

### <a name="power-bi-reports-use-unmanaged-odpnet"></a>Power BI-Berichte verwenden Unmanaged ODP.NET

Power BI-Berichte verwenden **Unmanaged ODP.NET**. Führen Sie diese Schritte aus, um Unmanaged ODP.NET zu registrieren:

1. Registrieren Sie ODP.NET Unmanaged Client bei GAC:

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. Fügen Sie ODP.NET Unmanaged Client-Einträge zu „machine.config“ hinzu:

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3
 
## <a name="32-bit-drivers-for-report-builder"></a>32-Bit-Treiber für den Berichts-Generator

Die folgenden Schritte sind nur erforderlich, wenn Sie die neuesten 18x-Treiber verwenden. Es wird angenommen, dass die Dateien in „c:\oracle32“ installiert wurden.

1. Installieren Sie den [Oracle 32-Bit ODAC Oracle Universal Installer (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdev-4242174.html) von der Oracle-Downloadwebsite.
2. Registrieren Sie ODP.NET Managed Client bei GAC:  C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. Fügen Sie ODP.NET Managed Client-Einträge zu „machine.config“ hinzu:  C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /productversion:4.122.18.3

### <a name="power-bi-reports-use-unmanaged-odpnet"></a>Power BI-Berichte verwenden Unmanaged ODP.NET  

Power BI-Berichte verwenden **Unmanaged ODP.NET**. Führen Sie diese Schritte aus, um Unmanaged ODP.NET zu registrieren:

1. Registrieren Sie ODP.NET Unmanaged Client bei GAC:

   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. Fügen Sie ODP.NET Unmanaged Client-Einträge zu „machine.config“ hinzu:

   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3
 

 Verwenden Sie die Informationen in diesem Thema, um eine Datenquelle zu erstellen. Eine Schritt-für-Schritt-Anleitung finden Sie unter [Hinzufügen und Prüfen einer Datenverbindung &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Verbindungszeichenfolge  
 Erfragen Sie bei Ihrem Datenbankadministrator die Verbindungsinformationen und die Anmeldeinformationen, die verwendet werden sollen, um eine Verbindung mit der Datenquelle herzustellen. In der Verbindungszeichenfolge im folgenden Beispiel wird eine Oracle-Datenbank auf dem Server "Oracle18" im Unicode-Format angegeben. Der Servername muss mit dem in der Konfigurationsdatei "Tnsnames.ora" definierten Oracle-Serverinstanzname übereinstimmen.  
  
```  
Data Source="Oracle"; Unicode="True"  
```  
  
 Weitere Beispiele für Verbindungszeichenfolgen finden Sie unter [Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
##  <a name="Credentials"></a> Anmeldeinformationen  
 Anmeldeinformationen sind erforderlich, um Abfragen auszuführen und den Bericht lokal oder vom Berichtsserver aus in der Vorschau anzuzeigen.  
  
 Nachdem Sie den Bericht veröffentlicht haben, müssen Sie eventuell die Anmeldeinformationen für die Datenquelle ändern, sodass die Berechtigungen zum Abrufen der Daten beim Ausführen des Berichts auf dem Berichtsserver gültig sind.  
  
 Weitere Informationen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](specify-credential-and-connection-information-for-report-data-sources.md).  
  
  
##  <a name="Query"></a> Abfragen  
 Sie können ein Dataset erstellen, indem Sie in einer Dropdownliste eine gespeicherte Prozedur auswählen oder eine SQL-Abfrage erstellen. Zum Erstellen einer Abfrage muss der textbasierte Abfrage-Designer verwendet werden. Weitere Informationen finden Sie unter [Benutzeroberfläche des textbasierten Abfrage-Designers (Berichts-Generator)](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md).  
  
 Sie können gespeicherte Prozeduren angeben, die nur ein Resultset zurückgeben. Cursorbasierte Abfragen werden nicht unterstützt.  
  
##  <a name="Parameters"></a> Parameter  
 Wenn die Abfrage Abfragevariablen enthält, werden automatisch entsprechende Berichtsparameter generiert. Benannte Parameter werden von dieser Erweiterung unterstützt. Oracle Version 9 oder höher unterstützt mehrwertige Parameter.  
  
 Berichtsparameter werden mit Standardeigenschaftswerten erstellt, die Sie ggf. ändern müssen. Jeder Berichtsparameter ist z. B. vom Datentyp **Text**. Die Standardwerte müssen möglicherweise nach dem Erstellen der Berichtsparameter geändert werden. Weitere Informationen finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)" basiert.  
  
  
##  <a name="Remarks"></a> Hinweise  
 Bevor Sie eine Verbindung mit einer Oracle-Datenquelle herstellen können, muss der Systemadministrator die Version des .NET-Datenanbieters für Oracle installieren, die das Abrufen von Daten aus der Oracle-Datenbank unterstützt. Dieser Datenanbieter muss auf dem gleichen Computer wie der Berichts-Generator und auf dem Berichtsserver installiert werden.  
  
 Weitere Informationen finden Sie in den folgenden Artikeln:  
  
-   [Verwenden von Reporting Services zum Konfigurieren und Zugreifen auf eine Oracle-Datenquelle](https://docs.microsoft.com/archive/blogs/dataaccesstechnologies/configure-oracle-data-source-for-sql-server-reporting-services-ssdt-and-report-server)  
-   [Hinzufügen von Berechtigungen für den NETZWERKDIENST-Sicherheitsprinzipal](https://support.microsoft.com/kb/870668)  
  
### <a name="alternate-data-extensions"></a>Alternative Datenerweiterungen 
 
 Sie können Daten auch mit einem OLE DB-Datenquellentyp aus einer Oracle-Datenbank abrufen. Weitere Informationen finden Sie unter [OLE DB-Verbindungstyp &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md).  

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions" 
### <a name="report-models"></a>Berichtsmodelle  

 Sie können auch auf einer Oracle-Datenbank basierende Modelle erstellen.  
::: moniker-end
   
### <a name="platform-and-version-information"></a>Plattform- und Versionsinformationen  

 Weitere Informationen zur Plattform- und Versionsunterstützung finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  

  
## <a name="see-also"></a>Weitere Informationen

 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
