---
title: Upgrade auf lokalen SQL Server mit SQL Server oder SQL Server auf Azure-VMs, die über den Data Migration Assistant | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Data Migration Assistant mit einer lokalen SQL Server auf eine neuere Version von SQL Server oder SQL Server auf virtuellen Azure-Computer aktualisieren
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 8a68205fe742f386241ab0653afce5b274077cbd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946954"
---
# <a name="upgrade-on-premises-sql-server-to-sql-server-or-sql-server-on-azure-vms-using-the-data-migration-assistant"></a>Ein Upgrade auf einen lokalen SQL Server auf SQL Server oder SQL Server auf Azure-VMs mit den Data Migration Assistant

Im Data Migration Assistant bietet nahtlose Bewertungen von einer lokalen SQL Server und -Upgrades auf höhere Versionen von SQL Server oder Migration zu SQL Server auf virtuellen Azure-Computern oder Azure SQL-Datenbank.

Dieser Artikel enthält schrittweise Anleitungen zum Aktualisieren von einer lokalen SQL Server auf neuere Version von SQL Server oder SQL Server auf virtuellen Azure-Computern mithilfe von Data Migration Assistant.   

## <a name="create-a-new-migration-project"></a>Erstellen eines neuen Migrationsprojekts

1. Wählen Sie im linken Bereich **neu** (+), und klicken Sie dann die **Migration** Projekttyp.

2. Legen Sie auf den Quelle und Ziel-Servertyp **SQL Server** Wenn Sie einer lokalen SQL Server auf eine neuere Version von einem lokalen SQL Server aktualisieren.

3. Wählen Sie **Erstellen**aus.

   ![Migrationsprojekt erstellen](../dma/media/NewCreate.png)

## <a name="specify-the-source-and-target"></a>Geben Sie den Quell- und Zielservern

1. Für die Quelle, geben Sie den Namen der SQL Server-Instanz in der **Servernamen** -Feld in der **Source Server-Details** Abschnitt. 

2. Wählen Sie die **Authentifizierungstyp** von der SQL Server-Quellinstanz unterstützt werden.

3. Für das Ziel, geben Sie den Namen der SQL Server-Instanz in der **Servernamen** Feld der **Zieldetails Server** Abschnitt. 

4. Wählen Sie die **Authentifizierungstyp** unterstützt, die von der SQL Server-Zielinstanz.

5. Es wird empfohlen, dass Sie die Verbindung dazu verschlüsseln **Verbindung verschlüsseln** in die **Verbindungseigenschaften** Abschnitt.

6. Klicken Sie auf **Weiter**.

   ![Geben Sie die Quelle und Ziel-Seite](../dma/media/SourceTarget.png)

## <a name="add-databases"></a>Hinzufügen von Datenbanken

1. Wählen Sie die bestimmten Datenbanken, die Sie migrieren, indem Sie Ihre Auswahl nur diese Datenbanken, in den linken Bereich des möchten die **Datenbanken** Seite.

   Standardmäßig sind alle Benutzerdatenbanken auf der SQL Server-Quellinstanz für die Migration ausgewählt.

2. Verwenden Sie die migrationseinstellungen auf der rechten Seite der Seite, um die Migrationsoptionen festgelegt, die wie folgt auf die Datenbanken angewendet werden.

   > [!NOTE]
   > Sie können die migrationseinstellungen auf alle Datenbanken, die Sie migrieren, indem Sie den Server im linken Bereich auswählen, anwenden. Sie können auch eine einzelne Datenbank mit bestimmten Einstellungen konfigurieren, indem Sie die Datenbank im linken Bereich auswählen.

    A. Geben Sie die **freigegebene Speicherort zugegriffen werden kann, von Quell- und Ziel-SQL-Server für den Sicherungsvorgang**. Stellen Sie sicher, dass das Dienstkonto, das die Quelle mit SQL Server-Instanz verfügt über Schreibberechtigungen auf dem freigegebenen Speicherort, und das Ziel-Dienstkonto verfügt über für den freigegebenen Speicherort Leserechte.

    B. Geben Sie den Speicherort zum Wiederherstellen der Daten und transaktionale Protokolldateien auf dem Zielserver.

    ![Fügen Sie die Seite "Datenbanken"](../dma/media/AddDatabases.png)

3. Geben Sie einen freigegebenen Speicherort an, dass die Quelle und Ziel-SQL Server-Instanzen können, in zugreifen der **Optionen für Freigabespeicherort** Feld.

4. Wenn einen freigegebenen Speicherort kann nicht haben, den Quell- und Ziel-SQL-Server zugreifen kann, wählen Sie **kopieren Sie die datenbanksicherungen an einen anderen Speicherort, die der Zielserver Lese- und Wiederherstellungsvorgänge kann**. Geben Sie dann einen Wert für die **Speicherort für Sicherungen für Wiederherstellungsoption** Feld. 

   Stellen Sie sicher, dass das Benutzerkonto, das Ausführen von Data Migration Assistant Berechtigungen, um den Speicherort für die Sicherung gelesen hat, und Schreibberechtigungen für den Speicherort, von dem der Zielserver wird wiederhergestellt.

   ![Option zum Kopieren von datenbanksicherungen in anderen Speicherort](../dma/media/CopyDatabaseDifferentLocation.png)

5. Wählen Sie **Weiter**aus.

Im Data Migration Assistant führt Überprüfungen auf den Sicherungsordner, Daten- und Protokolldateien Dateispeicherorte. Wenn keine Überprüfung ein Fehler auftritt, beheben Sie die Optionen, und wählen Sie dann **Weiter**.

## <a name="select-logins"></a>Benutzernamen auswählen

1. Wählen Sie bestimmte Anmeldungen für die Migration.

   > [!IMPORTANT]
   > Stellen Sie sicher, dass die Anmeldungen aktivieren, die einen oder mehrere Benutzer in den für die Migration ausgewählten Datenbanken zugeordnet sind.   

   Standardmäßig werden alle SQL Server und Windows-Anmeldungen, die für die Migration gelten für die Migration ausgewählt.

2. Wählen Sie **Starten der Migration**.

   ![Wählen Sie Anmeldungen, und Starten der migration](../dma/media/SelectLogins.png)

## <a name="view-results"></a>Anzeigen der Ergebnisse

Sie können den Migrationsstatus überwachen, auf die **Ergebnisanzeige** Seite.

![Ergebnisseite anzeigen](../dma/media/ViewResults.png)

## <a name="export-migration-results"></a>Ergebnisse der schemamigration exportieren

1. Klicken Sie auf **Exportbericht** am unteren Rand der **Ergebnisanzeige** Seite, um die Ergebnisse der Migration in eine CSV-Datei zu speichern.

2. Überprüfen Sie die gespeicherte Datei ausführliche Informationen über die Migration von Benutzernamen, und klicken Sie dann überprüfen Sie die Änderungen zu.

## <a name="see-also"></a>Siehe auch

- [Data Migration Assistant (DMA)](../dma/dma-overview.md)
- [Data Migration Assistant: Konfigurationseinstellungen für](../dma/dma-configurationsettings.md)
- [Data Migration Assistant: Bewährte Methoden](../dma/dma-bestpractices.md)
