---
title: Berechtigungen in Parallel Datawarehouse | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die Anforderungen und Optionen zum Verwalten von Berechtigungen für die Datenbank für Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 1ac058e42b8bad4f499210835a1f85c3cc7a08a5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62639519"
---
# <a name="managing-permissions-in-parallel-data-warehouse"></a>Verwalten von Berechtigungen in Parallel Data Warehouse
Dieser Artikel beschreibt die Anforderungen und Optionen zum Verwalten von Berechtigungen für die Datenbank für SQL Server PDW.  
  
## <a name="BackupRestoreBasics"></a>Erste Schritte mit Datenbank-Engine-Berechtigungen  
Datenbank-Engine-Berechtigungen für SQL Server PDW werden auf Serverebene über Anmeldungen, und klicken Sie auf der Datenbankebene über Datenbankbenutzer und benutzerdefinierte Datenbankrollen verwaltet.  
  
**Anmeldungen**  
Anmeldungen sind einzelne Benutzerkonten für die Anmeldung bei der SQL Server PDW. SQL Server PDW unterstützt Anmeldungen mithilfe der Windows-Authentifizierung und SQL Server-Authentifizierung.  Anmeldenamen für die Windows-Authentifizierung können Windows-Benutzer oder Windows-Gruppen aus beliebigen Domänen, der SQL Server PDW vertraut sein. SQL Server-Authentifizierung, Anmeldungen definiert und von SQL Server PDW authentifiziert werden und muss durch Angabe eines Kennworts erstellt werden.  
  
Mitglieder der **Sysadmin** festen Serverrolle (z. B. die **sa** Anmeldung) können mit einer Datenbank verbinden, ohne Sie zu einem Datenbankbenutzer zugeordnet wird. Zugeordnet sind, die **Dbo** Benutzer. Der Besitzer der Datenbank wird auch als zugeordnet der **Dbo** Benutzer.  
  
**Server-Rollen**  
Es gibt vier besondere Serverrollen mit einem Satz von vorkonfigurierten Rollen, die Gruppe von Berechtigungen für auf Serverebene zu bieten. Die **Sysadmin**, **"mediumrc"**, **"largerc"**, und **XLargeRCfixed** Serverrollen sind die einzige Server-Rollen, die derzeit in SQL implementiert PDW-Server. Die **sa** Anmeldung ist das einzige Mitglied der **Sysadmin** -Serverrolle sein, und zusätzliche Anmeldungen können nicht hinzugefügt werden die **Sysadmin** Rolle. Anmeldenamen erteilt werden die **CONTROL SERVER** Berechtigung, die ähnlich, jedoch nicht identisch sein, um die **Sysadmin** -Serverrolle sein. Verwendung [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md) zum Hinzufügen von Mitgliedern, die andere Serverrollen. Benutzerdefinierte Serverrollen werden in SQL Server PDW nicht unterstützt.  
  
**Datenbankbenutzer**  
Anmeldungen erhalten Zugriff auf eine Datenbank durch Erstellen eines Datenbankbenutzers in einer Datenbank, und dieser Datenbankbenutzer einer Anmeldung zugeordnet. Der Datenbank-Benutzername ist in der Regel identisch mit dem Anmeldenamen, obwohl dies nicht so sein muss. Jeder Datenbankbenutzer ist einer einzelnen Anmeldung zugeordnet. Eine Anmeldung kann nur einem Benutzer in einer Datenbank zugeordnet werden, kann aber als Datenbankbenutzer in mehreren unterschiedlichen Datenbanken zugeordnet werden.  
  
**Feste Datenbankrollen**  
Feste Datenbankrollen sind eine Reihe von vorkonfigurierten Rollen, die Gruppe von Berechtigungen auf Datenbankebene bereitstellen. Datenbankbenutzer und benutzerdefinierte Datenbankrollen können mithilfe von festen Datenbankrollen hinzugefügt werden die [Sp_addrolemember](../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) Verfahren. Weitere Informationen zu festen Datenbankrollen, finden Sie unter [feste Datenbankrollen](#fixed-database-roles).  
  
**Benutzerdefinierte Datenbankrollen**  
Benutzer mit der **CREATE ROLE** Berechtigung kann neue benutzerdefinierte Datenbankrollen zur Darstellung von Gruppen von Benutzern mit gemeinsamen Berechtigungen erstellen. In der Regel werden Berechtigungen der gesamten Rolle erteilt oder verweigert, was die Verwaltung und Überwachung von Berechtigungen vereinfacht.  
  
Berechtigungen werden Sicherheitsprinzipalen (Anmeldungen, Benutzer und Rollen) gewährt, mit der **GRANT** Anweisung. Berechtigungen explizit verweigert werden, mithilfe der **Verweigern** Befehl. Entfernt eine zuvor erteilte oder verweigerte Berechtigung mithilfe der **widerrufen** Anweisung. Berechtigungen sind kumulativ, was heißt, dass der Benutzer alle Berechtigungen erhält, die dem Benutzer, der Anmeldung oder den Gruppe erteilt wurden, denen der Benutzer angehört. Durch jedwede Berechtigungsverweigerung werden alle erteilten Berechtigungen außer Kraft gesetzt. <!-- MISSING LINKS (For information, syntax, and available permissions with these commands, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md)).  -->  
  
