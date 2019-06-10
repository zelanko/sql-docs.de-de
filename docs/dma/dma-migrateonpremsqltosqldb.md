---
title: Migrieren einer lokalen SQLServer oder SQL Server auf virtuellen Azure-Computern in Azure SQL-Datenbank mit den Data Migration Assistant | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit Data Migration Assistant zum Migrieren von einer lokalen SQL Server zu Azure SQL-Datenbank
ms.custom: ''
ms.date: 03/12/2019
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
ms.openlocfilehash: 592b581ae4981e42bea2f6bf6f9135018917b002
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794355"
---
# <a name="migrate-on-premises-sql-server-or-sql-server-on-azure-vms-to-azure-sql-database-using-the-data-migration-assistant"></a>Migrieren von lokalen SQLServer oder SQL Server auf virtuellen Azure-Computern in Azure SQL-Datenbank, die über den Data Migration Assistant

Im Data Migration Assistant bietet nahtlose Bewertungen von einer lokalen SQL Server und -Upgrades auf höhere Versionen von SQL Server oder Migration zu SQL Server auf virtuellen Azure-Computern oder Azure SQL-Datenbank.

Dieser Artikel enthält schrittweise Anleitungen zum Migrieren von SQL Server auf einer lokalen Umgebung in Azure SQL-Datenbank mit den Data Migration Assistant.   

## <a name="create-a-new-migration-project"></a>Erstellen eines neuen Migrationsprojekts

1. Wählen Sie im linken Bereich **neu** (+), und wählen Sie dann die **Migration** Projekttyp.

2. Legen Sie den Quelltyp **SQL Server** und geben Sie zum Zielserver **Azure SQL-Datenbank**.

3. Wählen Sie **Erstellen**aus.

   ![Migrationsprojekt erstellen](../dma/media/NewCreate1.png)

## <a name="specify-the-source-server-and-database"></a>Geben Sie den Quellserver und der Datenbank

1. Für die Quelle unter **Herstellen einer Verbindung mit Quellserver**in die **Servernamen** Text Geben Sie den Namen der Quelle SQL Server-Instanz.

2. Wählen Sie die **Authentifizierungstyp** von der SQL Server-Quellinstanz unterstützt werden.

   > [!NOTE]
   > Es handelt sich um Recommedned, dass die Verbindung, indem Sie auswählen Verschlüsseln der **Verbindung verschlüsseln** Kontrollkästchen unter **Verbindung Poperties**.

    ![Quellserver auswählen](../dma/media/select-source-server.png)

3. Wählen Sie **Verbinden**.

4. Wählen Sie eine einzelne Quelle-Datenbank zu Azure SQL-Datenbank migrieren.

   > [!NOTE]
   > Wenn Sie möchten, zu bewerten, die Datenbank und zum Anwenden empfohlen Korrekturen vor der Migration, wählen die **bewerten Datenbank vor der Migration?** Kontrollkästchen.

    ![Wählen Sie die Quelldatenbank](../dma/media/select-source-database.png)

5. Wählen Sie **Weiter**aus.

## <a name="specify-the-target-server-and-database"></a>Geben Sie den Zielserver und die Datenbank

1. Für das Ziel unter **Herstellen einer Verbindung mit Zielserver**in die **Servernamen** Text Geben Sie den Namen der Azure SQL-Datenbank-Instanz. 

2. Wählen Sie die **Authentifizierungstyp** unterstützt, die von der Azure SQL-Datenbank-Zielinstanz.

   > [!NOTE]
   > Es handelt sich um Recommedned, dass die Verbindung, indem Sie auswählen Verschlüsseln der **Verbindung verschlüsseln** Kontrollkästchen unter **Verbindung Poperties**.

     ![Wählen Sie Zielserver](../dma/media/select-target-server.png)

3. Wählen Sie **Verbinden**.

4. Wählen Sie eine einzelne Zieldatenbank zu dem migriert werden sollen.

   > [!NOTE]
   > Wenn Sie beabsichtigen, Migrieren von Windows-Benutzer, in der **Ziel externe Domäne Benutzername** Text stellen Sie sicher, dass der externe Benutzername des Domäne Zieldatenbanken richtig angegeben ist.

    ![Wählen Sie die Zieldatenbank](../dma/media/select-target-database.png)

5. Wählen Sie **Weiter**aus.

## <a name="select-schema-objects"></a>Wählen Sie die Schemaobjekte

1.  Wählen Sie die Schemaobjekte aus der Quelldatenbank, die Sie mit Azure SQL-Datenbank migrieren möchten.

    ![Wählen Sie die Schemaobjekte](../dma/media/select-schema-objects.png)

       > [!NOTE]
       > Einige der Objekte, die als nicht konvertiert werden können – wird automatische Korrektur Möglichkeiten angezeigt. Durch Klicken auf diese Objekte auf der linken Seite zeigt die vorgeschlagenen Korrekturen im rechten Bereich. Überprüfen Sie die Korrekturen aus, und wählen Sie entweder anwenden oder ignorieren alle Änderungen, die Objekte. Beachten Sie, dass anwenden oder ignorieren alle Änderungen für ein Objekt nicht über Änderungen an andere Datenbankobjekte auswirkt. Anweisungen, die nicht konvertiert oder automatisch behoben sind in die Zieldatenbank reproduziert und kommentiert.

    ![Vorgeschlagene Korrektur](../dma/media/suggested-fix.png)

2. Wählen Sie **allgemeine SQL-Skript**.
 
3. Überprüfen Sie das generierte Skript aus.

    ![Generiertes Skript](../dma/media/generated-script.png)

## <a name="deploy-schema"></a>Schema bereitstellen

1. Wählen Sie **Schema bereitstellen**.

2. Überprüfen Sie die Ergebnisse der schemabereitstellung aus.
 
    ![Die Ergebnisse der Schema-Bereitstellung](../dma/media/schema-deployment-results.png)

3. Wählen Sie **Datenmigration** um den Datenmigrationsprozess zu initiieren.
 
4. Wählen Sie die Tabellen mit den Daten, die Sie migrieren möchten.

    ![Wählen Sie zu migrierende Tabellen aus](../dma/media/select-tables-to-migrate.png) 

5. Wählen Sie **Datenmigration starten**.
 
Die letzte Bildschirm zeigt den Gesamtstatus.

   ![Migrationsstatus](../dma/media/migration-status.png) 

## <a name="see-also"></a>Siehe auch

- [Data Migration Assistant (DMA)](../dma/dma-overview.md)
- [Data Migration Assistant: Konfigurationseinstellungen](../dma/dma-configurationsettings.md)
- [Data Migration Assistant: Bewährte Methoden](../dma/dma-bestpractices.md)
