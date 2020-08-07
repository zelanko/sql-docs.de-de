---
title: Installieren von SSMA-Komponenten auf SQL Server (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/14/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 1c66255f57a69db0807ab1620cafd60444f296c8
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87865388"
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Installieren von SSMA-Komponenten auf SQL Server (sybasedesql)

Zusätzlich zur Installation von SSMA müssen Sie für die Verwendung der Server seitigen Datenmigration auch-Komponenten auf dem Computer installieren, auf dem ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Diese Komponenten umfassen das SSMA-Erweiterungspaket, das die Datenmigration unterstützt, und Sybase-Anbieter, um die Server-zu-Server-Konnektivität zu ermöglichen.

## <a name="ssma-for-sybase-extension-pack"></a>SSMA für Sybase-Erweiterungspaket

Das SSMA-Erweiterungspaket fügt die Datenbanken **sysdb** und **ssmatesterdb_syb**der angegebenen Instanz von hinzu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Die **sysdb** -Datenbank enthält die Tabellen und gespeicherten Prozeduren, die zum Migrieren von Daten erforderlich sind. Die **ssmatester_syb** -Datenbank enthält das Schema **ssma_sybase_utilities**, in dem die von der SSMA-Tester-Komponente verwendeten Objekte (Tabellen, Trigger, Sichten) erstellt werden.

Beim Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden von SSMA außerdem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agentaufträge erstellt, wenn die serverseitige Daten Migrations-Engine zum Migrieren der Daten verwendet wird.

### <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor der Installation von SSMA für Sybase-Serverkomponenten unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sicher, dass das System die folgenden Anforderungen erfüllt:

- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Instanz ist installiert.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder eine höhere Version.
- Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.7.2 oder eine spätere Version. Sie können Sie über das [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)abrufen.
- Der Sybase-OLE DB/ADO.net/ODBC-Anbieter und die Verbindung mit dem SAP ASE-Datenbankserver, der die zu migrierenden Datenbanken enthält. Sie können Anbieter aus dem SAP ASE-Produkt Medium installieren. Weitere Informationen zur Konnektivität finden [Sie unter Herstellen einer Verbindung mit der Sybase-ASE &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).
- Der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser-Dienst muss während der Installation ausgeführt werden. Diese wird verwendet, um eine Liste der Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Setup-Assistenten aufzufüllen. Sie können den- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Dienst nach der Installation deaktivieren.

  > [!NOTE]
  > Wenn der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser-Dienst ausgeführt wird, im Setup aber immer noch keine Liste der Instanzen angezeigt wird, müssen Sie die Blockierung des UDP-Ports 1434 deaktivieren. Mit der Windows-Firewall können Sie den Port vorübergehend entsperren, oder Sie können die Windows-Firewall temporär deaktivieren. Möglicherweise müssen Sie die Antivirussoftware auch vorübergehend deaktivieren. Stellen Sie sicher, dass Sie nach der Installation Firewalls und Antivirensoftware aktivieren.

### <a name="installing-the-extension-pack"></a>Installieren des Erweiterungspakets

Sie können das Erweiterungspaket jederzeit installieren, bevor Sie Daten zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

> [!IMPORTANT]
> Um das Erweiterungspaket zu installieren, müssen Sie Mitglied der sysadmin-Server Rolle auf der-Instanz sein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

So installieren Sie das Erweiterungspaket:

1. Kopieren Sie **SSMAforSybaseExtensionPack_*n*. msi**, wobei *n* die Buildnummer ist, auf den Computer, auf dem ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
2. Doppelklicken Sie auf **SSMAforSybaseExtensionPack_*n*. msi**.
3. Klicken Sie auf der Seite **Willkommen**auf **Weiter**.
4. Lesen Sie auf der Seite **Endbenutzer-Lizenzvertrag** den Lizenzvertrag. Wenn Sie zustimmen, aktivieren Sie die Option **Ich akzeptiere die Vereinbarung** , und klicken Sie dann auf **weiter**.
5. Klicken Sie auf der Seite Setuptyp **auswählen** auf **typisch**.
6. Klicken Sie auf der Seite **Bereit zum Installieren** auf **Installieren**.
7. Klicken Sie auf der Seite der **erste Schritt der Installation ist abgeschlossen** auf **weiter**.

   Ein neues Dialogfeld wird angezeigt, in dem Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Extension Pack-Installation auswählen.

8. Wählen Sie die Instanz von aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , in der Sie SAP ASE-Datenbanken migrieren möchten, und klicken Sie auf **weiter**.

   Die Standard Instanz hat denselben Namen wie der Computer. Auf benannte Instanzen folgt ein umgekehrter Schrägstrich und der Instanzname.

9. Wählen Sie auf der Seite Verbindung die Authentifizierungsmethode aus, und klicken Sie dann auf **weiter**.

   Die Windows-Authentifizierung verwendet Ihre Windows-Anmelde Informationen, um sich bei der Instanz von anzumelden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Wenn Sie Server Authentifizierung auswählen, müssen Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Namen und ein Kennwort eingeben.

10. Im nächsten Schritt müssen Sie das Kennwort für einen Hauptschlüssel festlegen, der zum Verschlüsseln vertraulicher Daten verwendet wird, die während der serverseitigen Datenmigration in der Erweiterungspaket-Datenbank gespeichert werden. Geben **Sie ein**sicheres Kennwort ein, und klicken Sie auf

11. Wählen Sie auf der nächsten Seite **Utilities Database *n* installieren aus, und installieren Sie Extension Pack-Bibliotheken**, wobei *n* die Versionsnummer ist. Wenn Sie das Tester-Feature verwenden möchten, aktivieren Sie das Kontrollkästchen **Tester Datenbank installieren** , und klicken Sie dann auf **weiter**.

    Die **sysdb** -Datenbank wird mit den Tabellen und gespeicherten Prozeduren erstellt, die für die Datenmigration erforderlich sind (mithilfe der serverseitigen Daten Migrations-Engine), die in dieser Datenbank erstellt werden.

    Wenn die Option zum **Installieren der Tester-Datenbank** aktiviert ist, wird die **ssmatesterdb_syb** Datenbank erstellt.

12. Sobald die Installation fertiggestellt ist, wird eine Eingabeaufforderung angezeigt, in der Sie gefragt werden, ob Sie die hilfsprogrammdatenbank auf einer anderen Instanz von installieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wählen Sie **Ja**aus, und klicken Sie dann auf **weiter**, um den Assistenten zu beenden, und **Wählen Sie** dann **Beenden**

### <a name="sql-server-database-objects"></a>Datenbankobjekte SQL Server

Nachdem Sie das Erweiterungspaket installiert haben, wird eine **ssma_syb. bcp_migration_packages** -Tabelle in der **sysdb** -Datenbank angezeigt. Außerdem werden die folgenden gespeicherten Prozeduren angezeigt:

- `bcp_clean_migration_data`
- `bcp_ensure_message_table`
- `bcp_insert_new_message`
- `bcp_post_process`
- `bcp_read_new_migration_messages`
- `bcp_save_migration_package`
- `bcp_smart_truncate`
- `bcp_start_migration_process`
- `get_jobstep_info`
- `stop_agent_process`

Jedes Mal, wenn Sie Daten zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , erstellt SSMA einen- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Auftrag. Diese Aufträge werden **ssma_syb Daten Migrationspaket {GUID}** benannt und sind im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Knoten Agent von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] im Ordner Aufträge sichtbar.  