Das folgende Beispiel zeigt eine allgemeine und empfohlene Methode zum Konfigurieren von Berechtigungen.  
  
1.  Wenn Windows-Authentifizierung verwenden, erstellen Sie einen Anmeldenamen für jeden Windows-Benutzer oder die Windows-Gruppe, die in SQL Server PDW verbunden wird. Wenn Sie SQL Server-Authentifizierung verwenden möchten, erstellen Sie einen Anmeldenamen für jede Person, die in SQL Server PDW eine Verbindung herstellen.  
  
2.  Erstellen Sie einen Datenbankbenutzer für jede Anmeldung, in dem alle erforderlichen Datenbanken.  
  
3.  Erstellen Sie eine oder mehrere benutzerdefinierte Datenbankrollen, jeweils eine ähnliche Funktion darstellen. Beispiele: Finanzanalyst und Vertriebsanalyst.  
  
4.  Fügen Sie eine oder mehrere benutzerdefinierte Datenbankrollen Datenbankbenutzer hinzu.  
  
5.  Erteilen Sie den benutzerdefinierten Datenbankrollen Berechtigungen.  
  
Anmeldungen sind auf Serverebene Objekte und können durch anzeigen aufgeführt [Sys. server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md). Nur die Berechtigungen auf Serverebene können Serverprinzipale gewährt werden.  
  
Benutzer und Datenbankrollen sind auf Datenbankebene Objekte und können durch anzeigen aufgeführt [Sys. database_principals](../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md). Berechtigungen auf Datenbankebene können nur datenbankprinzipale gewährt werden.  
  
## <a name="BackupTypes"></a>Standardberechtigungen  
In der folgenden Liste werden die Standardberechtigungen beschrieben:  
  
-   Wenn ein Anmeldename erstellt wird, durch die using-Direktiven **CREATE LOGIN** -Anweisung, um die Anmeldung empfängt die **CONNECT SQL** ermöglichen die Anmeldung bei der Herstellung einer Verbindung in der SQL Server PDW berechtigt.  
  
-   Wenn ein Datenbankbenutzer erstellt wird, mit der **CREATE USER** -Anweisung, die der Benutzer erhält die **CONNECT ON DATABASE::**_< Database_name >_ Berechtigung ermöglicht das Melden Sie sich mit der Datenbank als ein Benutzer eine Verbindung herstellen.  
  
-   Alle Prinzipale, einschließlich der öffentlichen Rolle, haben standardmäßig keine expliziten oder impliziten Berechtigungen, da implizite Berechtigungen in explizite Berechtigungen geerbt werden. Aus diesem Grund werden, wenn keine expliziten Berechtigungen vorhanden sind, es kann auch sein keine impliziten Berechtigungen.  
  
-   Wird eine Anmeldung über den Besitzer eines Objekts oder die Datenbank, verfügt die Anmeldung immer alle Berechtigungen für das Objekt oder die Datenbank. Die Besitzerrechte sind nicht als explizite Berechtigungen sichtbar. Die **GRANT**, **widerrufen**, und **Verweigern** Anweisungen haben keine Auswirkungen auf den von Besitzberechtigungen. Besitz kann geändert werden, indem die [ALTER AUTHORIZATION](../t-sql/statements/alter-authorization-transact-sql.md) Anweisung.  
  
-   Die sa-Anmeldung verfügt über alle Berechtigungen auf dem Gerät. Ähnlich wie Besitzerrechte, die sa-Berechtigungen können nicht geändert werden und sind nicht als explizite Berechtigungen sichtbar. Die **GRANT**, **widerrufen**, und **Verweigern** Anweisungen haben keine Auswirkungen auf sa-Berechtigungen.  
  
