---
title: Migrieren von DB2-Daten in SQL Server (DB2ToSQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Daten aus einer DB2-Datenbank zu SQL Server oder Azure SQL-Datenbank migrieren, nachdem Sie die konvertierten Objekte synchronisiert haben.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 86cbd39f-6dac-409a-9ce1-7dd54403f84b
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 2f3ca5b9f222e52b7913d5688b6e8c6adfbd526d
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94869718"
---
# <a name="migrating-db2-data-into-sql-server-db2tosql"></a>Migrieren von DB2-Daten in SQL Server (DB2ToSQL)
Nachdem Sie die konvertierten Objekte mit erfolgreich synchronisiert haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie Daten von DB2 zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
> Wenn es sich bei der verwendeten Engine um ein Server seitiges Daten Migrations Modul handelt, müssen Sie vor dem Migrieren von Daten das SSMA für DB2-Erweiterungspaket und die DB2-Anbieter auf dem Computer installieren, auf dem SSMA ausgeführt wird. Der SQL Server-Agent-Dienst muss ebenfalls ausgeführt werden. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter Installieren von [SSMA-Komponenten auf SQL Server](./installing-ssma-components-on-sql-server-db2tosql.md)  
  
## <a name="setting-migration-options"></a>Festlegen von Migrations Optionen  
Überprüfen Sie vor dem Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Projekt Migrations Optionen im Dialogfeld **Projekteinstellungen** .  
  
-   Mithilfe dieses Dialog Felds können Sie Optionen wie die Batch Größe für die Migration, das Sperren von Tabellen, die Einschränkungs Überprüfung, die Behandlung von NULL-Werten und die Verarbeitung von Identitäts Werten festlegen. Weitere Informationen zu den Projekt Migrations Einstellungen finden Sie unter [Projekteinstellungen (Migration)](./project-settings-migration-db2tosql.md).  
  
-   Die **Migrations-Engine** im Dialogfeld **Projekteinstellungen** ermöglicht dem Benutzer, den Migrationsprozess mit zwei Arten von Daten Migrations Modulen auszuführen:  
  
    1.  Client seitiges Datenmigrations-Engine  
  
    2.  Server seitiges Datenmigrations-Engine  
  
**Client seitige Daten Migration:**  
  
-   Wählen Sie im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus, um die Datenmigration auf Clientseite zu initiieren.  
  
-   In den **Projekteinstellungen** ist die Option **Client seitiges Daten Migrations** Modul festgelegt.  
  
    > [!NOTE]  
    > Die **Client seitige Daten Migrations-Engine** befindet sich in der SSMA-Anwendung und ist daher nicht von der Verfügbarkeit des Erweiterungspakets abhängig.  
  
**Server seitige Daten Migration:**  
  
-   Während der Server seitigen Datenmigration befindet sich die-Engine in der Zieldatenbank. Sie wird über das Erweiterungspaket installiert. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter Installieren von [SSMA-Komponenten auf SQL Server](./installing-ssma-components-on-sql-server-db2tosql.md)  
  
-   Wählen Sie im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Daten Migrations** Modul aus, um die Migration auf Serverseite zu initiieren.  
  
## <a name="migrating-data-to-sql-server"></a>Migrieren von Daten zu SQL Server  
Beim Migrieren von Daten handelt es sich um einen Massen Ladevorgang, mit dem Daten Zeilen aus DB2-Tabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen in Transaktionen verschoben werden. Die Anzahl der Zeilen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in jeder Transaktion geladen werden, wird in den Projekteinstellungen konfiguriert.  
  
Stellen Sie sicher, dass der Ausgabebereich angezeigt wird, um Migrations Meldungen anzuzeigen. Wählen Sie andernfalls im Menü **Ansicht** die Option **Ausgabe** aus.  
  
**So migrieren Sie Daten**  
  
1.  Überprüfen Sie Folgendes:  
  
    -   Die DB2-Anbieter sind auf dem Computer installiert, auf dem SSMA ausgeführt wird.  
  
    -   Sie haben die konvertierten Objekte mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank synchronisiert.  
  
2.  Wählen Sie im DB2-metadatenexplorer die Objekte aus, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Wenn Sie Daten für alle Schemas migrieren möchten, aktivieren Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Erweitern Sie zum Migrieren von Daten oder zum weglassen einzelner Tabellen zunächst das Schema, erweitern Sie **Tabellen**, und aktivieren oder deaktivieren Sie dann das Kontrollkästchen neben der Tabelle.  
  
3.  Zum Migrieren von Daten entstehen zwei Fälle:  
  
    **Client seitige Daten Migration:**  
  
    -   Wählen Sie zum Ausführen der **Client seitigen Datenmigration** im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus.  
  
    **Server seitige Daten Migration:**  
  
    -   Stellen Sie vor dem Ausführen der Datenmigration auf Serverseite Folgendes sicher:  
  
        1.  Das SSMA für DB2-Erweiterungspaket wird auf der-Instanz installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
        2.  Der SQL Server-Agent-Dienst wird auf der-Instanz ausgeführt SQL Server.  
  
    -   Wählen Sie zum Durchführen der **serverseitigen Datenmigration** im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Datenmigrations-Engine** aus.  
  
4.  Klicken Sie mit der rechten Maustaste auf **Schemas** in DB2 Metadata Explorer, und klicken Sie dann auf **Daten migrieren**. Sie können auch Daten für einzelne Objekte oder Objektkategorien migrieren: Klicken Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner. Wählen Sie die Option **Daten migrieren** aus.  
  
    > [!NOTE]  
    > Wenn das SSMA für DB2-Erweiterungspaket nicht auf der-Instanz installiert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und **serverseitiges Datenmigrations-Engine** ausgewählt ist, wird beim Migrieren der Daten zur Zieldatenbank der folgende Fehler festgestellt: "SSMA-Daten Migrations Komponenten wurden auf SQL Server nicht gefunden. serverseitige Datenmigration ist nicht möglich. Überprüfen Sie, ob das Erweiterungspaket ordnungsgemäß installiert ist. Klicken Sie auf **Abbrechen** , um die Datenmigration zu beenden.  
  
5.  Geben Sie im Dialogfeld **mit DB2 verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie dann auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit DB2 finden Sie unter [Herstellen einer Verbindung mit DB2 Database &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
  
    Geben Sie zum Herstellen einer Verbindung mit der Zieldatenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Dialogfeld **mit SQL Server verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit finden Sie unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Herstellen einer Verbindung mit SQL Server](./connecting-to-sql-server-db2tosql.md)  
  
    Nachrichten werden im **Ausgabe** Bereich angezeigt. Wenn die Migration beendet ist, wird der **Daten Migrationsbericht** angezeigt. Wenn keine Daten migriert wurden, klicken Sie auf die Zeile, die die Fehler enthält, und klicken Sie dann auf **Details**. Wenn Sie den Bericht fertiggestellt haben, klicken Sie auf **Schließen**. Weitere Informationen zum Daten Migrationsbericht finden Sie unter [Daten Migrationsbericht (SSMA Common)](../sybase/data-migration-report-sybasetosql.md) .  
  
> [!NOTE]  
> Wenn die SQL Express-Edition als Zieldatenbank verwendet wird, ist nur die Client seitige Datenmigration zulässig, und die serverseitige Datenmigration wird nicht unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von DB2-Daten in SQL Server &#40;DB2ToSQL-&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
