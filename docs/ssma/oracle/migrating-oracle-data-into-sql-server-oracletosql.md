---
title: Migrieren von Oracle-Daten in SQLServer (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Oracle Data Migration, Client-Side Migration
- Oracle Data Migration,Server-Side Migration
ms.assetid: e23c5268-41ed-4e55-9fe7-a11376202a13
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 3e076317b902c053ed51059712dd7752e8ce78a5
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392529"
---
# <a name="migrating-oracle-data-into-sql-server-oracletosql"></a>Migrieren von Oracle-Daten zu SQL Server (OracleToSQL)
Nachdem Sie die konvertierten Objekte mit erfolgreich synchronisiert haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], können Sie Daten aus Oracle in migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Wenn die Engine verwendeten Server Side Data Migration-Engine ist, klicken Sie dann, müssen bevor Sie Daten migrieren können Sie installieren SSMA für Oracle-Erweiterungspaket und die Oracle-Anbieter auf dem Computer mit SSMA. Der SQL Server-Agent-Dienst muss auch ausgeführt werden. Weitere Informationen dazu, wie Sie das Pack für die Erweiterung installieren, finden Sie unter [Installation von Server-Komponenten (OracleToSQL)](http://msdn.microsoft.com/33070e5f-4e39-4b70-ae81-b8af6e4983c5)  
  
## <a name="setting-migration-options"></a>Festlegen von Migrationsoptionen für die  
Vor der Migration Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], überprüfen Sie die Projektoptionen für die Migration in die **Projekteinstellungen** Dialogfeld.  
  
