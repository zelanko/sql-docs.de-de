---
title: Analysieren konsolidierter Bewertungsberichte mit Power BI
titleSuffix: Data Migration Assistant
description: Erfahren Sie, wie Sie mit Power BI Berichte zur Daten Migrations Bewertung analysieren, die Sie in importiert und konsolidiert haben SQL Server
ms.custom: seo-lt-2019
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
ms.openlocfilehash: f2385914fc97fa8e118d871ddac6e0cdc9d49247
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056506"
---
# <a name="analyze-consolidated-assessment-reports-created-by-data-migration-assistant-with-power-bi"></a>Analysieren konsolidierter Bewertungsberichte, die von Datenmigrations-Assistent mit erstellt wurden Power BI

In diesem Artikel wird beschrieben, wie Sie einen Power BI Bericht erstellen, um konsolidierte Migrations Bewertungen zu analysieren.

Informationen zum Konsolidieren von Migrations Bewertungen, die vom Datenmigrations-Assistent erstellt wurden, finden Sie unter [Konsolidieren von Bewertungsberichten](../dma/dma-consolidatereports.md).

## <a name="sample-power-bi-reports"></a>Beispiel Power BI Berichte

Sie können Beispiele für Power BI Berichte für konsolidierte Migrations Bewertungen aus diesem [GitHub-Repository](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant)herunterladen.

Die folgenden Berichte sind enthalten: 

