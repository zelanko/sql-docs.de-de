---
title: Migrieren von Oracle-Daten in SQL Server (oracleto SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Daten aus einer Oracle-Datenbank zu SQL Server migrieren, nachdem Sie die konvertierten Objekte mithilfe der SSMA für Oracle-Anwendung synchronisiert haben.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Data Migration, Client-Side Migration
- Oracle Data Migration,Server-Side Migration
ms.assetid: e23c5268-41ed-4e55-9fe7-a11376202a13
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: f617b850482383400d599d7608644f27da58f17e
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293817"
---
# <a name="migrating-oracle-data-into-sql-server-oracletosql"></a>Migrieren von Oracle-Daten zu SQL Server (OracleToSQL)
Nachdem Sie die konvertierten Objekte mit erfolgreich synchronisiert haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie Daten von Oracle zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
> Wenn es sich bei der verwendeten Engine um ein Server seitiges Daten Migrations Modul handelt, müssen Sie vor dem Migrieren von Daten das SSMA für Oracle-Erweiterungspaket und die Oracle-Anbieter auf dem Computer installieren, auf dem SSMA ausgeführt wird. Der SQL Server-Agent-Dienst muss ebenfalls ausgeführt werden. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter [Installieren von Server Komponenten (oracleto SQL)](https://msdn.microsoft.com/33070e5f-4e39-4b70-ae81-b8af6e4983c5) .  
  
## <a name="setting-migration-options"></a>Festlegen von Migrations Optionen  
Überprüfen Sie vor dem Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Projekt Migrations Optionen im Dialogfeld **Projekteinstellungen** .  
  
-   Mithilfe dieses Dialog Felds können Sie Optionen wie die Batch Größe für die Migration, das Sperren von Tabellen, die Einschränkungs Überprüfung, die Behandlung von NULL-Werten und die Verarbeitung von Identitäts Werten festlegen. Weitere Informationen zu den Projekt Migrations Einstellungen finden Sie unter [Project Settings (Migration) (oracleto SQL)](https://msdn.microsoft.com/fcd6b988-633b-4b2b-9f36-6368b5e86b60).  
  
-   Die **Migrations-Engine** im Dialogfeld **Projekteinstellungen** ermöglicht dem Benutzer, den Migrationsprozess mit zwei Arten von Daten Migrations Modulen auszuführen:  
  
    1.  Client seitiges Datenmigrations-Engine  
  
    2.  Server seitiges Datenmigrations-Engine  
  
**Client seitige Daten Migration:**  
  
-   Wählen Sie im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus, um die Datenmigration auf Clientseite zu initiieren.  
  
-   In den **Projekteinstellungen**ist die Option **Client seitiges Daten Migrations** Modul festgelegt.  
  
    > [!NOTE]  
    > Die **Client seitige Daten Migrations-Engine** befindet sich in der SSMA-Anwendung und ist daher nicht von der Verfügbarkeit des Erweiterungspakets abhängig.  
  
**Server seitige Daten Migration:**  
  
-   Während der Server seitigen Datenmigration befindet sich die-Engine in der Zieldatenbank. Sie wird über das Erweiterungspaket installiert. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter Installieren von [Server Komponenten auf SQL Server](installing-ssma-components-on-sql-server-oracletosql.md)  
  
-   Wählen Sie im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Daten Migrations** Modul aus, um die Migration auf Serverseite zu initiieren.  
  
## <a name="migrating-data-to-sql-server"></a>Migrieren von Daten zu SQL Server  
Beim Migrieren von Daten handelt es sich um einen Massen Ladevorgang, mit dem Daten Zeilen aus Oracle-Tabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen in Transaktionen verschoben werden. Die Anzahl der Zeilen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in jeder Transaktion geladen werden, wird in den Projekteinstellungen konfiguriert.  
  
Stellen Sie sicher, dass der Ausgabebereich angezeigt wird, um Migrations Meldungen anzuzeigen. Wählen Sie andernfalls im Menü **Ansicht** die Option **Ausgabe**aus.  
  
**So migrieren Sie Daten**  
  
1.  Überprüfen Sie Folgendes:  
  
    -   Die Oracle-Anbieter sind auf dem Computer installiert, auf dem SSMA ausgeführt wird.  
  
    -   Sie haben die konvertierten Objekte mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank synchronisiert.  
  
2.  Wählen Sie im Oracle-metadatenexplorer die Objekte aus, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Wenn Sie Daten für alle Schemas migrieren möchten, aktivieren Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Erweitern Sie zum Migrieren von Daten oder zum weglassen einzelner Tabellen zunächst das Schema, erweitern Sie **Tabellen**, und aktivieren oder deaktivieren Sie dann das Kontrollkästchen neben der Tabelle.  
  
3.  Zum Migrieren von Daten entstehen zwei Fälle:  
  
    **Client seitige Daten Migration:**  
  
    -   Wählen Sie zum Ausführen der **Client seitigen Datenmigration**im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus.  
  
    **Server seitige Daten Migration:**  
  
    -   Stellen Sie vor dem Ausführen der Datenmigration auf Serverseite Folgendes sicher:  
  
        1.  Das SSMA für Oracle-Erweiterungspaket wird auf der-Instanz installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
        2.  Der SQL Server-Agent-Dienst wird auf der-Instanz ausgeführt SQL Server.  
  
    -   Wählen Sie zum Durchführen der **serverseitigen Datenmigration**im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Datenmigrations-Engine** aus.  
  
4.  Klicken Sie mit der rechten Maustaste auf **Schemas** in Oracle Metadata Explorer, und klicken Sie dann auf **Daten migrieren**. Sie können auch Daten für einzelne Objekte oder Objektkategorien migrieren: Klicken Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner. Wählen Sie die Option **Daten migrieren** aus.  
  
    > [!NOTE]  
    > Wenn das SSMA für Oracle-Erweiterungspaket nicht auf der-Instanz installiert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und **serverseitiges Datenmigrations-Engine** ausgewählt ist, wird beim Migrieren der Daten zur Zieldatenbank der folgende Fehler festgestellt: "SSMA-Daten Migrations Komponenten wurden auf SQL Server nicht gefunden. serverseitige Datenmigration ist nicht möglich. Überprüfen Sie, ob das Erweiterungspaket ordnungsgemäß installiert ist. Klicken Sie auf **Abbrechen** , um die Datenmigration zu beenden.  
  
5.  Geben Sie im Dialogfeld **mit Oracle verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie dann auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit Oracle finden [Sie unter Herstellen einer Verbindung mit Oracle &#40;oracleto SQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md)  
  
    Geben Sie zum Herstellen einer Verbindung mit der Zieldatenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Dialogfeld **mit SQL Server verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit finden Sie unter Herstellen einer Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [mit SQL Server](https://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Nachrichten werden im **Ausgabe** Bereich angezeigt. Wenn die Migration beendet ist, wird der **Daten Migrationsbericht** angezeigt. Wenn keine Daten migriert wurden, klicken Sie auf die Zeile, die die Fehler enthält, und klicken Sie dann auf **Details**. Wenn Sie den Bericht fertiggestellt haben, klicken Sie auf **Schließen**. Weitere Informationen zum Daten Migrationsbericht finden Sie unter [Daten Migrationsbericht (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241) .  
  
> [!NOTE]  
> Wenn die SQL Express-Edition als Zieldatenbank verwendet wird, ist nur die Client seitige Datenmigration zulässig, und die serverseitige Datenmigration wird nicht unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Oracle-Datenbanken zu SQL Server &#40;oracleto SQL-&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
