---
title: Installieren von SSMA-Komponenten auf SQLServer (MySQLToSql)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- SSMA extension pack, Installation
ms.assetid: 6772d0c5-258f-4d7b-afb0-b5f810e71af1
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1f80198787dd85d8f0c65e9881925641f9f081e5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63233033"
---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>Installieren von SSMA-Komponenten für SQL Server (MySqlToSql)
Zusätzlich zum Installieren von SSMA, müssen Sie auch den Komponenten installieren, auf dem Computer, auf denen ausgeführt wird, ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Zu diesen Komponenten gehören der SSMA-Erweiterungspaket, unterstützt die Datenmigration und Anbieter von MySQL Server-zu-Server-Konnektivität zu aktivieren.  
  
## <a name="ssma-for-mysql-extension-pack"></a>SSMA für MySQL-Erweiterungspaket  
Der SSMA-Erweiterungspaket Fügt eine Datenbank, **Sysdb**, mit der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Diese Datenbank enthält die Tabellen und gespeicherte Prozeduren, die zum Migrieren von Daten erforderlich sind.  
  
Darüber hinaus beim Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Aufträge, wenn Server Side Data Migration-Engine für die Migration der das verwendet wird.  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
Vor der Installation von SSMA für MySQL Server-Komponenten auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], stellen Sie sicher, dass der Computer die folgenden Anforderungen erfüllt:  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 oder höher.  
  
-   Die MySQL-Client-Anbieter, und eine Verbindung mit der MySQL-Datenbank, die Sie migrieren möchten. Sie können den Anbieter aus der MySQL-Produktdatenträger oder MySQL-Website installieren.  
  
-   Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst muss ausgeführt werden, während der Installation. Wird verwendet, um eine Liste der Instanzen des Auffüllen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Setup-Assistenten. Sie können die Deaktivieren der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst nach der Installation.  
  
    > [!NOTE]  
    > Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst wird ausgeführt, aber Sie noch nicht sehe, dass eine Liste von Instanzen im Setup, müssen Sie UDP-Port 1434 zulassen. Sie können Windows-Firewall verwenden, um vorübergehend den Port zulassen, oder Sie können Windows-Firewall vorübergehend deaktivieren. Möglicherweise müssen auch vorübergehend deaktivieren, antivirus-Software. Stellen Sie sicher, dass Firewalls und antivirus-Software nach der Installation zu ermöglichen.  
  
### <a name="installing-the-extension-pack"></a>Das Erweiterungspaket installieren  
Sie können vor dem Migrieren von Daten auf, das Erweiterungspaket installieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Um das Erweiterungspaket installieren zu können, muss Sie Mitglied der **Sysadmin** -Serverrolle auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Das Erweiterungspaket installieren**  
  
1.  Kopieren Sie SSMA für MySQL-Erweiterungspaket aus. *n*. Install.exe, wobei *n* ist, auf dem Computer, auf denen ausgeführt wird, die Nummer des Builds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Doppelklicken Sie SSMA für MySQL-Erweiterung Pack ein. *n*. Install.exe.  
  
3.  Klicken Sie im Dialogfeld "Willkommen" auf **Weiter**.  
  
4.  Lesen Sie im Dialogfeld Software-Lizenzbedingungen den Lizenzvertrag. Wenn Sie zustimmen, wählen Sie die **ich stimme den Bedingungen des Lizenzvertrags** , und klicken Sie dann auf **Weiter**.  
  
5.  Klicken Sie auf das Dialogfeld Installationsart auswählen, auf **Standard**.  
  
6.  Klicken Sie auf die "bereit zur Installation-Dialogfeld" **installieren**.  
  
7.  Klicken Sie auf die im Dialogfeld erste Schritt der Installation abgeschlossen, **Weiter**.  
  
    Ein neues Dialogfeld wird angezeigt, in dem Sie die Instanz von auswählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Erweiterung-Paketinstallation.  
  
8.  Wählen Sie die Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , in dem Sie Migrieren der MySQL-Schemas, und klicken Sie dann auf **Weiter**.  
  
    Die Standardinstanz hat den gleichen Namen wie der Computer an. Benannte Instanzen werden ein umgekehrter Schrägstrich und der Instanzname folgt.  
  
9. Klicken Sie auf das Dialogfeld "Verbindung", wählen Sie die Authentifizierungsmethode aus, und klicken Sie dann auf **Weiter**.  
  
    Windows-Authentifizierung wird Ihre Windows-Anmeldeinformationen verwenden, um zu versuchen, melden Sie sich mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bei Auswahl von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung, geben Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldename und Kennwort.  
  
10. Wählen Sie im nächsten Dialogfeld **installieren Dienstprogramme Datenbank** *n*, wobei *n* ist die Versionsnummer, und klicken Sie dann auf **Weiter**.  
  
    Die **Sysdb** Datenbank wird erstellt, mit den Tabellen und gespeicherte Prozeduren, die erforderlich sind, für die Datenmigration (mit Server-Seite-Migration Datenmodul) werden in dieser Datenbank erstellt.  
  
11. So installieren Sie die Hilfsprogramme in eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Option **Ja**, und klicken Sie dann auf **Weiter**. Um den Assistenten zu beenden, klicken Sie auf **keine**.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für MySQL-Client &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
