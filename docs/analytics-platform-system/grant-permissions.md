---
title: 'GRANT-T-SQL-Berechtigungen: Parallel Data Warehouse | Microsoft-Dokumentation'
description: GRANT-T-SQL-Berechtigungen für Datenbankvorgänge in Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 01ef7b199a07be8bbc2dc1dee40d9c4d5771db1b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63157511"
---
# <a name="grant-t-sql-permissions-for-parallel-data-warehouse"></a>GRANT-T-SQL-Berechtigungen für Parallel Data Warehouse
GRANT-T-SQL-Berechtigungen für Datenbankvorgänge in Parallel Data Warehouse.

## <a name="grant-permissions-to-submit-database-queries"></a>Gewähren von Berechtigungen für Abfragen zu übermitteln.
Dieser Abschnitt beschreibt das Gewähren von Berechtigungen für Datenbankrollen und Benutzern zum Abfragen von Daten auf der SQL Server-PDW-Appliance.  
  
Die Anweisungen zum Gewähren von Berechtigungen zum Abfragen von Daten ist abhängig von den Bereich des gewünschten Zugriffs. Die folgenden SQL-Anweisungen erstellen Sie eine Anmeldung, die mit dem Namen KimAbercrombie, die auf das Gerät zugreifen können, erstellen ein Datenbankbenutzers KimAbercrombie in werden die **AdventureWorksPDW2012** Datenbank, eine Datenbankrolle mit dem Namen PDWQueryData erstellen, fügt die Verwendung Grundlage, dass KimAbercrombie PDWQueryData-Rolle und klicken Sie dann Optionen zum Gewähren des Zugriffs für Abfragen, anzeigen, ob der Zugriff auf das Objekt oder Datenbankebene gewährt wird.  
  
```sql  
USE master;  
GO  
  
CREATE LOGIN KimAbercrombie WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
USE AdventureWorksPDW2012;  
GO  
  
CREATE USER KimAbercrombie;  
GO  
  
CREATE ROLE PDWQueryData;  
GO  
  
EXEC sp_addrolemember 'PDWQueryData', 'KimAbercrombie'  
GO  
  
-- If the permission is granted against a table or view only, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO PDWQueryData;  
GO  
  
-- If the permission is granted for the database, use this syntax:  
GRANT SELECT ON DATABASE::AdventureWorksPDW2012 TO PDWQueryData;  
GO  
  
-- If KimAbercrombie is the only user that needs to access a table, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO KimAbercrombie;  
GO  
```  
  
## <a name="grant-permissions-to-use-the-admin-console"></a>Gewähren von Berechtigungen für die Admin-Konsole verwenden
In diesem Abschnitt wird beschrieben, wie zum Gewähren von Berechtigungen zu Anmeldungen die Admin-Konsole verwendet wird.  
  
**Verwenden Sie die Admin-Konsole**  
  
Verwenden Sie die Verwaltungskonsole erfordert eine Anmeldung Serverebene **VIEW SERVER STATE** Berechtigung. Die folgende SQL-Anweisung erteilt die **VIEW SERVER STATE** -Berechtigung `KimAbercrombie` sodass Sven die Admin-Konsole verwenden kann, überwachen die SQL Server-PDW-Appliance.  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**Beenden von Sitzungen**  
  
Wenn einer Anmeldung die Berechtigung zum Beenden von Sitzungen, erteilen Sie dem **ALTER ANY CONNECTION** Berechtigung wie folgt:  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>Erteilen von Berechtigungen zum Laden von Daten
In diesem Abschnitt wird beschrieben, wie zum Gewähren von Berechtigungen für Datenbankrollen und Datenbankbenutzer zum Laden von Daten auf dem SQL Server-PDWappliance wird.  
  
Das folgende Skript zeigt, welche Berechtigungen für die einzelnen Optionen laden erforderlich sind. Sie können diese Option, um Ihre speziellen Anforderungen ändern.  
  