-   Serverrolle PUBLIC keine Berechtigungen in der Standardeinstellung erhält und keine Berechtigungen aus anderen Serverrollen erbt. Die Serverrolle PUBLIC kann die explizite Berechtigungen und zugewiesen werden die **GRANT**, **widerrufen**, und **Verweigern** Anweisungen.  
  
-   Transaktionen erfordern keine Berechtigungen. Alle Prinzipale können ausführen, die **BEGIN TRANSACTION**, **COMMIT**, und **ROLLBACK** Transaction-Befehle. Ein Prinzipal muss jedoch die entsprechenden Berechtigungen zum Ausführen jeder Anweisung innerhalb der Transaktion haben.  
  
-   Die Anweisung **USE** erfordert keine Berechtigungen. Alle Prinzipale können ausführen, die **verwenden** -Anweisung für eine beliebige Datenbank jedoch Zugriff auf eine Datenbank sie einen Benutzerprinzipal in der Datenbank benötigen oder der Gastbenutzer aktiviert sein muss.  
  
### <a name="the-public-role"></a>Die PUBLIC-Rolle  
Alle neuen Anmeldungen der Appliance gehören automatisch an die PUBLIC-Rolle. Die Serverrolle PUBLIC weist folgende Merkmale auf:  
  
-   Die Serverrolle PUBLIC verfügt über keine Berechtigungen in der Standardeinstellung.  
  
-   Alle Prinzipale sind Mitglieder der Serverrolle PUBLIC, und die PUBLIC-Serverrolle ist nicht Mitglied einer anderen Serverrolle.  
  
-   Die Serverrolle PUBLIC kann nicht über implizite Berechtigungen erben. Alle Berechtigungen, die die öffentliche Rolle gewährt werden, müssen explizit erteilt werden.  
  
## <a name="BackupProc"></a>Festlegen von Berechtigungen  
Ob eine Anmeldung die Berechtigung für eine bestimmte Aktion auszuführen sind, hängt von den Berechtigungen erteilt oder verweigert, Anmeldenamen, Benutzer und Rollen, denen der Benutzer Mitglied ist. Auf Serverebene Berechtigungen (wie z. B. **CREATE LOGIN** und **VIEW SERVER STATE**) auf Serverebene Prinzipalen (Anmeldenamen) verfügbar sind. Berechtigungen auf Datenbankebene (z. B. **wählen** aus einer Tabelle oder **EXECUTE** für eine Prozedur) auf Datenbankebene Prinzipale (Benutzer und Datenbankrollen) verfügbar sind.  
  
### <a name="implicit-and-explicit-permissions"></a>Implizite und explizite Berechtigungen  
Eine *explizite Berechtigung* ist eine **GRANT**- oder **DENY**-Berechtigung, die einem Prinzipal durch eine **GRANT**- oder **DENY**-Anweisung zugewiesen wurde. Berechtigungen auf Datenbankebene finden Sie in der [Sys. database_permissions](../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) anzeigen. Auf Serverebene Berechtigungen sind aufgeführt, der [Sys. server_permissions](../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) anzeigen.  
  
Ein *implizite Berechtigung* ist eine **GRANT** oder **Verweigern** Berechtigung, die ein Prinzipal (Anmeldename oder Rolle) geerbt hat. Eine Berechtigung kann auf folgende Weise geerbt werden.  
  
-   Ein Prinzipal kann eine Berechtigung aus einer Rolle erben, wenn der Prinzipal ein Mitglied der Rolle ist, auch wenn der Prinzipal eine explizite keinen **GRANT** oder **Verweigern** Berechtigung.  
  
-   Ein Prinzipal kann eine Berechtigung für ein untergeordnetes Objekt (z. B. eine Tabelle) erben, wenn der Prinzipal eine Berechtigung auf einem der Bereiche übergeordneten Objekte (z. B. das Schema der Tabelle oder die Berechtigung für die gesamte Datenbank) verfügt.  
  
-   Ein Prinzipal kann eine Berechtigung an, dass eine Berechtigung, die eine untergeordnete Berechtigung enthält, erben. Z. B. die **ALTER ANY USER** Berechtigung enthält, die sowohl die **CREATE USER** und **ALTER ON USER::** _<name>_ Berechtigungen.  
  
