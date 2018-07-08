---
title: Importieren und Konsolidieren von Data Migration Assistant assessmentberichten (SQL Server) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Berichte zur Bewertung von Data Migration Assistant in eine SQL Server-Datenbank zu importieren und mehreren Berichten zu konsolidieren.
ms.custom: ''
ms.date: 04/16/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: be9fc224093f0d5ae14372d4674a52589a2d4801
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781771"
---
# <a name="import-and-consolidate-data-migration-assistant-assessment-reports"></a>Importieren und Konsolidieren von assessmentberichten Data Migration Assistant

Sie können die Befehlszeile verwenden, Migration Bewertungen im unbeaufsichtigten Modus ausführen, beginnend mit den Data Migration Assistant v2. 1. Dieses Feature können Sie die Bewertungen ausgeführt und skaliert. Die der Bewertungsergebnisse in Form einer JSON- oder CSV-Datei.

Sie können mehrere Datenbanken in eine einzelne Instanziierung des Data Migration Assistant-Befehlszeilen-Hilfsprogramms zu bewerten und alle Bewertungen Ergebnisse in eine einzelne JSON-Datei exportieren. Alternativ können Sie eine Datenbank zum Zeitpunkt bewerten und später die Ergebnisse aus diesen mehrere JSON-Dateien in einer SQL-Datenbank zu konsolidieren.

Informationen zum Data Migration Assistant von der Befehlszeile aus ausführen, finden Sie unter [ausführen Data Migration Assistant über Befehlszeile](../dma/dma-commandline.md). 

## <a name="import-assessment-results-into-a-sql-server-database"></a>Importieren Sie Ergebnisse in einer SQL Server-Datenbank

Verwenden Sie das PowerShell-Skript finden Sie in diesem [Github-Repository](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant) um die Bewertungsergebnisse aus JSON-Dateien in SQL Server-Datenbank zu importieren.

> [!NOTE]
> PowerShell 5.x oder höher ist erforderlich.

Wenn Sie das Skript ausführen, müssen Sie die folgenden Informationen angeben: 

- **ServerName**: Name des SQL Server-Instanz, dass Sie die Bewertung importieren möchten aus JSON-Dateien führt.

- **DatabaseName**: der Name der Datenbank, die die Ergebnisse in importiert zu erhalten.

- **JsonDirectory**: der Ordner, die die Bewertungsergebnisse, in eine oder mehrere JSON-Dateien gespeichert.

- **ProcessTo**: SQL Server

Fügen Sie die vorherigen Werte wie folgt im Abschnitt "Funktionen ausführen" hinzu.

```
dmaProcessor -serverName localhost \`\
-databaseName DMAReporting \`\
-jsonDirectory "C:\\temp\\DMACmd\\output\\" \`\
-processTo SQLServer
```

Das PowerShell-Skript wird in der SQL-Instanz, die Sie angegeben haben, die folgenden Objekte erstellt, wenn die Objekte nicht bereits vorhanden sind:

- **Datenbank** : dem Namen in die PowerShell-Parameter

  - Wichtigstes repository

- **Tabelle** – ReportData

  - Für die Berichterstattung

- **Tabelle** -BreakingChangeWeighting

  - Verweistabelle für alle Änderungen. Hier können Sie Ihre eigenen Werte Gewichtung, um zu beeinflussen, eine genauere Prozentsatz (%)-Upgrade erfolgreich Rangfolge definieren.

- **Ansicht** – UpgradeSuccessRanking\_OnPrem

  - Die Ansicht ein Erfolgsfaktor für jede zu migrierte lokale Datenbank anzeigen.

- **Ansicht** – UpgradeSuccessRanking\_Azure

  - Die Ansicht ein Erfolgsfaktor für jede zu migrierte lokale Datenbank anzeigen.

- **Gespeicherte Prozedur** – JSONResults\_einfügen

  - Zum Importieren von Daten aus einer JSON-Datei in SQL Server verwendet.

- **Gespeicherte Prozedur** – AzureFeatureParityResults\_einfügen

  - Verwendet, um die Azure-Feature Parity Ergebnisse aus einer JSON-Datei in SQL Server zu importieren.

- **Tabellentyp** – JSONResults

  - Zum Speichern der JSON-Ergebnisse für lokale Bewertungen, und übergeben Sie an der JSONResults\_gespeicherte Prozedur Insert

- **Tabellentyp** – AzureFeatureParityResults

  - Verwendet, um enthalten die das Azure Feature Parity Ergebnisse für Azure-Bewertungen und übergeben Sie an der AzureFeatureParityResults\_gespeicherte Prozedur Insert

