---
title: Bewertung der Bereitschaft einer Migration zu Azure SQL-Datenbank SQL Server-Datenbestand | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit Data Migration Assistant zum Migrieren von einer SQL Server-Datenbestand für die Migration zu Azure SQL-Datenbank
ms.custom: ''
ms.date: 07/16/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: jroth
ms.openlocfilehash: d317fb3f0c2227744318eeaead71514095afbdec
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269382"
---
# <a name="assess-the-readiness-of-a-sql-server-data-estate-migrating-to-azure-sql-database-using-the-data-migration-assistant"></a>Bewertung der Bereitschaft einer SQL Server-Datenbestand Migrieren zu Azure SQL-Datenbank, die über den Data Migration Assistant

Migrieren von Hunderten von SQL Server-Instanzen und Tausende von Datenbanken in Azure SQL-Datenbank, unsere Platform-as-a-Service (PaaS)-Angebots ist eine erhebliche Aufgabe. Um den Prozess so weit wie möglich zu vereinfachen, müssen Sie darauf vertrauen zu Ihrer relativen Eignung für die Migration. Identifizieren von Eintauchen, einschließlich der Server und Datenbanken, vollständig bereit ist oder auf die Migration vorbereiten mit minimalem Aufwand erfordern, vereinfacht und beschleunigt Ihre bemühungen.

