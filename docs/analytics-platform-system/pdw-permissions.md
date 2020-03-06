---
title: Berechtigungen
description: In diesem Artikel werden die Anforderungen und Optionen für die Verwaltung von Daten Bank Berechtigungen für parallele Data Warehouse beschrieben.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 499ac56d8a462f62dac92b97654a9ace12bd356e
ms.sourcegitcommit: ff1bd69a8335ad656b220e78acb37dbef86bc78a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78339571"
---
# <a name="managing-permissions-in-parallel-data-warehouse"></a>Paralleles Verwalten von Berechtigungen Data Warehouse
In diesem Artikel werden die Anforderungen und Optionen für die Verwaltung von Daten Bank Berechtigungen für SQL Server PDW beschrieben.

## <a name="BackupRestoreBasics"></a>Grundlagen zu Datenbank-Engine Berechtigungen
Datenbank-Engine Berechtigungen auf SQL Server PDW werden auf Server Ebene über Anmeldungen und auf Datenbankebene über Datenbankbenutzer und benutzerdefinierte Daten bankrollen verwaltet.

**Anmeldungen** Anmeldungen sind einzelne Benutzerkonten für die Anmeldung beim SQL Server PDW. SQL Server PDW unterstützt Anmeldungen unter Verwendung der Windows-Authentifizierung und SQL Server Authentifizierung.  Windows-Authentifizierungs Anmeldungen können Windows-Benutzer oder Windows-Gruppen aus jeder Domäne sein, der von SQL Server PDW vertraut wird. SQL Server Authentifizierungs Anmeldungen werden von SQL Server PDW definiert und authentifiziert und müssen durch Angabe eines Kennworts erstellt werden.

Mitglieder der festen Server Rolle **sysadmin** (z. b. der **sa** -Anmeldung) können eine Verbindung mit einer Datenbank herstellen, ohne dass Sie einem Datenbankbenutzer zugeordnet werden müssen. Sie werden dem Benutzer **dbo** zugeordnet. Der Besitzer der Datenbank wird auch als **dbo** -Benutzer zugeordnet.

**Server Rollen** Es gibt vier spezielle Server Rollen mit einem Satz vorkonfigurierter Rollen, die eine bequeme Gruppe von Berechtigungen auf Serverebene bereitstellen. Die Server Rollen " **sysadmin**", " **mediumrc**", " **largerc**" und " **xlargercfixed** " sind die einzige Server Rolle, die derzeit in SQL Server PDW implementiert ist. Der **sa** -Anmelde Name ist das einzige Mitglied der festen Server Rolle **sysadmin** , und der **sysadmin** -Rolle können keine zusätzlichen Anmeldungen hinzugefügt werden. Anmeldungen kann die **Control Server** -Berechtigung erteilt werden, die in der festen Server Rolle **sysadmin** ähnlich, aber nicht identisch ist. Verwenden Sie [Alter Server Role](../t-sql/statements/alter-server-role-transact-sql.md) , um Mitglieder zu den anderen Server Rollen hinzuzufügen. Der SQL Server PDW unterstützt keine benutzerdefinierten Server Rollen.

**Datenbankbenutzer** Anmeldungen wird der Zugriff auf eine Datenbank gewährt, indem ein Datenbankbenutzer in einer Datenbank erstellt und dieser Datenbankbenutzer einer Anmeldung zugeordnet wird. Der Datenbank-Benutzername ist in der Regel identisch mit dem Anmeldenamen, obwohl dies nicht so sein muss. Jeder Datenbankbenutzer ist einer einzelnen Anmeldung zugeordnet. Eine Anmeldung kann nur einem Benutzer in einer Datenbank zugeordnet werden, kann aber als Datenbankbenutzer in mehreren unterschiedlichen Datenbanken zugeordnet werden.

