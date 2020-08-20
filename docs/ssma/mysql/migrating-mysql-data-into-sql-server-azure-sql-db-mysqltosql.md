---
description: Migrieren von MySQL-Daten in SQL Server Azure SQL-Datenbank (mysqlto SQL)
title: Migrieren von MySQL-Daten in SQL Server Azure SQL-Datenbank (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Data Migration, server side data migration
- Data Migration,client side data migration
ms.assetid: a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 9fa753d472c5a7ead39faf88bc2479bc1caa9bc3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497742"
---
# <a name="migrating-mysql-data-into-sql-server---azure-sql-database-mysqltosql"></a>Migrieren von MySQL-Daten in SQL Server Azure SQL-Datenbank (mysqlto SQL)
Nachdem Sie die konvertierten Objekte erfolgreich mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure synchronisiert haben, können Sie Daten von MySQL zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure migrieren.  
  
> [!IMPORTANT]  
> Wenn es sich bei der verwendeten Engine um ein Server seitiges Daten Migrations Modul handelt, müssen Sie vor dem Migrieren von Daten das SSMA für MySQL-Erweiterungspaket und die MySQL-Anbieter auf dem Computer installieren, auf dem SSMA ausgeführt wird. Der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienst muss ebenfalls ausgeführt werden. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter Installieren von [SSMA-Komponenten auf SQL Server (MySQL zu SQL)](https://msdn.microsoft.com/6772d0c5-258f-4d7b-afb0-b5f810e71af1) .  
  
## <a name="setting-migration-options"></a>Festlegen von Migrations Optionen  
Überprüfen Sie vor dem Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure die Projekt Migrations Optionen im Dialogfeld **Projekteinstellungen** .  
  
-   Mithilfe dieses Dialog Felds können Sie Optionen wie die Batch Größe für die Migration, das Sperren von Tabellen, die Einschränkungs Überprüfung, die Behandlung von NULL-Werten und die Verarbeitung von Identitäts Werten festlegen. Weitere Informationen zu den Projekt Migrations Einstellungen finden Sie unter [Projekteinstellungen (Migration)](https://msdn.microsoft.com/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9).  
  
    Weitere Informationen zu **erweiterten Daten Migrations Einstellungen**finden Sie unter [Einstellungen für die Datenmigration](data-migration-settings-mysqltosql.md) .  
  
-   Die **Migrations-Engine** im Dialogfeld **Projekteinstellungen** ermöglicht dem Benutzer, den Migrationsprozess mit zwei Arten von Daten Migrations Modulen auszuführen:  
  
    1.  Client seitiges Datenmigrations-Engine  
  
    2.  Server seitiges Datenmigrations-Engine  
  
**Client seitige Daten Migration:**  
  
-   Wählen Sie im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus, um die Datenmigration auf Clientseite zu initiieren.  
  
-   In den **Projekteinstellungen**ist die Option **Client seitiges Daten Migrations** Modul festgelegt.  
  
    > [!NOTE]  
    > Die **Client seitige Daten Migrations-Engine** befindet sich in der SSMA-Anwendung und ist daher nicht von der Verfügbarkeit des Erweiterungspakets abhängig.  
  
**Server seitige Daten Migration:**  
  
-   Während der Server seitigen Datenmigration befindet sich die-Engine in der Zieldatenbank. Sie wird über das Erweiterungspaket installiert. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter Installieren von [SSMA-Komponenten auf SQL Server (MySQL zu SQL)](https://msdn.microsoft.com/6772d0c5-258f-4d7b-afb0-b5f810e71af1) .  
  
-   Wählen Sie im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Daten Migrations** Modul aus, um die Migration auf Serverseite zu initiieren.  
  
> [!IMPORTANT]  
> Die **Client seitige Daten Migrations** Option ist nur für SQL Azure verfügbar.  
  
## <a name="migrating-data-to-sql-server-or-sql-azure"></a>Migrieren von Daten zu SQL Server oder SQL Azure  
Beim Migrieren von Daten handelt es sich um einen Massen Ladevorgang, der Daten Zeilen aus MySQL-Tabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Transaktionen verschiebt oder in diese SQL Azure. Die Anzahl der Zeilen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in jeder Transaktion geladen werden, wird in den Projekteinstellungen konfiguriert.  
  
Stellen Sie sicher, dass der Ausgabebereich angezeigt wird, um Migrations Meldungen anzuzeigen. Wählen Sie andernfalls im Menü **Ansicht** die Option **Ausgabe**aus.  
  
**So migrieren Sie Daten**  
  
1.  Überprüfen Sie Folgendes:  
  
    -   Die MySQL-Anbieter sind auf dem Computer installiert, auf dem SSMA ausgeführt wird.  
  
    -   Sie haben die konvertierten Objekte mit der Zieldatenbank (SQL Server/SQL Azure) synchronisiert.  
  
2.  Wählen Sie im MySQL-metadatenexplorer die Objekte aus, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Wenn Sie Daten für alle Schemas migrieren möchten, aktivieren Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Erweitern Sie zum Migrieren von Daten oder zum weglassen einzelner Tabellen zunächst das Schema, erweitern Sie **Tabellen**, und aktivieren oder deaktivieren Sie dann das Kontrollkästchen neben der Tabelle.  
  
3.  Zum Migrieren von Daten entstehen zwei Fälle:  
  
    **Client seitige Daten Migration:**  
  
    -   Wählen Sie zum Ausführen der **Client seitigen Datenmigration**im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus.  
  
    **Server seitige Daten Migration:**  
  
    -   Stellen Sie vor dem Ausführen der Datenmigration auf Serverseite Folgendes sicher:  
  
        1.  Das SSMA für MySQL-Erweiterungspaket wird auf der Instanz von SQL Server installiert.  
  
        2.  Der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienst wird auf der-Instanz ausgeführt SQL Server  
  
    -   Wählen Sie zum Durchführen der **serverseitigen Datenmigration**im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Datenmigrations-Engine** aus.  
  
4.  Klicken Sie im MySQL-metadatenexplorer mit der rechten Maustaste auf **Schemas** , und klicken Sie dann auf **Daten migri** Sie können auch Daten für einzelne Objekte oder Objektkategorien migrieren: Klicken Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner. Wählen Sie die Option **Daten migrieren** aus.  
  
    > [!NOTE]  
    > Wenn das SSMA für MySQL-Erweiterungspaket nicht auf der Instanz von SQL Server installiert ist und **serverseitiges Datenmigrations-Engine** ausgewählt ist, wird beim Migrieren der Daten zur Zieldatenbank der folgende Fehler festgestellt: "SSMA-Daten Migrations Komponenten wurden auf SQL Server nicht gefunden. serverseitige Datenmigration ist nicht möglich. Überprüfen Sie, ob das Erweiterungspaket ordnungsgemäß installiert ist. Klicken Sie auf **Abbrechen** , um die Datenmigration zu beenden.  
  
5.  Geben Sie im Dialogfeld **mit MySQL verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie dann auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit MySQL finden Sie unter [Herstellen einer Verbindung mit MySQL &#40;mysqlto SQL&#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
    Wenn die Zieldatenbank SQL Server ist, geben Sie im Dialogfeld **mit SQL Server verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit SQL Server finden Sie unter Herstellen einer Verbindung [mit SQL Server](https://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Wenn die Zieldatenbank SQL Azure ist, geben Sie im Dialogfeld **mit SQL Azure verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit SQL Azure finden Sie unter Herstellen einer Verbindung [mit Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/connect-to-azure-sql-db-mysqltosql.md)  
  
    Nachrichten werden im **Ausgabe** Bereich angezeigt. Wenn die Migration beendet ist, wird der **Daten Migrationsbericht** angezeigt. Wenn keine Daten migriert wurden, klicken Sie auf die Zeile, die die Fehler enthält, und klicken Sie dann auf **Details**. Wenn Sie den Bericht fertiggestellt haben, klicken Sie auf **Schließen**. Weitere Informationen zum Daten Migrationsbericht finden Sie unter [Daten Migrationsbericht (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241) .  
  
> [!NOTE]  
> Wenn die SQL Express-Edition als Zieldatenbank verwendet wird, ist nur die Client seitige Datenmigration zulässig, und die serverseitige Datenmigration wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
