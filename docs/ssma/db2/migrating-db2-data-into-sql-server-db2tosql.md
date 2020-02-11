---
title: Migrieren von DB2-Daten in SQL Server (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 86cbd39f-6dac-409a-9ce1-7dd54403f84b
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 9cc7b3dd309dfac9e35021ca3234ca66483181e9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68074102"
---
# <a name="migrating-db2-data-into-sql-server-db2tosql"></a>Migrieren von DB2-Daten in SQL Server (DB2ToSQL)
Nachdem Sie die konvertierten Objekte mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erfolgreich synchronisiert haben, können Sie Daten von DB2 zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrieren.  
  
> [!IMPORTANT]  
> Wenn es sich bei der verwendeten Engine um ein Server seitiges Daten Migrations Modul handelt, müssen Sie vor dem Migrieren von Daten das SSMA für DB2-Erweiterungspaket und die DB2-Anbieter auf dem Computer installieren, auf dem SSMA ausgeführt wird. Der SQL Server-Agent-Dienst muss ebenfalls ausgeführt werden. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter Installieren von [SSMA-Komponenten auf SQL Server](https://msdn.microsoft.com/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
## <a name="setting-migration-options"></a>Festlegen von Migrations Optionen  
Überprüfen Sie vor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dem Migrieren von Daten zu die Projekt Migrations Optionen im Dialogfeld **Projekteinstellungen** .  
  
-   Mithilfe dieses Dialog Felds können Sie Optionen wie die Batch Größe für die Migration, das Sperren von Tabellen, die Einschränkungs Überprüfung, die Behandlung von NULL-Werten und die Verarbeitung von Identitäts Werten festlegen. Weitere Informationen zu den Projekt Migrations Einstellungen finden Sie unter [Projekteinstellungen (Migration)](https://msdn.microsoft.com/48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae).  
  
-   Die **Migrations-Engine** im Dialogfeld **Projekteinstellungen** ermöglicht dem Benutzer, den Migrationsprozess mit zwei Arten von Daten Migrations Modulen auszuführen:  
  
    1.  Client seitiges Datenmigrations-Engine  
  
    2.  Server seitiges Datenmigrations-Engine  
  
**Client seitige Daten Migration:**  
  
-   Wählen Sie im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus, um die Datenmigration auf Clientseite zu initiieren.  
  
-   In den **Projekteinstellungen**ist die Option **Client seitiges Daten Migrations** Modul festgelegt.  
  
    > [!NOTE]  
    > Die **Client seitige Daten Migrations-Engine** befindet sich in der SSMA-Anwendung und ist daher nicht von der Verfügbarkeit des Erweiterungspakets abhängig.  
  
**Server seitige Daten Migration:**  
  
-   Während der Server seitigen Datenmigration befindet sich die-Engine in der Zieldatenbank. Sie wird über das Erweiterungspaket installiert. Weitere Informationen zum Installieren des Erweiterungspakets finden Sie unter Installieren von [SSMA-Komponenten auf SQL Server](https://msdn.microsoft.com/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
-   Wählen Sie im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Daten Migrations** Modul aus, um die Migration auf Serverseite zu initiieren.  
  
## <a name="migrating-data-to-sql-server"></a>Migrieren von Daten zu SQL Server  
Beim Migrieren von Daten handelt es sich um einen Massen Ladevorgang, mit dem Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeilen aus DB2-Tabellen in Tabellen in Transaktionen verschoben werden. Die Anzahl der Zeilen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in in jeder Transaktion geladen werden, wird in den Projekteinstellungen konfiguriert.  
  
Stellen Sie sicher, dass der Ausgabebereich angezeigt wird, um Migrations Meldungen anzuzeigen. Wählen Sie andernfalls im Menü **Ansicht** die Option **Ausgabe**aus.  
  
**So migrieren Sie Daten**  
  
1.  Überprüfen Sie Folgendes:  
  
    -   Die DB2-Anbieter sind auf dem Computer installiert, auf dem SSMA ausgeführt wird.  
  
    -   Sie haben die konvertierten Objekte mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank synchronisiert.  
  
2.  Wählen Sie im DB2-metadatenexplorer die Objekte aus, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Wenn Sie Daten für alle Schemas migrieren möchten, aktivieren Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Erweitern Sie zum Migrieren von Daten oder zum weglassen einzelner Tabellen zunächst das Schema, erweitern Sie **Tabellen**, und aktivieren oder deaktivieren Sie dann das Kontrollkästchen neben der Tabelle.  
  
3.  Zum Migrieren von Daten entstehen zwei Fälle:  
  
    **Client seitige Daten Migration:**  
  
    -   Wählen Sie zum Ausführen der **Client seitigen Datenmigration**im Dialogfeld **Projekteinstellungen** die Option **Client seitiges Daten Migrations** Modul aus.  
  
    **Server seitige Daten Migration:**  
  
    -   Stellen Sie vor dem Ausführen der Datenmigration auf Serverseite Folgendes sicher:  
  
        1.  Das SSMA für DB2-Erweiterungspaket wird auf der-Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert.  
  
        2.  Der SQL Server-Agent-Dienst wird auf der-Instanz ausgeführt SQL Server.  
  
    -   Wählen Sie zum Durchführen der **serverseitigen Datenmigration**im Dialogfeld **Projekteinstellungen** die Option **serverseitiges Datenmigrations-Engine** aus.  
  
4.  Klicken Sie mit der rechten Maustaste auf **Schemas** in DB2 Metadata Explorer, und klicken Sie dann auf **Daten migrieren**. Sie können auch Daten für einzelne Objekte oder Objektkategorien migrieren: Klicken Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner. Wählen Sie die Option **Daten migrieren** aus.  
  
    > [!NOTE]  
    > Wenn das SSMA für DB2-Erweiterungspaket nicht auf der-Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert ist und **serverseitiges Datenmigrations-Engine** ausgewählt ist, wird beim Migrieren der Daten zur Zieldatenbank der folgende Fehler festgestellt: "SSMA-Daten Migrations Komponenten wurden auf SQL Server nicht gefunden. serverseitige Datenmigration ist nicht möglich. Überprüfen Sie, ob das Erweiterungspaket ordnungsgemäß installiert ist. Klicken Sie auf **Abbrechen** , um die Datenmigration zu beenden.  
  
5.  Geben Sie im Dialogfeld **mit DB2 verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie dann auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung mit DB2 finden Sie unter [Herstellen einer Verbindung mit DB2 Database &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
  
    Geben Sie zum Herstellen einer Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit der Zieldatenbank im Dialogfeld **mit SQL Server verbinden** die Anmelde Informationen für die Verbindung ein, und klicken Sie auf **verbinden**. Weitere Informationen zum Herstellen einer Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit finden Sie unter [Herstellen einer Verbindung mit SQL Server](https://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e)  
  
    Nachrichten werden im **Ausgabe** Bereich angezeigt. Wenn die Migration beendet ist, wird der **Daten Migrationsbericht** angezeigt. Wenn keine Daten migriert wurden, klicken Sie auf die Zeile, die die Fehler enthält, und klicken Sie dann auf **Details**. Wenn Sie den Bericht fertiggestellt haben, klicken Sie auf **Schließen**. Weitere Informationen zum Daten Migrationsbericht finden Sie unter [Daten Migrationsbericht (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241) .  
  
> [!NOTE]  
> Wenn die SQL Express-Edition als Zieldatenbank verwendet wird, ist nur die Client seitige Datenmigration zulässig, und die serverseitige Datenmigration wird nicht unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von DB2-Daten in SQL Server &#40;DB2ToSQL-&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
