---
title: Analysieren Sie konsolidierte Data Migration Assistant-Bewertung-Berichte mit Power BI (SQL Server) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Power BI zu verwenden, um Data Migration-Bewertungsberichte zu analysieren, die Sie importiert haben, und konsolidiert, die in SQL Server
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: jroth
ms.openlocfilehash: 996bf79c296ff11c708c687f5a084d73b0bcde95
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794328"
---
# <a name="analyze-consolidated-assessment-reports-created-by-data-migration-assistant-with-power-bi"></a>Analysieren Sie konsolidierte Bewertungsberichte erstellt, die von Data Migration Assistant mit Power BI

Dieser Artikel beschreibt, wie eine Power BI-Berichts zum Analysieren von konsolidierten Migration Bewertungen zu erstellen.

Informationen zum Konsolidieren von Migration Bewertungen, die von den Data Migration Assistant erstellt, finden Sie unter [Bewertungsberichte konsolidieren](../dma/dma-consolidatereports.md).

## <a name="sample-power-bi-reports"></a>Beispiel-Power BI-Berichten

Sie können Beispiele für Power BI-Berichte für konsolidierte Migration Bewertungen aus diesem [Github-Repository](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant).

Die folgenden Berichte sind enthalten: 

- [Dashboard](#dashboard-report)

  Enthält Statistiken der Momentaufnahme und einen Drilldown-Bericht.

- [Lokale Upgradebereitschaft](#on-premises-upgrade-readiness-report)

  Die Datenquelle ist die UpgradeSuccessRanking-Ansicht in der Datenbank DMAReporting.  Dieser Bericht zeigt den Prozentsatz Upgrade erfolgreich für Ihre Datenbanken bewerteten.

- [Lokale Featureparität](#on-premises-feature-parity-report)

  Zeigt die Vorschläge zu Features für die SQL Server-Zielversion.

- [Azure SQL-Datenbank mit Upgrade readiness](#azure-sql-db-upgrade-readiness-report)

  Die Datenquelle ist die UpgradeSuccessRanking-Ansicht in der Datenbank DMAReporting.  Dieser Bericht zeigt den Prozentsatz Upgrade Erfolg für Datenbanken, die für Migrationen von Azure SQL-Datenbank bewertet.

- [Azure SQL-Datenbank nicht unterstützte Funktionen](#azure-sql-db-unsupported-features-report)

  Zeigt Funktionen in Ihre vorhandenen Datenbanken, die in Azure SQL-Datenbank (V12) nicht unterstützt werden.

Sie können diese Berichte in Ihrer Umgebung funktioniert, ändern Sie die Datenquelle in Power BI ändern. 

1. Aktivieren Sie den Pfeil nach unten neben **Abfragen bearbeiten**, und wählen Sie **datenquelleneinstellungen**.

   ![Bearbeiten von Abfragen im Menü Einstellungen für die Datenquelle](../dma/media/DataSourceSettings.png)

1. Wählen Sie **Quelle ändern...** , und geben Sie die Werte für Server und Datenbank.

   ![Quelle ändern, Server und Datenbank](../dma/media/ChangeSource.png)

1. Wählen Sie **OK**, und wählen Sie dann **schließen**.

1. Aktualisieren Sie Ihre Berichte.

   ![Aktualisieren von Power BI-Bericht](../dma/media/RefreshReport.png)

### <a name="dashboard-report"></a>Dashboardbericht

![Dashboardbericht](../dma/media/DashboardReport.png)

Das Dashboard zeigt Details aller Ihre Bewertungen. Sie können die Slicer auf der linken Seite verwenden, zum Filtern nach Instanz oder Datenbank. Sie können das Balkendiagramm verwenden, um einen Drilldown in bestimmte Kategorien, um festzustellen, wo die Probleme liegen.

Um einen Drilldown ausführen möchten, wählen Sie den Kreis mit den Pfeil nach unten in der oberen rechten Ecke des Balkendiagramms.

![Drilldown für Kategorie](../dma/media/CategoryDrillDown.png)

Die Drilldown-Sequenz wird festgelegt, wie in der folgenden Abbildung dargestellt (unter **Achse**). Um die Reihenfolge zu ändern, ziehen Sie die Spalten in der gewünschten Reihenfolge.

![Visualisierungen, Balkendiagramm-Achse](../dma/media/VisualizationsAxis.png)

In dieser Ansicht wird noch leistungsfähiger, wenn Sie zuerst nach einer bestimmten Datenbank filtern, und klicken Sie dann einen Drilldown für die bestimmte Kategorie Probleme. Im folgenden Beispiel wird die HR-Datenbank für die Instanz ausgewählt **SQL01** alle Objekte anzuzeigen, die Migrationen (wichtige Änderungen) verhindern.

![Grundlegende Änderungen für die HR-Datenbank](../dma/media/BreakingChanges.png)

### <a name="on-premises-upgrade-readiness-report"></a>Lokales aktualisieren Bericht "Testfallbereitschaft"

![Lokales aktualisieren Bericht "Testfallbereitschaft"](../dma/media/OnPremisesUpgradeReadinessReport.png)

Dieser Bericht zeigt eine Momentaufnahme kann die Datenbanken sind auf eine neuere Version von SQL Server zu migrieren. Die Daten in diesem Bericht stammen aus das "Dbo". UpgradeSuccessFactor\_OnPrem-Sicht in der DMAReporting-Datenbank.

Filtern nach Instanz- und Datenbanknamen und die Bewertung Karten oben verwenden, sehen Sie die Version die Datenbank zu migriert werden kann. Z. B. Wenn Sie von der AdventureWorks 2012-Datenbank filtern, sehen Sie, dass die Datenbank bereit für alle SQL Server-Versionen, die im Bericht aufgeführt ist. Dies wird bestimmt, indem Sie sicherstellen, dass es sind keine aktuellen Änderungen für diese Datenbank und die Kompatibilität.

![Aktualisieren von Erfolgsfaktor für AdventureWorks-Datenbank](../dma/media/UpgradeSuccessFactor.png)

### <a name="on-premises-feature-parity-report"></a>Lokale feature Parity-Bericht

![Lokale feature Parity-Bericht](../dma/media/OnPremisesFeatureParityReport.png)

Verwenden Sie diesen Bericht, um neue Features hervorzuheben, die für die Datenbank in der SQL Server-Zielversion verwendet werden kann.

Wenn Sie eine Funktion in das Trichterdiagramm auswählen, werden die Daten im unteren Bereich hervorgehoben, welche Objekte von der Funktion betroffen sind. Im folgenden Beispiel die **Stretch-Datenbank zum Einsparen von Speicherkosten** Feature aktiviert ist, und eine Tabelle ist aufgeführt, die von dieser Funktion profitieren könnten.

![Feature-Empfehlung für Stretch Database](../dma/media/FeatureRecommend_StretchDatabase.png)

### <a name="azure-sql-db-upgrade-readiness-report"></a>Azure SQL-Datenbank mit Upgrade Readiness-Bericht

![Azure SQL-Datenbank mit Upgrade Readiness-Bericht](../dma/media/AzureSQLDBUpgradeReadinessReport.png)

Dieser Bericht zeigt die Datenbank-Bereitschaft zum Migrieren zu Azure SQL-Datenbank V12. Die Daten aus diesem Bericht stammen aus das "Dbo". In der Datenbank DMAReporting UpgradeSuccessRanking-Ansicht.

### <a name="azure-features-parity-report"></a>Azure-Features Parität Bericht

![Azure-Features Parität Bericht](../dma/media/AzureFeaturesParityReport.png)

Mithilfe dieses Berichts, markieren Sie die *Ebene Instanzfunktionen* werden von Azure SQL-Datenbank V12 nicht unterstützt.

Wenn Sie eine Funktion in das Trichterdiagramm auswählen, enthält die Daten am unteren Rand der Instanzen und Funktionen der Datenbank, die unterstützt werden. Im folgenden Beispiel wird dieses Feature ausgewählt: **Immer auf der Verfügbarkeit Konfiguration wird nicht unterstützt in Azure SQL-Datenbank**.  

![Always on-Verfügbarkeitsgruppen-Funktion](../dma/media/Feature_AlwaysOnAvailability.png)

 
### <a name="azure-sql-db-unsupported-features-report"></a>Bericht zur Azure SQL-Datenbank nicht unterstützte Funktionen

![Bericht zur Azure SQL-Datenbank nicht unterstützte Funktionen](../dma/media/AzureSQLDBUnsupportedFeaturesReport.png)

Dieser Bericht hebt hervor, welche Funktionen nicht unterstützt werden, für einen bestimmten **Datenbank** Wenn das Ziel ist Azure SQL-Datenbank (V12).

Mithilfe der Filterung durch den Datenbank-Namen und Feature-Wert, in das Trichterdiagramm können Sie Details für die nicht unterstützten Funktionen anzeigen. Details enthalten, welches Objekt betroffen ist und Empfehlungen zur Behandlung des Problems.

Z. B. das Filtern nach der DTC-Datenbank und **schreibgeschützte Datenbanken können nicht aktualisiert werden**, sehen Sie eine Liste von Objekten, die betroffen sind.

![Schreibgeschützte Datenbanken nicht aktualisiert Problem](../dma/media/ReadOnlyDatabases.png)

## <a name="see-also"></a>Siehe auch

[Übersicht über Data Migration Assistant](../dma/dma-overview.md)

[Data Migration Assistant herunterladen](https://www.microsoft.com/download/details.aspx?id=53595)

[Power BI-download](https://powerbi.microsoft.com/)
