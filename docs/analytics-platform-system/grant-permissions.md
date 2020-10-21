---
title: Erteilen von T-SQL-Berechtigungen
description: Erteilen Sie T-SQL-Berechtigungen für Daten Bank Vorgänge parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6bbe78979c393490a52e1051fe158ae138f93dcc
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257473"
---
# <a name="grant-t-sql-permissions-for-parallel-data-warehouse"></a>Erteilen von T-SQL-Berechtigungen für parallele Data Warehouse
Erteilen Sie T-SQL-Berechtigungen für Daten Bank Vorgänge parallel Data Warehouse.

## <a name="grant-permissions-to-submit-database-queries"></a>Erteilen von Berechtigungen zum Übermitteln von Datenbankabfragen
In diesem Abschnitt wird beschrieben, wie Daten bankrollen und Benutzern Berechtigungen zum Abfragen von Daten auf der SQL Server PDW Appliance erteilt werden.  
  
Die Anweisungen, die zum Erteilen von Berechtigungen für Abfrage Daten verwendet werden, hängen vom gewünschten Zugriffs Bereich ab. Die folgenden SQL-Anweisungen erstellen eine Anmeldung mit dem Namen "kimabercrombie", die auf das Gerät zugreifen kann. Erstellen Sie einen Datenbankbenutzer mit dem Namen "kimabercrombie" in der **AdventureWorksPDW2012** -Datenbank, erstellen Sie eine Daten Bank Rolle mit dem Namen "pdwquerydata", fügt der Rolle "pdwquerydata" die Verwendung von "kimabercrombie" hinzu, und zeigen Sie dann Optionen zum Gewähren des Abfrage Zugriffs an, je nachdem, ob der Zugriff auf Objekt  
  
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
  
## <a name="grant-permissions-to-use-the-admin-console"></a>Erteilen von Berechtigungen für die Verwendung der Verwaltungskonsole
In diesem Abschnitt wird beschrieben, wie Sie Anmeldungen Berechtigungen für die Verwendung der-Verwaltungskonsole erteilen.  
  
**Verwenden der Verwaltungskonsole**  
  
Um die Verwaltungskonsole zu verwenden, ist für eine Anmeldung die Berechtigung Server **Status anzeigen auf** Serverebene erforderlich. Mit der folgenden SQL-Anweisung wird dem Anmelde Namen die **View Server State** -Berechtigung erteilt, sodass Sven die `KimAbercrombie` SQL Server PDW Appliance mithilfe der Verwaltungskonsole überwachen kann.  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**Abbrechen von Sitzungen**  
  
Erteilen Sie die Berechtigung **ALTER ANY Connection** wie folgt, um einem Anmelde Namen die Berechtigung zum Beenden von Sitzungen zu erteilen:  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>Erteilen von Berechtigungen zum Laden von Daten
In diesem Abschnitt wird beschrieben, wie Daten bankrollen und Datenbankbenutzern Berechtigungen zum Laden von Daten auf die SQL Server pdwappliance erteilt werden.  
  
Das folgende Skript zeigt, welche Berechtigungen für jede Lade Option erforderlich sind. Sie können diese an Ihre speziellen Anforderungen anpassen.  
  
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
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>Erteilen von Berechtigungen für Daten kopieren von der Appliance
In diesem Abschnitt wird beschrieben, wie einem Benutzer oder einer Daten Bank Rolle Berechtigungen zum Kopieren von Daten aus der SQL Server PDW Appliance erteilt werden.  
  
Zum Verschieben von Daten an einen anderen Speicherort ist die **Select** -Berechtigung für die Tabelle mit den zu verschiebenden Daten erforderlich.  
  
Wenn das Ziel für die Daten ein weiteres SQL Server PDW ist, muss der Benutzer über **CREATE TABLE** Berechtigung für das Ziel und die **Alter Schema** -Berechtigung für das Schema verfügen, das die Tabelle enthalten wird.  
  
## <a name="grant-permissions-to-manage-databases"></a>Erteilen von Berechtigungen zum Verwalten von Datenbanken
In diesem Abschnitt wird beschrieben, wie einem Datenbankbenutzer Berechtigungen zum Verwalten einer Datenbank auf der SQL Server PDW Appliance erteilt werden.  
  
In einigen Situationen weist ein Unternehmen einen Vorgesetzten für eine Datenbank zu. Der Manager steuert den Zugriff auf die Datenbank durch andere Anmeldungen sowie die Daten und Objekte in der Datenbank. Erteilen Sie dem Benutzer die **Control** -Berechtigung für die Datenbank, um alle Objekte, Rollen und Benutzer in einer Datenbank zu verwalten. Die folgende Anweisung erteilt dem Benutzer die **Control** -Berechtigung für die **AdventureWorksPDW2012** -Datenbank `KimAbercrombie` .  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
Wenn Sie einer Person die Berechtigung erteilen möchten, alle Datenbanken auf dem Gerät zu steuern, erteilen Sie die **ALTER ANY DATABASE** -Berechtigung in der Master-Datenbank.  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>Erteilen von Berechtigungen zum Verwalten von Anmeldungen, Benutzern und Daten bankrollen
In diesem Abschnitt wird beschrieben, wie Berechtigungen zum Verwalten von Anmeldungen, Datenbankbenutzern und Daten bankrollen erteilt werden.  
  
