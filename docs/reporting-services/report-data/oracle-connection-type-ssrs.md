---
title: Oracle-Verbindungstyp (SSRS und Power BI-Berichtsserver)
description: Mithilfe der Informationen in diesem Artikel zum Oracle-Verbindungstyp erfahren Sie, wie Sie eine Datenquelle erstellen.
ms.date: 11/03/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1df8e6c21f4aba600d36314ea224d1a77d6f2332
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97464441"
---
# <a name="oracle-connection-type-ssrs--power-bi-report-server"></a>Oracle-Verbindungstyp (SSRS und Power BI-Berichtsserver)

Wenn Sie Daten aus einer Oracle-Datenbank im Bericht verwenden möchten, benötigen Sie ein Dataset, das auf einer Berichtsdatenquelle vom Typ "Oracle" basiert. Dieser integrierte Datenquellentyp verwendet direkt den Oracle-Datenanbieter und erfordert eine Oracle-Clientsoftwarekomponente. In diesem Artikel wird erläutert, wie Sie Treiber für Reporting Services, den Power BI-Berichtsserver, den Berichts-Generator und Power BI Desktop herunterladen und installieren.


Verwenden Sie die Informationen in diesem Artikel, um eine Datenquelle zu erstellen. Eine Schritt-für-Schritt-Anleitung finden Sie unter [Hinzufügen und Prüfen einer Datenverbindung &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md). 

