---
title: Aktualisieren Sie SQL Server mithilfe des Datenmigrations-Assistent
description: Erfahren Sie, wie Sie Datenmigrations-Assistent zum Aktualisieren eines lokalen SQL Server auf eine spätere Version von SQL Server oder zum SQL Server auf Azure-VMS verwenden.
ms.custom: seo-lt-2019
ms.date: 05/18/2019
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
ms.author: jtoland
ms.openlocfilehash: fc78354e3b422342e376bd7ebe75233dcd3ffaee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74056531"
---
# <a name="upgrade-sql-server-using-the-data-migration-assistant"></a>Aktualisieren Sie SQL Server mithilfe des Datenmigrations-Assistent

Der Datenmigrations-Assistent ermöglicht eine nahtlose Bewertung SQL Server lokalen Updates und Upgrades auf spätere Versionen von SQL Server oder migraSQL Server tionen auf Azure-VMS oder Azure SQL-Datenbank.

Dieser Artikel enthält Schritt-für-Schritt-Anleitungen für das Upgrade von SQL Server lokal auf spätere Versionen SQL Server oder zum SQL Server auf Azure-VMS mithilfe der Datenmigrations-Assistent.

## <a name="create-a-new-migration-project"></a>Erstellen eines neuen Migrationsprojekts

1. Klicken Sie im linken Bereich auf **neu** (+) und dann auf den Projekttyp **Migration** .

2. Legen Sie den Quell-und den Ziel Servertyp auf **SQL Server** fest, wenn Sie ein lokales SQL Server auf eine spätere Version des lokalen SQL Server aktualisieren.

3. Klicken Sie auf **Erstellen**.

   ![Migrationsprojekt erstellen](../dma/media/NewCreate.png)

## <a name="specify-the-source-and-target"></a>Quelle und Ziel angeben

1. Geben Sie für die Quelle im Abschnitt **Quell Server Details** den SQL Server Instanznamen in das Feld **Server Name** ein. 

2. Wählen Sie den **Authentifizierungstyp** aus, der von der SQL Server-Quellinstanz unterstützt wird.

3. Geben Sie im Abschnitt **Zielserver Details** den SQL Server Instanznamen in das Feld **Server Name** ein. 

4. Wählen Sie den **Authentifizierungstyp** aus, der vom Ziel SQL Server Instanz unterstützt

5. Es wird empfohlen, dass Sie die Verbindung verschlüsseln, indem Sie im Abschnitt " **Verbindungs Eigenschaften** " die Option **Verbindung verschlüsseln** auswählen.

6. Klicken Sie auf **Weiter**.

   ![Quell-und Zielseite angeben](../dma/media/SourceTarget.png)

## <a name="add-databases"></a>Datenbanken hinzufügen

1. Wählen Sie die gewünschten Datenbanken aus, die Sie migrieren möchten, indem Sie im linken Bereich der Seite **Datenbanken hinzufügen** nur diese Datenbanken auswählen.

   Standardmäßig werden alle Benutzer Datenbanken auf der Quell SQL Server Instanz für die Migration ausgewählt.

2. Verwenden Sie die Migrations Einstellungen auf der rechten Seite der Seite, um die Migrations Optionen festzulegen, die auf die-Datenbanken angewendet werden. gehen Sie hierzu wie folgt vor:

   > [!NOTE]
   > Sie können die Migrations Einstellungen auf alle zu migrierenden Datenbanken anwenden, indem Sie den Server im linken Bereich auswählen. Sie können auch eine einzelne Datenbank mit bestimmten Einstellungen konfigurieren, indem Sie die Datenbank im linken Bereich auswählen.

    a. Geben Sie den frei **gegebenen Speicherort an, der für Quell-und Ziel-SQL Server für den Sicherungs Vorgang** Stellen Sie sicher, dass das Dienst Konto, das die Quell SQL Server Instanz ausführen, über Schreibberechtigungen für den freigegebenen Speicherort verfügt und das Ziel Dienst Konto über Leseberechtigungen für den freigegebenen Speicherort verfügt

    b. Geben Sie den Speicherort zum Wiederherstellen der Daten-und Transaktionsprotokoll Dateien auf dem Zielserver an.

    ![Seite Datenbanken hinzufügen](../dma/media/AddDatabases.png)

3. Geben Sie im Feld **Optionen für Freigabe Speicherort** einen freigegebenen Speicherort ein, auf den die Quell-und Ziel SQL Server Instanzen zugreifen können.

4. Wenn Sie keinen freigegebenen Speicherort bereitstellen können, auf den der Quell-und der Ziel-SQL-Server Zugriff haben, wählen Sie **Datenbanksicherungen an einen anderen Speicherort kopieren aus, von dem der Zielserver lesen und wiederherstellen kann**. Geben Sie dann einen Wert für das Feld **Speicherort für Sicherungen für die Wiederherstellung** ein. 

   Stellen Sie sicher, dass das Benutzerkonto, das Datenmigrations-Assistent ausgeführt wird, über Leseberechtigungen für den Sicherungs Speicherort und Schreibberechtigungen für den Speicherort verfügt, von dem der Zielserver wieder hergestellt

   ![Option zum Kopieren von Datenbanksicherungen an einen anderen Speicherort](../dma/media/CopyDatabaseDifferentLocation.png)

5. Wählen Sie **Weiter** aus.

Der Datenmigrations-Assistent führt Validierungen für die Sicherungsordner, die Daten und die Protokolldatei Speicherorte aus. Wenn bei der Validierung ein Fehler auftritt, beheben Sie die Optionen, und klicken Sie dann auf **weiter**.

## <a name="select-logins"></a>Auswählen von Benutzernamen

1. Wählen Sie bestimmte Anmeldungen für die Migration aus.

   > [!IMPORTANT]
   > Stellen Sie sicher, dass Sie die Anmeldungen auswählen, die einem oder mehreren Benutzern in den für die Migration ausgewählten Datenbanken zugeordnet sind.   

   Standardmäßig werden alle SQL Server-und Windows-Anmeldungen, die für die Migration qualifiziert sind, für die Migration ausgewählt.

2. Wählen Sie **Migration starten** aus.

   ![Auswählen von Anmeldungen und Starten der Migration](../dma/media/SelectLogins.png)

## <a name="view-results"></a>Anzeigen der Ergebnisse

Sie können den Migrations Fortschritt auf der Seite **Ergebnisse anzeigen** überwachen.

![Ergebnisseite anzeigen](../dma/media/ViewResults.png)

## <a name="export-migration-results"></a>Migrations Ergebnisse exportieren

1. Klicken Sie unten auf der Seite **Ergebnisse anzeigen** auf **Bericht exportieren** , um die Migrations Ergebnisse in einer CSV-Datei zu speichern.

2. Überprüfen Sie die gespeicherte Datei auf Details zur Anmelde Migration, und überprüfen Sie dann die Änderungen.

## <a name="see-also"></a>Weitere Informationen:

- [Datenmigrations-Assistent (DMA)](../dma/dma-overview.md)
- [Datenmigrations-Assistent: Konfigurationseinstellungen](../dma/dma-configurationsettings.md)
- [Datenmigrations-Assistent: bewährte Methoden](../dma/dma-bestpractices.md)