**Fixed-Daten bankrollen** Bei fester Daten bankrollen handelt es sich um einen Satz vorkonfigurierter Rollen, die eine bequeme Gruppe von Berechtigungen auf Datenbankebene bereitstellen Datenbankbenutzer und benutzerdefinierte Daten bankrollen können den festgelegten Daten bankrollen mithilfe des [sp_addrolemember](../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) Verfahrens hinzugefügt werden. Weitere Informationen zu festgelegten Daten bankrollen finden Sie unter [Fixed Database Rollen](#fixed-database-roles).

**Benutzerdefinierte Daten bankrollen** Benutzer mit der Berechtigung " **Rolle erstellen** " können neue benutzerdefinierte Daten bankrollen erstellen, um Gruppen von Benutzern mit gemeinsamen Berechtigungen darzustellen. In der Regel werden Berechtigungen der gesamten Rolle erteilt oder verweigert, was die Verwaltung und Überwachung von Berechtigungen vereinfacht.

Berechtigungen werden Sicherheits Prinzipale (Anmeldungen, Benutzern und Rollen) mithilfe der **Grant** -Anweisung erteilt. Berechtigungen werden mithilfe des **Deny** -Befehls explizit verweigert. Eine zuvor erteilte oder verweigerte Berechtigung wird mithilfe der **widerrufen** -Anweisung entfernt. Berechtigungen sind kumulativ, was heißt, dass der Benutzer alle Berechtigungen erhält, die dem Benutzer, der Anmeldung oder den Gruppe erteilt wurden, denen der Benutzer angehört. Durch jedwede Berechtigungsverweigerung werden alle erteilten Berechtigungen außer Kraft gesetzt. <!-- MISSING LINKS (For information, syntax, and available permissions with these commands, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md)).  -->

Das folgende Beispiel zeigt eine allgemeine und empfohlene Methode zum Konfigurieren von Berechtigungen.

1.  Wenn Sie die Windows-Authentifizierung verwenden, erstellen Sie einen Anmelde Namen für jeden Windows-Benutzer oder jede Windows-Gruppe, der eine Verbindung mit SQL Server PDW Wenn Sie SQL Server Authentifizierung verwenden, erstellen Sie eine Anmeldung für jede Person, die eine Verbindung mit SQL Server PDW herstellt.

2.  Erstellen Sie einen Datenbankbenutzer für jede Anmeldung in allen erforderlichen Datenbanken.

3.  Erstellen Sie eine oder mehrere benutzerdefinierte Daten bankrollen, die jeweils eine ähnliche Funktion darstellen. Beispiele: Finanzanalyst und Vertriebsanalyst.

4.  Fügen Sie einer oder mehreren benutzerdefinierten Daten bankrollen Datenbankbenutzer hinzu.

5.  Erteilen Sie den benutzerdefinierten Datenbankrollen Berechtigungen.

Anmeldungen sind Objekte auf Serverebene und können durch Anzeigen von [sys. server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)aufgelistet werden. Server Prinzipale können nur Berechtigungen auf Serverebene erteilt werden.

Benutzer und Daten bankrollen sind Objekte auf Datenbankebene und können durch Anzeigen von [sys. database_principals](../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)aufgelistet werden. Daten Bank Prinzipale können nur Berechtigungen auf Datenbankebene erteilt werden.

## <a name="BackupTypes"></a>Standardberechtigungen
In der folgenden Liste werden die Standardberechtigungen beschrieben:

-   Wenn eine Anmeldung von using-Direktiven **Create Login** -Anweisung erstellt wird, erhält der Anmelde Name die **Connect SQL** -Berechtigung, sodass der Anmelde Name eine Verbindung mit dem SQL Server PDW herstellen kann.

-   Wenn ein Datenbankbenutzer mithilfe der **Create User** -Anweisung erstellt wird, erhält der Benutzer die Berechtigung **Connect on Database::** _<database_name>_ , sodass der Anmelde Name als Benutzer eine Verbindung mit dieser Datenbank herstellen kann.

-   Alle Prinzipale, einschließlich der public-Rolle, haben standardmäßig keine expliziten oder impliziten Berechtigungen, da implizite Berechtigungen von expliziten Berechtigungen geerbt werden. Wenn keine expliziten Berechtigungen vorhanden sind, können daher auch keine impliziten Berechtigungen vorhanden sein.

-   Wenn ein Anmelde Name zum Besitzer eines Objekts oder einer Datenbank wird, verfügt der Anmelde Name immer über alle Berechtigungen für das Objekt oder die Datenbank. Die Besitz Berechtigungen sind nicht als explizite Berechtigungen sichtbar. Die **Grant**- **,** Revo-und **Deny** -Anweisungen haben keine Auswirkung auf Besitz Berechtigungen. Der Besitz kann mithilfe der [ALTER AUTHORIZATION](../t-sql/statements/alter-authorization-transact-sql.md) -Anweisung geändert werden.

