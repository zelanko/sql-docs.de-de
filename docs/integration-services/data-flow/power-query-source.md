---
title: Power Query-Quelle | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Power Query-Quelle im SQL Server Integration Services-Datenfluss konfigurieren.
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: integration-services
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.powerqueryconnmgr.f1
- sql13.ssis.designer.powerquerysource.queries.f1
- sql13.ssis.designer.powerquerysource.connmgrs.f1
- sql14.ssis.designer.powerqueryconnmgr.f1
- sql14.ssis.designer.powerquerysource.queries.f1
- sql14.ssis.designer.powerquerysource.connmgrs.f1
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
manager: craigg
ms.openlocfilehash: 3ca141c40420b4d2e71a660220075413d9ca8c64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66015082"
---
# <a name="power-query-source-preview"></a>Power Query-Quelle (Preview)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Dieser Artikel beschreibt, wie Sie die Eigenschaften der Power Query-Quelle im SQL Server Integration Services-Datenfluss konfigurieren. Power Query ist eine Technologie, mit der Sie eine Verbindung mit verschiedenen Datenquellen herstellen und Daten mithilfe von Excel/Power BI Desktop transformieren können. Weitere Informationen finden Sie in dem Artikel [Power Query – Übersicht und Schulung](https://support.office.com/article/power-query-overview-and-learning-ed614c81-4b00-4291-bd3a-55d80767f81d). Das von Power Query generierte Skript kann kopiert und in die Power Query-Quelle im SSIS-Datenfluss eingefügt werden, um sie zu konfigurieren.
  
