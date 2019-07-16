---
title: Migrieren von DB2-Daten in SQLServer (DB2ToSQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074102"
---
# <a name="migrating-db2-data-into-sql-server-db2tosql"></a>Migrieren von DB2-Daten in SQLServer (DB2ToSQL)
Nachdem Sie die konvertierten Objekte mit erfolgreich synchronisiert haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], können Sie Daten aus DB2 in migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Wenn die Engine verwendeten Server Side Data Migration-Engine ist, klicken Sie dann, müssen bevor Sie Daten migrieren können Sie installieren SSMA für DB2-Erweiterungspaket und die DB2-Anbieter auf dem Computer mit SSMA. Der SQL Server-Agent-Dienst muss auch ausgeführt werden. Weitere Informationen dazu, wie Sie das Pack für die Erweiterung installieren, finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server](https://msdn.microsoft.com/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
## <a name="setting-migration-options"></a>Festlegen von Migrationsoptionen für die  
Vor der Migration Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], überprüfen Sie die Projektoptionen für die Migration in die **Projekteinstellungen** Dialogfeld.  
  
-   Mithilfe dieses Dialogfelds können Sie Optionen wie z. B. die Batchgröße für die Migration, Tabellensperre, Überprüfung von Einschränkungen, null-Wert-Behandlung und Behandlung der Wert festlegen. Weitere Informationen zu den Projekteinstellungen für die Migration, finden Sie unter [Project Settings (Migration)](https://msdn.microsoft.com/48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae).  
  
-   Die **Migrationsmodul** in die **Projekteinstellungen** Dialogfeld ermöglicht es dem Benutzer zum Ausführen des Migrationsprozesses mithilfe von zwei Typen von Data Migration-Engines:  
  
    1.  Client-Seite-Migration Datenmodul  
  
    2.  Server-Seite-Migration Datenmodul  
  
**Client-Side-Datenmigration:**  
  
-   Wählen Sie die Informationen zum Initiieren des Daten-Migration auf dem Client die **Client-Seite-Migration Datenmodul** option die **Projekteinstellungen** Dialogfeld.  
  
-   In **Projekteinstellungen**, **Client-Seite-Migration Datenmodul** Option festgelegt ist.  
  
    > [!NOTE]  
    > Die **clientseitige Data Migration-Engine** befindet sich in der SSMA-Anwendung und ist daher nicht abhängig von der Verfügbarkeit des Packs Erweiterung.  
  
**Datenmigration für Server-Seite:**  
  
-   Während der Datenmigration von Server-Seite befindet sich das Modul in der Zieldatenbank ein. Er wird über das Pack für die Erweiterung installiert. Weitere Informationen zum Installieren der Erweiterung Pack finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server](https://msdn.microsoft.com/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
-   Um die Migration auf dem Server zu initiieren, wählen Sie die **Servermodul für die Migration von Seite Daten** option die **Projekteinstellungen** im Dialogfeld.  
  
## <a name="migrating-data-to-sql-server"></a>Migrieren von Daten in SQLServer  
Migrieren von Daten ist ein Massenladen-Vorgang, die Zeilen mit Daten aus DB2-Tabellen in Verschiebt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen in Transaktionen. Anzahl der Zeilen in den geladenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in jede Transaktion wird in den projekteinstellungen konfiguriert.  
  
Migration Nachrichten sicher, dass im Ausgabebereich angezeigt wird. Aus der **Ansicht** , wählen Sie im Menü **Ausgabe**.  
  
**Zum Migrieren von Daten**  
  
1.  Überprüfen Sie Folgendes:  
  
    -   Der DB2-Datenanbieter sind auf dem Computer installiert, die SSMA ausgeführt wird.  
  
    -   Sie haben die konvertierten Objekte mit synchronisiert die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank.  
  
2.  Wählen Sie die Objekte, die Daten enthalten, die Sie migrieren möchten, im DB2-Metadaten-Explorer:  
  
    -   Um Daten für alle Schemas migrieren möchten, aktivieren Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Zum Migrieren von Daten aus, oder lassen Sie einzelne Tabellen, zuerst das Schema erweitern, erweitern Sie **Tabellen**, und klicken Sie dann aktivieren oder deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
3.  Zum Migrieren von Daten auftreten, zwei Fälle:  
  
    **Client-Side-Datenmigration:**  
  
    -   Zum Ausführen von **Datenmigration für Client-Side**, wählen die **Client-Seite-Migration Datenmodul** option die **Projekteinstellungen** Dialogfeld.  
  
    **Datenmigration für Server-Seite:**  
  
    -   Bevor Sie die Migration von Daten auf dem Server durchführen, stellen Sie Folgendes sicher:  
  
        1.  SSMA für DB2-Erweiterungspaket wird installiert, auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
        2.  Der SQL Server-Agent-Dienst wird auf der Instanz von SQL Server ausgeführt.  
  
    -   Zum Ausführen von **Server Side Datenmigration**, wählen die **Servermodul für die Migration von Seite Daten** option die **Projekteinstellungen** Dialogfeld.  
  
4.  Mit der rechten Maustaste **Schemas** in DB2-Metadaten-Explorer, und klicken Sie dann auf **Migrieren von Daten**. Sie können auch Daten für einzelne Objekte oder Kategorien von Objekten migrieren: Mit der rechten Maustaste das Objekt oder der übergeordnete Ordner; Wählen Sie die **Migrieren von Daten** Option.  
  
    > [!NOTE]  
    > Wenn SSMA for DB2-Erweiterungspaket nicht, auf der Instanz von installiert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und wenn **Server-Seite-Migration Datenmodul** ausgewählt ist, wird beim Migrieren Ihrer Daten in die Zieldatenbank aus, der folgende Fehler aufgetreten ist: "Datenmigration SSMA-Komponenten auf SQL Server nicht gefunden, serverseitige Datenmigration ist nicht möglich. Überprüfen Sie, ob die Erweiterung Pack ordnungsgemäß installiert ist ". Klicken Sie auf **Abbrechen** um die Datenmigration zu beenden.  
  
5.  In der **Herstellen einer Verbindung mit DB2** Dialogfeld Geben Sie Anmeldeinformationen für die Verbindung, und klicken Sie dann auf **Connect**. Weitere Informationen zum Herstellen einer Verbindung mit DB2, finden Sie unter [Herstellen einer Verbindung mit DB2-Datenbank &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
  
    Für die Verbindung mit der Zieldatenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], geben Sie die Anmeldeinformationen für die Verbindung in der **Herstellen einer Verbindung mit SQL Server** (Dialogfeld), und klicken Sie auf **Connect**. Weitere Informationen zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter [Herstellen einer Verbindung mit SQL Server](https://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e)  
  
    Nachrichten werden angezeigt, der **Ausgabe** Bereich. Wenn die Migration abgeschlossen ist, wird die **Data Migration Report** angezeigt wird. Wenn keine Daten migriert haben, klicken Sie auf die Zeile, die den Fehler enthält, und klicken Sie dann auf **Details**. Wenn Sie mit dem Bericht fertig sind, klicken Sie auf **schließen**. Weitere Informationen zu den Data Migration Report, finden Sie unter [Data Migration Report (häufig SSMA)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Bei der SQL Express-Edition als die Zieldatenbank verwendet wird, wird nur die Seite Daten Clientmigration ist zulässig, und Datenmigration für Server-Seite wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von DB2-Daten in SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