-   Der sysadmin-Anmeldename verfügt über alle Berechtigungen auf dem Gerät. Ähnlich wie Besitzerrechte, können sa-Berechtigungen nicht geändert werden und sind nicht als explizite Berechtigungen sichtbar. Die **Grant**- **,** Revo-und **Deny** -Anweisungen haben keine Auswirkung auf SA-Berechtigungen.

-   Die öffentliche Server Rolle erhält standardmäßig keine Berechtigungen und erbt keine Berechtigungen von anderen Server Rollen. Der Public Server-Rolle können explizite Berechtigungen mit den Anweisungen **Grant**, **Widerruf**und **Deny** erteilt werden.

-   Transaktionen erfordern keine Berechtigungen. Alle Prinzipale können die Befehle **BEGIN TRANSACTION**, **Commit**und **Rollback** Transaction ausführen. Ein Prinzipal muss jedoch über die entsprechenden Berechtigungen verfügen, um jede Anweisung innerhalb der Transaktion auszuführen.

-   Die Anweisung **USE** erfordert keine Berechtigungen. Alle Prinzipale können die **use** -Anweisung für eine beliebige Datenbank ausführen. für den Zugriff auf eine Datenbank müssen Sie jedoch über einen Benutzer Prinzipal in der Datenbank verfügen, oder der Gastbenutzer muss aktiviert sein.

### <a name="the-public-role"></a>Die public-Rolle
Alle neuen Appliance-Anmeldungen gehören automatisch zur public-Rolle. Die öffentliche Server Rolle weist die folgenden Eigenschaften auf:

-   Die öffentliche Server Rolle hat standardmäßig keine Berechtigungen.

-   Alle Prinzipale sind Mitglieder der öffentlichen Server Rolle, und die öffentliche Server Rolle ist nicht Mitglied einer anderen Server Rolle.

-   Die öffentliche Server Rolle kann keine impliziten Berechtigungen erben. Alle Berechtigungen, die der public-Rolle erteilt werden, müssen explizit erteilt werden.

## <a name="BackupProc"></a>Festlegen von Berechtigungen
Ob ein Anmelde Name über die Berechtigung zum Durchführen einer bestimmten Aktion verfügt, hängt von den Berechtigungen ab, die für die Anmeldung, den Benutzer und die Rollen erteilt oder verweigert werden, bei denen der Benutzer Mitglied ist. Berechtigungen auf Serverebene (z. b. **Create Login** und **View Server State**) sind für Prinzipale auf Serverebene (Anmeldungen) verfügbar. Berechtigungen auf Datenbankebene (z. b. **Select** from a Table oder **Execute** for a Procedure) sind für Prinzipale auf Datenbankebene (Benutzer und Daten bankrollen) verfügbar.

### <a name="implicit-and-explicit-permissions"></a>Implizite und explizite Berechtigungen
Eine *explizite Berechtigung* ist eine **GRANT**- oder **DENY**-Berechtigung, die einem Prinzipal durch eine **GRANT**- oder **DENY**-Anweisung zugewiesen wurde. Berechtigungen auf Datenbankebene werden in der [sys. database_permissions](../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) -Sicht aufgelistet. Berechtigungen auf Server Ebene werden in der [sys. server_permissions](../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) -Sicht aufgelistet.

Eine *implizite Berechtigung* ist eine **Grant** -oder **Deny** -Berechtigung, die ein Prinzipal (-Anmelde Name oder Server Rolle) geerbt hat. Eine Berechtigung kann auf folgende Weise geerbt werden.

-   Ein Prinzipal kann eine Berechtigung von einer Rolle erben, wenn der Prinzipal ein Mitglied der Rolle ist, auch wenn der Prinzipal nicht über eine explizite **Grant** -oder **Deny** -Berechtigung verfügt.

-   Ein Prinzipal kann eine Berechtigung für ein untergeordnetes Objekt (z. b. eine Tabelle) erben, wenn der Prinzipal über eine Berechtigung für eines der übergeordneten Objekte (z. b. das Schema der Tabelle oder die Berechtigung für die gesamte Datenbank) verfügt.

-   Ein Prinzipal kann eine Berechtigung erben, indem er über eine Berechtigung verfügt, die eine untergeordnete Berechtigung enthält. Die Berechtigung **ALTER ANY User** umfasst z. b. die **Berechtigungen CREATE User** und **Alter on User::** _<name>_ .