```sql  
-- Create server login for the examples that follow.  
USE master;  
CREATE LOGIN BI_ETLUser WITH PASSWORD = '******';  
  
--Grant BULK Load permissions   
GRANT ADMINISTER BULK OPERATIONS TO BI_ETLUser;  
  
--Grant Staging database permissions  
USE stagedb;  
CREATE USER BI_ETLUser for login BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
EXEC sp_addrolemember 'db_ddladmin','BI_ETLUser';  
  
-- The CREATE TABLE permission is required for the database hosting the temporary table.  
-- This may be the staging database (if specified) or destination database.   
-- The CREATE permission is not required if loading in fastappend mode.  
GRANT CREATE TABLE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in append or fastappend mode, the INSERT permission is required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
  
-- If loading in reload mode, the INSERT and DELETE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT DELETE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in upsert mode, the INSERT and UPDATE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT UPDATE ON database::stagedb TO BI_ETLUser;  
  
-- Destination DB  
USE tpch_1gb;  
CREATE USER BI_ETLUser FOR LOGIN BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
```  
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>Gewähren von Berechtigungen für das Kopieren von Daten nicht auf dem Gerät
Dieser Abschnitt beschreibt, wie Berechtigungen für einen Benutzer oder Datenbankrolle zum Kopieren von Daten aus der SQL Server-PDW-Appliance zu gewähren.  
  
Zum Verschieben von Daten an einen anderen Speicherort erfordert **wählen** -Berechtigung für die Tabelle mit den Daten verschoben werden soll.  
  
Wenn das Ziel für die Daten einer anderen SQL Server PDW ist, kann der Benutzer benötigen **CREATE TABLE** Berechtigung am Ziel und **ALTER SCHEMA** -Berechtigung für das Schema, das die Tabelle enthalten soll.  
  
## <a name="grant-permissions-to-manage-databases"></a>Erteilen von Berechtigungen zum Verwalten von Datenbanken
In diesem Abschnitt wird beschrieben, gewähren Sie Berechtigungen für einen Datenbankbenutzer zum Verwalten einer Datenbank auf der SQL Server-PDW-Appliance.  
  
In einigen Fällen weist ein Unternehmen einen Manager für eine Datenbank. Der Manager steuert den Zugriff, den andere Anmeldungen auf die Datenbank als auch die Daten und Objekte in der Datenbank verfügen. Zum Verwalten aller Objekte, Rollen und Benutzer in einer Datenbank gewähren Sie dem Benutzer die **Steuerelement** Berechtigung für die Datenbank. Die folgende Anweisung erteilt die **Steuerelement** -Berechtigung für die **AdventureWorksPDW2012** Datenbank für den Benutzer `KimAbercrombie`.  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
Um eine Person die Berechtigung für alle Datenbanken auf dem Gerät steuern gewähren, gewähren dem **ALTER ANY DATABASE** -Berechtigung in der master-Datenbank.  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>Erteilen von Berechtigungen zum Verwalten von Anmeldungen, Benutzer und Datenbankrollen
In diesem Abschnitt wird beschrieben, wie zum Gewähren von Berechtigungen zum Verwalten von Anmeldungen, Datenbankbenutzer und Datenbankrollen werden.  
  
### <a name="PermsAdminConsole"></a>Erteilen von Berechtigungen zum Verwalten von Anmeldungen  
**Hinzufügen oder Verwalten von Anmeldungen**  
  
Die folgenden SQL-Anweisungen erstellen Sie eine Anmeldung, die mit dem Namen KimAbercrombie, die neue Anmeldungen erstellen kann die [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) Anweisung und ändern Sie die vorhandene Anmeldungen mithilfe der [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md) Anweisung.  
  
