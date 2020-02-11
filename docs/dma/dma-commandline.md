---
title: Ausführen von Datenmigrations-Assistent von der Befehlszeile aus
description: Erfahren Sie, wie Sie Datenmigrations-Assistent über die Befehlszeile ausführen, um SQL Server Datenbanken für die Migration zu bewerten.
ms.custom: seo-lt-2019
ms.date: 05/06/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: 3fbf2429a384ad64b1b416e3920a193d92a6c387
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74056619"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Ausführen von Datenmigrations-Assistent von der Befehlszeile aus

Mit Version 2,1 und höher wird bei der Installation von Datenmigrations-Assistent auch dmacmd. exe in *% Program Files\\% Microsoft-Datenmigrations-Assistent\\*installiert. Verwenden Sie dmacmd. exe, um die Datenbanken im unbeaufsichtigten Modus zu bewerten und das Ergebnis in der JSON-oder CSV-Datei auszugeben. Diese Methode ist besonders nützlich, wenn Sie mehrere Datenbanken oder große Datenbanken bewerten. 

> [!NOTE]
> Dmacmd. exe unterstützt nur das Ausführen von Bewertungen. Migrationen werden zurzeit nicht unterstützt.

## <a name="assessments-using-the-command-line-interface-cli"></a>Bewertungen mithilfe der Befehlszeilenschnittstelle (CLI)

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentSourcePlatform="SourcePlatform"]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```

|Argument  |BESCHREIBUNG  | Erforderlich (j/N)
|---------|---------|---------------|
| `/help or /?`     | Verwenden von "dmacmd. exe"-Hilfe Text        | N
|`/AssessmentName`     |   Name des Bewertungs Projekts   | J
|`/AssessmentDatabases`     | Durch Leerzeichen getrennte Liste mit Verbindungs Zeichenfolgen. Beim Datenbanknamen (anfangs Katalog) wird Groß-/Kleinschreibung beachtet. | J
|`/AssessmentSourcePlatform`     | Quell Plattform für die Bewertung: <br>Unterstützte Werte für die Bewertung: sqlonprem, rdssqlserver (Standard) <br>Unterstützte Werte für die Ziel Bereitschafts Bewertung: sqlonprem, rdssqlserver (Standard), Cassandra (Vorschau)   | N
|`/AssessmentTargetPlatform`     | Zielplattform für die Bewertung:  <br> Unterstützte Werte für die Bewertung: azuresqldatabase, managedsqlserver, SqlServer2012, SqlServer2014, SqlServer2016, SqlServerLinux2017 und SqlServerWindows2017 (Standard)  <br> Unterstützte Werte für die Ziel Bereitschafts Bewertung: managedsqlserver (Standard), cosmosdb (Vorschau)   | N
|`/AssessmentEvaluateFeatureParity`  | Ausführen von featureparitäts Regeln. Wenn die Quell Plattform rdssqlserver ist, wird die featureparitäts Auswertung für die Zielplattform azuresqldatabase nicht unterstützt.  | N
|`/AssessmentEvaluateCompatibilityIssues`     | Ausführen von Kompatibilitäts Regeln  | J <br> (Entweder "bewertentevaluatecompatibilityissues" oder "valumentevaluaterecommendations" ist erforderlich.)
|`/AssessmentEvaluateRecommendations`     | Funktions Empfehlungen ausführen        | J <br> (Entweder "bewertentevaluatecompatibilityissues" oder "valumentevaluaterecommendations" ist erforderlich)
|`/AssessmentOverwriteResult`     | Ergebnisdatei überschreiben    | N
|`/AssessmentResultJson`     | Vollständiger Pfad zur JSON-Ergebnisdatei     | J <br> (Entweder "bewermentresultjson" oder "bewermentresultcsv" ist erforderlich)
|`/AssessmentResultCsv`    | Vollständiger Pfad zur CSV-Ergebnisdatei   | J <br> (Entweder "bewermentresultjson" oder "bewermentresultcsv" ist erforderlich)
|`/Action`    | Verwenden Sie skuempfehlungs, um SKU-Empfehlungen zu erhalten, verwenden Sie assesstargetreadiness zum Durchführen der Ziel Bereitschafts Bewertung.   | N
|`/SourceConnections`    | Durch Leerzeichen getrennte Liste der Verbindungs Zeichenfolgen. Der Datenbankname (anfangs Katalog) ist optional. Wenn kein Datenbankname angegeben wird, werden alle Datenbanken in der Quelle bewertet.   | J <br> (Erforderlich, wenn die Aktion "assesstargetreadiness" ist)
|`/TargetReadinessConfiguration`    | Vollständiger Pfad zur XML-Datei, in der die Werte für Name, Quell Verbindungen und Ergebnisdatei beschrieben werden.   | J <br> (Entweder targetreadinmeconfiguration oder sourceconnections ist erforderlich.)
|`/FeatureDiscoveryReportJson`    | Pfad zum JSON-Bericht der Funktions Ermittlung. Wenn diese Datei generiert wird, kann Sie verwendet werden, um die Ziel Bereitschafts Bewertung erneut auszuführen, ohne eine Verbindung mit der Quelle herzustellen. | N
|`/ImportFeatureDiscoveryReportJson`    | Der Pfad zum zuvor erstellten JSON-Bericht für die Funktions Ermittlung. Anstelle von Quell Verbindungen wird diese Datei verwendet.   | N

## <a name="examples-of-assessments-using-the-cli"></a>Beispiele für Bewertungen mithilfe der CLI

**Dmacmd. exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Einzeldaten Bank Bewertung mithilfe der Windows-Authentifizierung und Ausführen von Kompatibilitäts Regeln**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```