### <a name="determining-permissions-when-performing-actions"></a>Festlegen von Berechtigungen beim Ausführen von Aktionen  
Der Prozess des bestimmens der Berechtigung zum Zuweisen von einem Prinzipal ist komplex. Die Komplexität tritt auf, wenn implizite Berechtigungen bestimmt wird, da Prinzipale mehrerer Rollen Mitglied können und Berechtigungen über mehrere Ebenen in der Hierarchie für die Rolle übergeben werden können.  
  
Die folgende Liste beschreibt die allgemeinen Regeln zum Festlegen von Berechtigungen:  
  
-   Besitz impliziert Berechtigung.  
  
    Ein Besitzer des Objekts verfügt über alle Berechtigungen für das Objekt. Ebenso verfügt über ein Datenbankbesitzer alle Berechtigungen für die Datenbank und alle Berechtigungen für die Objekte in der Datenbank. Diese Berechtigungen können nicht geändert werden.  
  
-   Berechtigungen können über mehrere Ebenen in der Hierarchie der serverrollenmitgliedschaften geerbt werden.  
  
    Nehmen wir beispielsweise an, dass Sie die folgende Situation haben:  
  
    -   Anmeldung David ist ein Mitglied der Datenbankrolle PerfAnalysts.  
  
    -   PerfAnalysts ist Mitglied der Datenbankrolle "Produktion".  
  
    -   David und PerfAnalysts verfügen über keine **wählen** -Berechtigung für die Customer-Tabelle. Die Berechtigung wurde widerrufen oder nie explizit erteilt.  
  
    -   Produktion hat **wählen** -Berechtigung für die Customer-Tabelle.  
  
    In diesem Fall übernimmt PerfAnalysts **GRANT** -Berechtigung für die Customer-Tabelle aus der Produktion und David erben **GRANT** -Berechtigung für die Customer-Tabelle aus der Produktion.  
  
-   **DENY** überschreibt **GRANT** Wenn Berechtigungen in Konflikt stehen.  
  
    Nehmen wir beispielsweise an, die Anmeldung David verfügt über keine Berechtigungen für die Customer-Tabelle und ist Mitglied von zwei Datenbankrollen-dbgroup1, dem **Verweigern** -Berechtigung für die Customer-Tabelle und dbgroup2, dem **gewähren** Berechtigung für die Customer-Tabelle. In diesem Fall David übernimmt die **Verweigern** -Berechtigung für die Customer-Tabelle. Dies ist der Fall, ob die Rollen ihrer Berechtigungen explizit oder implizit erzielt.  
  
### <a name="auditing-permissions"></a>Überwachung von Berechtigungen  
Überprüfen Sie die Berechtigungen eines Benutzers Folgendes, um zu ermitteln.  
  
-   Führen Sie die folgende Abfrage aus, um zu bestimmen, welche Anmeldungen Systemadministratoren sind.  
  
    ```sql  
    SELECT SPLogins.name, 'is a member of ', SPRoles.name   
    FROM sys.server_role_members AS SRM   
    JOIN sys.server_principals AS SPRoles   
        ON SRM.role_principal_id = SPRoles.principal_id   
    JOIN sys.server_principals AS SPLogins   
        ON SRM.member_principal_id = SPLogins.principal_id;  
    ```  
  
-   Führen Sie die folgende Abfrage aus, um zu bestimmen, welche Anmeldungen explizite Berechtigungen gewährt wurden.  
  
    ```sql  
    SELECT name, 'has the ', state_desc , permission_name, ' permission'  
    FROM sys.server_permissions AS SP  
    JOIN sys.server_principals AS SPRoles   
        ON SP.grantee_principal_id = SPRoles.principal_id;  
    ```  
  
-   Führen Sie die folgende Abfrage in einer Benutzerdatenbank aus, um zu bestimmen, welche Datenbankbenutzer Mitglied einer Datenbankrolle an.  
  
    ```sql  
    SELECT DPUsers.name, 'is a member of ', DPRoles.name    
    FROM sys.database_role_members AS DRM  
    JOIN sys.database_principals AS DPRoles   
        ON DRM.role_principal_id = DPRoles.principal_id  
    JOIN sys.database_principals AS DPUsers  
        ON DRM.member_principal_id = DPUsers.principal_id;  
    ```  
  