Die **ALTER ANY LOGIN** Berechtigung gewährt, die Möglichkeit, neue Anmeldenamen zu erstellen und löschen vorhandene. Sobald eine Anmeldung vorhanden ist, kann die Anmeldung verwaltet werden, von Anmeldungen mit der **ALTER ANY LOGIN** Berechtigung oder die **ALTER** Berechtigung für diesen Anmeldenamen. Eine Anmeldung kann das Kennwort und einer Standarddatenbank für seine eigene Anmeldung ändern.  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>Gewähren von Berechtigungen für die Anmeldung Sitzungen verwalten  
Um die Möglichkeit haben, zeigen Sie alle Sitzungen auf dem Server müssen die **VIEW SERVER STATE** Berechtigung. Beenden die Sitzungen, die von anderen Anmeldungen erforderlich, dass die **ALTER ANY CONNECTION** Berechtigung. Im folgenden Beispiel wird die `KimAbercrombie` Anmeldung, die zuvor erstellt haben.  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>Erteilen der Berechtigung zum Verwalten von Datenbankbenutzern  
Erstellen und Löschen von Datenbankbenutzern erfordert die **ALTER ANY USER** Berechtigung. Verwalten von vorhandenen Benutzern muss die **ALTER ANY USER** Berechtigung oder die **ALTER** Berechtigung für diesen Benutzer. Im folgenden Beispiel wird die `KimAbercrombie` Anmeldung, die zuvor erstellt haben.  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>Erteilen Sie über die entsprechenden Berechtigungen zum Verwalten von Datenbankrollen  
Erstellen und löschen eine benutzerdefinierte Datenbankrollen erfordert die **ALTER ANY ROLE** Berechtigung. Im folgenden Beispiel wird die `KimAbercrombie` Anmelde- und verwenden, die zuvor erstellt haben.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>Anmeldenamen, Benutzer und Rolle Berechtigung Diagramme  
Die folgenden Diagramme können verwirrend sein, aber darin wird veranschaulicht, wie höhere Hebel Berechtigungen (z.B.) präziser Berechtigungen, die separat (z. B. ALTER) erteilt werden können. Es ist eine bewährte Methode, die die geringste Menge an Berechtigungen für eine Person, die notwendigen Aufgaben immer gewähren. Gewähren Sie spezifischere Berechtigungen anstelle der Berechtigungen auf oberster Ebene, zu diesem Zweck.  
  
**Login-Berechtigungen verfügen:**  
  
![APS-sicherheitsanmeldeberechtigungen](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**Benutzerberechtigungen:**  
  
![APS-sicherheitsbenutzerberechtigungen](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**Berechtigungen für die Rolle:**  
  
![APS-Sicherheitsrollenberechtigungen](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>Gewähren von Berechtigungen für das Überwachen der Appliance
Die SQL Server-PDW-Appliance kann mithilfe der Admin-Verwaltungskonsole oder SQL Server-PDW-Systemsichten überwacht werden. Anmeldungen sind erforderlich, die auf Serverebene **VIEW SERVER STATE** über die Berechtigung zum Überwachen der Appliance. Anmeldungen der **ALTER ANY CONNECTION** Berechtigung für die Verbindungen zu beenden, indem Sie mit der Verwaltungskonsole oder der **KILL** Befehl. Weitere Informationen zu Berechtigungen erforderlich, um die Verwaltungskonsole zu verwenden, finden Sie unter [Erteilen von Berechtigungen zum Verwenden der Verwaltungskonsole &#40;SQL Server PDW&#41;](#grant-permissions-to-use-the-admin-console).  
  
### <a name="PermsAdminConsole"></a>Erteilen von Berechtigungen zum Überwachen der Appliance mithilfe von Systemansichten  
Folgenden SQL-Anweisungen erstellen Sie eine Anmeldung, die mit dem Namen `monitor_login` und gewährt der **VIEW SERVER STATE** Berechtigung für die `monitor_login` Anmeldung.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>Erteilen von Berechtigungen zum Überwachen der Appliance mithilfe von Systemansichten und Verbindungen beendet.  
Die folgenden SQL-Anweisungen erstellen Sie eine Anmeldung, die mit dem Namen `monitor_and_terminate_login` und gewährt der **VIEW SERVER STATE** und **ALTER ANY CONNECTION** Berechtigungen für die `monitor_and_terminate_login` Anmeldung.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
Admin-Anmeldungen erstellen zu können, finden Sie unter [fester Serverrollen](pdw-permissions.md#fixed-server-roles).  
  
## <a name="see-also"></a>Siehe auch
[CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)  
[BENUTZER ERSTELLEN](../t-sql/statements/create-user-transact-sql.md)  
[ROLLE ERSTELLEN](../t-sql/statements/create-role-transact-sql.md)  
[Load](load-overview.md)  