## <a name="sybase-providers"></a>Sybase-Anbieter

Wenn Sie die serverseitige Datenmigration zum Verschieben von Daten aus SAP ASE in verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , werden die Daten direkt zwischen SAP ASE und migriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . SSMA wird nicht durchlaufen, da dadurch die Datenmigration verlangsamt würde.

### <a name="installing-the-sybase-providers"></a>Installieren der Sybase-Anbieter

Die folgenden Anweisungen enthalten die grundlegenden Installationsschritte zum Installieren von Sybase-Anbietern. Die genauen Anweisungen unterscheiden sich abhängig von der Version des Sybase-Setup Programms.

> [!IMPORTANT]
> Vergewissern Sie sich vor dem Ausführen des Setup Programms, dass Sie Ihre Lizenzierungs Verträge nicht verletzen.

1. Führen Sie das Sybase-ASE-Setup Programm aus.
2. Wählen Sie benutzerdefiniertes Setup.
3. Wählen Sie auf der Seite Funktionsauswahl die Datenanbieter ODBC, OLE DB und ADO.net aus.
4. Überprüfen Sie die ausgewählten Features, und klicken Sie dann auf **Fertig** stellen, um den Datenanbieter zu installieren.

## <a name="see-also"></a>Weitere Informationen

- [Installieren von SSMA für den Sybase-Client](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)
- [Migrieren von Sybase ASE-Datenbanken zu SQL Server Azure SQL-Datenbank](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)