-   Führen Sie die folgende Abfrage in einer Benutzerdatenbank aus, um zu bestimmen, Datenbankbenutzer und Rollen gewährt oder bestimmte Berechtigungen verweigert wurden. Sie müssen mit Abfrage zusätzliche Ansichten wie z. B. sys.objects und sys.schemas, um die Elemente beschrieben, mit der Major_id zu identifizieren.  
  
    ```sql  
    SELECT DPUsers.name, 'has the ', permission_name,   
    'permission on the item described as class = ', class, 'id = ', major_id  
    FROM sys.database_permissions AS DP  
    JOIN sys.database_principals AS DPUsers  
        ON DP.grantee_principal_id = DPUsers.principal_id;  
    ```  
  
## <a name="RestoreProc"></a>Bewährte Methoden für die Datenbank-Berechtigungen  
  
-   Erteilen Sie Berechtigungen auf der höchsten granularen Ebene, der möglich ist. Erteilen von Berechtigungen in der Tabelle oder Sicht-Berechtigungen auf Serverebene können nicht mehr beherrschbar sein. Erteilen von Berechtigungen auf Datenbankebene können aber sein zu toleranten. Wenn die Datenbank mit Schemas zum Arbeitsaufgaben Grenzen definiert ausgelegt ist, vielleicht ist das Erteilen von Berechtigungen für das Schema einen geeigneten Kompromiss zwischen der Tabellenebene und Datenbankebene.  
  
-   Erteilen Sie Berechtigungen für Rollen statt für Benutzer oder Anmeldenamen ein. Verwalten von Berechtigungen mit Rollen, sodass Benutzer nicht erleichtert Ihnen schnell gewährt oder widerrufen einen Satz von Berechtigungen für einen Benutzer oder die Anmeldung, indem Sie sie in oder aus der Rolle zu verschieben. Wenn eine Funktion von einer Person zu einem anderen übertragen, können die Berechtigungen auf Rollenebene während der Rolle mitgliedschaftsänderungen unverändert.  
  
-   Erteilen Sie Berechtigungen für Rollen, die basierend auf der Funktion, und klicken Sie auf höherer Ebene Funktionen von Gruppen, die die Funktion tätigkeitsrollen basierend auf der Unternehmensportal-Gruppe, die die Aktionen zu kombinieren.  
  
-   Jeder Benutzer sollte einen eindeutigen Anmeldenamen verfügen. Dürfen Sie Benutzer keine Anmeldungen freigeben. Bereitstellen eines für jeden Benutzer einen Audit-Trail gewährleistet und vereinfacht die berechtigungsverwaltung.  
  
## <a name="fixed-database-roles"></a>Feste Datenbankrollen
SQL Server bietet vorkonfiguriert, dass (feste) auf Datenbankebene-Rollen, denen Sie die Berechtigungen auf einem Server verwalten können. Die vorkonfigurierten Rollen wurden behoben, insofern Sie nicht die Berechtigungen für diese ändern können. Benutzerdefinierte Datenbankrollen können auch erstellt werden. Sie können die benutzerdefinierte Datenbankrollen zugewiesenen Berechtigungen ändern.  
  
Rollen sind Sicherheitsprinzipale, in denen andere Prinzipale gruppieren. Datenbankrollen werden datenbankweiten Geltungsbereich der Berechtigungen. Datenbankbenutzern und anderen Datenbankrollen können als Mitglieder der Datenbankrollen hinzugefügt werden. Die festen Datenbankrollen können nicht miteinander hinzugefügt werden. (*Rollen* entsprechen den *Gruppen* im Betriebssystem Windows.)  
  
Es gibt 9 festen Datenbankrollen.  
  
-   **db_owner**  
  
-   **db_securityadmin**  
  
-   **db_accessadmin**  
  
-   **db_backupoperator**  
  
-   **db_ddladmin**  
  
-   **db_datawriter**  
  
-   **db_datareader**  
  
-   **db_denydatawriter**  
  
-   **db_denydatareader**  
  
### <a name="permissions-of-the-fixed-database-roles"></a>Berechtigungen der festen Datenbankrollen  
Das System mit festen Serverrollen und feste Datenbankrollen ist die einem älteren System, das in der die Prüfung erzeugt. Feste Rollen werden weiterhin unterstützt und sind nützlich in Umgebungen, in denen es nur wenige Benutzer und die sicherheitsanforderungen sind einfach. Ab SQL Server 2005 ist wurde eine weitere ausführliche Informationen zu den gewähren der Berechtigung erstellt. Dieses neue System ist genauer, wodurch viele weitere Optionen für gewähren und Verweigern von Berechtigungen bereitstellen. Die zusätzliche Komplexität des Systems eine feiner abgestimmte macht es schwieriger, erfahren, aber die meisten Unternehmenssysteme sollten Berechtigungen gewähren anstatt die festen Rollen auf. <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md). -->Das folgende Diagramm zeigt die Berechtigungen, die einzelnen festen Datenbankrollen zugeordnet sind. Alle Berechtigungen in dieser SQL Server-Grafik sind nicht verfügbar (oder erforderlichen) im APS.  
  
