---
title: Migrieren von SQL Server zu Azure SQL-Datenbank mithilfe des Datenmigrations-Assistent
description: Erfahren Sie, wie Sie mit Datenmigrations-Assistent eine lokale SQL Server zu Azure SQL-Datenbank migrieren.
ms.date: 06/29/2020
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
ms.custom: seo-lt-2019
ms.openlocfilehash: ec6b5ad0ab2047e72a1f3e3e5dfcd9fc49b954d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749786"
---
# <a name="migrate-on-premises-sql-server-or-sql-server-on-azure-vms-to-azure-sql-database-using-the-data-migration-assistant"></a>Migrieren von lokalen SQL Server oder SQL Server auf Azure-VMS zu Azure SQL-Datenbank mithilfe des Datenmigrations-Assistent

Der Datenmigrations-Assistent ermöglicht eine nahtlose Bewertung SQL Server lokalen Updates und Upgrades auf spätere Versionen von SQL Server oder migraSQL Server tionen auf Azure-VMS oder Azure SQL-Datenbank.

Dieser Artikel enthält Schritt-für-Schritt-Anleitungen zum Migrieren von SQL Server lokal zu Azure SQL-Datenbank mithilfe des Datenmigrations-Assistent.

## <a name="create-a-new-migration-project"></a>Erstellen eines neuen Migrationsprojekts

1. Klicken Sie im linken Bereich auf **neu** (+), und wählen Sie dann den Projekttyp **Migration** aus.

2. Legen Sie den Quelltyp auf **SQL Server** und den Ziel Servertyp auf **Azure SQL-Datenbank**fest.

3. Klicken Sie auf **Erstellen**.

   ![Migrationsprojekt erstellen](../dma/media/NewCreate1.png)

## <a name="specify-the-source-server-and-database"></a>Angeben des Quellservers und der Datenbank

1. Geben Sie für die Quelle unter **Verbindung mit Quell Server herstellen**im Textfeld **Servername** den Namen der Quell SQL Server-Instanz ein.

2. Wählen Sie den **Authentifizierungstyp** aus, der von der SQL Server-Quellinstanz unterstützt wird.

   > [!NOTE]
   > Es wird empfohlen, die Verbindung zu verschlüsseln, indem Sie unter **Verbindungs-poperties**das Kontrollkästchen **Verbindung verschlüsseln** aktivieren.

    ![Quell Server auswählen](../dma/media/select-source-server.png)

3. Wählen Sie **Verbinden**.

4. Wählen Sie eine einzelne Quelldatenbank aus, um zu Azure SQL-Datenbank zu migrieren.

   > [!NOTE]
   > Wenn Sie die Datenbank bewerten und empfohlene Korrekturen vor der Migration anwenden möchten, aktivieren Sie das Kontrollkästchen **Datenbank vor der Migration bewerten?** .

    ![Quelldatenbank auswählen](../dma/media/select-source-database.png)

5. Wählen Sie **Weiter** aus.

## <a name="specify-the-target-server-and-database"></a>Angeben des Zielservers und der Datenbank

1. Geben Sie für das Ziel unter **Verbindung mit Zielserver herstellen**im Textfeld **Servername** den Namen der Azure SQL-Daten Bank Instanz ein. 

2. Wählen Sie den **Authentifizierungstyp** aus, der von der Azure SQL-Datenbank-Ziel Instanz

   > [!NOTE]
   > Es wird empfohlen, die Verbindung zu verschlüsseln, indem Sie unter **Verbindungs-poperties**das Kontrollkästchen **Verbindung verschlüsseln** aktivieren.

     ![Zielserver auswählen](../dma/media/select-target-server.png)

3. Wählen Sie **Verbinden**.

4. Wählen Sie eine Zieldatenbank aus, zu der migriert werden soll.

   > [!NOTE]
   > Wenn Sie beabsichtigen, Windows-Benutzer zu migrieren, stellen Sie im Textfeld **Ziel externer Benutzer Domänen Name** sicher, dass der Ziel Name der externen Benutzer Domäne ordnungsgemäß angegeben ist.

    ![Zieldatenbank auswählen](../dma/media/select-target-database.png)

5. Wählen Sie **Weiter** aus.

## <a name="select-schema-objects"></a>Auswählen von Schemaobjekten

1. Wählen Sie die Schemaobjekte aus der Quelldatenbank aus, die Sie zu Azure SQL-Datenbank migrieren möchten.

    ![Auswählen von Schemaobjekten](../dma/media/select-schema-objects.png)

    > [!NOTE]
    > Für die Objekte, an denen Änderungen vorgenommen werden müssen, damit sie migriert werden können, gibt es Möglichkeiten zur automatischen Problembehandlung. Wenn Sie im linken Bereich auf diese Objekte klicken, werden die vorgeschlagenen Möglichkeiten zur Fehlerbehebung auf der rechten Seite angezeigt. Prüfen Sie diese, und entscheiden Sie für jedes Objekt, ob Sie alle Änderungen akzeptieren oder ignorieren möchten. Beachten Sie, dass es keine Auswirkungen auf Änderungen anderer Datenbankobjekte hat, wenn Sie alle Änderungen annehmen oder ignorieren. Anweisungen, die nicht konvertiert oder automatisch verbessert werden können, werden in der Zieldatenbank reproduziert und mit einem Kommentar versehen.

    ![Vorgeschlagene Lösung](../dma/media/suggested-fix.png)

2. Wählen Sie **Allgemeines SQL-Skript**aus.

3. Überprüfen Sie das generierte Skript.

    ![Generiertes Skript](../dma/media/generated-script.png)

## <a name="deploy-schema"></a>Bereitstellen des Schemas

1. Wählen Sie **Schema**bereitstellen aus.

2. Sehen Sie sich die Ergebnisse der Schemabereitstellung an.

    ![Ergebnisse der Schema Bereitstellung](../dma/media/schema-deployment-results.png)

3. Wählen Sie **Daten migrieren** aus, um den Daten Migrationsprozess zu initiieren.

4. Wählen Sie die Tabellen mit den Daten aus, die Sie migrieren möchten.

    ![Tabellen für die Migration auswählen](../dma/media/select-tables-to-migrate.png) 

5. Wählen Sie **Datenmigration starten**aus.

Auf dem letzten Bildschirm wird der allgemeine Status angezeigt.

   ![Migrationsstatus](../dma/media/migration-status.png) 

## <a name="see-also"></a>Weitere Informationen

* [Datenmigrations-Assistent (DMA)](../dma/dma-overview.md)
* [Datenmigrations-Assistent: Konfigurationseinstellungen](../dma/dma-configurationsettings.md)
* [Datenmigrations-Assistent: bewährte Methoden](../dma/dma-bestpractices.md)
