---
title: Ausführen von Data Migration Assistant von der Befehlszeile aus (SQL Server) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Data Migration Assistant ausführen, über die Befehlszeile, um SQL Server-Datenbanken für die Migration zu bewerten.
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: ccb2b0b6a60bfc2df94f2cc09b087a22b22ce7ab
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105835"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Ausführen von Data Migration Assistant über die Befehlszeile

Mit der Version 2.1 und höher bei Installation von Data Migration Assistant, werden auch installiert dmacmd.exe in *%ProgramFiles%\\Microsoft Data Migration Assistant\\*. Verwenden Sie dmacmd.exe zu, um Ihre Datenbanken in einem unbeaufsichtigten Modus zu bewerten, und geben Sie das Ergebnis in JSON oder CSV-Datei. Diese Methode ist besonders nützlich, wenn mehrere Datenbanken oder große Datenbanken zu bewerten. 

> [!NOTE]
> Dmacmd.exe unterstützt das Ausführen von Bewertungen nur. Migrationen werden zu diesem Zeitpunkt nicht unterstützt.

## <a name="assessments-using-the-command-line-interface-cli"></a>Bewertungen, die mithilfe der Befehlszeilenschnittstelle (CLI)

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentSourcePlatform="SourcePlatform"]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```

|Argument  |Description  | Erforderlich (J/N)
|---------|---------|---------------|
| `/help or /?`     | Wie Sie mit der dmacmd.exe-Hilfetext        | N
|`/AssessmentName`     |   Name des Bewertungsprojekts   | J
|`/AssessmentDatabases`     | Leerzeichen getrennte Liste von Verbindungszeichenfolgen. Datenbanknamen (Anfangskatalog) wird die Groß-/Kleinschreibung beachtet. | J
|`/AssessmentSourcePlatform`     | Source-Plattform für die Bewertung: <br>Unterstützte Werte für die Bewertung: SqlOnPrem, RdsSqlServer (Standard) <br>Unterstützte Werte für die Ziel-Bereitschaftsbewertung: SqlOnPrem, RdsSqlServer (Standard), Cassandra (Vorschauversion)   | N
|`/AssessmentTargetPlatform`     | Die Zielplattform für die Bewertung:  <br> Unterstützte Werte für die Bewertung: "Azuresqldatabase" "," ManagedSqlServer "," SqlServer2012 "," SqlServer2014 "," SqlServer2016 "," SqlServerLinux2017 "und" SqlServerWindows2017 (Standard)  <br> Unterstützte Werte für die Ziel-Bereitschaftsbewertung: ManagedSqlServer (Standard), COSMOS DB (Vorschau)   | N
|`/AssessmentEvaluateFeatureParity`  | Featureparitätsregeln auszuführen. Wenn Source-Plattform RdsSqlServer ist, wird-featureevaluierung Parität für die Zielplattform "azuresqldatabase" nicht unterstützt  | N
|`/AssessmentEvaluateCompatibilityIssues`     | Führen Sie Kompatibilitätsregeln  | J <br> (Entweder AssessmentEvaluateCompatibilityIssues oder AssessmentEvaluateRecommendations ist erforderlich.)
|`/AssessmentEvaluateRecommendations`     | Führen Sie die Vorschläge zu Features        | J <br> (Entweder AssessmentEvaluateCompatibilityIssues oder AssessmentEvaluateRecommendations ist erforderlich)
|`/AssessmentOverwriteResult`     | Überschreiben Sie die Ergebnisdatei    | N
|`/AssessmentResultJson`     | Vollständiger Pfad in die JSON-Ergebnisdatei     | J <br> (Entweder AssessmentResultJson oder AssessmentResultCsv ist erforderlich)
|`/AssessmentResultCsv`    | Vollständigen Pfad zu der CSV-Ergebnisdatei   | J <br> (Entweder AssessmentResultJson oder AssessmentResultCsv ist erforderlich)
|`/Action`    | Mithilfe SkuRecommendation SKU-Empfehlungen zu erhalten, verwenden AssessTargetReadiness, zum Bewerten der Bereitschaft Ziel ausführen.   | N
|`/SourceConnections`    | Leerzeichen getrennte Liste von Verbindungszeichenfolgen. Datenbanknamen (Anfangskatalog) ist optional. Wenn kein Datenbankname angegeben wird, werden dann alle Datenbanken auf dem Quellcomputer bewertet.   | J <br> (Bei Aktion "AssessTargetReadiness" ist erforderlich)
|`/TargetReadinessConfiguration`    | Vollständiger Pfad der XML-Datei, die Werte für Name, datenquellenverbindungen und Ergebnisdatei beschreibt.   | J <br> (Entweder TargetReadinessConfiguration oder SourceConnections ist erforderlich)
|`/FeatureDiscoveryReportJson`    | Pfad zur JSON-Bericht die Feature-Ermittlung. Wenn diese Datei generiert wird, klicken Sie dann es dienen bereitschaftstest für Ziel erneut ausführen, ohne eine Verbindung mit der Quelle. | N
|`/ImportFeatureDiscoveryReportJson`    | Pfad zu der Funktion JSON-ermittlungsbericht zuvor erstellt haben. Anstelle von datenquellenverbindungen wird diese Datei verwendet werden.   | N

## <a name="examples-of-assessments-using-the-cli"></a>Beispiele für Bewertungen, die mithilfe der Befehlszeilenschnittstelle

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Einzelne-Datenbank-Bewertung, die mit der Windows-Authentifizierung und Ausführung Kompatibilitätsregeln**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```

