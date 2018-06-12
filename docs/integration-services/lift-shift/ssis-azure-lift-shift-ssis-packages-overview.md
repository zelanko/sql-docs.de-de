---
title: Migration von SQL Server Integration Services-Workloads in die Cloud per Lift & Shift | Microsoft-Dokumentation
ms.date: 05/22/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f62987a7edc2d04f88c3cfe98f04f0bd6043b44a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585572"
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Migration von SQL Server Integration Services-Workloads in die Cloud per Lift & Shift
Sie können Ihre SQL Server Integration Services-Pakete und -Workloads (SSIS) nun in die Azure-Cloud verschieben.
-   Speichern und verwalten Sie SSIS-Projekte und -Pakete in der SSIS-Katalogdatenbank (SSISDB) in Azure SQL-Datenbank oder verwaltete SQL-Datenbank-Instanz (Vorschauversion).
-   Führen Sie Pakete in einer Instanz von Azure SSIS Integration Runtime aus, eine Komponente von Azure Data Factory.
-   Verwenden Sie vertraute Tools für allgemeine Aufgaben, z.B. SQL Server Management Studio (SSMS).

## <a name="benefits"></a>Vorteile
Das Verschieben Ihrer SSIS-Workload in Azure hat folgende potenzielle Vorteile:
-   **Verringern Sie Betriebskosten** und den Aufwand der Verwaltung der Infrastruktur, der anfällt, wenn Sie SSIS lokal oder auf virtuellen Azure-Computern ausführen.
-   **Erhöhen Sie die Hochverfügbarkeit** und die Hochverfügbarkeitsfeatures von Azure und Azure SQL-Datenbank durch die Möglichkeit, mehrere Knoten pro Cluster anzugeben.
-   **Erhöhen Sie die Skalierbarkeit** durch die Möglichkeit, mehrere Kerne pro Knoten (zentrales Hochskalieren) und mehrere Knoten pro Cluster (horizontales Hochskalieren) anzugeben.

## <a name="architecture-overview"></a>Übersicht über die Architektur
In der folgenden Tabelle werden die Unterschiede zwischen der lokalen Ausführung von SSIS und SSIS in Azure hervorgehoben. Der wichtigste Unterschied ist die Trennung des Speichers von Runtime. Azure Data Factory hostet die Runtime-Engine für SSIS-Pakete in Azure. Die Runtime-Engine wird als Azure SSIS Integration Runtime (Azure SSIS IR) bezeichnet. Weitere Informationen finden Sie unter [Azure SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime).

| Speicherung | Typ | Skalierbarkeit |
|---|---|---|
| Lokal (SQL Server) | Von SQL Server gehostete SSIS-Runtime | SSIS Scale Out (in SQL Server 2017 und höher)<br/><br/>Benutzerdefinierte Projektmappen (in früheren Versionen von SQL Server) |
| In Azure (SQL-Datenbank oder verwaltete SQL-Datenbank-Instanz (Vorschauversion)) | Azure SSIS Integration Runtime, eine Komponente von Azure Data Factory | Skalierungsoptionen für die Azure SSIS Integration Runtime |
| | | |

Sie müssen Azure SSIS IR nur einmal bereitstellen. Danach können Sie vertraute Tools wie SQL Server Data Tools (SSDT) und SQL Server Management Studio (SSMS) für das Bereitstellen, Konfigurieren, Ausführen, Überwachen, Planen und Verwalten von Paketen verwenden.

## <a name="version-support"></a>Versionsunterstützung

Sie können ein Paket in Azure bereitstellen, das mit einer beliebigen Version von SSIS erstellt wurde. Wenn Sie ein Paket in Azure bereitstellen, wird das Paket automatisch in das aktuelle Paketformat geändert, sofern es zu keinen Überprüfungsfehlern kam. Das heißt, es wird immer auf die aktuelle Version von SSIS aktualisiert.

Der Bereitstellungsprozess überprüft Pakete, um sicherzustellen, dass sie auf der Integration Runtime von Azure SSIS ausgeführt werden können. Weitere Informationen finden Sie unter [Überprüfen von in Azure bereitgestellten SSIS-Paketen](ssis-azure-validate-packages.md).

## <a name="prerequisites"></a>Voraussetzungen

Zum Bereitstellen von SSIS-Paketen in Azure benötigen Sie eine der folgenden Versionen von SQL Server Data Tools (SSDT):
-   Version 15.3 oder höher für Visual Studio 2017.
-   Version 17.2 oder höher für Visual Studio 2015.