**Bewertung von Einzel Datenbanken mithilfe SQL Server Authentifizierung und Funktions Empfehlung**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;User Id=myUsername;Password=myPassword;"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Einzeldaten Bank Bewertung für Zielplattform SQL Server 2012, Ergebnisse in JSON-und CSV-Datei speichern**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2012"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Einzeldaten Bank Bewertung für die Zielplattform SQL Azure Datenbank, Ergebnisse in JSON-und CSV-Datei speichern**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="AzureSqlDatabaseV12"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"
```

**Bewertung mehrerer Datenbanken**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```

**Bewertung der Ziel Bereitschaft einer einzelnen Datenbank mithilfe der Windows-Authentifizierung**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;Integrated Security=true" 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"
```

**Ziel-Bereitschaft zur Bewertung einzelner Datenbanken mithilfe SQL Server-Authentifizierung**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;User Id=myUsername;Password=myPassword;" /AssessmentEvaluateRecommendations 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json" 

```

**Einzeldaten Bank Bewertung für die Zielplattform SQL Azure Datenbank, Ergebnisse in JSON-und CSV-Datei speichern**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentSourcePlatform="SqlOnPrem"
/AssessmentTargetPlatform="AzureSqlDatabase"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"

```

**Bewertung der Ziel Bereitschaft mit mehreren Datenbanken**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/AssessmentSourcePlatform=SourcePlatform
/AssessmentTargetPlatform=TargetPlatform
/SourceConnections="Server=SQLServerInstanceName1;Initial Catalog=DatabaseName1;Integrated Security=true" "Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated Security=true" "Server=SQLServerInstanceName2;Initial Catalog=DatabaseName3;Integrated Security=true"
/AssessmentOverwriteResult  
/AssessmentResultJson="C:\Results\test2016.json"

(/AssessmentSourcePlatform and /AssessmentTargetPlatform are optional.)
```