### <a name="grant-permissions-to-manage-logins"></a><a name="PermsAdminConsole"></a>Erteilen von Berechtigungen zum Verwalten von Anmeldungen  
**Hinzufügen oder Verwalten von Anmeldungen**  
  
Die folgenden SQL-Anweisungen erstellen einen Anmelde Namen mit dem Namen "kimabercrombie", der neue Anmeldungen mithilfe der [Create Login](../t-sql/statements/create-login-transact-sql.md) -Anweisung erstellen und vorhandene Anmeldungen mithilfe der [Alter Login](../t-sql/statements/alter-login-transact-sql.md) -Anweisung ändern kann.  
  
Mit der Berechtigung **ALTER ANY Login** können neue Anmeldungen erstellt und Drop Exisiting erstellt werden. Sobald eine Anmeldung vorhanden ist, kann die Anmeldung von Anmeldungen mit der **ALTER ANY Login** -Berechtigung oder der **Alter** -Berechtigung für diese Anmeldung verwaltet werden. Ein Anmelde Name kann das Kennwort und die Standarddatenbank für die eigene Anmeldung ändern.  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>Erteilen von Berechtigungen zum Verwalten von Anmelde Sitzungen  
Damit alle Sitzungen auf dem Server angezeigt werden können, ist die **View Server State** -Berechtigung erforderlich. Die Möglichkeit, die Sitzungen anderer Anmeldungen zu beenden, erfordert die **ALTER ANY Connection** -Berechtigung. Im folgenden Beispiel wird der `KimAbercrombie` zuvor erstellte-Anmelde Name verwendet.  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>Erteilen der Berechtigung zum Verwalten von Datenbankbenutzern  
Zum Erstellen und Löschen von Datenbankbenutzern ist die **ALTER ANY User** -Berechtigung erforderlich. Zum Verwalten vorhandener Benutzer ist die **ALTER ANY User** -Berechtigung oder die **Alter** -Berechtigung für diesen Benutzer erforderlich. Im folgenden Beispiel wird der `KimAbercrombie` zuvor erstellte-Anmelde Name verwendet.  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>Erteilen von Berechtigungen zum Verwalten von Daten bankrollen  
Zum Erstellen und Löschen von benutzerdefinierten Daten bankrollen ist die **ALTER ANY ROLE** -Berechtigung erforderlich. Im folgenden Beispiel werden die `KimAbercrombie` Anmelde Informationen und die zuvor erstellte Verwendung verwendet.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>Diagramme zu Anmelde-, Benutzer-und Rollen Berechtigungen  
Die folgenden Diagramme können verwirrend sein, aber Sie zeigen, wie höhere Berechtigungs Berechtigungen (z. b. Steuerelement) präziseere Berechtigungen enthalten, die separat gewährt werden können (z. b. Alter). Es ist eine bewährte Vorgehensweise, jedem Benutzer stets die geringsten Berechtigungen zu erteilen, um die erforderlichen Aufgaben auszuführen. Erteilen Sie zu diesem Zweck spezifischere Berechtigungen anstelle der Berechtigungen auf oberster Ebene.  
  
**Anmelde Berechtigungen:**  
  
![APS-Sicherheitsanmeldeberechtigungen](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**Benutzerberechtigungen:**  
  
![APS-Sicherheitsbenutzerberechtigungen](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**Rollen Berechtigungen:**  
  
![APS-Sicherheitsrollenberechtigungen](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>Erteilen von Berechtigungen zum Überwachen der Appliance
Die SQL Server PDW Appliance kann entweder über die Verwaltungskonsole oder über SQL Server PDW System Sichten überwacht werden. Anmeldungen erfordern die Berechtigung Server **Status anzeigen** auf Serverebene, um das Gerät zu überwachen. Für-Anmeldungen ist die Berechtigung **ALTER ANY Connection** zum Beenden von Verbindungen über die Verwaltungskonsole oder den **Kill** -Befehl erforderlich. Informationen zu den Berechtigungen, die für die Verwendung der-Verwaltungskonsole erforderlich sind, finden [Sie unter Erteilen von Berechtigungen für die Verwendung der Verwaltungskonsole &#40;SQL Server PDW&#41;](#grant-permissions-to-use-the-admin-console).  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views"></a><a name="PermsAdminConsole"></a>Erteilen der Berechtigung zum Überwachen der Appliance mithilfe von System Sichten  
Die folgenden SQL-Anweisungen erstellen eine Anmeldung `monitor_login` mit dem Namen und gewähren der Anmeldung die **View Server State** -Berechtigung `monitor_login` .  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>Erteilen der Berechtigung zum Überwachen der Appliance mithilfe von System Sichten und Beenden von Verbindungen  
Die folgenden SQL-Anweisungen erstellen eine Anmeldung `monitor_and_terminate_login` mit dem Namen und gewähren der Anmeldung die Berechtigungen **View Server State** und **ALTER ANY Connection** `monitor_and_terminate_login` .  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
Informationen zum Erstellen von Administrator Anmeldungen finden Sie unter [Fixed Server Rollen](pdw-permissions.md#fixed-server-roles).  
  
## <a name="see-also"></a>Weitere Informationen
[CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)  
[CREATE USER](../t-sql/statements/create-user-transact-sql.md)  
[CREATE ROLE](../t-sql/statements/create-role-transact-sql.md)  
[Load](load-overview.md)  