### <a name="determining-permissions-when-performing-actions"></a>Festlegen von Berechtigungen beim Ausführen von Aktionen
Der Prozess der Bestimmung, welche Berechtigung einem Prinzipal zugewiesen werden soll, ist komplex. Die Komplexität tritt auf, wenn implizite Berechtigungen festgelegt werden, da Prinzipale Mitglieder mehrerer Rollen sein können und Berechtigungen über mehrere Ebenen in der Rollen Hierarchie übermittelt werden können.

In der folgenden Liste werden allgemeine Regeln zum Bestimmen von Berechtigungen beschrieben:

-   Der Besitz impliziert die Berechtigung.

    Ein Objektbesitzer verfügt über alle Berechtigungen für das Objekt. Ebenso verfügt ein Datenbankbesitzer über alle Berechtigungen für die Datenbank und über alle Berechtigungen für die Objekte in der Datenbank. Diese Berechtigungen können nicht geändert werden.

-   Berechtigungen können über mehrere Ebenen in der Hierarchie der Server Rollen Mitgliedschaften hinweg geerbt werden.

    Angenommen, Sie haben folgende Situation:

    -   Login David ist ein Mitglied der Daten Bank Rolle perfanalysts.

    -   Perfanalysts ist ein Mitglied der Daten bankrollen Produktion.

    -   David und perfanalysts haben keine **Select** -Berechtigung für die Customer-Tabelle. Die Berechtigung wurde entweder widerrufen oder nie explizit erteilt.

    -   Die Produktion verfügt über die **Select** -Berechtigung für die Customer-Tabelle.

    In diesem Fall erben perfanalysts die **Grant** -Berechtigung für die Tabelle "Customer" aus der Produktionsumgebung, und David erbt die **Grant** -Berechtigung für die Tabelle "Customer" aus der Produktionsumgebung.

-   **Deny** überschreibt **Grant** , wenn Berechtigungs Konflikte auftreten.

    Angenommen, Login David hat keine Berechtigungen für die Customer-Tabelle und ist Mitglied von zwei Daten bankrollen dbgroup1, die die **Deny** -Berechtigung für die Customer-Tabelle und dbgroup2 haben, die über die **Grant** -Berechtigung für die Customer-Tabelle verfügt. In diesem Fall erbt David die **Deny** -Berechtigung für die Customer-Tabelle. Dies ist der Fall, wenn die Rollen Ihre Berechtigungen explizit oder implizit erhalten haben.

### <a name="auditing-permissions"></a>Überwachungs Berechtigungen
Überprüfen Sie Folgendes, um die Berechtigungen eines Benutzers zu untersuchen.

-   Führen Sie die folgende Abfrage aus, um zu bestimmen, welche Anmeldungen Systemadministratoren sind.

    ```sql
    SELECT SPLogins.name, 'is a member of ', SPRoles.name 
    FROM sys.server_role_members AS SRM 
    JOIN sys.server_principals AS SPRoles 
        ON SRM.role_principal_id = SPRoles.principal_id 
    JOIN sys.server_principals AS SPLogins 
        ON SRM.member_principal_id = SPLogins.principal_id;
    ```

-   Führen Sie die folgende Abfrage aus, um zu bestimmen, welchen Anmeldungen explizite Berechtigungen erteilt wurden.

    ```sql
    SELECT name, 'has the ', state_desc , permission_name, ' permission'
    FROM sys.server_permissions AS SP
    JOIN sys.server_principals AS SPRoles 
        ON SP.grantee_principal_id = SPRoles.principal_id;
    ```

-   Führen Sie die folgende Abfrage in einer Benutzerdatenbank aus, um zu bestimmen, welche Datenbankbenutzer Mitglieder einer Daten Bank Rolle sind.

    ```sql
    SELECT DPUsers.name, 'is a member of ', DPRoles.name  
    FROM sys.database_role_members AS DRM
    JOIN sys.database_principals AS DPRoles 
        ON DRM.role_principal_id = DPRoles.principal_id
    JOIN sys.database_principals AS DPUsers
        ON DRM.member_principal_id = DPUsers.principal_id;
    ```

