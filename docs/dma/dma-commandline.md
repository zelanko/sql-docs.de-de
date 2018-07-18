---
title: Ausführen von Data Migration Assistant von der Befehlszeile aus (SQL Server) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Data Migration Assistant ausführen, über die Befehlszeile, um SQL Server-Datenbanken für die Migration zu bewerten.
ms.custom: ''
ms.date: 09/01/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 6b364dc03d48cbc1c0487362712e10f7ab0b782e
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785461"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Ausführen von Data Migration Assistant über die Befehlszeile
Mit der Version 2.1 und höher bei Installation von Data Migration Assistant, werden auch installiert dmacmd.exe in *%ProgramFiles%\\Microsoft Data Migration Assistant\\*. Verwenden Sie dmacmd.exe zu, um Ihre Datenbanken in einem unbeaufsichtigten Modus zu bewerten, und geben Sie das Ergebnis in JSON oder CSV-Datei. Diese Methode ist besonders nützlich, wenn mehrere Datenbanken oder große Datenbanken zu bewerten. 

> [!NOTE]
> Dmacmd.exe unterstützt das Ausführen von Bewertungen nur. Migrationen werden zu diesem Zeitpunkt nicht unterstützt.


## <a name="command-line-arguments"></a>Befehlszeilenargumente

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
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
|`/AssessmentTargetPlatform`     | Zielplattform für die Bewertung, unterstützte Werte: SqlServer2012 "," SqlServer2014 "," SqlServer2016 "und" AzureSqlDatabaseV12. Der Standardwert ist SqlServer2016   | N
|`/AssessmentEvaluateFeatureParity`  | Featureparitätsregeln auszuführen  | N
|`/AssessmentEvaluateCompatibilityIssues`     | Führen Sie Kompatibilitätsregeln  | J <br> (Entweder AssessmentEvaluateCompatibilityIssues oder AssessmentEvaluateRecommendations ist erforderlich.)
|`/AssessmentEvaluateRecommendations`     | Führen Sie die Vorschläge zu Features        | J <br> (AssessmentEvaluateCompatibilityIssues oder AssessmentEvaluateRecommendationsis erforderlich)
|`/AssessmentOverwriteResult`     | Überschreiben Sie die Ergebnisdatei    | N
|`/AssessmentResultJson`     | Vollständiger Pfad in die JSON-Ergebnisdatei     | J <br> (Entweder AssessmentResultJson oder AssessmentResultCsv ist erforderlich)
|`/AssessmentResultCsv`    | Vollständigen Pfad zu der CSV-Ergebnisdatei   | J <br>(Entweder AssessmentResultJson oder AssessmentResultCsv ist erforderlich)




## <a name="examples"></a>Beispiele

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Einzelne-Datenbank-Bewertung, die mit der Windows-Authentifizierung und Ausführung Kompatibilitätsregeln**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***Integrated Security=true*"**
***/AssessmentEvaluateCompatibilityIssues*** /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```



**Single-datenbankbewertung mithilfe von SQL Server-Authentifizierung und Ausführung Feature-Empfehlung**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***User Id=myUsername;Password=myPassword;***"
***/AssessmentEvaluateRecommendations*** /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```


**Single-Database-Bewertung für die Zielplattform SQL Server 2012, Ergebnisse in JSON und CSV-Datei speichern**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
***/AssessmentTargetPlatform="SqlServer2012"***
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
***/AssessmentResultJson***="C:\\temp\\Results\\AssessmentReport.json"
***/AssessmentResultCsv***="C:\\temp\\Results\\AssessmentReport.csv"
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
***/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"***
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```



## <a name="see-also"></a>Siehe auch

[Data Migration Assistant herunterladen](https://www.microsoft.com/download/details.aspx?id=53595)