PowerShell-Skript erstellt eine **verarbeitete** Verzeichnis in das angegebene Verzeichnis, das die JSON-Dateien enthält, die verarbeitet werden sollen.

Nachdem das Skript abgeschlossen ist, werden die Ergebnisse in die Tabelle ReportData importiert.

### <a name="viewing-the-results-in-sql-server"></a>Anzeigen der Ergebnisse in SQL Server

Nachdem die Daten geladen wurden, verbinden Sie sich mit Ihrer SQL Server-Instanz. Ihr Bildschirm sollte angezeigt werden, wie in der folgenden Abbildung gezeigt:

![Konsolidierte Berichte in SQL Server-Datenbank](../dma/media/DMAReportingDatabase.png)

Das "Dbo". ReportData-Tabelle enthält den Inhalt der JSON-Datei in unformatierter Form an.

## <a name="on-premises-upgrade-success-ranking"></a>Lokales aktualisieren Erfolg Rangfolge

Um eine Liste der Datenbanken und der Rang Erfolg in Prozent (%) zu sehen, wählen Sie das "Dbo" ein. UpgradeSuccessRanking_OnPrem-Ansicht:

![Anzeige von Daten im UpgradeSuccessRaning_OnPrem](../dma/media/UpgradeSuccessRankingView.png)

Hier können Sie für eine bestimmte Datenbank finden Sie unter Was ist, dass das Upgrade erfolgreich Risiko für die verschiedenen Kompatibilitätsgraden funktionsfähig. Daher wurde beispielsweise die HR-Datenbank für den Kompatibilitätsgraden 100, 110, 120 und 130 bewertet. Dieser Bewertung können Sie visuell zu verfolgen, wie viel Aufwand bei der Migration auf eine neuere Version von SQL Server von der aktuellen Version, die die Datenbank derzeit auf beteiligt ist.

In der Regel ist die Metrik, die, der Ihnen wichtig, sind wie viele Änderungen gibt es für eine bestimmte Datenbank. Im obigen Beispiel sehen Sie sich, dass die HR-Datenbank ein Upgrade Erfolgsfaktor von 50 % bei Kompatibilitätsgraden 100, 110, 120 und 130 verfügt.

Diese Metrik kann beeinflusst werden, durch die Gewichtung-Werte in das "Dbo" ändern. BreakingChangeWeighting-Tabelle.

Im folgenden Beispiel der Aufwand zum Beheben des Syntax-Problems in der HR-Datenbank ist als hoch eingestuft, damit Sie der Wert 3 zugewiesen wird **Aufwand**. Da es zur Behebung des Problems Syntax lange dauern würde nicht, wird der Wert 1 zugewiesen **FixTime**. Da wäre Kosten beteiligt, die Sie die Änderung vorgenommen, wird der Wert 2 zugewiesen **Kosten**. Dieser Wert ändert sich der kombinierten Changerank auf 2.

> [!NOTE]
> Die Bewertung wird auf einer Skala von 1 bis 5.  1 steht für niedrige und 5 werden hoch. Darüber hinaus ist die ChangeRank eine berechnete Spalte.

![Aufwand, Kosten und FixTime Werte für Syntaxproblem.](../dma/media/SyntaxIssueEffort.png)

In diesem Beispiel, bei der Abfrage des "Dbo". UpgradeSuccessRanking_OnPrem Ansicht wurde das Upgrade Erfolgsfaktor für die HR-Datenbank Informationen zu grundlegenden Änderungen verworfen.

![Aktualisieren von Erfolgsfaktor für die HR-Datenbank](../dma/media/UpgradeSuccessFactor_HR.png)

## <a name="azure-upgrade-success-ranking"></a>Rangfolge von Azure Upgrade erfolgreich

Um eine Liste der Datenbanken, um die Migration zu Azure SQL-Datenbank und ihren Erfolg QUANTILSRANG anzuzeigen, wählen Sie das "Dbo" ein. UpgradeSuccessRanking_Azure anzeigen.

![Anzeige von Daten im UpgradeSuccessRanking_Azure](../dma/media/UpgradeSuccessRankingView_Azure.png)

Hier können Sie den Wert MigrationBlocker interessiert. 100,00 bedeutet, dass 100 % ige erfolgswahrscheinlichkeit Rang für das Verschieben einer Datenbank in Azure SQL-Datenbank v12 vorhanden ist.

Der Unterschied in dieser Ansicht ist, dass derzeit keine Überschreibung für die Gewichtung für die Migration Blocker Regeln ändern.

Informationen für die berichterstellung für diese Daten mit Power BI finden Sie unter [erstatten Sie Bericht über die konsolidierte Assessments mit Power BI](../dma/dma-powerbiassesreport.md).