-   Führen Sie die folgende Abfrage in einer Benutzerdatenbank aus, um zu bestimmen, welchen Datenbankbenutzern und-Rollen bestimmte Berechtigungen erteilt oder verweigert wurden. Sie müssen zusätzliche Sichten Abfragen, wie z. b. sys. Objects und sys. Schemas, um die mit dem major_id beschriebenen Elemente zu identifizieren.

    ```sql
    SELECT DPUsers.name, 'has the ', permission_name, 
    'permission on the item described as class = ', class, 'id = ', major_id
    FROM sys.database_permissions AS DP
    JOIN sys.database_principals AS DPUsers
        ON DP.grantee_principal_id = DPUsers.principal_id;
    ```

## <a name="RestoreProc"></a>Bewährte Methoden für Daten Bank Berechtigungen

-   Erteilen Sie Berechtigungen auf der differenzierteren Ebene, die praktikabel ist. Das Erteilen von Berechtigungen auf der Tabellen-oder Sicht Ebene kann möglicherweise nicht mehr verwaltet werden. Das Erteilen von Berechtigungen auf Datenbankebene ist jedoch möglicherweise zu nicht zulässig. Wenn die Datenbank mit Schemas zum Definieren von Arbeits Begrenzungen entworfen wurde, ist die Erteilung der Berechtigung für das Schema möglicherweise eine angemessene Gefährdung zwischen der Tabellenebene und der Datenbankebene.

-   Erteilen von Berechtigungen für Rollen anstelle von Benutzern oder Anmeldungen. Das Verwalten von Rechten mithilfe von Rollen anstelle von Benutzern erleichtert das schnelle gewähren oder widerrufen eines Berechtigungs Satzes für einen Benutzer oder eine Anmeldung, indem Sie Sie in die oder aus der Rolle verschieben. Wenn eine Funktion von einer Person an eine andere weitergeleitet wird, können die Berechtigungen auf Rollen Ebene unverändert bleiben, während die Rollen Mitgliedschaft geändert wird.

-   Erteilen von Berechtigungen für Rollen, die auf der Auftrags Funktion basieren, und in Gruppen Rollen höherer Ebene, die die Auftrags Funktions Rollen basierend auf der Unternehmensgruppe, die die Aktionen ausführt, kombinieren.

-   Jeder Endbenutzer sollte über eine eindeutige Anmeldung verfügen. Gestatten Sie Benutzern nicht das Freigeben von Anmeldungen. Durch die Bereitstellung eines Anmelde namens für jeden Benutzer wird ein Audit-Trail und die Berechtigungs Verwaltung vereinfacht.

## <a name="fixed-database-roles"></a>Feste Datenbankrollen
SQL Server stellt vorkonfigurierte (fixierte) Rollen auf Datenbankebene bereit, um Sie bei der Verwaltung der Berechtigungen auf einem Server zu unterstützen. Die vorkonfigurierten Rollen wurden in korrigiert, sodass Sie die Ihnen zugewiesenen Berechtigungen nicht ändern können. Benutzerdefinierte Daten bankrollen können auch erstellt werden. Sie können die Berechtigungen ändern, die benutzerdefinierten Daten bankrollen zugewiesen sind.

Rollen sind Sicherheits Prinzipale, die andere Prinzipale gruppieren. Daten bankrollen sind im Berechtigungs Bereich Daten Bank weit. Datenbankbenutzer und andere Daten bankrollen können als Mitglieder von Daten bankrollen hinzugefügt werden. Die fixierten Daten bankrollen können nicht einander hinzugefügt werden. (*Rollen* entsprechen den *Gruppen* im Betriebssystem Windows.)

Es gibt 9 Daten bankrollen.

-   **db_owner**

-   **db_securityadmin**

-   **db_accessadmin**

-   **db_backupoperator**

-   **db_ddladmin**

-   **db_datawriter**

-   **db_datareader**

-   **db_denydatawriter**

-   **db_denydatareader**

### <a name="permissions-of-the-fixed-database-roles"></a>Berechtigungen der Fixed-Daten bankrollen
Das System fester Server Rollen und fester Daten bankrollen ist ein Legacy System, das in den 80er Jahren entstanden ist. Behobene Rollen werden weiterhin unterstützt und sind in Umgebungen nützlich, in denen es nur wenige Benutzer gibt und die Sicherheitsanforderungen einfach sind. Ab SQL Server 2005 wurde ein ausführlicheres System zum Erteilen der Berechtigung erstellt. Dieses neue System ist präziser und bietet viele weitere Optionen für das erteilen und Verweigern von Berechtigungen. Die zusätzliche Komplexität des differenzierteren Systems erschwert das Erlernen, aber die meisten Unternehmenssysteme sollten Berechtigungen erteilen, anstatt die Fixed-Rollen zu verwenden. <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md). -->Das folgende Diagramm zeigt die Berechtigungen, die jeder festgelegten Daten Bank Rolle zugeordnet sind. Alle Berechtigungen in dieser SQL Server Grafik sind in APS nicht verfügbar (oder erforderlich).

