---
title: Bewährte Methoden für die Sicherheit eigenständiger Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- contained database, threats
ms.assetid: 026ca5fc-95da-46b6-b882-fa20f765b51d
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: aef1d046b409a7ebcaa0cb7db8370cf2f61590eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060976"
---
# <a name="security-best-practices-with-contained-databases"></a>Bewährte Methoden für die Sicherheit eigenständiger Datenbanken
  Eigenständige Datenbanken bergen einige eindeutige Risiken. Diese müssen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Administratoren erkannt und gemindert werden. Die meisten Bedrohungen beziehen sich auf die `USER WITH PASSWORD` Authentifizierungsprozess, den die Authentifizierungsgrenze von der [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf Datenbankebene.  
  
## <a name="threats-related-to-users"></a>Bedrohungen in Bezug auf Benutzer  
 Benutzer in einer eigenständigen Datenbank mit der `ALTER ANY USER` Berechtigung, z. B. Mitglieder der der **Db_owner** und **Db_securityadmin** festen Datenbankrollen, können Sie Zugriff auf die Datenbank ohne gewähren die Wissen und Erlaubnis Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrator. Wenn Benutzern der Zugriff auf eine eigenständige Datenbank gewährt wird, vergrößert dies die potenzielle Angriffsfläche der gesamten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz. Administratoren sollten diese Delegierung der Zugriffssteuerung verstehen, und nur mit großer Vorsicht gewähren Benutzern in der eigenständigen Datenbank werden die `ALTER ANY USER` Berechtigung. Alle Datenbankbesitzer verfügen über die `ALTER ANY USER` Berechtigung. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administratoren sollten die Benutzer in einer eigenständigen Datenbank in regelmäßigen Abständen überwachen.  
  
### <a name="accessing-other-databases-using-the-guest-account"></a>Zugreifen auf andere Datenbanken mit dem guest-Konto  
 Datenbankbesitzer und Datenbankbenutzer mit der `ALTER ANY USER`-Berechtigung können Benutzer für die eigenständige Datenbank erstellen. Nach dem Herstellen einer Verbindung mit einer eigenständigen Datenbank in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kann ein Benutzer der eigenständigen Datenbank auf andere Datenbanken in [!INCLUDE[ssDE](../../includes/ssde-md.md)]zugreifen, wenn für die anderen Datenbanken das **guest** -Konto aktiviert ist.  
  
### <a name="creating-a-duplicate-user-in-another-database"></a>Erstellen eines doppelten Benutzers in einer anderen Datenbank  
 Bei einigen Anwendungen muss ein Benutzer u. U. in der Lage sein, auf mehr als eine Datenbank zuzugreifen. Dazu können identische eigenständige Datenbankbenutzer in jeder Datenbank erstellt werden. Verwenden Sie die SID-Option, wenn Sie den zweiten Benutzer mit einem Kennwort erstellen. Im folgenden Beispiel werden zwei identische Benutzer in zwei Datenbanken erstellt.  
  
```  
USE DB1;  
GO  
CREATE USER Carlo WITH PASSWORD = '<strong password>';   
-- Return the SID of the user  
SELECT SID FROM sys.database_principals WHERE name = 'Carlo';  
  
-- Change to the second database  
USE DB2;  
GO  
CREATE USER Carlo WITH PASSWORD = '<same password>', SID = <SID from DB1>;  
GO  
```  
  
 Um eine datenbankübergreifende Abfrage auszuführen, legen Sie die `TRUSTWORTHY` Option für die aufrufende Datenbank. Wenn sich der oben definierte Benutzer (Carlo) beispielsweise in DB1 befindet und `SELECT * FROM db2.dbo.Table1;` ausgeführt werden soll, muss die `TRUSTWORTHY`-Einstellung für die Datenbank DB1 aktiviert sein. Führen Sie den folgenden Code aus, um die `TRUSTWORHTY` auf festlegen.  
  
```  
ALTER DATABASE DB1 SET TRUSTWORTHY ON;  
```  
  
### <a name="creating-a-user-that-duplicates-a-login"></a>Erstellen eines Benutzers, der eine Anmeldung dupliziert  
 Wenn ein Benutzer einer eigenständigen Datenbank mit Kennwort erstellt wird und dabei ein Name angegeben wird, der einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung entspricht und mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung eine Verbindung unter Angabe der eigenständigen Datenbank als Anfangskatalog hergestellt wird, kann mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung keine Verbindung hergestellt werden. Die Verbindung wird als Benutzer der eigenständigen Datenbank mit Kennwortprinzipal für die eigenständige Datenbank und nicht als Benutzer entsprechend der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung ausgewertet. Dies kann einen vorsätzlichen oder versehentlichen Denial of Service-Angriff für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung verursachen.  
  
-   Als Best Practice sollten Mitglieder der festen Serverrolle **sysadmin** erwägen, Verbindungen immer ohne die Option des Anfangskatalogs herzustellen. Dadurch wird die Anmeldung mit der master-Datenbank hergestellt, und Missbrauchsversuche des Anmeldeversuchs durch Datenbankbesitzer sind ausgeschlossen. Der Administrator mit der eigenständigen Datenbank wechseln kann die `USE`  *\<Datenbank >* Anweisung. Sie können auch die Standarddatenbank der Anmeldung auf die eigenständige Datenbank festlegen. Dadurch wird die Anmeldung bei **master**abgeschlossen, und die Anmeldung wird an die eigenständige Datenbank übertragen.  
  
-   Als Best Practice wird empfohlen, keine Benutzer von eigenständigen Datenbanken mit Kennwörtern zu erstellen, die denselben Namen wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldungen aufweisen.  
  
-   Wenn die doppelte Anmeldung vorhanden ist, eine Verbindung herstellen, um die **master** Datenbank ohne einen Anfangskatalog anzugeben, und führen dann die `USE` Befehl aus, um zur eigenständigen Datenbank zu wechseln.  
  
-   Wenn eigenständige Datenbanken vorhanden sind, sollten Benutzer von Datenbanken, die keine eigenständigen Datenbanken darstellen, ohne Verwendung eines Anfangskatalogs oder unter Angabe des Namens einer abhängigen Datenbank als Anfangskatalog eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] herstellen. Dadurch wird vermieden, dass Verbindungen mit der eigenständigen Datenbank hergestellt werden, die von [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Administratoren weniger direkt kontrolliert wird.  
  
### <a name="increasing-access-by-changing-the-containment-status-of-a-database"></a>Ausweiten des Zugriffs durch Ändern des Kapselungsstatus einer Datenbank  
 Anmeldungen, die über die `ALTER ANY DATABASE` Berechtigung, z. B. Mitglieder der der **Dbcreator** feste Serverrolle, und Benutzer in einer nicht enthaltenen Datenbank mit der `CONTROL DATABASE` Berechtigung, z. B. Mitglieder der der **Db_owner**  festen Datenbankrolle "", können die kapselungseinstellung einer Datenbank ändern. Wenn die Kapselungseinstellung einer Datenbank von `NONE` in `PARTIAL` oder `FULL` geändert wird, kann Benutzerzugriff gewährt werden, indem Benutzer von eigenständigen Datenbanken mit Kennwörtern erstellt werden. Dies kann den Zugriff ohne Wissen oder Zustimmung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administratoren ermöglichen. Um zu verhindern, dass Datenbanken eigenständig sind, legen Sie die [!INCLUDE[ssDE](../../includes/ssde-md.md)] `contained database authentication` -Option auf 0. Um Verbindungen von Benutzern eigenständiger Datenbanken mit Kennwörtern für ausgewählte eigenständige Datenbanken zu verhindern, verwenden Sie Anmeldungstrigger, um Anmeldeversuche von Benutzern eigenständiger Datenbanken mit Kennwörtern abzubrechen.  
  
### <a name="attaching-a-contained-database"></a>Anfügen einer eigenständigen Datenbank  
 Durch Anfügen einer eigenständigen Datenbank können Administratoren auch unerwünschten Benutzern den Zugriff auf die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz gewähren. Administrator, die bezüglich dieses Risikos besorgt sind, können die Datenbank im `RESTRICTED_USER`-Modus online schalten, in dem die Authentifizierung für Benutzer eigenständiger Datenbanken mit Kennwörtern verhindert wird. Nur Prinzipale, die durch Anmeldungen autorisiert wurden, können auf [!INCLUDE[ssDE](../../includes/ssde-md.md)]zugreifen.  
  
 Benutzer werden mit den zum Zeitpunkt ihrer Erstellung geltenden Kennwortanforderungen erstellt, und Kennwörter werden bei einer angefügten Datenbank nicht erneut überprüft. Durch das Anfügen einer eigenständigen Datenbank, die unsichere Kennwörter zulässt, an ein System mit einer strengeren Kennwortrichtlinie können Administratoren Kennwörter für [!INCLUDE[ssDE](../../includes/ssde-md.md)]zulassen, die nicht der aktuellen Kennwortrichtlinie entsprechen Administratoren können vermeiden, dass die unsicheren Kennwörter beibehalten werden, indem sie festlegen, dass alle Kennwörter für die angefügte Datenbank zurückgesetzt werden.  
  
### <a name="password-policies"></a>Kennwortrichtlinien  
 Für Kennwörter in einer Datenbank ist u. U. vorgeschrieben, dass es sich um sichere Kennwörter handeln muss, sie müssen jedoch nicht durch strikte Kennwortrichtlinien geschützt sein. Verwenden Sie nach Möglichkeit stets die Windows-Authentifizierung, die Vorteile der umfassenderen Kennwortrichtlinien von Windows zu nutzen.  
  
### <a name="kerberos-authentication"></a>Kerberos-Authentifizierung  
 Benutzer eigenständiger Datenbanken mit Kennwörtern können die Kerberos-Authentifizierung nicht verwenden. Verwenden Sie nach Möglichkeit die Windows-Authentifizierung, um die Vorteile von Windows-Funktionen (z. B. Kerberos) zu nutzen.  
  
### <a name="offline-dictionary-attack"></a>Offlinewörterbuchangriff  
 Die Kennworthashs für Benutzer eigenständiger Datenbanken mit Kennwörtern werden in der eigenständigen Datenbank gespeichert. Jeder Benutzer mit Zugriff auf die Datenbankdateien kann einen Wörterbuchangriff auf die Benutzer eigenständiger Datenbanken mit Kennwörtern in einem nicht überwachten System ausführen. Um diese Bedrohung zu mindern, beschränken Sie den Zugriff auf die Datenbankdateien, oder lassen Sie Verbindungen mit eigenständigen Datenbanken nur mit Windows-Authentifizierung zu.  
  
## <a name="escaping-a-contained-database"></a>Versehen einer eigenständigen Datenbank mit Escapezeichen  
 Wenn eine Datenbank teilweise eigenständig ist, sollten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administratoren die Berechtigungen von Benutzern und Modulen in eigenständigen Datenbanken regelmäßig überwachen.  
  
## <a name="denial-of-service-through-autoclose"></a>Denial-of-Service-Angriff durch AUTO_CLOSE  
 Konfigurieren Sie eigenständige Datenbanken nicht so, dass sie automatisch geschlossen werden. Wenn die Datenbank nach dem Schließen geöffnet wird, um einen Benutzer zu authentifizieren, werden zusätzliche Ressourcen belegt, und dies kann in einem Denial-of-Service-Angriff ausgenutzt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenständige Datenbanken](contained-databases.md)   
 [Migrieren zu einer partiell eigenständigen Datenbank](migrate-to-a-partially-contained-database.md)  
  
  