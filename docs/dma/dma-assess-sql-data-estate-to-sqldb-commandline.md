---
title: 'Dmacmd: Bewerten der SQL Server Bereitschaft für die Migration zu Azure SQL'
titleSuffix: Data Migration Assistant
description: Erfahren Sie, wie Sie mit Datenmigrations-Assistent Befehlszeilen Tool (dmacmd) ein SQL Server Data Estate für die Migration zu Azure SQL bewerten.
ms.date: 10/02/2020
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.custom: ''
ms.openlocfilehash: f81cddcb5f1279bd444799884b150294a037b3e1
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91867695"
---
# <a name="dmacmd-assess-readiness-of-a-sql-server-data-estate-migrating-to-azure-sql"></a>Dmacmd: Bewerten der Bereitschaft einer SQL Server-Datenbankmigration zu Azure SQL 

Wenn viele Organisationen versuchen, zu Azure zu migrieren, ist es wichtig, vorhandene lokale SQL Server Instanzen zu bewerten und das richtige Azure SQL-Ziel zu identifizieren: Azure SQL-Datenbank, Azure SQL-verwaltete Instanz oder SQL Server auf Azure-VMS. 

[Datenmigrations-Assistent (DMA)](dma-overview.md) unterstützt Sie bei der Bewertung einer SQL Server Instanz für ein bestimmtes Azure SQL-Ziel und misst die Bereitschaft von SQL Server Datenbanken, die zu Azure SQL migrieren. Laden Sie DMA-Bewertungsergebnisse in Azure migrate Hub hoch, um eine zentralisierte Bereitschafts Ansicht des gesamten Datentyps zu erhalten. 

In diesem Artikel erfahren Sie, wie Sie mit der DMA-Befehlszeilenschnittstelle (dmacmd) Bewertungen in der Skala ausführen und die Ergebnisse in Azure migrate Hub hochladen. Alternativ können Sie stattdessen die [DMA-GUI](dma-assess-sql-data-estate-to-sqldb.md) verwenden, um die Bewertung durchzuführen. 

## <a name="prerequisites"></a>Voraussetzungen 

Um dmacmd zum Durchführen einer Bewertung und zum Hochladen der Ergebnisse in Azure migrate Hub zu verwenden, benötigen Sie Folgendes: 