![feste APS-Sicherheitsdatenbankrollen](./media/pdw-permissions/APS_security_fixed_db_roles.png "APS_security_fixed_db_roles")

### <a name="related-content"></a>Verwandte Inhalte

-   Informationen zum Erstellen von benutzerdefinierten Rollen finden Sie unter [Create Role](../t-sql/statements/create-role-transact-sql.md).


## <a name="fixed-server-roles"></a>Feste Serverrollen
Festes Server Rollen werden automatisch von SQL Server erstellt. SQL Server PDW verfügt über eine begrenzte Implementierung SQL Server fester Server Rollen. Nur " **sysadmin** " und " **Public** " verfügen über Benutzeranmeldungen als Mitglieder. Die Rollen **festen setupadmin** und **dbcreator** werden intern von SQL Server PDW verwendet. Weitere Mitglieder können keiner Rolle hinzugefügt oder entfernt werden.

### <a name="sysadmin-fixed-server-role"></a>festen Server Rolle "sysadmin"
Mitglieder der festen Serverrolle **sysadmin** können alle Aktivitäten auf dem Server ausführen. Der **sa** -Anmelde Name ist das einzige Mitglied der festen Server Rolle **sysadmin** . Zusätzliche Anmeldungen können nicht der festen Server Rolle **sysadmin** hinzugefügt werden. Das Erteilen der Berechtigung **CONTROL SERVER** gleicht der Mitgliedschaft in der festen Serverrolle **sysadmin**. Im folgenden Beispiel wird die **Control Server** -Berechtigung für einen Anmelde Namen mit dem Namen Fay erteilt.

```sql
USE master;
GO
GRANT CONTROL SERVER TO Fay;
```

> [!IMPORTANT]
> Die **Control Server** -Berechtigung bietet eine fast umfassende Kontrolle über SQL Server PDW. Stellen Sie, wenn möglich, stattdessen präzisetere Berechtigungen für Anmeldungen bereit. Beispielsweise sollten Sie die Berechtigungen **View Server State**, **ALTER ANY Login**, **View any Database**oder **CREATE ANY DATABASE** erteilen.

### <a name="public-server-role"></a>öffentliche Server Rolle
Jeder Anmelde Name, der eine Verbindung mit SQL Server PDW herstellen kann, ist ein Mitglied der **öffentlichen** Server Rolle. Alle-Anmeldungen erben die Berechtigungen, die für ein beliebiges Objekt **Public** erteilt wurden. Weisen Sie nur **öffentliche** Berechtigungen für ein Objekt zu, wenn Sie möchten, dass das Objekt für alle Benutzer verfügbar ist. Die Mitgliedschaft in der **Public** -Rolle kann nicht geändert werden.

> [!NOTE]
> **Public** wird anders implementiert als andere Rollen. Da alle Server Prinzipale Mitglieder von Public sind, wird die Mitgliedschaft in der **Public** -Rolle nicht in der **sys. server_role_members** -DMV aufgeführt.

### <a name="fixed-server-roles-vs-granting-permissions"></a>Korrigieren von Server Rollen im Vergleich zum Erteilen von Berechtigungen
Das System fester Server Rollen und fester Daten bankrollen ist ein Legacy System, das in den 80er Jahren entstanden ist. Behobene Rollen werden weiterhin unterstützt und sind in Umgebungen nützlich, in denen es nur wenige Benutzer gibt und die Sicherheitsanforderungen einfach sind. Ab SQL Server 2005 wurde ein ausführlicheres System zum Erteilen der Berechtigung erstellt. Dieses neue System ist präziser und bietet viele weitere Optionen für das erteilen und Verweigern von Berechtigungen. Die zusätzliche Komplexität des differenzierteren Systems erschwert das Erlernen, aber die meisten Unternehmenssysteme sollten Berechtigungen erteilen, anstatt die Fixed-Rollen zu verwenden. <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  -->

## <a name="related-topics"></a>Verwandte Themen

- [Erteilen von Berechtigungen](grant-permissions.md)

<!-- MISSING LINKS
## See Also
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)
-->