Informationen über die Voraussetzungen für die Azure SSIS Integration Runtime finden Sie unter [Bereitstellen von SQL Server Integration Services-Paketen in Azure: Voraussetzungen](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure#prerequisites).

> [!NOTE]
> Während dieser öffentlichen Vorschauversion ist Azure SSIS Integration Runtime noch nicht in allen Regionen verfügbar. Weitere Informationen zu den unterstützten Regionen finden Sie unter [Verfügbare Produkte nach Region – Microsoft Azure](https://azure.microsoft.com/regions/services/).

## <a name="provision-ssis-on-azure"></a>Bereitstellen von SSIS in Azure

Bevor Sie SSIS-Pakete in Azure bereitstellen und ausführen können, müssen Sie die SSIS-Katalogdatenbank (SSISDB) und Azure SSIS Integration Runtime bereitstellen. Führen Sie die Bereitstellungsschritte in diesem Artikel aus: [Bereitstellen von SQL Server Integration Services-Paketen in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

Wenn Sie Azure SSIS IR bereitstellen, können Sie zentral und horizontal hochskalieren, indem Sie Werte für die folgenden Optionen angeben:
-   Die Knotengröße (einschließlich der Anzahl von Kernen) und die Anzahl von Knoten im Cluster.
-   Die vorhandene Instanz von Azure SQL-Datenbank, auf der die SSIS-Katalogdatenbank (SSISDB) gehostet werden soll, und die Dienstebene der Datenbank.
-   Die maximalen parallelen Ausführungen pro Knoten.

Weitere Informationen zur Leistung finden Sie unter [Konfigurieren von Azure SSIS Integration Runtime für hohe Leistung](https://docs.microsoft.com/azure/data-factory/configure-azure-ssis-integration-runtime-performance).

## <a name="design-packages"></a>Entwerfen von Paketen

Sie können Pakete weiterhin lokal in SSDT oder in Visual Studio (wenn SSDT installiert ist) **entwerfen und erstellen**.

### <a name="connect-to-data-sources"></a>Verbindung mit Datenquellen herstellen

Weitere Informationen zur Verbindung mit lokalen Datenquellen aus der Cloud mithilfe der **Windows-Authentifizierung** finden Sie unter [Herstellen einer Verbindung mit lokalen Datenquellen und Azure-Dateifreigaben mit der Windows-Authentifizierung](ssis-azure-connect-with-windows-auth.md).

Informationen dazu, wie Sie eine Verbindung zu Dateien und Dateifreigaben herstellen, finden Sie unter [Speichern und Abrufen von Dateien auf lokalen Dateifreigaben und Dateifreigaben in Azure mit SSIS](ssis-azure-files-file-shares.md).

### <a name="available-ssis-components"></a>Verfügbare SSIS-Komponenten

Wenn Sie eine Instanz von SQL-Datenbank bereitstellen, um SSISDB zu hosten, werden auch das Azure Feature Pack für SSIS und die weitervertreibbare Komponente von Access installiert. Diese Komponenten stellen zusätzlich zu den Datenquellen, die von den integrierten Komponenten unterstützt werden, die Konnektivität zu **Excel- und Access-Dateien** und zu verschiedenen **Azure**-Datenquellen bereit.

Sie können auch weitere Komponenten installieren, wie z.B. einen Treiber, der standardmäßig nicht installiert ist. Weitere Informationen finden Sie unter [Custom setup for the Azure-SSIS integration runtime (Benutzerdefiniertes Setup von Azure SSIS Integration Runtime)](/azure/articles/data-factory/how-to-configure-azure-ssis-ir-custom-setup.md).

Wenn Sie ein unabhängiger Softwareanbieter sind, können Sie die Installation Ihrer lizensierten Komponente aktualisieren, um sie in Azure zur Verfügung zu stellen. Weitere Informationen finden Sie unter [Entwickeln kostenpflichtiger oder lizenzierter benutzerdefinierter Komponenten für Azure SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/how-to-develop-azure-ssis-ir-licensed-components).

### <a name="transaction-support"></a>Transaktionsunterstützung

Sie können mit SQL Server auf virtuellen Computern in Azure und lokal Microsoft Distributed Transaction Coordinator-Transaktionen (MS DTC) verwenden. Verwenden Sie die Funktion für die benutzerdefinierte Installation, um MS DTC auf jedem Knoten von Azure SSIS IR zu konfigurieren. Weitere Informationen finden Sie unter [Custom setup for the Azure-SSIS integration runtime (Benutzerdefiniertes Setup von Azure SSIS Integration Runtime)](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup).

Mit Azure SQL-Datenbank können Sie nur elastische Transaktionen verwenden. Weitere Informationen finden Sie unter [Verteilte Transaktionen in mehreren Clouddatenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-transactions-overview).

## <a name="deploy-and-run-packages"></a>Bereitstellen und Ausführen von Paketen

Erste Schritte finden Sie unter [Bereitstellen, Ausführen und Überwachen eines SSIS-Pakets in Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="connect-to-ssisdb"></a>Herstellen einer Verbindung mit SSISDB

Der **Name der SQL-Datenbank**, die SSISDB hostet, stellt den ersten Teil des vierteiligen Namens dar, den Sie beim Bereitstellen und Ausführen von Paketen von SSDT und SSMS im folgenden Format verwenden müssen: `<sql_database_name>.database.windows.net`. Informationen darüber, wie Sie eine Verbindung zur SSIS-Katalogdatenbank in Azure herstellen, finden Sie unter [Herstellen einer Verbindung mit der SSISDB-Katalogdatenbank in Azure](ssis-azure-connect-to-catalog-database.md).

### <a name="deploy-projects-and-packages"></a>Bereitstellen von Projekten und Paketen

Sie müssen das **Projektbereitstellungsmodell** verwenden und nicht das Paketbereitstellungsmodell, wenn Sie Projekte für SSISDB in Azure bereitstellen.

Zum Bereitstellen von Projekten in Azure können Sie folgende vertraute Tools und Skriptoptionen verwenden:
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (von SSMS, Visual Studio Code oder einem anderen Tool)
-   Ein Befehlszeilentool
-   PowerShell oder C# und das Objektmodell der SSIS-Verwaltung

Unter [Bereitstellen, Ausführen und Überwachen eines SSIS-Pakets in Azure](ssis-azure-deploy-run-monitor-tutorial.md) finden Sie ein Bereitstellungsbeispiel, in dem SSMS und der Bereitstellungs-Assistent für Integration Services verwendet werden.

### <a name="run-packages"></a>Ausführen von Paketen

Unter [Ausführen eines SSIS-Pakets in Azure](ssis-azure-run-packages.md) finden Sie eine Übersicht über die Methoden, mit denen in Azure bereitgestellte SSIS-Pakete ausgeführt werden können.

## <a name="pass-runtime-values-with-environments"></a>Übergeben von Laufzeitwerten mit Umgebungen

Wenn Sie mindestens einen Laufzeitwert an Pakete übergeben möchten, die als Teil einer Azure Data Factory-Pipeline ausgeführt werden, müssen Sie mit SQL Server Management Studio (SSMS) SSIS-Ausführungsumgebungen in SSISDB erstellen. Erstellen Sie in jeder Umgebung Variablen, und weisen Sie Werte zu, die den Parametern für Ihre Projekte oder Pakete entsprechen. Konfigurieren Sie Ihre SSIS-Pakete in SSMS, um Ihren Projekt- oder Paketparametern diese Umgebungsvariablen zuzuordnen. Wenn Sie die Pakete in einer Data Factory-Pipeline ausführen, können Sie zwischen Umgebungen wechseln, indem Sie auf der Registerkarte „Einstellungen“ der Benutzeroberfläche der Aktivität „SSIS-Paket ausführen“ verschiedene Umgebungspfade angeben.

Weitere Informationen zu SSIS-Umgebungen finden Sie unter [Erstellen und Zuordnen einer Serverumgebung](../packages/deploy-integration-services-ssis-projects-and-packages.md#create-and-map-a-server-environment). Weitere Informationen zum Ausführen eines Pakets als Teil einer Azure Data Factory-Pipeline finden Sie unter [Ausführen eines SSIS-Pakets mit der Aktivität „SSIS-Paket ausführen“ in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).

## <a name="monitor-packages"></a>Überwachen von Paketen
Sie können das folgende Berichtstool in SSMS verwenden, um ausgeführte Pakete in SSMS zu überwachen.
-   Klicken Sie mit der rechten Maustaste auf **SSISDB**, und klicken Sie dann auf **Aktive Vorgänge**, um das Dialogfeld **Aktive Vorgänge** zu öffnen.
-   Wählen Sie im Objekt-Explorer ein Paket aus, klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Berichte** > **Standardberichte** > **Alle Ausführungen**.

Informationen zum Überwachen der Azure SSIS Integration Runtime finden Sie unter [Monitor the Azure-SSIS integration runtime (Überwachen der Azure SSIS Integration Runtime)](https://docs.microsoft.com/azure/data-factory/monitor-integration-runtime#azure-ssis-integration-runtime).

## <a name="schedule-packages"></a>Planen von Paketen
Sie können eine Vielzahl von Tools verwenden, um die Ausführung von in Azure SQL-Datenbank gespeicherten Paketen zu planen. Weitere Informationen finden Sie unter [Schedule SSIS package execution on Azure (Planen der Ausführung von SSIS-Paketen in Azure)](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu den ersten Schritten mit SSIS-Workloads in Azure finden Sie in folgenden Artikeln:
-   [Bereitstellen von SQL Server Integration Services-Paketen in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)
-   [Bereitstellen, Ausführen und Überwachen eines SSIS-Pakets in Azure](ssis-azure-deploy-run-monitor-tutorial.md)