- Die [neueste Version von Datenmigrations-Assistent (DMA)](https://www.microsoft.com/en-us/download/details.aspx?id=53595).
- Ein [Azure migrate-Projekt](dma-assess-sql-data-estate-to-sqldb.md#create-a-project-and-add-a-tool). 
- Zugriff der Rolle "Mitwirkender" auf die Azure migrate Projekt Ressource.

## <a name="use-dmacmd"></a>Verwenden von dmacmd

Verwenden Sie eine XML-Datei als Eingabe, um Bewertungen in der Skala mithilfe der Befehlszeilenschnittstelle (DMACMD.exe) auszuführen. 

Verwenden Sie den folgenden Beispiel Befehl, um eine XML-Datei an dmacmd zu übergeben und die Bewertung zu starten:

```console
C:\Program Files\Microsoft Data Migration Assistant\DmaCmd.exe /Action=Assess /AssessmentConfiguration= C:\Demo\ScaleAssessment\Assess-for-AzureSQLMI.xml
```

Der Inhalt von Sample `Assess-for-AzureSQLMI.xml` definiert die Elemente, um SQL Server Instanzen für ein SQL verwaltete Instanz Ziel zu bewerten: 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<AssessmentConfiguration xmlns="http://microsoft.com/schemas/SqlServer/Advisor/AssessmentConfiguration">
   <AssessmentName>Scale-Assessment-for-AzureSQLManagedInstance</AssessmentName>
   <AssessmentSourcePlatform>SqlOnPrem</AssessmentSourcePlatform>
   <AssessmentTargetPlatform>ManagedSqlServer</AssessmentTargetPlatform>
   <AssessmentDatabases>
      <AssessmentDatabase>Server=ServerName\SQL2017;Integrated Security=true</AssessmentDatabase>
      <AssessmentDatabase>Server=ServerName\SQL2016;Integrated Security=true;Initial Catalog=AdventureWorks2016</AssessmentDatabase>
      <AssessmentDatabase>Server=ServerName\SQL2016;Integrated Security=true;Initial Catalog=TestDB</AssessmentDatabase>
   </AssessmentDatabases>
   <AssessmentResultDma>C:\Demo\ScaleAssessment\AssessmentConfiguration\Scale-Assessment-for-AzureSQLManagedInstance.dma</AssessmentResultDma>
   <AssessmentResultJson>C:\Demo\ScaleAssessment\AssessmentConfiguration\Scale-Assessment-for-AzureSQLManagedInstance.json</AssessmentResultJson>
   <AssessmentResultCsv>C:\Demo\ScaleAssessment\AssessmentConfiguration\Scale-Assessment-for-AzureSQLManagedInstance.csv</AssessmentResultCsv>
   <AssessmentOverwriteResult>true</AssessmentOverwriteResult>
   <AssessmentEvaluateCompatibilityIssues>true</AssessmentEvaluateCompatibilityIssues>
   <AssessmentEvaluateFeatureParity>true</AssessmentEvaluateFeatureParity>
   <AzureCloudEnvironment>Azure</AzureCloudEnvironment>
   <SubscriptionId>xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx</SubscriptionId>
   <AzureMigrateProjectName>Scale-Assessment-for-AzureSQLMI</AzureMigrateProjectName>
   <ResourceGroupName>Resource-Group-Name</ResourceGroupName>
   <AzureAuthenticationInteractiveAuthentication>true</AzureAuthenticationInteractiveAuthentication>
   <AzureAuthenticationTenantId>xxxxxxxx-xxxx-xxxxxxxx</AzureAuthenticationTenantId>
   <EnableAssessmentUploadToAzureMigrate>true</EnableAssessmentUploadToAzureMigrate>
</AssessmentConfiguration>
```



## <a name="xml-elements"></a>XML-Elemente 

Die XML-Elemente, die an dmacmd übermittelt werden, werden in der folgenden Tabelle definiert: 


|**XML-Element** |**Definition**  |
|---------|---------|
|`AssessmentName`|Der Name der Bewertung.|
|`AssessmentSourcePlatform`|Quelle SQL Server Plattform. Der Standardwert ist `SqlOnPrem`.|
|`AssessmentTargetPlatform`|Ziel SQL Server Plattform.  </br> `AzureSqlDatabase` ist für ein Azure SQL-Daten Bank Ziel. </br> `ManagedSqlServer` ist für ein Azure SQL-verwaltete Instanz Ziel. </br></br>Das Beispiel " **Assessment-for-azuresqlmi** " bewertet ein SQL verwaltete Instanz-Ziel.|
|`AssessmentDatabases`|Wenn Sie alle Datenbanken in einer Instanz bewerten müssen, geben Sie nur den Instanznamen an, und geben Sie in jeder Zeile bestimmte Datenbanken an. </br></br>Das Beispiel **Assessment-for-azuresqlmi** bewertet alle Datenbanken in der Instanz `Servername\SQL2017` und zwei bestimmte Datenbanken in der Instanz `Servername\SQL2016` .  |
|`AssessmentResultDma` </br> `AssessmentResultJson` </br> `AssessmentResultCsv` | Gibt das Format der Ergebnisdatei an. `.DMA`, `.JSON` `.CSV` bzw. Doppelklicken Sie `.DMA` , um in der DMA-Benutzeroberfläche zu öffnen. <br> `AssessmentResultDma` ist erforderlich, um Bewertungsergebnisse in Azure migrate Hub hochzuladen.  |
|`AssessmentOverwriteResult`| Gibt an, ob eine vorhandene Bewertungsergebnis Datei mit demselben Pfad wie oder überschrieben `AssessmentResultJson` werden soll `AssessmentResultDma` `AssessmentResultCsv` .|
|`AssessmentEvaluateCompatibilityIssues` </br> `AssessmentEvaluateFeatureParity` |Führen Sie eine Bewertung durch, um Kompatibilitätsprobleme und featureparitäts Probleme auszuwerten|
|`AzureCloudEnvironment`|Azure-cloudumgebung, mit der eine Verbindung hergestellt werden soll </br></br> Unterstützte Werte: </br>`Azure (default)`, `AzureChina`, `AzureGermany`, `AzureUSGovernment`.|
|`SubscriptionId`|Die Azure-Abonnement-ID.|
|`AzureMigrateProjectName`|Azure migrate Projektname, in den Bewertungsergebnisse hochgeladen werden sollen.|
|`ResourceGroupName`|Azure migrate Ressourcengruppen Name.|
|`AzureAuthenticationInteractiveAuthentication`|Legen Sie auf fest, `true` um das Authentifizierungs Fenster aufklappen.|
|`AzureAuthenticationTenantId`|Die ID des Azure Active Directory-Mandanten. </br></br>Rufen Sie dies auf dem **Übersichts** Blatt Azure Active Directory im [Azure-Portal](https://portal.azure.com)ab. |
|`EnableAssessmentUploadToAzureMigrate`| Legen Sie auf fest, `true` um Bewertungsergebnisse in Azure migrate Hub hochzuladen und zu veröffentlichen.|
|   |   |


## <a name="results"></a>Ergebnisse 

Dmacmd gibt einen Status aus, wenn er erfolgreich abgeschlossen wurde. 


Im folgenden finden Sie eine Beispielausgabe für das Ergebnis: 

```console
Assessment finished for project: Scale-Assessment-for-AzureSQLManagedInstance
DATABASES:
Succeeded             : 4
Failed                : 0
SERVER INSTANCES:
Succeeded             : 2
Failed                : 0
CSV result file       : C:\Demo\ScaleAssessment\Scale-Assessment-for-AzureSQLManagedInstance.csv
JSON result file      : C:\Demo\ScaleAssessment\Scale-Assessment-for-AzureSQLManagedInstance.json
--------------------------------------------------------------------------------
```

Anzeigen hochgeladener Ergebnisse in [Azure migrate](dma-assess-sql-data-estate-to-sqldb.md#view-target-readiness-assessment-results) für eine zentralisierte Ansicht des gesamten Datentyps. . 

## <a name="best-practices"></a>Bewährte Methoden 

Beachten Sie bei der Verwendung von dmacmd die folgenden bewährten Methoden: 

- Gruppieren Sie SQL Server Instanzen und Datenbanken auf der Grundlage der Anwendung logisch, anstatt alle SQL Server Instanzen im gesamten Datenbestand zu bewerten. 
- Erstellen Sie für jedes Azure SQL-Ziel ein separates Azure migrate Projekt, um das Überschreiben von Ergebnissen zu vermeiden. 
- Die Zeit für die Durchführung einer Bewertung hängt von der Anzahl der Datenbankobjekte ab. Vermeiden Sie nach Möglichkeit das Ausführen von Bewertungen für das Produktionssystem und das Auslagern auf einen virtuellen Computer oder einen Stagingserver, insbesondere bei Datenbanken mit einer großen Anzahl von Objekten. 


## <a name="see-also"></a>Weitere Informationen

* [Datenmigrations-Assistent (DMA)](../dma/dma-overview.md)
* [Datenmigrations-Assistent: Konfigurationseinstellungen](../dma/dma-configurationsettings.md)
* [Datenmigrations-Assistent: bewährte Methoden](../dma/dma-bestpractices.md)