> [!IMPORTANT]
> Die folgenden Befehle, die das OraProvCfg.exe-Tool von Oracle verwendet, um die (nicht) verwalteten ODP.NET-Treiber von Oracle zu registrieren, können als Beispiele für die oben genannten Microsoft-Produkte verwendet werden. Für die Konfiguration der ODP.NET-Treiber, die für Ihre Umgebung spezifisch sind, müssen Sie sich möglicherweise an den Oracle-Support wenden oder die Oracle-Dokumentation zum [Konfigurieren eines Oracle-Datenanbieters für .NET](https://docs.oracle.com/en/database/oracle/oracle-database/19/odpnt/InstallConfig.html#GUID-1F689B90-2CC4-4907-B8FE-A5F4EE36F673) lesen.

## <a name="64-bit-drivers-for-the-report-servers"></a>64-Bit-Treiber für die Berichtsserver

Installieren Sie den [Oracle 64-Bit ODAC Oracle Universal Installer (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdeploy-4242173.html) von der Oracle-Downloadwebsite. Die folgenden Schritte sind nur erforderlich, wenn Sie Oracle ODAC-Treiber der Version 12.2 oder höher verwenden. Andernfalls werden sie bei einer neuen Oracle-Installation standardmäßig in einer nicht für den gesamten Computer geltenden Konfiguration installiert. Bei diesen Schritten wird davon ausgegangen, dass Sie die ODAC 18.x-Dateien im Ordner „c:\oracle64“ installiert haben.


### <a name="paginated-rdl-reports-use-managed-odpnet"></a>Paginierte Berichte verwenden eine verwaltete ODP.NET-Instanz

Der Power BI-Berichtsserver und Microsoft SQL Server Reporting Services 2016 und höher verwenden alle eine **verwaltete ODP.NET-Instanz** für paginierte Berichte. Führen Sie diese Schritte aus, um eine verwaltete ODP.NET-Instanz zu registrieren:

1. Registrieren Sie ODP.NET Managed Client bei GAC:

   ```
   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
   ```

2. Fügen Sie ODP.NET Managed Client-Einträge zu „machine.config“ hinzu:

   ```
   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
   ```

### <a name="power-bi-reports-use-unmanaged-odpnet"></a>Power BI-Berichte verwenden Unmanaged ODP.NET

Der Power BI-Berichtsserver verwendet eine **nicht verwaltete ODP.NET-Instanz** für Power BI-Berichte. Führen Sie diese Schritte aus, um Unmanaged ODP.NET zu registrieren:

1. Registrieren Sie ODP.NET Unmanaged Client bei GAC:

   ```
   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
   ```
2. Fügen Sie ODP.NET Unmanaged Client-Einträge zu „machine.config“ hinzu:

   ```
   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
   ```

## <a name="32-bit-drivers-for-report-builder"></a>32-Bit-Treiber für den Berichts-Generator

Der Berichts-Generator verwendet eine **verwaltete ODP.NET-Instanz** für die Autorisierung von paginierten Berichten. Die folgenden Schritte sind nur erforderlich, wenn Sie Oracle ODAC-Treiber der Version 12.2 oder höher verwenden. Andernfalls werden sie bei einer neuen Oracle-Installation standardmäßig in einer nicht für den gesamten Computer geltenden Konfiguration installiert. Bei diesen Schritten wird davon ausgegangen, dass Sie die ODAC 18.x-Dateien im Ordner „c:\oracle32“ installiert haben, in dem auch der Berichts-Generator installiert ist. Führen Sie diese Schritte aus, um eine verwaltete ODP.NET-Instanz zu registrieren:

1. Installieren Sie den [Oracle 32-Bit ODAC Oracle Universal Installer (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdev-4242174.html) von der Oracle-Downloadwebsite.

2. Registrieren Sie ODP.NET Managed Client bei GAC:

   ```
   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
   ```

3. Fügen Sie ODP.NET Managed Client-Einträge zu „machine.config“ hinzu:

   ```
   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
   ```

## <a name="64-bit-and-32-bit-drivers-for-power-bi-desktop"></a>64 Bit- und 32 Bit-Treiber für Power BI Desktop

Power BI Desktop verwendet eine **nicht verwaltete ODP.NET-Instanz** für die Erstellung von Power BI-Berichten. Die folgenden Schritte sind nur erforderlich, wenn Sie Oracle ODAC-Treiber der Version 12.2 oder höher verwenden. Andernfalls werden sie bei einer neuen Oracle-Installation standardmäßig in einer nicht für den gesamten Computer geltenden Konfiguration installiert. Bei diesen Schritten wird davon ausgegangen, dass Sie die ODAC 18.x-Dateien im Ordner „c:\oracle64“ für die 64-Bit-Version von Power BI Desktop oder im Ordner „c:\oracle32“ für die 32-Bit-Version von Power BI Desktop installiert haben. Führen Sie diese Schritte aus, um Unmanaged ODP.NET zu registrieren:

### <a name="64-bit-power-bi-desktop"></a>64 Bit-Version von Power BI Desktop

1. Installieren Sie den [Oracle 64-Bit ODAC Oracle Universal Installer (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdeploy-4242173.html) von der Oracle-Downloadwebsite.
2. Registrieren Sie ODP.NET Unmanaged Client bei GAC:

   ```
   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
   ```

3. Fügen Sie ODP.NET Unmanaged Client-Einträge zu „machine.config“ hinzu:

   ```
   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
   ```

### <a name="32-bit-power-bi-desktop"></a>32 Bit-Version von Power BI Desktop

1. Installieren Sie den [Oracle 32-Bit ODAC Oracle Universal Installer (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdev-4242174.html) von der Oracle-Downloadwebsite.

2. Registrieren Sie ODP.NET Unmanaged Client bei GAC:

   ```
   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
   ```

3. Fügen Sie ODP.NET Unmanaged Client-Einträge zu „machine.config“ hinzu:

   ```
   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
   ```

##  <a name="connection-string"></a><a name="Connection"></a> Verbindungszeichenfolge  

Erfragen Sie bei Ihrem Datenbankadministrator die Verbindungsinformationen und die Anmeldeinformationen, die verwendet werden sollen, um eine Verbindung mit der Datenquelle herzustellen. In der Verbindungszeichenfolge im folgenden Beispiel wird eine Oracle-Datenbank auf dem Server "Oracle18" im Unicode-Format angegeben. Der Servername muss mit dem in der Konfigurationsdatei "Tnsnames.ora" definierten Oracle-Serverinstanzname übereinstimmen.  
  
```  
Data Source="Oracle"; Unicode="True"  
```  
  
Weitere Beispiele für Verbindungszeichenfolgen finden Sie unter [Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
##  <a name="credentials"></a><a name="Credentials"></a> Anmeldeinformationen  
Anmeldeinformationen sind erforderlich, um Abfragen auszuführen und den Bericht lokal oder vom Berichtsserver aus in der Vorschau anzuzeigen.  
  
Nachdem Sie den Bericht veröffentlicht haben, müssen Sie eventuell die Anmeldeinformationen für die Datenquelle ändern, sodass die Berechtigungen zum Abrufen der Daten beim Ausführen des Berichts auf dem Berichtsserver gültig sind.  
  
Weitere Informationen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](specify-credential-and-connection-information-for-report-data-sources.md).  
  
##  <a name="queries"></a><a name="Query"></a> Abfragen  
Sie können ein Dataset erstellen, indem Sie in einer Dropdownliste eine gespeicherte Prozedur auswählen oder eine SQL-Abfrage erstellen. Zum Erstellen einer Abfrage muss der textbasierte Abfrage-Designer verwendet werden. Weitere Informationen finden Sie unter [Benutzeroberfläche des textbasierten Abfrage-Designers (Berichts-Generator)](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md).  
  
Sie können gespeicherte Prozeduren angeben, die nur ein Resultset zurückgeben. Cursorbasierte Abfragen werden nicht unterstützt.  
  
##  <a name="parameters"></a><a name="Parameters"></a> Parameter  

Wenn die Abfrage Abfragevariablen enthält, werden automatisch entsprechende Berichtsparameter generiert. Benannte Parameter werden von dieser Erweiterung unterstützt. Oracle Version 9 oder höher unterstützt mehrwertige Parameter.  
  
 Berichtsparameter werden mit Standardeigenschaftswerten erstellt, die Sie ggf. ändern müssen. Jeder Berichtsparameter ist z. B. vom Datentyp **Text**. Die Standardwerte müssen möglicherweise nach dem Erstellen der Berichtsparameter geändert werden. Weitere Informationen finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)" basiert.  
  
##  <a name="remarks"></a><a name="Remarks"></a> Hinweise  

Bevor Sie eine Verbindung mit einer Oracle-Datenquelle herstellen können, muss der Systemadministrator die Version des .NET-Datenanbieters für Oracle installieren, die das Abrufen von Daten aus der Oracle-Datenbank unterstützt. Dieser Datenanbieter muss auf dem gleichen Computer wie der Berichts-Generator und auf dem Berichtsserver installiert werden.  
  
Weitere Informationen finden Sie in den folgenden Artikeln:  
  
- [Verwenden von Reporting Services zum Konfigurieren und Zugreifen auf eine Oracle-Datenquelle](/archive/blogs/dataaccesstechnologies/configure-oracle-data-source-for-sql-server-reporting-services-ssdt-and-report-server)  
- [Hinzufügen von Berechtigungen für den NETZWERKDIENST-Sicherheitsprinzipal](https://support.microsoft.com/kb/870668)  
  
### <a name="alternate-data-extensions"></a>Alternative Datenerweiterungen 

Sie können Daten auch mit einem OLE DB-Datenquellentyp aus einer Oracle-Datenbank abrufen. Weitere Informationen finden Sie unter [OLE DB-Verbindungstyp &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md).  

::: moniker range=">=sql-server-2017"

### <a name="report-models"></a>Berichtsmodelle

 Sie können auch auf einer Oracle-Datenbank basierende Modelle erstellen.  
::: moniker-end

### <a name="platform-and-version-information"></a>Plattform- und Versionsinformationen  

Weitere Informationen zur Plattform- und Versionsunterstützung finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  

## <a name="see-also"></a>Weitere Informationen

[Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   

[Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   

[Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)