![APS-Sicherheit, die festen Datenbankrollen](./media/pdw-permissions/APS_security_fixed_db_roles.png "APS_security_fixed_db_roles")  
  
### <a name="related-content"></a>Verwandte Inhalte  
  
-   Erstellen von benutzerdefinierten Rollen finden Sie [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md).  
  
  
## <a name="fixed-server-roles"></a>Feste Serverrollen
Feste Serverrollen werden automatisch von SQL Server erstellt. SQL Server PDW verfügt über eine eingeschränkte Implementierung von SQL Server, die festen Serverrollen. Nur die **Sysadmin** und **öffentliche** benutzeranmeldungen als Mitglieder haben. Die **Setupadmin** und **Dbcreator** Rollen werden intern von SQL Server PDW verwendet. Zusätzliche Member können nicht hinzugefügt oder aus keiner Rolle entfernt werden.  
  
### <a name="sysadmin-fixed-server-role"></a>Sysadmin feste Serverrolle  
Mitglieder der festen Serverrolle **sysadmin** können alle Aktivitäten auf dem Server ausführen. Die **sa** Anmeldung ist das einzige Mitglied der **Sysadmin** -Serverrolle sein. Zusätzliche Anmeldungen können nicht hinzugefügt werden, um die **Sysadmin** -Serverrolle sein. Das Erteilen der Berechtigung **CONTROL SERVER** gleicht der Mitgliedschaft in der festen Serverrolle **sysadmin**. Im folgenden Beispiel wird die **CONTROL SERVER** Berechtigung für einen Anmeldenamen mit dem Namen Fay.  
  
```sql  
USE master;  
GO  
GRANT CONTROL SERVER TO Fay;  
```  
  
> [!IMPORTANT]  
> Die **CONTROL SERVER** Berechtigung bietet nahezu vollständige Kontrolle über SQL Server PDW. Wann immer möglich, geben Sie stattdessen fein abgestimmte Berechtigungen zu Anmeldungen auf. Betrachten Sie beispielsweise das Gewähren der **VIEW SERVER STATE**, **ALTER ANY LOGIN**, **VIEW ANY DATABASE**, oder **CREATE ANY DATABASE** Berechtigungen.  
  
### <a name="public-server-role"></a>Serverrolle Public  
Jede Anmeldung, die eine Verbindung, in SQL Server PDW herstellen kann ist ein Mitglied der **öffentliche** -Serverrolle. Alle Anmeldungen, erben die Berechtigungen für **öffentliche** auf ein beliebiges Objekt. Weisen Sie nur **öffentliche** Berechtigungen für ein Objekt, wenn das Objekt, das für alle Benutzer verfügbar sein soll. Sie können nicht geändert, Mitgliedschaft in der **öffentliche** Rolle.  
  
> [!NOTE]  
> **Öffentliche** wird anders implementiert als andere Rollen. Da alle Serverprinzipale Member von öffentlichen, die Mitgliedschaft sind die **öffentliche** -Rolle ist nicht aufgeführt, der **Sys. server_role_members** DMV.  
  
### <a name="fixed-server-roles-vs-granting-permissions"></a>Feste Serverrollen im Vergleich zu Erteilen von Berechtigungen  
Das System mit festen Serverrollen und feste Datenbankrollen ist die einem älteren System, das in der die Prüfung erzeugt. Feste Rollen werden weiterhin unterstützt und sind nützlich in Umgebungen, in denen es nur wenige Benutzer und die sicherheitsanforderungen sind einfach. Ab SQL Server 2005 ist wurde eine weitere ausführliche Informationen zu den gewähren der Berechtigung erstellt. Dieses neue System ist genauer, wodurch viele weitere Optionen für gewähren und Verweigern von Berechtigungen bereitstellen. Die zusätzliche Komplexität des Systems eine feiner abgestimmte macht es schwieriger, erfahren, aber die meisten Unternehmenssysteme sollten Berechtigungen gewähren anstatt die festen Rollen auf. <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  -->  
  
## <a name="related-topics"></a>Verwandte Themen  
  
- [Erteilen von Berechtigungen](grant-permissions.md)

<!-- MISSING LINKS
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->