- [BRE](#dashboard-report)

  Umfasst momentaufnahmenstatistiken und einen Drilldownbericht.

- [Lokale Upgradebereitschaft](#on-premises-upgrade-readiness-report)

  Die Datenquelle ist die upgradebug-Sicht in der dmareporting-Datenbank.  Dieser Bericht zeigt den Erfolg der prozentualen Aktualisierung für Ihre bewerteten Datenbanken an.

- [Parität bei der lokalen Funktion](#on-premises-feature-parity-report)

  Zeigt die Funktions Empfehlungen für die Ziel SQL Server Version an.

- [Upgradebereitschaft der Azure SQL-Datenbank](#azure-sql-db-upgrade-readiness-report)

  Die Datenquelle ist die upgradebug-Sicht in der dmareporting-Datenbank.  Dieser Bericht zeigt den Erfolg der prozentualen Aktualisierung für Datenbanken an, die für Migrationen von Azure SQL-DB

- [Nicht unterstützte Azure SQL DB-Features](#azure-sql-db-unsupported-features-report)

  Zeigt Features in Ihren vorhandenen Datenbanken an, die in Azure SQL DB (V12) nicht unterstützt werden.

Sie können diese Berichte so ändern, dass Sie mit Ihrer Umgebung funktionieren, indem Sie die Datenquelle in Power BI ändern. 

1. Wählen Sie den Pfeil nach unten neben **Abfragen bearbeiten**aus, und wählen Sie **Datenquellen Einstellungen**aus.

   ![Menü "Abfragen bearbeiten", Datenquellen Einstellungen](../dma/media/DataSourceSettings.png)

1. Wählen Sie **Quelle ändern...** aus, und geben Sie die Werte für den Server und die Datenbank ein.

   ![Ändern der Quelle, des Servers und der Datenbank](../dma/media/ChangeSource.png)

1. Wählen Sie **OK**aus, und klicken Sie dann auf **Schließen**.

1. Aktualisieren Sie Ihre Berichte.

   ![Power BI Bericht aktualisieren](../dma/media/RefreshReport.png)

### <a name="dashboard-report"></a>Dashboardbericht

![Dashboardbericht](../dma/media/DashboardReport.png)

Das Dashboard zeigt Details zu all ihren Bewertungen an. Mithilfe der Slicer auf der linken Seite können Sie nach Instanz oder Datenbank filtern. Mithilfe des Balkendiagramms können Sie einen Drilldown in bestimmte Kategorien durchführen, um zu sehen, wo die Probleme liegen.

Um einen Drilldown auszuführen, wählen Sie den Kreis mit dem Pfeil nach unten in der oberen rechten Ecke des Balkendiagramms aus.

![Kategorie Drilldown](../dma/media/CategoryDrillDown.png)

Die Drilldown-Sequenz wird wie in der folgenden Abbildung dargestellt (unter **Achse**) festgelegt. Um die Sequenz zu ändern, ziehen Sie die Spalten in die gewünschte Reihenfolge.

![Visualisierungen, Balkendiagramm Achse](../dma/media/VisualizationsAxis.png)

Diese Ansicht wird noch leistungsfähiger, wenn Sie zum ersten Mal nach einer bestimmten Datenbank filtern und dann einen Drilldown auf die spezifischen kategorieprobleme ausführen. Im folgenden Beispiel wird die Personaldatenbank für Instanz **SQL01** ausgewählt, um alle Objekte anzuzeigen, die Migrationen verhindern (wichtige Änderungen).

![Wichtige Änderungen für die Personaldatenbank](../dma/media/BreakingChanges.png)

### <a name="on-premises-upgrade-readiness-report"></a>Bericht über lokale Upgradebereitschaft

![Bericht über lokale Upgradebereitschaft](../dma/media/OnPremisesUpgradeReadinessReport.png)

Dieser Bericht enthält eine Momentaufnahme der Vorbereitung der Datenbanken auf eine spätere Version SQL Server. Die Daten in diesem Bericht stammen aus dem dbo. Upgradebug-Faktor\_lokale Ansicht in der dmareporting-Datenbank.

Wenn Sie nach Instanz und Datenbankname Filtern und die Bewertungskarten oben verwenden, können Sie sehen, in welcher Version die Datenbank migriert werden konnte. Wenn Sie z. b. nach der AdventureWorks 2012-Datenbank filtern, können Sie sehen, dass die Datenbank bereit ist, zu allen im Bericht aufgeführten SQL Server Versionen zu wechseln. Dies wird bestimmt, indem sichergestellt wird, dass für diese Datenbank und den Kompatibilitäts Grad keine wichtigen Änderungen vorhanden sind.

![Erfolgreicher upgradefaktor für die AdventureWorks-Datenbank](../dma/media/UpgradeSuccessFactor.png)

### <a name="on-premises-feature-parity-report"></a>Bericht zur lokalen Funktions Parität

![Bericht zur lokalen Funktions Parität](../dma/media/OnPremisesFeatureParityReport.png)

Verwenden Sie diesen Bericht, um neue Funktionen hervorzuheben, die für die Datenbank in der Ziel SQL Server Version verwendet werden können.

Wenn Sie im Trichter Diagramm eine Funktion auswählen, wird durch die Daten am unteren Rand hervorgehoben, welche Objekte von der Funktion betroffen sind. Im folgenden Beispiel wird die Funktion **Stretch Database for Storage-Einsparungen** ausgewählt, und es wird eine Tabelle aufgeführt, die von dieser Funktion profitieren kann.

![Funktions Empfehlung für Stretch Database](../dma/media/FeatureRecommend_StretchDatabase.png)

### <a name="azure-sql-db-upgrade-readiness-report"></a>Azure SQL-DB-Upgradebereitschaft-Bericht

![Azure SQL-DB-Upgradebereitschaft-Bericht](../dma/media/AzureSQLDBUpgradeReadinessReport.png)

Dieser Bericht zeigt die Daten Bank Bereitschaft für die Migration zu Azure SQL-Datenbank V12. Die Daten aus diesem Bericht stammen aus dem dbo. Die Upgrade Success Ranking-Sicht in der dmareporting-Datenbank.

### <a name="azure-features-parity-report"></a>Paritäts Bericht zu Azure-Features

![Paritäts Bericht zu Azure-Features](../dma/media/AzureFeaturesParityReport.png)

Mithilfe dieses Berichts, markieren Sie die *Ebene Instanzfunktionen* werden von Azure SQL-Datenbank V12 nicht unterstützt.

Wenn Sie im Trichter Diagramm eine Funktion auswählen, werden in den unten stehenden Daten die Instanzen und Datenbankfunktionen aufgelistet, die nicht unterstützt werden. Im folgenden Beispiel wird diese Funktion ausgewählt: die **Konfiguration der Always on-Verfügbarkeits Gruppe wird in Azure SQL-Datenbank nicht unterstützt**.  

![Feature der Always on-Verfügbarkeits Gruppe](../dma/media/Feature_AlwaysOnAvailability.png)

 
### <a name="azure-sql-db-unsupported-features-report"></a>Bericht zu nicht unterstützten Azure SQL-DB-Features

![Bericht zu nicht unterstützten Azure SQL-DB-Features](../dma/media/AzureSQLDBUnsupportedFeaturesReport.png)

In diesem Bericht wird hervorgehoben, welche Features für eine bestimmte **Datenbank** nicht unterstützt werden, wenn das Ziel Azure SQL-Datenbank (V12) ist.

Wenn Sie nach dem Datenbanknamen und dem Merkmals Wert im Trichter Diagramm filtern, können Sie Details zu der nicht unterstützten Funktion anzeigen. Details umfassen, welches Objekt betroffen ist, sowie Empfehlungen zur Behebung des Problems.

Beispielsweise kann das Filtern nach DTC-Datenbank und schreibgeschützten **Datenbanken nicht aktualisiert werden**. es wird eine Liste der betroffenen Objekte angezeigt.

![Problem bei schreibgeschützten Datenbanken kann nicht aktualisiert werden](../dma/media/ReadOnlyDatabases.png)

## <a name="see-also"></a>Siehe auch

[Übersicht über Datenmigrations-Assistent](../dma/dma-overview.md)

[Datenmigrations-Assistent Download](https://www.microsoft.com/download/details.aspx?id=53595)

[Power BI Download](https://powerbi.microsoft.com/)
