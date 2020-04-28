---
title: Installieren von SSMA-Komponenten auf SQL Server (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1fbc3a8f74b21bd5a53bdd874b5c41ef522e29f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029009"
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Installieren von SSMA-Komponenten auf SQL Server (SybaseToSQL)
Zusätzlich zur Installation von SSMA müssen Sie für die Verwendung der Server seitigen Datenmigration auch-Komponenten auf dem Computer installieren, auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dem ausgeführt wird. Diese Komponenten umfassen das SSMA-Erweiterungspaket, das die Datenmigration unterstützt, und Sybase-Anbieter, um die Server-zu-Server-Konnektivität zu ermöglichen.  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA für Sybase-Erweiterungspaket  
Das SSMA-Erweiterungspaket fügt die Datenbanken **sysdb** und **ssmatesterdb_syb**der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hinzu. Die **sysdb** -Datenbank enthält die Tabellen und gespeicherten Prozeduren, die zum Migrieren von Daten erforderlich sind. Die **ssmatester_syb** -Datenbank enthält das Schema **ssma_sybase_utilities**, in dem die von der SSMA-Tester-Komponente verwendeten Objekte (Tabellen, Trigger, Sichten) erstellt werden.  
  
Beim Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]werden von SSMA außerdem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agentaufträge erstellt, wenn die serverseitige Daten Migrations-Engine zum Migrieren der Daten verwendet wird.  
  
### <a name="installing-the-extension-pack"></a>Installieren des Erweiterungspakets  
Sie können das Erweiterungspaket jederzeit installieren, bevor Sie Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrieren.  
  
> [!IMPORTANT]  
> Um das Erweiterungspaket zu installieren, müssen Sie Mitglied der sysadmin-Server Rolle auf der-Instanz sein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**So installieren Sie das Erweiterungspaket**  
  
1.  Kopieren Sie SSMA für das Sybase-Erweiterungspaket. *n*. Installieren Sie. exe, wobei *n* die Buildnummer ist, auf dem Computer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auf dem ausgeführt wird.  
  
2.  Doppelklicken Sie auf SSMA für Sybase-Erweiterungspaket. *n*. Installieren Sie. exe.  
  
3.  Klicken Sie auf der Seite Willkommenauf **Weiter**.  
  
4.  Lesen Sie auf der Seite Endbenutzer-Lizenzvertrag den Lizenzvertrag. Wenn Sie zustimmen, aktivieren Sie das Kontrollkästchen **Ich stimme den Bedingungen des Lizenzvertrags** zu, und klicken Sie dann auf **weiter**.  
  
5.  Klicken Sie auf der Seite Setuptyp auswählen auf **typisch**.  
  
6.  Klicken Sie auf der Seite Installations bereit auf **Installieren**.  
  
7.  Klicken Sie auf der Seite der erste Schritt der Installation ist abgeschlossen auf **weiter**.  
  
    Ein neues Dialogfeld wird angezeigt, in dem Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Extension Pack-Installation auswählen.  
  
8.  Wählen Sie die Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von aus, in der Sie ASE-Datenbanken migrieren möchten, und klicken Sie auf **weiter**.  
  
    Die Standard Instanz hat denselben Namen wie der Computer. Auf benannte Instanzen folgt ein umgekehrter Schrägstrich und der Instanzname.  
  
9. Wählen Sie auf der Seite Verbindungsparameter die Authentifizierungsmethode aus, und klicken Sie dann auf **weiter**.  
  
    Die Windows-Authentifizierung verwendet Ihre Windows-Anmelde Informationen, um sich bei der Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von anzumelden. Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung auswählen, müssen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Anmelde Namen und ein Kennwort eingeben.  
  
10. Wählen Sie auf der Seite Server verwalten die Option **Utilities Database** *n*, wobei *n* die Versionsnummer ist, und klicken Sie dann auf **weiter**.  
  
    Die **sysdb** -Datenbank wird erstellt, und die gespeicherten Prozeduren werden in dieser Datenbank erstellt.  
  
    Wenn die Option zum **Installieren der Tester-Datenbank** aktiviert ist, wird der Tester **ssmatesterdb_syb** Datenbank erstellt.  
  
11. Um die Hilfsprogramme für eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu installieren, wählen Sie **zu Instanzen zurückkehren**aus, und klicken Sie dann auf **weiter**. Oder klicken Sie auf **Beenden**, um den Assistenten zu beenden.  
  
### <a name="sql-server-database-objects"></a>Datenbankobjekte SQL Server  
Nachdem Sie das Erweiterungspaket installiert haben, wird eine **ssma_syb. bcp_migration_packages** -Tabelle in der **sysdb** -Datenbank angezeigt. Außerdem werden die folgenden gespeicherten Prozeduren angezeigt:  
  
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
  
Jedes Mal, wenn Sie Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrieren, erstellt SSMA einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag. Diese Aufträge werden **ssma_syb Daten Migrationspaket {GUID}** benannt und sind im Knoten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] im Ordner Aufträge sichtbar.  
  
## <a name="sybase-providers"></a>Sybase-Anbieter  
Beim Migrieren von Daten von ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu/SQL Azure werden die Daten direkt zwischen ASE und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure migriert. SSMA wird nicht durchlaufen, da dadurch die Datenmigration verlangsamt würde.  
  
### <a name="installing-the-sybase-providers"></a>Installieren der Sybase-Anbieter  
Die folgenden Anweisungen enthalten die grundlegenden Installationsschritte zum Installieren von Sybase-Anbietern. Die genauen Anweisungen unterscheiden sich abhängig von der Version des Sybase-Setup Programms.  
  
> [!IMPORTANT]  
> Vergewissern Sie sich vor dem Ausführen des Setup Programms, dass Sie Ihre Lizenzierungs Verträge nicht verletzen.  
  
1.  Führen Sie das Sybase-ASE-Setup Programm aus.  
  
2.  Wählen Sie benutzerdefiniertes Setup.  
  
3.  Wählen Sie auf der Seite Funktionsauswahl die Datenanbieter ODBC, OLE DB und ADO.net aus.  
  
4.  Überprüfen Sie die ausgewählten Features, und klicken Sie dann auf **Fertig** stellen, um den Datenanbieter zu installieren.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für den Sybase-Client &#40;sybasedesql&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
