---
title: Installieren von SSMA-Komponenten auf SQLServer (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2041901a851ca755b1079535ccbf763472ec7bc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853358"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>Installieren von SSMA-Komponenten auf SQL Server (OracleToSQL)
Zusätzlich zum Installieren von SSMA, müssen Sie auch den Komponenten installieren, auf dem Computer, auf denen ausgeführt wird, ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Zu diesen Komponenten gehören der SSMA-Erweiterungspaket, unterstützt die Datenmigration und Oracle-Anbieter, um die Verbindung mit Server-zu-Server zuzulassen.  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA für Oracle-Erweiterungspaket  
Der SSMA-Erweiterungspaket fügt die Datenbanken, **Sysdb** und **Ssmatesterdb**, mit der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die Datenbank **Sysdb** enthält die Tabellen und gespeicherte Prozeduren, die erforderlich sind, zum Migrieren von Daten sowie die benutzerdefinierten Funktionen, die Oracle-Systemfunktionen zu emulieren. Die **Ssmatesterdb** Datenbank enthält die Tabellen und Prozeduren, die von der Komponente Tester erforderlich sind.  
  
Darüber hinaus beim Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträge, wenn Server Side Data Migration-Engine verwendet wird, für die Migration der das.  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
Vor der Installation von SSMA für Oracle-Server-Komponenten auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], stellen Sie sicher, dass das System die folgenden Anforderungen erfüllt:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz installiert ist. SSMA ist SQL Server 2008 Express Edition nicht unterstützt.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 oder höher.  
  
-   Der Oracle-Client-Anbieter oder OLE DB-Anbieter für Oracle und Verbindung mit der Oracle-Datenbank, die Sie migrieren möchten. Sie können den Anbieter aus der Oracle-Produktdatenträger oder Oracle-Website installieren.  
  
-   Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst muss ausgeführt werden, während der Installation. Wird verwendet, um eine Liste der Instanzen des Auffüllen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Setup-Assistenten. Sie können die Deaktivieren der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst nach der Installation.  
  
    > [!NOTE]  
    > Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst wird ausgeführt, aber Sie noch nicht sehe, dass eine Liste von Instanzen im Setup, müssen Sie UDP-Port 1434 zulassen. Sie können Windows-Firewall verwenden, um vorübergehend den Port zulassen, oder Sie können Windows-Firewall vorübergehend deaktivieren. Möglicherweise müssen auch vorübergehend deaktivieren, antivirus-Software. Stellen Sie sicher, dass Firewalls und antivirus-Software nach der Installation zu ermöglichen.  
  
### <a name="installing-the-extension-pack"></a>Das Erweiterungspaket installieren  
Sie können vor dem Migrieren von Daten auf, das Erweiterungspaket installieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Um das Erweiterungspaket installieren zu können, muss Sie Mitglied der **Sysadmin** -Serverrolle auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Das Erweiterungspaket installieren**  
  
1.  Wenn Sie dies noch nicht getan haben, extrahieren Sie alle Dateien aus der SSMA-Zip-Datei.  
  
    Je nach Version WinZip haben, können Sie entweder Doppelklicken Sie auf die Datei, oder mit der rechten Maustaste in der das und auswählen **alle extrahieren** oder **in WinZip öffnen**. Befolgen Sie die Anweisungen in der WinZip-Benutzeroberfläche zum Extrahieren der Dateien ein.  
  
2.  Kopieren Sie SSMA für Oracle-Erweiterungspaket aus. *n*. Install.exe, wobei *n* ist, auf dem Computer, auf denen ausgeführt wird, die Nummer des Builds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Doppelklicken Sie SSMA für Oracle-Erweiterungspaket aus. *n*. Install.exe.  
  
4.  Klicken Sie auf der Seite Willkommen auf **Weiter**.  
  
5.  Lesen Sie auf der Seite Lizenzbedingungen den Lizenzvertrag. Wenn Sie zustimmen, wählen Sie die **ich stimme den Bedingungen des Lizenzvertrags** , und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der Seite Installationstyp auswählen auf **Standard**.  
  
7.  Klicken Sie auf der Seite Installationsbereit auf **installieren**.  
  
8.  Klicken Sie auf den abgeschlossen-der erste Schritt der Installationsseite auf **Weiter**.  
  
    Ein neues Dialogfeld wird angezeigt, in dem Sie die Instanz von auswählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Erweiterung-Paketinstallation.  
  
9. Wählen Sie die Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , in dem Sie migrieren von Oracle-Schemas, und klicken Sie dann auf **Weiter**.  
  
    Die Standardinstanz hat den gleichen Namen wie der Computer an. Benannte Instanzen werden ein umgekehrter Schrägstrich und der Instanzname folgt.  
  
10. Klicken Sie auf der Verbindungsseite, wählen Sie die Authentifizierungsmethode aus, und klicken Sie dann auf **Weiter**.  
  
    Windows-Authentifizierung wird Ihre Windows-Anmeldeinformationen verwenden, um zu versuchen, melden Sie sich mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bei Auswahl von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung, geben Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldename und Kennwort.  
  
11. Wählen Sie auf der nächsten Seite **installieren Dienstprogramme Datenbank** *n*, wobei *n* ist die Versionsnummer, und klicken Sie dann auf **Weiter**.  
  
    Die **Sysdb** Datenbank erstellt wird und die benutzerdefinierten Funktionen und gespeicherten Prozeduren werden in dieser Datenbank erstellt.  
  
    Wenn **Tester-Datenbank installieren** Option wird überprüft der Tester **Ssmatesterdb** Datenbank erstellt wird.  
  
12. So installieren Sie die Hilfsprogramme in eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Option **Ja**, und klicken Sie dann auf **Weiter**. Um den Assistenten zu beenden, klicken Sie auf **keine**.  
  
13. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit dem Sqlcmd-Hilfsprogramm, führen Sie das folgende Skript aus, um CLR zu aktivieren:  
  
    ```  
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```  
    Wenn die CLR nicht aktiviert ist, wird die folgende Fehlermeldung Verbindungsaufbau SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    SSMA konnten die Erweiterung Pack Assembly Versionsinformationen nicht abgerufen werden. Installieren Sie das Pack für die Erweiterung auf dem Datenbankserver.  
  
### <a name="sql-server-database-objects"></a>SQL Server-Datenbankobjekten  
Nach der Installation der Erweiterung Pack werden Sie eine finden Sie unter einem **ssma_oracle.bcp_migration_packages** Tabelle eine **ssma_oracle.db_storage** Tabelle und ein **ssma_oracle.db_error_list** -Tabelle in der **Sysdb** Datenbank. Sie sehen auch viele gespeicherte Prozeduren und benutzerdefinierten Funktionen in der **Ssma_oracle** Schema.  
  
Jedes Mal, die Sie zum Migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA erstellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag. Diese Aufträge werden mit dem Namen **Ssma_oracle Migration Datenpaket {GUID}**, und in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Knoten der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] im Ordner "Aufträge".  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für Oracle-Client &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
