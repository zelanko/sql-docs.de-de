---
title: Installieren von SSMA-Komponenten auf SQLServer (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6121c75390e7493052a16b2e898eac69283e41ec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63294570"
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Installieren von SSMA-Komponenten auf SQL Server (SybaseToSQL)
Zusätzlich zum Installieren von SSMA für die Verwendung von Server-Side-Datenmigration, müssen Sie auch Komponenten installieren, auf dem Computer, auf denen ausgeführt wird, ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Zu diesen Komponenten gehören der SSMA-Erweiterungspaket, unterstützt die Datenmigration und Sybase-Anbieter, um die Verbindung mit Server-zu-Server zuzulassen.  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA für Sybase-Erweiterungspaket  
Der SSMA-Erweiterungspaket fügt die Datenbanken, **Sysdb** und **Ssmatesterdb_syb**, mit der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die **Sysdb** Datenbank enthält die Tabellen und gespeicherte Prozeduren, die zum Migrieren von Daten erforderlich sind. Die **Ssmatester_syb** Datenbank enthält das Schema **Ssma_sybase_utilities**, in dem die Objekte (Tabellen, Trigger, Ansichten) verwendet, die von der SSMA-Tester-Komponente erstellt werden.  
  
Darüber hinaus beim Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträge, wenn Server Side Data Migration-Engine verwendet wird, für die Migration der das.  
  
### <a name="installing-the-extension-pack"></a>Das Erweiterungspaket installieren  
Sie können vor dem Migrieren von Daten auf, das Erweiterungspaket installieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Um das Erweiterungspaket installieren zu können, muss Sie Mitglied der Serverrolle "Sysadmin" auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Das Erweiterungspaket installieren**  
  
1.  Kopieren Sie SSMA für Sybase-Erweiterungspaket aus. *n*. Install.exe, wobei *n* ist, auf dem Computer, auf denen ausgeführt wird, die Nummer des Builds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Doppelklicken Sie SSMA für Sybase-Erweiterungspaket aus. *n*. Install.exe.  
  
3.  Klicken Sie auf der Seite Willkommen auf **Weiter**.  
  
4.  Lesen Sie auf der Seite Lizenzbedingungen den Lizenzvertrag. Wenn Sie zustimmen, wählen Sie die **ich stimme den Bedingungen des Lizenzvertrags** , und klicken Sie dann auf **Weiter**.  
  
5.  Klicken Sie auf der Seite Installationstyp auswählen auf **Standard**.  
  
6.  Klicken Sie auf der Seite Installationsbereit auf **installieren**.  
  
7.  Klicken Sie auf den abgeschlossen-der erste Schritt der Installationsseite auf **Weiter**.  
  
    Ein neues Dialogfeld wird angezeigt, in dem Sie die Instanz von auswählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Erweiterung-Paketinstallation.  
  
8.  Wählen Sie die Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , in dem Sie migrieren ASE-Datenbanken, und klicken Sie dann auf **Weiter**.  
  
    Die Standardinstanz hat den gleichen Namen wie der Computer an. Benannte Instanzen werden ein umgekehrter Schrägstrich und der Instanzname folgt.  
  
9. Klicken Sie auf der Seite Verbindungsparameter, wählen Sie die Authentifizierungsmethode aus, und klicken Sie dann auf **Weiter**.  
  
    Windows-Authentifizierung wird Ihre Windows-Anmeldeinformationen verwenden, um zu versuchen, melden Sie sich mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bei Auswahl von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung, geben Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldename und Kennwort.  
  
10. Wählen Sie auf der Seite Server verwalten **installieren Dienstprogramme Datenbank** *n*, wobei *n* ist die Versionsnummer, und klicken Sie dann auf **Weiter**.  
  
    Die **Sysdb** Datenbank erstellt wird und die gespeicherten Prozeduren werden in dieser Datenbank erstellt.  
  
    Wenn **Tester-Datenbank installieren** Option wird überprüft der Tester **Ssmatesterdb_syb** Datenbank erstellt wird.  
  
11. Hilfsprogramme für die zu einer anderen Instanz installieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Option **zurück zu Instanzen**, und klicken Sie dann auf **Weiter**. Um den Assistenten zu beenden, klicken Sie auf **beenden**.  
  
### <a name="sql-server-database-objects"></a>SQL Server-Datenbankobjekten  
Nach der Installation der Erweiterung Pack werden Sie eine finden Sie unter einem **ssma_syb.bcp_migration_packages** -Tabelle in der **Sysdb** Datenbank. Sie sehen auch die folgenden gespeicherten Prozeduren:  
  
-   **bcp_clean_migration_data**  
  
-   **bcp_ensure_message_table**  
  
-   **bcp_insert_new_message**  
  
-   **bcp_post_process**  
  
-   **bcp_read_new_migration_messages**  
  
-   **bcp_save_migration_package**  
  
-   **bcp_smart_truncate**  
  
-   **bcp_start_migration_process**  
  
-   **get_jobstep_info**  
  
-   **stop_agent_process**  
  
Jedes Mal, die Sie zum Migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA erstellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag. Diese Aufträge werden mit dem Namen **Ssma_syb Migration Datenpaket {GUID}** , und in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Knoten der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] im Ordner "Aufträge".  
  
## <a name="sybase-providers"></a>Sybase-Anbieter  
Wenn Sie Daten aus der App Service-Umgebung migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Azure, die Daten migriert werden, direkt zwischen ASE und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Azure. Es wird nicht über SSMA übertragen werden, da dies die Datenmigration verlangsamen würde.  
  
### <a name="installing-the-sybase-providers"></a>Installieren die Anbieter für Sybase  
Die folgenden Anweisungen bieten die grundlegenden Installationsschritte für die Sybase-Anbieter zu installieren. Die genauen Anweisungen variiert abhängig von der Version des Sybase-Setup-Programms.  
  
> [!IMPORTANT]  
> Bevor Sie das Setupprogramm ausführen, stellen Sie sicher, dass Sie nicht gegen die lizenzveREINBARUNG verstoßen.  
  
1.  Führen Sie das Setupprogramm von Sybase ASE.  
  
2.  Wählen Sie die benutzerdefinierte Installation.  
  
3.  Wählen Sie auf der Seite Funktionsauswahl die Datenanbieter für ODBC, OLE DB und ADO.NET ein.  
  
4.  Überprüfen Sie die ausgewählten Funktionen, und klicken Sie dann auf **Fertig stellen** Datenanbieter zu installieren.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für Sybase Client &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
