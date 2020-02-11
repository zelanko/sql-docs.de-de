---
title: Installieren von SSMA-Komponenten auf SQL Server (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 10/01/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 1f0cea859e9465eebefebc061ee51107dc7844aa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71713309"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>Installieren von SSMA-Komponenten auf SQL Server (oracleto SQL)

Zusätzlich zur Installation von SSMA müssen Sie auch Komponenten auf dem Computer installieren, auf dem ausgeführt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wird. Diese Komponenten umfassen das SSMA-Erweiterungspaket, das die Datenmigration unterstützt, und Oracle-Anbieter, um die Server-zu-Server-Konnektivität zu ermöglichen.  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA für Oracle-Erweiterungspaket

Das SSMA-Erweiterungspaket fügt der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Datenbanken **sysdb** und **ssmatesterdb** hinzu. Die Datenbank **sysdb** enthält die Tabellen und gespeicherten Prozeduren, die zum Migrieren von Daten und benutzerdefinierten Funktionen erforderlich sind, die Oracle-Systemfunktionen emulieren. Die **ssmatesterdb** -Datenbank enthält die Tabellen und Prozeduren, die für die Tester-Komponente erforderlich sind.  
  
Beim Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]werden von SSMA außerdem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agentaufträge erstellt, wenn die serverseitige Daten Migrations-Engine zum Migrieren der Daten verwendet wird.  
  
### <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor der Installation der SSMA für Oracle- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Serverkomponenten unter sicher, dass das System die folgenden Anforderungen erfüllt:  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Instanz ist installiert. SSMA unterstützt nicht SQL Server 2008 Express Edition.
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder eine höhere Version.  
  
- Den Oracle-Client Anbieter oder den OLE DB-Anbieter für Oracle und die Verbindung mit der Oracle-Datenbank, die Sie migrieren möchten. Sie können Anbieter auf dem Oracle-Produkt Medium oder auf der Oracle-Website installieren.  
  
- Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst muss während der Installation ausgeführt werden. Diese wird verwendet, um eine Liste der Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Setup-Assistenten aufzufüllen. Sie können den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser Dienst nach der Installation deaktivieren.  
  
    > [!NOTE]  
    > Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst ausgeführt wird, im Setup aber immer noch keine Liste der Instanzen angezeigt wird, müssen Sie die Blockierung des UDP-Ports 1434 deaktivieren. Mit der Windows-Firewall können Sie den Port vorübergehend entsperren, oder Sie können die Windows-Firewall temporär deaktivieren. Möglicherweise müssen Sie die Antivirussoftware auch vorübergehend deaktivieren. Stellen Sie sicher, dass Sie nach der Installation Firewalls und Antivirensoftware aktivieren.  
  
### <a name="installing-the-extension-pack"></a>Installieren des Erweiterungspakets

Sie können das Erweiterungspaket jederzeit installieren, bevor Sie Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrieren.  
  
> [!IMPORTANT]  
> Um das Erweiterungspaket zu installieren, müssen Sie Mitglied der **sysadmin** -Server Rolle auf der-Instanz sein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**So installieren Sie das Erweiterungspaket**
  
1. Wenn Sie dies noch nicht getan haben, extrahieren Sie alle Dateien aus der SSMA-ZIP-Datei.  
  
    Abhängig von der Version von WinZip, die Sie haben, können Sie entweder auf die Datei doppelklicken oder mit der rechten Maustaste auf die Datei klicken und dann **Alle extrahieren** oder **in WinZip öffnen**auswählen. Befolgen Sie die Anweisungen in der WinZip-Benutzeroberfläche, um die Dateien zu extrahieren.  
  
2. Kopieren Sie **SSMA für das Oracle-Erweiterungspaket.* n*. Installieren Sie. exe** (wobei *n* für die Buildnummer steht) für den Computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], auf dem ausgeführt wird.  
  
3. Doppelklicken Sie auf **SSMA for Oracle Extension Pack.* n*. Installieren Sie. exe**.  
  
4. Wählen Sie auf der Seite **Willkommen** die Option **Weiter** aus.  
  
5. Lesen Sie auf der Seite **Endbenutzer-Lizenzvertrag** den Lizenzvertrag. Wenn Sie zustimmen, aktivieren Sie das Kontrollkästchen **Ich stimme den Bedingungen des Lizenzvertrags** zu, und klicken Sie dann auf **weiter**.  
  
6. Wählen Sie auf der Seite Setuptyp **auswählen** die Option **typisch**aus.  
  
7. Wählen Sie auf der Seite **bereit zum Installieren** die Option **Installieren**aus.  
  
8. Wählen Sie auf der Seite **der erste Schritt der Installation ist abgeschlossen** die Option **weiter**aus.  
  
    Ein neues Dialogfeld wird angezeigt, in dem Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Extension Pack-Installation auswählen.  
  
9. Wählen Sie die Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von aus, zu der Sie Oracle-Schemas migrieren möchten, und klicken Sie dann auf **weiter**.  
  
    Die Standard Instanz hat denselben Namen wie der Computer. Auf benannte Instanzen folgt ein umgekehrter Schrägstrich und der Instanzname.  
  
10. Wählen Sie auf der Seite Verbindung die Authentifizierungsmethode aus, und klicken Sie dann auf **weiter**.  
  
    Die Windows-Authentifizierung verwendet Ihre Windows-Anmelde Informationen, um sich bei der Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von anzumelden. Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung auswählen, müssen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Anmelde Namen und ein Kennwort eingeben.  
  
11. Wählen Sie auf der nächsten Seite **Utilities Database** *n*, wobei *n* die Versionsnummer ist, und klicken Sie dann auf **weiter**.  
  
    Die **sysdb** -Datenbank wird erstellt, und die benutzerdefinierten Funktionen und gespeicherten Prozeduren werden in dieser Datenbank erstellt.  
  
    Wenn die Option zum **Installieren der Tester-Datenbank** aktiviert ist, wird die Testversion der **ssmatesterdb** -Datenbank erstellt.  
  
12. Um die Hilfsprogramme für eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu installieren, wählen Sie **Ja**aus, und klicken Sie dann auf **weiter**, oder klicken Sie auf **Nein**, um den Assistenten zu beenden.  
  
13. Führen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Sie in oder mit dem Hilfsprogramm sqlcmd das folgende Skript aus, um CLR zu aktivieren:  
  
    ```
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```

    Wenn CLR nicht aktiviert ist, erhalten Sie den folgenden Fehler, wenn SSMA eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Verbindung mit herstellt:  
  
    SSMA konnte die Versionsinformationen der Erweiterungspaket-Assembly nicht abrufen. Installieren Sie das Erweiterungspaket auf dem Datenbankserver erneut.  
  
### <a name="sql-server-database-objects"></a>Datenbankobjekte SQL Server  

Nachdem Sie das Erweiterungspaket installiert haben, wird eine **ssma_oracle. bcp_migration_packages** -Tabelle in der **sysdb** -Datenbank angezeigt.

Jedes Mal, wenn Sie Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu migrieren, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSMA einen-Agent-Auftrag. Diese Aufträge werden **ssma_oracle Daten Migrationspaket {GUID}** benannt und sind im Knoten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] im Ordner Aufträge sichtbar.  
  
## <a name="see-also"></a>Weitere Informationen

[Installieren von SSMA für Oracle Client &#40;oracleto SQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Migrieren von Oracle-Datenbanken zu SQL Server &#40;oracleto SQL-&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
