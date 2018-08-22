---
title: Migrieren von MySQL-Daten in SQLServer – Azure SQL-Datenbank (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Data Migration, server side data migration
- Data Migration,client side data migration
ms.assetid: a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82
caps.latest.revision: 24
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4651ec2de2680d9c1c855f352768228e1835f22b
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393225"
---
# <a name="migrating-mysql-data-into-sql-server---azure-sql-db-mysqltosql"></a>Migrieren von MySQL-Daten in SQLServer – Azure SQL-Datenbank (MySQLToSQL))
Nachdem Sie die konvertierten Objekte mit erfolgreich synchronisiert haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, können Sie Daten aus MySQL migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
> [!IMPORTANT]  
> Ist die Engine verwendeten Server Side Data Migration-Engine, klicken Sie dann vor der Migration Daten müssen Sie SSMA für MySQL-Erweiterungspaket und die MySQL-Anbieter auf dem Computer mit SSMA installieren. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst muss auch ausgeführt werden. Weitere Informationen dazu, wie Sie das Pack für die Erweiterung installieren, finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server (MySQL zu SQL)](http://msdn.microsoft.com/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
## <a name="setting-migration-options"></a>Festlegen von Migrationsoptionen für die  
Vor dem Migrieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, überprüfen die Projektoptionen für die Migration in die **Projekteinstellungen** Dialogfeld.  
  
-   Mithilfe dieses Dialogfelds können Sie Optionen wie z. B. die Batchgröße für die Migration, Tabellensperre, Überprüfung von Einschränkungen, null-Wert-Behandlung und Wert-Behandlung festlegen. Weitere Informationen zu den Projekteinstellungen für die Migration, finden Sie unter [Project Settings (Migration)](http://msdn.microsoft.com/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9).  
  
    Weitere Informationen zu **erweiterte Data Migration Settings**, finden Sie unter [Data Migration Settings](data-migration-settings-mysqltosql.md)  
  
-   Die **Migrationsmodul** in die **Projekteinstellungen** Dialogfeld ermöglicht es dem Benutzer zum Ausführen des Migrationsprozesses mithilfe von zwei Typen von Data Migration-Engines:  
  
    1.  Client-Seite-Migration Datenmodul  
  
    2.  Server-Seite-Migration Datenmodul  
  
**Client-Side-Datenmigration:**  
  
-   Wählen Sie die Informationen zum Initiieren des Daten-Migration auf dem Client die **Client-Seite-Migration Datenmodul** option die **Projekteinstellungen** Dialogfeld.  
  
-   In **Projekteinstellungen**, **Client-Seite-Migration Datenmodul** Option festgelegt ist.  
  
    > [!NOTE]  
    > Die **clientseitige Data Migration-Engine** befindet sich in der SSMA-Anwendung und ist daher nicht abhängig von der Verfügbarkeit des Packs Erweiterung.  
  
**Datenmigration für Server-Seite:**  
  
-   Während der Datenmigration von Server-Seite befindet sich das Modul in der Zieldatenbank ein. Er wird über das Pack für die Erweiterung installiert. Weitere Informationen zum Installieren der Erweiterung Pack finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server (MySQL zu SQL)](http://msdn.microsoft.com/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
-   Um die Migration auf dem Server zu initiieren, wählen Sie die **Servermodul für die Migration von Seite Daten** option die **Projekteinstellungen** im Dialogfeld.  
  
> [!IMPORTANT]  
> **Client-Side-Datenmigration** Option ist nur für SQL Azure verfügbar.  
  
## <a name="migrating-data-to-sql-server-or-sql-azure"></a>Migrieren von Daten in SQLServer oder SQL Azure  
Migrieren von Daten ist ein Massenladen-Vorgang, die Zeilen mit Daten aus MySQL-Tabellen in Verschiebt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabellen in Transaktionen. Anzahl der Zeilen in den geladenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in jede Transaktion wird in den projekteinstellungen konfiguriert.  
  
Migration Nachrichten sicher, dass im Ausgabebereich angezeigt wird. Aus der **Ansicht** , wählen Sie im Menü **Ausgabe**.  
  
**Zum Migrieren von Daten**  
  
1.  Überprüfen Sie Folgendes:  
  
    -   Die MySQL-Anbieter werden auf dem Computer installiert, die SSMA ausgeführt wird.  
  
    -   Sie haben die konvertierten Objekte synchronisiert, mit der Zieldatenbank (SQL Server / SQL Azure).  
  
2.  Wählen Sie im MySQL-Metadaten-Explorer die Objekte, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Um Daten für alle Schemas migrieren möchten, aktivieren Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Zum Migrieren von Daten aus, oder lassen Sie einzelne Tabellen, zuerst das Schema erweitern, erweitern Sie **Tabellen**, und klicken Sie dann aktivieren oder deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
3.  Zum Migrieren von Daten auftreten, zwei Fälle:  
  
    **Client-Side-Datenmigration:**  
  
    -   Zum Ausführen von **Datenmigration für Client-Side**, wählen die **Client-Seite-Migration Datenmodul** option die **Projekteinstellungen** Dialogfeld.  
  
    **Datenmigration für Server-Seite:**  
  
    -   Bevor Sie die Migration von Daten auf dem Server durchführen, stellen Sie Folgendes sicher:  
  
        1.  SSMA für MySQL-Erweiterungspaket wird auf der Instanz von SQL Server installiert.  
  
        2.  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Instanz von SQL Server-Agent-Dienst ausgeführt wird  
  
    -   Zum Ausführen von **Server Side Datenmigration**, wählen die **Servermodul für die Migration von Seite Daten** option die **Projekteinstellungen** Dialogfeld.  
  
4.  Mit der rechten Maustaste **Schemas** in MySQL-Metadaten-Explorer, und klicken Sie dann auf **Migrieren von Daten**. Sie können auch Daten für einzelne Objekte oder Kategorien von Objekten migrieren: mit der rechten Maustaste das Objekt oder der entsprechenden übergeordneten Ordner. Wählen Sie die **Migrieren von Daten** Option.  
  
    > [!NOTE]  
    > Wenn der SSMA für MySQL-Erweiterungspaket für die Instanz von SQL Server nicht installiert ist und **Servermodul für die Migration von Seite Daten** ausgewählt ist, wird beim Migrieren Ihrer Daten in die Zieldatenbank aus, der folgende Fehler aufgetreten ist: "SSMA Data Migration-Komponenten auf SQL Server nicht gefunden, serverseitige Datenmigration ist nicht möglich. Überprüfen Sie, ob die Erweiterung Pack ordnungsgemäß installiert ist ". Klicken Sie auf **Abbrechen** um die Datenmigration zu beenden.  
  
5.  In der **Herstellen einer Verbindung mit MySQL** Dialogfeld Geben Sie Anmeldeinformationen für die Verbindung, und klicken Sie dann auf **Connect**. Weitere Informationen zum Herstellen einer Verbindung mit MySQL finden Sie unter [Herstellen einer Verbindung mit MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
    Wenn die Zieldatenbank, SQL Server ist, und geben Sie dann die Anmeldeinformationen für die Verbindung in der **Herstellen einer Verbindung mit SQL Server** (Dialogfeld), und klicken Sie auf **Connect**. Weitere Informationen zum Herstellen einer Verbindung mit SQL Server finden Sie unter [Herstellen einer Verbindung mit SQL Server](http://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Wenn die Zieldatenbank, SQL Azure ist, und geben Sie dann die Anmeldeinformationen für die Verbindung in der **Herstellen einer Verbindung mit SQL Azure** (Dialogfeld), und klicken Sie auf **Connect**. Weitere Informationen zum Verbinden mit SQL Azure finden Sie unter [Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-azure-sql-db-mysqltosql.md)  
  
    Nachrichten werden angezeigt, der **Ausgabe** Bereich. Wenn die Migration abgeschlossen ist, wird die **Data Migration Report** angezeigt wird. Wenn keine Daten migriert haben, klicken Sie auf die Zeile, die den Fehler enthält, und klicken Sie dann auf **Details**. Wenn Sie mit dem Bericht fertig sind, klicken Sie auf **schließen**. Weitere Informationen zu den Data Migration Report, finden Sie unter [Data Migration Report (häufig SSMA)](http://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Bei der SQL Express-Edition als die Zieldatenbank verwendet wird, wird nur die Seite Daten Clientmigration ist zulässig, und Datenmigration für Server-Seite wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