**Ziel Bereitschafts Bewertung für alle Datenbanken auf einem Server mithilfe der Windows-Authentifizierung**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/SourceConnections="Server=SQLServerInstanceName;Integrated Security=true"
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Ziel Bereitschafts Bewertung durch das Importieren eines zuvor erstellten Funktions Ermittlungs Berichts**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/ImportFeatureDiscoveryReportJson="c:\temp\feature_report.json" 
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Ziel Bereitschafts Bewertung durch Bereitstellen einer Konfigurationsdatei**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/TargetReadinessConfiguration=.\Config.xml
```

Inhalt der Konfigurationsdatei bei Verwendung von Quell Verbindungen:

```
<?xml version="1.0" encoding="utf-8" ?>
<TargetReadinessConfiguration xmlns="https://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <SourcePlatform>Source Platform</SourcePlatform> <!-- Optional. The default is SqlOnPrem -->
  <TargetPlatform>TargetPlatform</TargetPlatform> <!-- Optional. The default is ManagedSqlServer -->
  <SourceConnections>
    <SourceConnection>connection string 1</SourceConnection>
    <SourceConnection>connection string 2</SourceConnection>
    <!-- ... -->
    <SourceConnection>connection string n</SourceConnection>
  </SourceConnections>
  <AssessmentResultJson>path\to\file.json</AssessmentResultJson>
  <FeatureDiscoveryReportJson>path\to\featurediscoveryreport.json</FeatureDiscoveryReportJson>
  <OverwriteResult>true</OverwriteResult> <!-- or false -->
</TargetReadinessConfiguration>
```

Inhalt der Konfigurationsdatei beim Importieren des Funktions Ermittlungs Berichts:

```
<TargetReadinessConfiguration xmlns="https://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <ImportFeatureDiscoveryReportJson>path\to\featurediscoveryfile.json</ImportFeatureDiscoveryReportJson>
  <AssessmentResultJson>path\to\resultfile.json</AssessmentResultJson>
  <OverwriteResult>true</OverwriteResult><!-- or false -->
</TargetReadinessConfiguration>
```

## <a name="azure-sql-databasemanaged-instance-sku-recommendations-using-the-cli"></a>Azure SQL-Datenbank/SKU-Empfehlungen für verwaltete Instanzen mithilfe der CLI

Diese Befehle unterstützen Empfehlungen für Bereitstellungs Optionen für eine einzelne Datenbank und eine verwaltete Instanz von Azure SQL-Datenbank.

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true 
```