Dieser Artikel enthält schrittweise Anweisungen für die Nutzung der [Data Migration Assistant](https://docs.microsoft.com/sql/dma/dma-overview?view=sql-server-2017) Zusammenfassung der Bereitschaftsergebnisse und diese auf Entwurfsoberfläche die [Azure Migrate](https://portal.azure.com/?feature.customPortal=false#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview) Hub.

## <a name="create-a-project-and-add-a-tool"></a>Erstellen Sie ein Projekt, und fügen Sie ein Tool hinzu.

Richten Sie ein neues Azure Migrate-Projekt in ein Azure-Abonnement, und fügen Sie dann ein Tool hinzu.

Ein Azure Migrate-Projekt dient zum Speichern der Erkundung, Bewertung und Migration von erfassten Metadaten der Umgebung, die Sie bewerten oder migrieren. Sie verwenden auch ein Projekt, um ermittelte Objekte nachzuverfolgen und um die Bewertung und Migration zu orchestrieren.

1. Melden Sie sich beim Azure-Portal, wählen **alle Dienste**, und suchen Sie nach Azure migrieren.
2. Klicken Sie unter **Services**Option **Azure Migrate**.

   ![Azure Migrate - Diensts](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-services.png)

3. Auf der **Übersicht** Seite **bewerten und Migrieren von Datenbanken**.

   ![Azure Migrate - Bewertung der initiieren](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-hub-assess.png)

4. In **Datenbanken**unter **Einstieg**Option **fügen Tools**.

   ![Azure Migrate - Tools hinzufügen](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-add-tools.png)

5. Auf der **Migrate-Projekt** wählen Ihr Azure-Abonnement und die Ressourcengruppe aus (sofern noch nicht vorhanden ist eine Ressourcengruppe erstellen).
6. Klicken Sie unter **Projektdetails**, geben Sie den Namen des Projekts und des geografischen Gebiets, in dem das Projekt erstellt werden sollen.

    ![Azure Migrate - Hinzufügen einer Tool (Dialogfeld)](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-add-tool-dialog.png)

    Sie können ein Azure Migrate-Projekt in allen diesen Gebieten erstellen.

    | **Geography**  | **Speicherort der Speicherregion** |
    | ------------- | ------------- |
    | Asien | Asien, Südosten "oder" Asien, Osten |
    | Europe | "Europa, Süden" oder "Europa, Westen" |
    | Vereinigtes Königreich | UK Süden und Vereinigtes Königreich, Westen |
    | United States | USA, Mitte oder USA, Westen 2 |

    Die Geografie, die für das Projekt angegebene wird nur verwendet, um die von einem lokalen virtuellen Computern erfassten Metadaten zu speichern. Sie können jeder Zielregion für die eigentliche Migration auswählen.

7. Wählen Sie **Weiter**, und fügen Sie eine Assessment-Tool hinzu.

   > [!NOTE]
   > Wenn Sie ein Projekt erstellen, müssen Sie mindestens eine Bewertung oder Migration Tool hinzufügen.

8. Auf der **wählen Assessment-Tool** Registerkarte **Azure zu migrieren: Die Bewertung Datenbank** wird als das Assessment-Tool hinzufügen. Wenn Sie eine Assessment-Tool derzeit nicht benötigen, wählen Sie die **Hinzufügen einer Assessment-Tool vorerst überspringen** Kontrollkästchen. Wählen Sie **Weiter**aus.

    ![Azure Migrate - Option Assessment-Tool-Registerkarte](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-select-assessment-tool.png)

9. Auf der **wählen Migrationstool** Registerkarte **Azure zu migrieren: Datenbankmigration** als Migrationstool hinzufügen wird angezeigt. Wenn Sie ein Migrationstool zurzeit nicht benötigen, wählen Sie die **hinzufügen ein Migrationstool vorerst überspringen**. Wählen Sie **Weiter**aus.

    ![Azure Migrate - Option Migration Tool-Registerkarte](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-select-migration-tool.png)

10. In **überprüfen und Hinzufügen der Tools**, überprüfen Sie die Einstellungen, und die SELECT-Anweisung **Tools hinzufügen**.

    ![Azure Migrate - überprüfen Sie, und fügen Sie die Registerkarte "Tools"](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-review-tools.png)

    Nach dem Erstellen des Projekts können Sie zusätzliche Tools für die Bewertung und Migration von Servern und arbeitsauslastungen, Datenbanken und -Web-apps auswählen.

## <a name="assess-and-upload-assessment-results"></a>Bewerten und Hochladen der Ergebnisse

Nachdem Sie ein Migrationsprojekt wurde erfolgreich unter erstellt **Bewertungstools**in die **Azure zu migrieren: Die Bewertung Datenbank** Feld Anweisungen zum Herunterladen und verwenden den Data Migration Assistant-Tool anzeigen.

   ![Azure Migrate - Bewertungstool hinzugefügt](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-assessment-tool-added.png)

1. Herunterladen Sie Data Migration Assistant über den angegebenen Link und installieren Sie es auf einem Computer mit Zugriff auf Ihre SQL Server-Quellinstanzen.
2. Starten Sie Data Migration Assistant.

### <a name="create-an-assessment"></a>Erstellen einer Bewertung

1. Wählen Sie auf der linken Seite die **+** Symbol, und wählen Sie die Bewertung **Projekttyp**
2. Geben Sie den Namen des Projekts, und wählen Sie dann auf dem Quell- und Zieltypen-Server.

    Wenn Sie Ihre lokalen SQL Server-Instanz auf eine neuere Version von SQL Server oder auf einer Azure-VM gehostete SQL Server aktualisieren, auf den Quell- und Ziel-Server-Datentyp festgelegt **SQL Server**. Der Typ des Zielservers festlegen, um **Azure verwaltete SQL-Datenbankinstanz** für bereitschaftstest für eine Azure SQL-Datenbank (PaaS)-Ziel.

3. Wählen Sie **Erstellen** aus.

   ![Azure Migrate - Data Migration Assistant-Schnittstelle](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-interface.png)

### <a name="choose-assessment-options"></a>Wählen Sie Bewertungsoptionen für die

1. Wählen Sie den Bericht.

    Sie können eine oder beide der folgenden Berichtstypen:
    * Überprüfen Sie die Datenbankkompatibilität
    * Featureparität überprüfen

   ![Optionsbildschirm von Azure Migrate - Data Migration Assistant - Bewertung](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-options-screen.png)

2. Wählen Sie **Weiter**aus.

### <a name="add-databases-to-assess"></a>Hinzufügen von Datenbanken, um zu bewerten

1. Wählen Sie **Quellen hinzufügen** um im Handumdrehen Verbindung sich im Menü zu öffnen.
2. Geben Sie den SQL Server-Instanznamen, wählen Sie den Authentifizierungstyp, legen Sie die Eigenschaften für die richtige Verbindung und wählen Sie dann **Connect**.
3. Wählen Sie die Datenbanken zu bewerten, und wählen Sie dann **hinzufügen**.

   > [!NOTE]
   > Sie können mehrere Datenbanken entfernen, indem Sie Sie sie auswählen, während die UMSCHALTTASTE oder STRG-Taste gedrückt halten, und klicken Sie dann auf Datenquellen zu entfernen. Sie können auch Datenbanken von mehreren SQL Server-Instanzen hinzufügen, indem Sie mithilfe der Schaltfläche zum Hinzufügen von Datenquellen verwenden.

4. Wählen Sie **Weiter** auf die Bewertung zu starten.

   ![Azure Migrate - Data Migration Assistant - Option Quellen Bildschirm](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-select-sources-screen.png)

5. Wählen Sie nach Abschluss die Bewertung **Hochladen in Azure Migrate**.

   ![Azure Migrate - Data Migration Assistant - Kritikenbildschirm Ergebnisse](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-review-results-screen.png)

6. Melden Sie sich beim Azure-Portal an.

   ![Azure Migrate - Data Migration Assistant - Kritikenbildschirm Ergebnisse](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-portal-signin.png)

7. Wählen Sie aus dem Abonnement und Azure Migrate-Projekt in die die Bewertungsergebnisse hochladen, und wählen Sie dann **hochladen**.

   Für die Bewertung der Upload-Bestätigung warten.

## <a name="view-target-readiness-assessment-results"></a>Ziel Readiness Assessment-Ergebnisse anzeigen

1. Melden Sie sich im Azure-Portal, Suche nach Azure migrieren möchten, und die SELECT-Anweisung **Azure Migrate**.

   ![Azure Migrate - Azure-Portal – Dienst suchen](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-portal-search.png)

2. Wählen Sie **bewerten und Migrieren von Datenbanken** , um die Bewertungsergebnisse zu erhalten.

   ![Azure Migrate - Bewertung von Überprüfungsergebnissen](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-hub-assess.png)

    Sie können die Zusammenfassung der SQL Server-Bereitschaft anzeigen, stellen Sie sicher, dass Sie in der richtigen Migrationsprojekt, andernfalls verwenden Option zum Auswählen einer anderen Migration-Projekts ändern.

    Jedes Mal, die Sie aktualisieren die Bewertungsergebnisse zu Azure migrieren, Project, Azure migrieren Hub konsolidiert alle Ergebnisse, und geben Sie den Zusammenfassungsbericht.  Sie können mehrere Data Migration Assistant Bewertungen parallel ausgeführt und Hochladen der Ergebnisse in die einmalige Migration-Projekts, um die der konsolidierten bereitschaftsbericht abzurufen.

   ![Azure Migrate - Bereitschaft von Überprüfungsergebnissen](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-review-readiness.png)

    **Datenbankinstanzen bewertet**:  Die Anzahl der SQL Server-Instanzen, die bisher bewertet.
    **Datenbanken bewertet**: Gesamtzahl der Datenbanken, die über eine oder mehrere SQL Server-Instanzen, die bewertet bewertet **Datenbanken, die für SQL-Datenbank können**:  Anzahl der Datenbanken, die zum Migrieren zu Azure SQL-Datenbank (PaaS) bereit.
    **Datenbanken, die für Azure SQL-VM können**:  Anzahl von Datenbanken bestehen ein oder mehrere migrationsblocker in Azure SQL-Datenbank (PaaS), aber für die Migration zu Azure SQL Server-VMs bereit.

3. Wählen Sie **bewertet Datenbankinstanzen** , um SQL Server-Instanz auf Ansicht zu erhalten.

   ![Azure Migrate - Instanz-Bereitschaft überprüfen](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-assessed-instances.png)

    Sie finden den Bereitschaftsstatus der Prozentsatz jeder SQL Server-Instanz, die Migration zu Azure SQL-Datenbank (PaaS).

4. Wählen Sie eine bestimmte Instanz, um die Datenbankansicht Bereitschaft zu erhalten.

   ![Azure Migrate - Datenbank-Bereitschaft überprüfen](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-assessed-databases.png)

    Sie können die Anzahl der migrationshindernisse pro Datenbank, die empfohlene Ziel pro Datenbank in der obigen Sicht sehen.

5. Überprüfen Sie die Bewertungsergebnisse DMA, um weitere Informationen zur migrationsblockierungen zu erhalten.

   ![Azure Migrate - Überprüfung migrationsblockierungen](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-migration-blockers.png)

## <a name="see-also"></a>Siehe auch

* [Data Migration Assistant (DMA)](../dma/dma-overview.md)
* [Data Migration Assistant: Konfigurationseinstellungen](../dma/dma-configurationsettings.md)
* [Data Migration Assistant: Bewährte Methoden](../dma/dma-bestpractices.md)