-   Mithilfe dieses Dialogfelds können Sie Optionen wie z. B. die Batchgröße für die Migration, Tabellensperre, Überprüfung von Einschränkungen, null-Wert-Behandlung und Behandlung der Wert festlegen. Weitere Informationen zu den Projekteinstellungen für die Migration, finden Sie unter [Project Settings (Migration) (OracleToSQL)](http://msdn.microsoft.com/fcd6b988-633b-4b2b-9f36-6368b5e86b60).  
  
-   Die **Migrationsmodul** in die **Projekteinstellungen** Dialogfeld ermöglicht es dem Benutzer zum Ausführen des Migrationsprozesses mithilfe von zwei Typen von Data Migration-Engines:  
  
    1.  Client-Seite-Migration Datenmodul  
  
    2.  Server-Seite-Migration Datenmodul  
  
**Client-Side-Datenmigration:**  
  
-   Wählen Sie die Informationen zum Initiieren des Daten-Migration auf dem Client die **Client-Seite-Migration Datenmodul** option die **Projekteinstellungen** Dialogfeld.  
  
-   In **Projekteinstellungen**, **Client-Seite-Migration Datenmodul** Option festgelegt ist.  
  
    > [!NOTE]  
    > Die **clientseitige Data Migration-Engine** befindet sich in der SSMA-Anwendung und ist daher nicht abhängig von der Verfügbarkeit des Packs Erweiterung.  
  
**Datenmigration für Server-Seite:**  
  
-   Während der Datenmigration von Server-Seite befindet sich das Modul in der Zieldatenbank ein. Er wird über das Pack für die Erweiterung installiert. Weitere Informationen zum Installieren der Erweiterung Pack finden Sie unter [Installation von Server-Komponenten auf SQL Server](installing-ssma-components-on-sql-server-oracletosql.md)  
  
-   Um die Migration auf dem Server zu initiieren, wählen Sie die **Servermodul für die Migration von Seite Daten** option die **Projekteinstellungen** im Dialogfeld.  
  
## <a name="migrating-data-to-sql-server"></a>Migrieren von Daten in SQLServer  
Migrieren von Daten ist ein Massenladen-Vorgang, die Zeilen mit Daten aus Oracle-Tabellen in Verschiebt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen in Transaktionen. Anzahl der Zeilen in den geladenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in jede Transaktion wird in den projekteinstellungen konfiguriert.  
  
Migration Nachrichten sicher, dass im Ausgabebereich angezeigt wird. Aus der **Ansicht** , wählen Sie im Menü **Ausgabe**.  
  
**Zum Migrieren von Daten**  
  
1.  Überprüfen Sie Folgendes:  
  
    -   Oracle-Anbieter werden auf dem Computer installiert, die SSMA ausgeführt wird.  
  
    -   Sie haben die konvertierten Objekte mit synchronisiert die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank.  
  
2.  Wählen Sie in der Oracle-Metadaten-Explorer die Objekte, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Um Daten für alle Schemas migrieren möchten, aktivieren Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Zum Migrieren von Daten aus, oder lassen Sie einzelne Tabellen, zuerst das Schema erweitern, erweitern Sie **Tabellen**, und klicken Sie dann aktivieren oder deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
3.  Zum Migrieren von Daten auftreten, zwei Fälle:  
  
    **Client-Side-Datenmigration:**  
  
    -   Zum Ausführen von **Datenmigration für Client-Side**, wählen die **Client-Seite-Migration Datenmodul** option die **Projekteinstellungen** Dialogfeld.  
  
    **Datenmigration für Server-Seite:**  
  
    -   Bevor Sie die Migration von Daten auf dem Server durchführen, stellen Sie Folgendes sicher:  
  
        1.  SSMA für Oracle-Erweiterungspaket wird installiert, auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
        2.  Der SQL Server-Agent-Dienst wird auf der Instanz von SQL Server ausgeführt.  
  
    -   Zum Ausführen von **Server Side Datenmigration**, wählen die **Servermodul für die Migration von Seite Daten** option die **Projekteinstellungen** Dialogfeld.  
  
4.  Mit der rechten Maustaste **Schemas** in Oracle-Metadaten-Explorer, und klicken Sie dann auf **Migrieren von Daten**. Sie können auch Daten für einzelne Objekte oder Kategorien von Objekten migrieren: mit der rechten Maustaste das Objekt oder der entsprechenden übergeordneten Ordner. Wählen Sie die **Migrieren von Daten** Option.  
  
    > [!NOTE]  
    > Wenn SSMA for Oracle-Erweiterungspaket nicht, auf der Instanz von installiert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und wenn **Servermodul für die Migration von Seite Daten** ausgewählt ist, wird beim Migrieren Ihrer Daten in die Zieldatenbank aus, der folgende Fehler aufgetreten ist: " Datenmigration der SSMA-Komponenten auf SQL Server nicht gefunden, serverseitige Datenmigration ist nicht möglich. Überprüfen Sie, ob die Erweiterung Pack ordnungsgemäß installiert ist ". Klicken Sie auf **Abbrechen** um die Datenmigration zu beenden.  
  
5.  In der **Herstellen einer Verbindung mit Oracle** Dialogfeld Geben Sie Anmeldeinformationen für die Verbindung, und klicken Sie dann auf **Connect**. Weitere Informationen zum Herstellen einer Verbindung mit Oracle finden Sie unter [Verbindung zu Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md)  
  
    Für die Verbindung mit der Zieldatenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], geben Sie die Anmeldeinformationen für die Verbindung in der **Herstellen einer Verbindung mit SQL Server** (Dialogfeld), und klicken Sie auf **Connect**. Weitere Informationen zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter [Herstellen einer Verbindung mit SQL Server](http://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Nachrichten werden angezeigt, der **Ausgabe** Bereich. Wenn die Migration abgeschlossen ist, wird die **Data Migration Report** angezeigt wird. Wenn keine Daten migriert haben, klicken Sie auf die Zeile, die den Fehler enthält, und klicken Sie dann auf **Details**. Wenn Sie mit dem Bericht fertig sind, klicken Sie auf **schließen**. Weitere Informationen zu den Data Migration Report, finden Sie unter [Data Migration Report (häufig SSMA)](http://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Bei der SQL Express-Edition als die Zieldatenbank verwendet wird, wird nur die Seite Daten Clientmigration ist zulässig, und Datenmigration für Server-Seite wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
