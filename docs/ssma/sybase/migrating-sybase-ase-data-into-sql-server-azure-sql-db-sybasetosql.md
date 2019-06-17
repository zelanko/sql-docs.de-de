---
title: Migrieren von Sybase ASE-Daten in SQLServer – Azure SQL-Datenbank | Microsoft-Dokumentation
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
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c358b0b4285a6512b2c0ac5db101bd7eed0f2ba5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62705731"
---
# <a name="migrating-sybase-ase-data-into-sql-server---azure-sql-db--sybasetosql"></a>Migrieren von Sybase ASE-Daten in SQLServer – Azure Sqldb (SybaseToSQL)
Nachdem die Sybase Adaptive Server Enterprise (ASE) Datenbankobjekte in erfolgreich geladen wurde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank können Sie Daten aus der App Service-Umgebung migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.  
  
> [!IMPORTANT]  
> Wenn die Engine verwendeten Server Side Data Migration-Engine ist, müssen klicken Sie dann vor dem Migrieren von Daten, Sie installieren SSMA für Sybase ASE-Erweiterungspaket und die Sybase ASE-Anbieter auf dem Computer, der SSMA ausgeführt wird. Der SQL Server-Agent-Dienst muss auch ausgeführt werden. Weitere Informationen dazu, wie Sie das Pack für die Erweiterung installieren, finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server (SybaseToSQL)](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
## <a name="setting-migration-options"></a>Festlegen von Migrationsoptionen für die  
Vor der Migration von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, überprüfen die Projektoptionen für die Migration in die **Projekteinstellungen** Dialogfeld.  
  
-   Mithilfe dieses Dialogfelds können Sie Optionen wie z. B. die Batchgröße für die Migration, Tabellensperre, Überprüfung von Einschränkungen, null-Wert-Behandlung und Behandlung der Wert festlegen. Weitere Informationen zu den Projekteinstellungen für die Migration, finden Sie unter [Project Settings (Migration) (Sybase)](https://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924).  
  
    Weitere Informationen zu **erweiterte Data Migration Settings**, finden Sie unter [Data Migration Settings](data-migration-settings-sybasetosql.md)  
  
-   Die **Migrationsmodul** in die **Projekteinstellungen** Dialogfeld ermöglicht es dem Benutzer zum Ausführen des Migrationsprozesses mithilfe von zwei Typen von Data Migration-Engines, viz.:  
  
    1.  Client-Seite-Migration Datenmodul  
  
    2.  Server-Seite-Migration Datenmodul  
  
**Client-Side-Datenmigration:**  
  
-   Wählen Sie die Option, um die Datenmigration auf der Clientseite zu initiieren, **Client-Seite-Migration Datenmodul** in die **Projekteinstellungen** Dialogfeld.  
  
-   In **Projekteinstellungen**, **Client-Seite-Migration Datenmodul** Option ist standardmäßig festgelegt.  
  
    > [!NOTE]  
    > Die Client-Seite-Migration-Engine befindet sich in der SSMA-Anwendung und ist daher nicht die Verfügbarkeit der Erweiterungspaket abhängig.  
  
**Datenmigration für Server-Seite:**  
  
-   Während der Datenmigration für Server-Seite befindet sich das Modul in der Zieldatenbank ein. Er wird über das Pack für die Erweiterung installiert. Weitere Informationen zum Installieren der Erweiterung Pack finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server (SybaseToSQL)](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
-   Um die Migration auf dem Server zu initiieren, wählen Sie die **Servermodul für die Migration von Seite Daten** option die **Projekteinstellungen** Dialogfeld.  
  
> [!NOTE]  
> Wenn Azure SQL-Datenbank verwendet wird, als die Zieldatenbank, nur **Datenmigration für Client-Side** ist zulässig und Datenmigration für Server-Seite wird nicht unterstützt.  
  
## <a name="migrating-data-to-sql-server-or-azure-sql-db"></a>Migrieren von Daten in SQLServer oder Azure SQL-Datenbank  
Migrieren von Daten ist ein Massenladen-Vorgang, die Zeilen mit Daten aus dem ASE-Tabellen in SQL Server-Tabellen in Transaktionen verschiebt. Die Anzahl der Zeilen, die in SQL Server oder Azure SQL-Datenbank geladen werden, in der jeweiligen Transaktion ist in den projekteinstellungen konfiguriert werden.  
  
Um die Migration Nachrichten anzuzeigen, sicher, dass im Ausgabebereich angezeigt wird. Wählen Sie andernfalls **Ausgabe** aus der **Ansicht** Menü.  
  
**Zum Migrieren von Daten**  
  
1.  Überprüfen Sie Folgendes:  
  
    -   Die ASE-Anbieter werden auf dem Computer installiert, die SSMA ausgeführt wird.  
  
    -   Sie haben die konvertierten Objekte mit der Zieldatenbank (SQL Server oder Azure SQL-Datenbank) synchronisiert.  
  
2.  Wählen Sie in der Sybase-Metadaten-Explorer die Objekte, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Um Daten für alle Schemas migrieren möchten, aktivieren Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Zum Migrieren von Daten aus, oder lassen Sie einzelne Tabellen, zuerst das Schema erweitern, erweitern Sie **Tabellen**, und klicken Sie dann aktivieren oder deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
3.  Zum Migrieren von Daten auftreten, zwei Fälle:  
  
    **Client-Side-Datenmigration:**  
  
    Zum Ausführen von **Datenmigration für Client-Side**, wählen die **Client-Seite-Migration Datenmodul** option die **Projekteinstellungen** Dialogfeld.  
  
    **Datenmigration für Server-Seite:**  
  
    -   Bevor Sie die Datenmigration für Server-Seite ausführen, stellen Sie Folgendes sicher:  
  
        1.  SSMA für Sybase-Erweiterungspaket wird auf der Instanz von SQL Server installiert.  
  
        2.  Der SQL Server-Agent-Dienst wird auf der Instanz von SQL Server ausgeführt werden.  
  
    -   Zum Ausführen von **Server Side Datenmigration**, wählen die **Servermodul für die Migration von Seite Daten** option die **Projekteinstellungen** Dialogfeld.  
  
4.  Mit der rechten Maustaste **Schemas** in Sybase-Metadaten-Explorer, und klicken Sie dann auf **Migrieren von Daten**. Sie können auch Daten für einzelne Objekte oder Kategorien von Objekten migrieren: Mit der rechten Maustaste das Objekt oder der übergeordnete Ordner, und wählen die **Migrieren von Daten** Option.  
  
    > [!NOTE]  
    > Wenn SSMA for Sybase-Erweiterungspaket für die Instanz von SQL Server nicht installiert ist und **Server-Seite-Migration Datenmodul** ausgewählt ist, wird beim Migrieren Ihrer Daten in die Zieldatenbank aus, der folgende Fehler aufgetreten ist: "Datenmigration SSMA-Komponenten auf SQL Server nicht gefunden, serverseitige Datenmigration ist nicht möglich. Überprüfen Sie, ob die Erweiterung Pack ordnungsgemäß installiert ist ". Klicken Sie auf **Abbrechen** um die Datenmigration zu beenden.  
  
5.  In der **Herstellen einer Verbindung mit Sybase ASE** Dialogfeld Geben Sie Anmeldeinformationen für die Verbindung, und klicken Sie dann auf **Connect**. Weitere Informationen zum Verbinden mit Sybase ASE finden Sie unter [Herstellen einer Verbindung mit Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md)  
  
    Wenn die Zieldatenbank, SQL Server ist, und geben Sie dann die Anmeldeinformationen für die Verbindung in der **Herstellen einer Verbindung mit SQL Server** (Dialogfeld), und klicken Sie auf **Connect**. Weitere Informationen zum Herstellen einer Verbindung mit SQL Server finden Sie unter [Herstellen einer Verbindung mit SQL-Server(SybaseToSQL)](https://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)  
  
    Wenn die Zieldatenbank Azure SQL-Datenbank ist, und geben Sie dann die Anmeldeinformationen für die Verbindung in der **Herstellen einer Verbindung mit Azure SQL-Datenbank** (Dialogfeld), und klicken Sie auf **Connect**. Weitere Informationen zum Verbinden mit Azure SQL-Datenbank finden Sie unter [eine Verbindung mit Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
    Nachrichten werden angezeigt, der **Ausgabe** Bereich. Wenn die Migration abgeschlossen ist, wird die **Data Migration Report** angezeigt wird. Wenn keine Daten migriert haben, klicken Sie auf die Zeile, die den Fehler enthält, und klicken Sie dann auf **Details**. Wenn Sie mit dem Bericht fertig sind, klicken Sie auf **schließen**. Weitere Informationen zu den Data Migration Report, finden Sie unter [Data Migration Report (häufig SSMA)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Bei der SQL Express-Edition als die Zieldatenbank verwendet wird, wird nur die Seite Daten Clientmigration ist zulässig, und Datenmigration für Server-Seite wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