> [!NOTE]
> Für das aktuelle Preview-Release kann die Power Query-Quelle zur Erleichterung des schnellen Sammelns von Feedback und regelmäßiger Funktionsverbesserungen nur in SQL Server Data Tools (SSDT) und Azure-SSIS Integration Runtime (IR) in Azure Data Factory (ADF) verwendet werden. Sie können die neuesten SSDT, die die Power Query-Quelle unterstützen, [hier](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017) herunterladen. Informationen zum Bereitstellen von Azure-SSIS IR finden Sie unter [Bereitstellen von SSIS in ADF](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

## <a name="configure-the-power-query-source"></a>Konfigurieren der Power Query-Quelle

Um den **Power Query-Quellen-Editor** in SSDT zu öffnen, ziehen Sie die **Power Query-Quelle** aus der SSIS-Toolbox, legen sie im Datenfluss-Designer ab, und doppelklicken darauf.  

![PQ-Quelle](media/power-query-source/pq-source.png)

Auf der linken Seite werden drei Registerkarten angezeigt. Auf der Registerkarte **Abfragen** können Sie Ihren Abfragemodus aus dem Dropdownmenü auswählen.
-   Im Modus **Einzelne Abfrage** können Sie ein einzelnes Power Query-Skript aus Excel/Power BI Desktop kopieren und dann einfügen.
-   Im Modus **Einzelne Abfrage aus Variable** können Sie eine Zeichenfolgenvariable angeben, die Ihre auszuführende Abfrage enthält.

![„Einzeln“ auf der PQ-Quellen-Registerkarte „Abfragen“](media/power-query-source/pq-source-queries-tab-single.png)

Auf der Registerkarte **Verbindungs-Manager** können Sie Power Query-Verbindungs-Manager hinzufügen oder entfernen, die Anmeldeinformationen für den Datenquellenzugriff enthalten. Wenn Sie die Schaltfläche **Datenquelle erkennen** auswählen, wird die in Ihrer Abfrage referenzierte Quelle identifiziert für Sie aufgelistet, damit Sie die geeigneten, vorhandenen Power Query Verbindungs-Manager zuweisen oder neue erstellen können.

![„Erkennen“ auf der PQ-Quellen-Registerkarte „Verbindungs-Manager“](media/power-query-source/pq-source-connection-managers-tab-detect.png)

![„Hinzufügen“ auf der PQ-Quellen-Registerkarte „Verbindungs-Manager“](media/power-query-source/pq-source-connection-managers-tab-add.png)

Schließlich können Sie auf der Registerkarte **Spalten** die Ausgabespalteninformationen bearbeiten.

![PQ-Quellen-Registerkarte „Spalten“](media/power-query-source/pq-source-columns-tab.png)

## <a name="configure-the-power-query-connection-manager"></a>Konfigurieren des Power Query-Verbindungs-Managers

Wenn Sie Ihren Datenfluss mit Power Query-Quelle in SSDT entwerfen, können Sie einen neuen Power Query-Verbindungs-Manager auf folgende Arten erstellen:
- Indirektes Erstellen auf der Registerkarte **Verbindungs-Manager** von Power Query-Quelle, nachdem Sie die Schaltfläche **Hinzufügen**/**Datenquelle erkennen** ausgewählt haben und dann im Dropdownmenü wie oben beschrieben **<New connection...>** auswählen.
- Direktes Erstellen, indem Sie mit der rechten Maustaste auf den Bereich **Verbindungs-Manager** Ihres Pakets klicken und im Dropdownmenü **Neue Verbindung...**  auswählen.

![„Hinzufügen“ im PQ-Quellen-Bereich „Verbindungs-Manager“](media/power-query-source/pq-source-connection-managers-panel-add.png)

Doppelklicken Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** in der Liste mit Verbindungs-Manager-Typen auf **PowerQuery**.

![Dialogfeld „Hinzufügen“ im PQ-Quellen-Bereich „Verbindungs-Manager“](media/power-query-source/pq-source-connection-managers-panel-add-dialog.png)

Im **Power Query-Verbindungs-Manager-Editor** müssen Sie **Datenquellenart**, **Datenquellenpfad** und **Authentifizierungsart** angeben sowie die entsprechenden Anmeldeinformationen zuweisen. Als **Datenquellenart** können Sie zurzeit eine von 22 Arten aus dem Dropdownmenü auswählen.

![„Art“ im PQ-Quellen-Verbindungs-Manager-Editor](media/power-query-source/pq-source-connection-manager-editor-kind.png)

Einige dieser Quellen (**Oracle**, **DB2**, **MySQL**, **PostgreSQL**, **Teradata**, **Sybase**) erfordern zusätzliche Installationen von ADO.NET-Treibern, die Sie über den Artikel [Power Query-Voraussetzungen](https://support.office.com/article/data-source-prerequisites-power-query-6062cf52-c764-45d0-a1c6-fbf8fc05b05a) abrufen können. Sie können die Schnittstelle für benutzerdefinierte Installationen verwenden, um sie in Ihrer Azure-SSIS IR zu installieren. Siehe hierzu den Artikel [Anpassen von Azure-SSIS IR](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup).

Als **Datenquellenpfad** können Sie datenquellenspezifische Eigenschaften eingeben, die eine Verbindungszeichenfolge ohne die Authentifizierungsinformationen ergeben. Beispielsweise wird der den Pfad für die **SQL**-Datenquelle als `<Server>;<Database>` gebildet. Sie können die Schaltfläche **Bearbeiten** auswählen, um datenquellenspezifischen Eigenschaften Werte zuzuweisen, die den Pfad bilden.

![„Pfad“ im PQ-Quellen-Verbindungs-Manager-Editor](media/power-query-source/pq-source-connection-manager-editor-path.png)

Schließlich können Sie als **Authentifizierungsart** **Anonym**/**Windows-Authentifizierung**/**Benutzername Kennwort**/**Schlüssel** aus dem Dropdownmenü auswählen, die entsprechenden Anmeldeinformationen eingeben und die Schaltfläche **Testverbindung** auswählen, um sicherzustellen, dass die Power Query Quelle ordnungsgemäß konfiguriert wurde.

![„Authentifizierung“ im PQ-Quellen-Verbindungs-Manager-Editor](media/power-query-source/pq-source-connection-manager-editor-authentication.png)

### <a name="current-limitations"></a>Aktuelle Einschränkungen

-   Die Datenquelle **Oracle** kann zurzeit nicht verwendet werden, da der Oracle ADO.NET-Treiber nicht in der Azure-SSIS IR installiert werden. Installieren Sie daher stattdessen den Oracle ODBC-Treiber, und verwenden Sie vorerst die **ODBC**-Datenquelle, um eine Verbindung mit Oracle herzustellen. Weitere Informationen finden Sie im **ORACLE STANDARD ODBC**-Beispiel in dem Artikel [Anpassen von Azure-SSIS IR](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup).

-   Die Datenquelle **Web** kann zurzeit nicht mit einem benutzerdefinierten Setup in der Azure-SSIS IR verwendet werden, verwenden Sie diese daher vorerst ohne benutzerdefiniertes Setup in der Azure-SSIS IR.

## <a name="next-steps"></a>Nächste Schritte
Erfahren Sie, wie Sie SSIS-Pakete in der Azure-SSIS IR als Aktivitäten erster Klasse in ADF-Pipelines ausführen. Siehe hierzu im Artikel [Ausführen der SSIS-Paket-Aktivitätslaufzeit](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).
