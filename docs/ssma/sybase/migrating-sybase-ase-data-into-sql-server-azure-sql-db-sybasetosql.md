---
title: Migrieren von Sybase ASE-Daten in SQL Server Azure SQL-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migrating data,Client Side Data Migration
- Migrating data,Server Side Data Migration
ms.assetid: 54a39f5e-9250-4387-a3ae-eae47c799811
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5bac0e5437a4700c6bfb4b349e1a5ca9cf421901
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934695"
---
# <a name="migrating-sybase-ase-data-into-sql-server---azure-sql-database--sybasetosql"></a>Migrieren von Sybase ASE-Daten in SQL Server Azure SQL-Datenbank (sybaseto SQL)
Nachdem Sie die Datenbankobjekte von Sybase Adaptive Server Enterprise (ASE) erfolgreich in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank geladen haben, können Sie Daten von ASE zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank migrieren.  
  
> [!IMPORTANT]  
> Wenn es sich bei der verwendeten Engine um ein Server seitiges Daten Migrations Modul handelt, müssen Sie vor dem Migrieren von Daten das SSMA für Sybase ASE Extension Pack und die Sybase ASE-Anbieter auf dem Computer installieren, auf dem SSMA ausgeführt wird. Der SQL Server-Agent-Dienst muss ebenfalls ausgeführt werden. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter Installieren von [SSMA-Komponenten auf SQL Server (sybasedesql)](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d) .  
  
## <a name="setting-migration-options"></a>Festlegen von Migrations Optionen  
Überprüfen Sie vor dem Migrieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank die Projekt Migrations Optionen im Dialogfeld **Projekteinstellungen** .  
  