**Single-datenbankbewertung mithilfe von SQL Server-Authentifizierung und Ausführung Feature-Empfehlung**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;User Id=myUsername;Password=myPassword;"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Single-Database-Bewertung für die Zielplattform SQL Server 2012, Ergebnisse in JSON und CSV-Datei speichern**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2012"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Bewertung der einzelnen-Datenbank für die Zielplattform SQL Azure-Datenbank speichern die Ergebnisse in JSON und CSV-Datei**

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

**Bewertung von mehreren Datenbanken**

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

**Single-Database bereitschaftstest für Ziel mithilfe der Windows-Authentifizierung**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;Integrated Security=true" 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"
```

**Single-Database bereitschaftstest für Ziel mithilfe von SQL Server-Authentifizierung**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;User Id=myUsername;Password=myPassword;" /AssessmentEvaluateRecommendations 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json" 

```

**Bewertung der einzelnen-Datenbank für die Zielplattform SQL Azure-Datenbank speichern die Ergebnisse in JSON und CSV-Datei**

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

**Ziel-bereitschaftsbewertung mehreren Datenbanken**

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

**Bereitschaftstest für das Ziel für alle Datenbanken auf einem Server mithilfe der Windows-Authentifizierung**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/SourceConnections="Server=SQLServerInstanceName;Integrated Security=true"
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Bewerten der Bereitschaft durch das Importieren von Feature Discovery-Bericht, die zuvor erstellte Ziel**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/ImportFeatureDiscoveryReportJson="c:\temp\feature_report.json" 
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Bewerten der Bereitschaft Ziel durch die Bereitstellung der Konfigurationsdatei**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/TargetReadinessConfiguration=.\Config.xml
```

Inhalt der Konfigurationsdatei bei Verwendung von datenquellenverbindungen:

```
<?xml version="1.0" encoding="utf-8" ?>
<TargetReadinessConfiguration xmlns="http://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
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

Inhalt der Konfigurationsdatei beim Feature Discovery-Bericht zu importieren:

```
<TargetReadinessConfiguration xmlns="http://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <ImportFeatureDiscoveryReportJson>path\to\featurediscoveryfile.json</ImportFeatureDiscoveryReportJson>
  <AssessmentResultJson>path\to\resultfile.json</AssessmentResultJson>
  <OverwriteResult>true</OverwriteResult><!-- or false -->
</TargetReadinessConfiguration>
```

## <a name="azure-sql-databasemanaged-instance-sku-recommendations-using-the-cli"></a>Azure SQL-Datenbank/verwaltete Instanz über die Befehlszeilenschnittstelle die SKU-Empfehlungen

