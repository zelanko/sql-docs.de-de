---
title: Durchführen einer SQL Server-Migrationsbewertung
titleSuffix: Data Migration Assistant
description: Erfahren Sie, wie Sie den Datenmigrations-Assistenten verwenden, um einen lokalen SQL Server zu bewerten, bevor Sie zu einem anderen SQL Server oder zu Azure SQL-Datenbank migrieren.
ms.date: 01/15/2020
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
ms.custom: seo-lt-2019
ms.openlocfilehash: 59dc8c96ebda5ac66fb6701d480cb6d633e83158
ms.sourcegitcommit: 48e259549f65f0433031ed6087dbd5d9c0a51398
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2020
ms.locfileid: "80809750"
---
# <a name="perform-a-sql-server-migration-assessment-with-data-migration-assistant"></a>Durchführen einer SQL Server-Migrationsbewertung mit dem Datenmigrations-Assistenten

Mit den folgenden Schritt-für-Schritt-Anleitungen können Sie Ihre erste Bewertung für die Migration zu lokalen SQL Server, SQL Server, die auf einer Azure-VM ausgeführt wird, oder Azure SQL-Datenbank mithilfe des Datenmigrations-Assistenten durchführen.

   > [!NOTE]
   > Data Migration Assistant v5.0 bietet Unterstützung für die Analyse von Datenbankkonnektivität und eingebetteten SQL-Abfragen im Anwendungscode. Weitere Informationen finden Sie im Blogbeitrag Verwenden des [Datenmigrations-Assistenten zum Bewerten der Datenzugriffsschicht einer Anwendung](https://techcommunity.microsoft.com/t5/Microsoft-Data-Migration/Using-Data-Migration-Assistant-to-assess-an-application-s-data/ba-p/990430).

## <a name="create-an-assessment"></a>Erstellen einer Bewertung

1. Wählen Sie das Symbol **Neu** (+) aus, und wählen Sie dann den **Projekttyp Bewertung** aus.

2. Legen Sie den Typ von Quell- und Zielserver fest.

    Wenn Sie Ihre lokale SQL Server-Instanz auf eine moderne lokale SQL Server-Instanz oder auf SQL Server aktualisieren, die auf einer Azure-VM gehostet wird, legen Sie den Quell- und Zielservertyp auf **SQL Server**fest. Wenn Sie zu Azure SQL-Datenbank migrieren, legen Sie stattdessen den Zielservertyp auf **Azure SQL-Datenbank**fest.

3. Klicken Sie auf **Erstellen**.

   ![Erstellen einer Bewertung](../dma/media/dma-assesssqlonprem/new-assessment.png)

## <a name="choose-assessment-options"></a>Auswahl von Bewertungsoptionen

1. Wählen Sie die SQL Server-Zielversion aus, in die Sie migrieren möchten.

2. Wählen Sie den Berichtstyp aus.

   Wenn Sie Ihre SQL Server-Quellinstanz für die Migration zu lokalen SQL Server oder zu SQL Server bewerten, die auf Azure VM-Zielen gehostet wird, können Sie einen oder beide der folgenden Bewertungsberichtstypen auswählen:

    - **Kompatibilitätsprobleme**
    - **Empfehlung neuer Funktionen**

   ![Auswählen eines Bewertungsberichtstyps für das SQL Server-Ziel](../dma/media/dma-assesssqlonprem/assessment-types.png)

   Bei der Bewertung der SQL Server-Quellinstanz für die Migration zu Azure SQL-Datenbank können Sie einen oder beide der folgenden Bewertungsberichtstypen auswählen:

    - **Check database compatibility (Datenbankkompatibilität prüfen)**
    - **Check feature parity (Featureparität prüfen)**

    ![Bewertungsberichtstyp für SQL-Datenbankziel auswählen](../dma/media/dma-assesssqlonprem/assessment-types-azure.png)

## <a name="add-databases-and-extended-events-trace-to-assess"></a>Hinzufügen von Datenbanken und erweiterte Ereignisablaufverfolgung zur Bewertung

1. Wählen Sie **Quellen hinzufügen** aus, um das Verbindungsflyout-Menü zu öffnen.

2. Geben Sie den Namen der SQL-Serverinstanz ein, wählen Sie den Authentifizierungstyp aus, legen Sie die richtigen Verbindungseigenschaften fest, und wählen Sie dann **Verbinden**aus.

3. Wählen Sie die zu bewertenden Datenbanken aus, und wählen Sie dann **Hinzufügen**aus.

    > [!NOTE]
    > Sie können mehrere Datenbanken entfernen, indem Sie sie auswählen, während Sie die Umschalt- oder Strg-Taste gedrückt halten, und dann auf **Quellen entfernen**klicken. Sie können auch Datenbanken von mehreren SQL Server-Instanzen hinzufügen, indem Sie **Quellen hinzufügen**auswählen.

4. Wenn Sie Ad-hoc- oder dynamische SQL-Abfragen oder DML-Anweisungen haben, die über die Anwendungsdatenschicht initiiert wurden, geben Sie den Pfad zu dem Ordner ein, in dem Sie alle Sitzungsdateien für erweiterte Ereignisse abgelegt haben, die Sie gesammelt haben, um die Arbeitslast auf dem SQL Server-Quellserver zu erfassen.

     Das folgende Beispiel zeigt, wie Sie eine erweiterte Ereignissitzung auf Ihrem Sql Server-Quell-SQL Server erstellen, um die Workload auf Anwendungsdatenebene zu erfassen.  Erfassen Sie die Arbeitsauslastung für die Dauer, die Ihre Spitzenarbeitslast darstellt.

    ```
    DROP EVENT SESSION [DatalayerSession] ON SERVER
    go
    CREATE EVENT SESSION [DatalayerSession] ON SERVER  
    ADD EVENT sqlserver.sql_batch_completed( 
        ACTION (sqlserver.sql_text,sqlserver.client_app_name,sqlserver.client_hostname,sqlserver.database_id))
    ADD TARGET package0.asynchronous_file_target(SET filename=N'C:\temp\Demos\DataLayerAppassess\DatalayerSession.xel')  
    WITH (MAX_MEMORY=2048 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=3 SECONDS,MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=OFF)
    go
    ---Start the session
    ALTER EVENT SESSION [DatalayerSession]
          ON SERVER
        STATE = START;
    ---Wait for few minutes
    
    ---Query events
        
        SELECT 
        object_name,
        CAST(event_data as xml) as event_data,
        file_name, 
        file_offset
    FROM sys.fn_xe_file_target_read_file('C:\temp\Demos\DataLayerAppassess\DatalayerSession*xel', 
                'C:\\temp\\Demos\\DataLayerAppassess\\DatalayerSession*xem', 
                null,
                null)
    ---Stop the session after capturing the peak load.
    ALTER EVENT SESSION [DatalayerSession]
          ON SERVER
        STATE = STOP;
        
        go
    ```

5. Klicken Sie auf **Weiter**, um die Bewertung zu starten.

    ![Quellen hinzufügen und Bewertung starten](../dma/media/dma-assesssqlonprem/select-database1.png)

> [!NOTE]
> Sie können mehrere Bewertungen gleichzeitig durchführen und den Status der Bewertungen anzeigen, indem Sie die Seite **Alle Bewertungen** öffnen.

## <a name="view-results"></a>Anzeigen der Ergebnisse

Die Dauer der Bewertung hängt von der Anzahl der hinzugefügten Datenbanken und der Schemagröße jeder Datenbank ab. Die Ergebnisse werden für jede Datenbank angezeigt, sobald sie verfügbar sind.

1. Wählen Sie die Datenbank aus, die die Bewertung abgeschlossen hat, und wechseln Sie dann mithilfe des Switchers zwischen **Kompatibilitätsproblemen** und **Feature-Empfehlungen.**

2. Überprüfen Sie die Kompatibilitätsprobleme auf allen Kompatibilitätsstufen, die von der SQL Server-Zielversion unterstützt werden, die Sie auf der Seite **Optionen** ausgewählt haben.

Sie können Kompatibilitätsprobleme überprüfen, indem Sie das betroffene Objekt, seine Details und möglicherweise eine Lösung für jedes Problem analysieren, das unter **Änderungen,** **Verhaltensänderungen**und **veraltete Features**identifiziert wurde.

![Bewertungsergebnisse anzeigen](../dma/media/dma-assesssqlonprem/review-results.png)

Ebenso können Sie die Feature-Empfehlung in den Bereichen **Performance**, **Storage**und **Security** überprüfen.

Feature-Empfehlungen decken verschiedene Arten von Funktionen ab, z. B. In-Memory-OLTP, Columnstore, Stretch-Datenbank, Always Encrypted, Dynamic Data Masking und Transparent Data Encryption.

![Feature-Empfehlungen anzeigen](../dma/media/dma-assesssqlonprem/feature-recommendations.png)

Für Azure SQL-Datenbank stellen die Bewertungen Probleme mit der Migrationsblockierung und Feature-Paritätsprobleme bereit.Überprüfen Sie die Ergebnisse für beide Kategorien, indem Sie die spezifischen Optionen auswählen.

- Die **SQL Server-Featureparitätskategorie** bietet eine umfassende Reihe von Empfehlungen, alternativen Ansätzen, die in Azure verfügbar sind, und mildernden Schritten. Es hilft Ihnen, diese Bemühungen in Ihren Migrationsprojekten zu planen.

  ![Anzeigen von Informationen für SQL Server-Featureparität](../dma/media/dma-assesssqlonprem/sql-feature-parity.png)

- Die Kategorie **Kompatibilitätsprobleme** bietet teilweise unterstützte oder nicht unterstützte Features, die die Migration lokaler SQL Server-Datenbanken zu Azure SQL-Datenbanken blockieren.Anschließend werden Empfehlungen zur Lösung dieser Probleme angezeigt.

  ![Anzeigen von Kompatibilitätsproblemen](../dma/media/dma-assesssqlonprem/compatibility-issues.png)

## <a name="assess-a-data-estate-for-target-readiness"></a>Bewerten eines Datennachlasses für die Zielbereitschaft

Wenn Sie diese Bewertungen weiter auf den gesamten Datenstand erweitern und die relative Bereitschaft von SQL Server-Instanzen und -Datenbanken für die Migration in Azure SQL-Datenbank ermitteln möchten, laden Sie die Ergebnisse in den Azure Migrate-Hub hoch, indem Sie **Upload to Azure Migrate**auswählen.

Auf diese Weise können Sie die konsolidierten Ergebnisse im Azure Migrate Hub-Projekt anzeigen.

Detaillierte, schrittweise Anleitungen für Zielbereitschaftsbewertungen finden Sie [hier](https://docs.microsoft.com/sql/dma/dma-assess-sql-data-estate-to-sqldb?view=sql-server-2017).

   ![Hochladen von Ergebnissen in Azure Migrate](../dma/media/dma-assesssqlonprem/upload-to-azure-migrate.png)

## <a name="export-results"></a>Exportieren von Ergebnissen

Nachdem alle Datenbanken die Bewertung abgeschlossen haben, wählen Sie **Bericht exportieren** aus, um die Ergebnisse in eine JSON-Datei oder eine CSV-Datei zu exportieren. Sie können die Daten dann nach Belieben analysieren.

## <a name="save-and-load-assessments"></a>Speichern und Laden von Bewertungen

Zusätzlich zum Exportieren der Ergebnisse einer Bewertung können Sie Bewertungsdetails in eine Datei speichern und eine Bewertungsdatei zur späteren Überprüfung laden.  Weitere Informationen finden Sie im Artikel [Speichern und Laden von Bewertungen mit dem Datenmigrationsassistenten](../dma/dma-save-load-assessments.md).