-   Mithilfe dieses Dialog Felds können Sie Optionen wie die Batch Größe für die Migration, das Sperren von Tabellen, die Einschränkungs Überprüfung, die Verarbeitung von NULL-Werten und die Verarbeitung von Identitäts Werten festlegen. Weitere Informationen zu den Projekt Migrations Einstellungen finden Sie unter [Projekteinstellungen (Migration) (Sybase)](https://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924).  
  
    Weitere Informationen zu **erweiterten Daten Migrations Einstellungen**finden Sie unter [Einstellungen für die Datenmigration](data-migration-settings-sybasetosql.md) .  
  
-   Die **Migrations-Engine** im Dialogfeld **Projekteinstellungen** ermöglicht dem Benutzer das Ausführen des Migrationsprozesses mit zwei Arten von Datenmigrations-Engines:  
  
    1.  Client seitiges Datenmigrations-Engine  
  
    2.  Server seitiges Datenmigrations-Engine  
  
**Client seitige Daten Migration:**  
  
-   Wählen Sie im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus, um die Datenmigration auf Clientseite zu initiieren.  
  
-   In den **Projekteinstellungen**ist die Option **Client seitiges Daten Migrations** Modul standardmäßig festgelegt.  
  
    > [!NOTE]  
    > Die Client seitige Daten Migrations-Engine befindet sich in der SSMA-Anwendung und ist daher nicht von der Verfügbarkeit des Erweiterungspakets abhängig.  
  
**Server seitige Daten Migration:**  
  
-   Bei der Server seitigen Datenmigration befindet sich die-Engine in der Zieldatenbank. Sie wird über das Erweiterungspaket installiert. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter Installieren von [SSMA-Komponenten auf SQL Server (sybasedesql)](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d) .  
  
-   Um die Migration auf dem Server zu initiieren, wählen Sie im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Datenmigrations-Engine** aus.  
  
> [!NOTE]  
> Wenn Azure SQL-Datenbank als Zieldatenbank verwendet wird, ist nur die **Client seitige Datenmigration** zulässig, und die serverseitige Datenmigration wird nicht unterstützt.  
  
## <a name="migrating-data-to-sql-server-or-azure-sql-database"></a>Migrieren von Daten zu SQL Server oder Azure SQL-Datenbank  
Beim Migrieren von Daten handelt es sich um einen Massen Ladevorgang, mit dem Daten Zeilen aus den ASE-Tabellen in SQL Server Tabellen in Transaktionen verschoben werden. Die Anzahl der in SQL Server oder Azure SQL-Datenbank geladenen Zeilen in jeder Transaktion wird in den Projekteinstellungen konfiguriert.  
  
Stellen Sie sicher, dass der Ausgabebereich angezeigt wird, um die Migrations Meldungen anzuzeigen. Wählen Sie andernfalls im Menü **Ansicht** die Option **Ausgabe** aus.  
  
**So migrieren Sie Daten**  
  
1.  Überprüfen Sie Folgendes:  
  
    -   Die ASE-Anbieter sind auf dem Computer installiert, auf dem SSMA ausgeführt wird.  
  
    -   Sie haben die konvertierten Objekte mit der Zieldatenbank (SQL Server oder Azure SQL-Datenbank) synchronisiert.  
  
2.  Wählen Sie im Sybase-metadatenexplorer die Objekte aus, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Wenn Sie Daten für alle Schemas migrieren möchten, aktivieren Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Erweitern Sie zum Migrieren von Daten oder zum weglassen einzelner Tabellen zunächst das Schema, erweitern Sie **Tabellen**, und aktivieren oder deaktivieren Sie dann das Kontrollkästchen neben der Tabelle.  
  
3.  Zum Migrieren von Daten entstehen zwei Fälle:  
  
    **Client seitige Daten Migration:**  
  
    Wählen Sie zum Ausführen der **Client seitigen Datenmigration**im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus.  
  
    **Server seitige Daten Migration:**  
  
    -   Vor dem Ausführen der Server seitigen Datenmigration sollten Sie Folgendes sicherstellen:  
  
        1.  Das SSMA für Sybase-Erweiterungspaket wird auf der Instanz von SQL Server installiert.  
  
        2.  Der SQL Server-Agent-Dienst wird auf der-Instanz ausgeführt SQL Server  
  
    -   Wählen Sie zum Durchführen der **serverseitigen Datenmigration**im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Datenmigrations-Engine** aus.  
  
4.  Klicken Sie im Sybase-metadatenexplorer mit der rechten Maustaste auf **Schemas** , und klicken Sie dann auf **Daten migri** Sie können auch Daten für einzelne Objekte oder Objektkategorien migrieren: Klicken Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner, und wählen Sie die Option **Daten migrieren** aus.  
  
    > [!NOTE]  
    > Wenn das SSMA für Sybase-Erweiterungspaket nicht auf der Instanz von SQL Server installiert ist und **serverseitiges Datenmigrations-Engine** ausgewählt ist, tritt beim Migrieren der Daten zur Zieldatenbank der folgende Fehler auf: "SSMA-Daten Migrations Komponenten wurden auf SQL Server nicht gefunden. serverseitige Datenmigration ist nicht möglich. Überprüfen Sie, ob das Erweiterungspaket ordnungsgemäß installiert ist. Klicken Sie auf **Abbrechen** , um die Datenmigration zu beenden.  
  
5.  Geben Sie im Dialogfeld **mit Sybase-ASE verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie dann auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit der Sybase-ASE finden Sie unter Herstellen einer Verbindung [mit Sybase &#40;sybasedesql&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md)  
  
    Wenn die Zieldatenbank SQL Server ist, geben Sie im Dialogfeld **mit SQL Server verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit SQL Server finden Sie unter Herstellen einer Verbindung [mit SQL Server (sybasedesql)](https://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) .  
  
    Wenn die Zieldatenbank Azure SQL-Datenbank ist, geben Sie im Dialogfeld Verbindung **mit Azure SQL-Datenbank herstellen** die Anmelde Informationen für die Verbindung ein, und klicken Sie auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit Azure SQL-Datenbank finden Sie unter [Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
    Nachrichten werden im **Ausgabe** Bereich angezeigt. Wenn die Migration beendet ist, wird der **Daten Migrationsbericht** angezeigt. Wenn keine Daten migriert wurden, klicken Sie auf die Zeile, die die Fehler enthält, und klicken Sie dann auf **Details**. Wenn Sie den Bericht fertiggestellt haben, klicken Sie auf **Schließen**. Weitere Informationen zum Daten Migrationsbericht finden Sie unter [Daten Migrationsbericht (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241) .  
  
> [!NOTE]  
> Wenn die SQL Express-Edition als Zieldatenbank verwendet wird, ist nur die Client seitige Datenmigration zulässig, und die serverseitige Datenmigration wird nicht unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