Diese Befehle unterstützen die Empfehlungen für Azure SQL-einzeldatenbanken und Bereitstellungsoptionen für die verwaltete Instanz.

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true 
```

|Argument  |Description  | Erforderlich (J/N)
|---------|---------|---------------|
|`/Action=SkuRecommendation` | Führen Sie die SKU-Bewertung über DMA-Befehlszeile | J
|`/SkuRecommendationInputDataFilePath` | Vollständiger Pfad der Performance Counter-Datei erfasst, auf dem Computer, auf dem Ihre Datenbanken gehostet | J
|`/SkuRecommendationTsvOutputResultsFilePath` | Vollständiger Pfad in die TSV-Ergebnisdatei | J <br> (Muss entweder "TSV" oder "JSON" oder "HTML-Pfad)
|`/SkuRecommendationJsonOutputResultsFilePath` | Vollständiger Pfad in die JSON-Ergebnisdatei | J <br> (Muss entweder "TSV" oder "JSON" oder "HTML-Pfad)
|`/SkuRecommendationHtmlResultsFilePath` | Vollständiger Pfad in die HTML-Ergebnisdatei | J <br> (Muss entweder "TSV" oder "JSON" oder "HTML-Pfad)
|`/SkuRecommendationPreventPriceRefresh` | Verhindert, dass die Preis-Aktualisierung auftreten. Verwenden Sie im Offlinemodus ausgeführt werden (z. B., "true"). | J <br> (Wählen Sie entweder dieses Argument für statische Preise oder müssen alle Argumente, die unten ausgewählt werden, um den aktuellen Preisen zu erhalten.)
|`/SkuRecommendationCurrencyCode` | Die Währung, in dem Preise angezeigt werden (z.B.) "USD") | J <br> (Für den aktuellen Preisen)
|`/SkuRecommendationOfferName` | Das Angebot benennen (z.B.) "MS-AZR-0003P"). Weitere Informationen finden Sie unter den [Microsoft Azure-Angebotsdetails](https://azure.microsoft.com/support/legal/offer-details/) Seite. | J <br> (Für den aktuellen Preisen)
|`/SkuRecommendationRegionName` | Benennen Sie die Region (z.B.) "WestUS") | J <br> (Für den aktuellen Preisen)
|`/SkuRecommendationSubscriptionId` | Die Abonnement-ID. | J <br> (Für den aktuellen Preisen)
|`/SkuRecommendationDatabasesToRecommend` | Durch Leerzeichen getrennte Liste von Datenbanken, für die Empfehlungen (z.B.) "Database1" "" database2 "" "Database3"). Namen wird Groß-/Kleinschreibung beachtet und doppelte Anführungszeichen gesetzt werden müssen. Wenn nicht angegeben, werden Empfehlungen für alle Datenbanken bereitgestellt. | N
|`/AzureAuthenticationTenantId` | Die Authentication-Mandant. | J <br> (Für den aktuellen Preisen)
|`/AzureAuthenticationClientId` | Die Client-ID der AAD-app für die Authentifizierung verwendet werden soll. | J <br> (Für den aktuellen Preisen)
|`/AzureAuthenticationInteractiveAuthentication` | Legen Sie auf "true", um das Fenster angezeigt. | J <br> (Für den aktuellen Preisen) <br>(Wählen Sie eine der 3 Authentifizierungsoptionen - Option 1)
|`/AzureAuthenticationCertificateStoreLocation` | Legen Sie auf den Speicherort des Zertifikatspeichers (z.B.) "CurrentUser"). | J <br>(Für den aktuellen Preisen) <br> (Wählen Sie eine der 3 Authentifizierungsoptionen - Option 2)
|`/AzureAuthenticationCertificateThumbprint` | Legen Sie auf den Zertifikatfingerabdruck. | J <br> (Für den aktuellen Preisen) <br>(Wählen Sie eine der 3 Authentifizierungsoptionen - Option 2)
|`/AzureAuthenticationToken` | Legen Sie auf das Zertifikatstoken. | J <br> (Für den aktuellen Preisen) <br>(Wählen Sie eine der 3 Authentifizierungsoptionen - Option 3)

## <a name="examples-of-sku-assessments-using-the-cli"></a>Beispiele für die SKU-Bewertungen, die mithilfe der Befehlszeilenschnittstelle

**Dmacmd.exe**

`Dmacmd.exe /? or DmaCmd.exe /help`

**Azure SQL DB/MI-SKU-Empfehlung mit Preis Aktualisierung (Get aktuellen Preisen) – interaktive Authentifizierung** 

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

**Azure SQL DB/MI-SKU-Empfehlung mit Preis Aktualisierung (Get aktuellen Preisen) - Clientzertifikatauthentifizierung**

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

**Azure SQL-Datenbank-SKU/MI-Empfehlung mit Preis Aktualisierung (Get aktuellen Preisen) - Token-Authentifizierung, und geben Sie die Datenbanken wird empfohlen**
  
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

**Azure SQL DB/MI-SKU-Empfehlung ohne Preis aktualisieren (verwenden statische Preise)** 
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true  
```

## <a name="see-also"></a>Siehe auch
- [Data Migration Assistant](https://aka.ms/get-dma) herunterladen.
- Der Artikel [identifizieren Sie die richtige Azure SQL-Datenbank-SKU für Ihre lokale Datenbank](https://aka.ms/dma-sku-recommend-sqldb).