|Argument  |BESCHREIBUNG  | Erforderlich (j/N)
|---------|---------|---------------|
|`/Action=SkuRecommendation` | Ausführen der SKU-Bewertung mithilfe der DMA-Befehlszeile | J
|`/SkuRecommendationInputDataFilePath` | Vollständiger Pfad zur Leistungsdaten Bank Datei, die von dem Computer erfasst wird, der Ihre Datenbanken | J
|`/SkuRecommendationTsvOutputResultsFilePath` | Vollständiger Pfad zur TSV-Ergebnisdatei | J <br> (Erfordert entweder TSV-oder JSON-oder HTML-Dateipfad)
|`/SkuRecommendationJsonOutputResultsFilePath` | Vollständiger Pfad zur JSON-Ergebnisdatei | J <br> (Erfordert entweder TSV-oder JSON-oder HTML-Dateipfad)
|`/SkuRecommendationHtmlResultsFilePath` | Vollständiger Pfad zur HTML-Ergebnisdatei | J <br> (Erfordert entweder TSV-oder JSON-oder HTML-Dateipfad)
|`/SkuRecommendationPreventPriceRefresh` | Verhindert, dass die Preis Aktualisierung stattfindet. Verwenden Sie, wenn Sie im Offline Modus ausgeführt werden (z. b. true). | J <br> (Wählen Sie entweder dieses Argument für statische Preise oder alle unten aufgeführten Argumente müssen ausgewählt werden, um die neuesten Preise zu erhalten.)
|`/SkuRecommendationCurrencyCode` | Die Währung, in der die Preise angezeigt werden sollen (z. b. "USD"). | J <br> (Für die neuesten Preise)
|`/SkuRecommendationOfferName` | Der Angebots Name (z. b. "MS-AZR-0003p"). Weitere Informationen finden Sie auf der Seite [Microsoft Azure Angebots Details](https://azure.microsoft.com/support/legal/offer-details/) . | J <br> (Für die neuesten Preise)
|`/SkuRecommendationRegionName` | Der Name der Region (z. b. "westus") | J <br> (Für die neuesten Preise)
|`/SkuRecommendationSubscriptionId` | Die Abonnement-ID. | J <br> (Für die neuesten Preise)
|`/SkuRecommendationDatabasesToRecommend` | Durch Leerzeichen getrennte Liste mit Datenbanken, die empfohlen werden sollen (z. b. "Database1" "Database2" "Database3"). Bei Namen wird die Groß-/Kleinschreibung beachtet und muss in doppelte Anführungszeichen eingeschlossen werden. Wenn die Angabe ausgelassen wird, werden für alle Datenbanken Empfehlungen bereitgestellt. | N
|`/AzureAuthenticationTenantId` | Der Authentifizierungs Mandant. | J <br> (Für die neuesten Preise)
|`/AzureAuthenticationClientId` | Die Client-ID der Aad-APP, die für die Authentifizierung verwendet wird. | J <br> (Für die neuesten Preise)
|`/AzureAuthenticationInteractiveAuthentication` | Legen Sie diese Einstellung auf true fest, um das Fenster aufklappen. | J <br> (Für die neuesten Preise) <br>(Wählen Sie eine der drei Authentifizierungs Optionen aus: Option 1)
|`/AzureAuthenticationCertificateStoreLocation` | Legen Sie den Speicherort des Zertifikats fest (z. b. "CurrentUser"). | J <br>(Für die neuesten Preise) <br> (Wählen Sie eine der drei Authentifizierungs Optionen aus: Option 2)
|`/AzureAuthenticationCertificateThumbprint` | Legen Sie auf den Zertifikat Fingerabdruck fest. | J <br> (Für die neuesten Preise) <br>(Wählen Sie eine der drei Authentifizierungs Optionen aus: Option 2)
|`/AzureAuthenticationToken` | Legen Sie auf das Zertifikat Token fest. | J <br> (Für die neuesten Preise) <br>(Wählen Sie eine der drei Authentifizierungs Optionen aus: Option 3)

## <a name="examples-of-sku-assessments-using-the-cli"></a>Beispiele für SKU-Bewertungen mithilfe der CLI

**Dmacmd. exe**

`Dmacmd.exe /? or DmaCmd.exe /help`

**Azure SQL-DB/Mi-SKU-Empfehlung mit Preis Aktualisierung (aktuelle Preise erhalten)-interaktive Authentifizierung** 

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationInteractiveAuthentication=true 
```

**Azure SQL-DB/Mi-SKU-Empfehlung mit Preis Aktualisierung (aktuelle Preise erhalten): Zertifikat Authentifizierung**

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationCertificateStoreLocation=<Your Certificate Store Location>
/AzureAuthenticationCertificateThumbprint=<Your Certificate Thumbprint>  
```

**Azure SQL DB-SKU/Mi-Empfehlung mit Preis Aktualisierung (aktuellste Preise): Tokenauthentifizierung und angeben der zu empfohlenen Datenbanken**
  
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationDatabasesToRecommend=“TPCDS1G,EDW_3G,TPCDS10G”
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationToken=<Your Authentication Token> 
```

**Azure SQL-DB/Mi-SKU-Empfehlung ohne Preis Aktualisierung (statische Preise verwenden)** 
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true  
```

## <a name="see-also"></a>Weitere Informationen
- [Datenmigrations-Assistent](https://aka.ms/get-dma) herunterladen.
- Der Artikel [identifiziert die richtige Azure SQL-Datenbank-SKU für Ihre lokale Datenbank](https://aka.ms/dma-sku-recommend-sqldb).
