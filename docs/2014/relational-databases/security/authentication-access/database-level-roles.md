---
title: Rollen auf Datenbankebene | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/22/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.database.f1
- sql12.swb.roleproperties.general.f1
- sql12.swb.roleproperties.object.f1
- SQL12.SWB.DBROLEPROPERTIES.GENERAL.F1
helpviewer_keywords:
- db_denydatareader role
- users [SQL Server], database roles
- database-level roles [SQL Server]
- db_denydatawriter role
- roles [SQL Server], database
- principals [SQL Server], database-level
- db_backupoperator role
- credentials [SQL Server], roles
- db_accessadmin role
- schemas [SQL Server], roles
- permissions [SQL Server], roles
- database roles [SQL Server], listed
- db_datareader role
- db_ddladmin role
- db_datawriter role
- db_securityadmin role
- db_owner role
- database roles [SQL Server]
- fixed database roles [SQL Server]
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: 7f3fa5f6-6b50-43bb-9047-1544ade55e39
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0354f0e55111e078f1682e38c3fb51aea8c365b3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055348"
---
# <a name="database-level-roles"></a>Rollen auf Datenbankebene
  Zur einfachen Verwaltung der Berechtigungen für Ihre Datenbanken stellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mehrere *Rollen* zur Verfügung. Dies sind Sicherheitsprinzipale, die andere Prinzipale gruppieren. Sie entsprechen den ***Gruppen*** im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Betriebssystem. Der Geltungsbereich der Berechtigungen von Rollen auf Datenbankebene erstreckt sich auf die gesamte Datenbank.  
  
 Es gibt in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zwei Typen von Rollen auf Datenbankebene: *feste Datenbankrollen* , die in der Datenbank vordefiniert sind, und *flexible Datenbankrollen* , die Sie erstellen können.  
  
 Feste Datenbankrollen werden auf der Datenbankebene definiert und sind in jeder Datenbank vorhanden. Mitglieder der Datenbankrolle **db_owner** können die Mitgliedschaft von festen Datenbankrollen ändern. In der msdb-Datenbank gibt es auch einige feste Datenbankrollen für spezielle Zwecke.  
  
 Sie können in Rollen auf Datenbankebene jedes Datenbankkonto und andere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Rollen hinzufügen. Jedes Mitglied einer festen Datenbankrolle kann der gleichen Rolle andere Anmeldenamen hinzufügen.  
  
> [!IMPORTANT]  
>  Fügen Sie keine flexiblen Datenbankrollen als Mitglieder fester Rollen hinzu. Dies könnte zu einer unbeabsichtigten Ausweitung von Privilegien führen.  
  
 In der folgenden Tabelle werden die festen Datenbankrollen und ihre Möglichkeiten aufgeführt. Diese Rollen sind in allen Datenbanken vorhanden.  
  
|Rollenname auf Datenbankebene|BESCHREIBUNG|  
|-------------------------------|-----------------|  
|**db_owner**|Mitglieder der festen Datenbankrolle **db_owner** können alle Aktivitäten zur Konfiguration und Wartung an der Datenbank ausführen und können die Datenbank auch löschen.|  
|**db_securityadmin**|Mitglieder der festen Datenbankrolle **db_securityadmin** können die Rollenmitgliedschaft ändern und Berechtigungen verwalten. Das Hinzufügen von Prinzipalen zu dieser Rolle könnte zu einer unbeabsichtigten Ausweitung von Privilegien führen.|  
|**db_accessadmin**|Mitglieder der festen Datenbankrolle **db_accessadmin** können den Zugriff auf die Datenbank für Windows-Anmeldungen, Windows-Gruppen und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldungen hinzufügen oder entfernen.|  
|**db_backupoperator**|Mitglieder der festen Datenbankrolle **db_backupoperator** können eine Sicherung der Datenbank durchführen.|  
|**db_ddladmin**|Mitglieder der festen Datenbankrolle **db_ddladmin** können in einer Datenbank sämtliche DDL-Befehle (Data Definition Language) ausführen.|  
|**db_datawriter**|Mitglieder der festen Datenbankrolle **db_datawriter** können Daten in allen Benutzertabellen hinzufügen, löschen oder ändern.|  
|**db_datareader**|Mitglieder der festen Datenbankrolle **db_datareader** können alle Daten aller Benutzertabellen lesen.|  
|**db_denydatawriter**|Mitglieder der festen Datenbankrolle **db_denydatareader** können keine Daten in den Benutzertabellen in einer Datenbank hinzufügen, ändern oder löschen.|  
|**db_denydatareader**|Mitglieder der festen Datenbankrolle **db_denydatareader** können keine Daten in den Benutzertabellen in einer Datenbank lesen.|  
  
## <a name="msdb-roles"></a>msdb-Rollen  
 Die msdb-Datenbank enthält die in der folgenden Tabelle aufgeführten Rollen für spezielle Zwecke.  
  
|Name der msdb-Rolle|BESCHREIBUNG|  
|--------------------|-----------------|  
|`db_ssisadmin`<br /><br /> **db_ssisoperator**<br /><br /> **db_ssisltduser**|Mitglieder dieser Datenbankrollen können [!INCLUDE[ssIS](../../../includes/ssis-md.md)]verwalten und verwenden. Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], die von einer früheren Version aktualisiert wurden, enthalten möglicherweise eine ältere Version der Rolle, die mit Data Transformation Services (DTS) und nicht mit [!INCLUDE[ssIS](../../../includes/ssis-md.md)] benannt wurde. Weitere Informationen finden Sie unter [Integration Services Roles &#40;SSIS Service&#41;](../../../integration-services/security/integration-services-roles-ssis-service.md) (Integration Services-Rollen [SSIS-Dienst]).|  
|`dc_admin`<br /><br /> **dc_operator**<br /><br /> **dc_proxy**|Mitglieder dieser Datenbankrollen können den Datensammler verwalten und verwenden. Weitere Informationen finden Sie unter [Data Collection](../../data-collection/data-collection.md).|  
|**PolicyAdministratorRole**|Mitglieder der Datenbankrolle **db_PolicyAdministratorRole** können alle Aktivitäten zur Konfiguration und Wartung für Richtlinien und Bedingungen der richtlinienbasierten Verwaltung ausführen. Weitere Informationen finden Sie unter [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../policy-based-management/administer-servers-by-using-policy-based-management.md).|  
|**ServerGroupAdministratorRole**<br /><br /> **ServerGroupReaderRole**|Mitglieder dieser Datenbankrollen können registrierte Servergruppen verwalten und verwenden.|  
|**dbm_monitor**|Wird in der-Datenbank erstellt, `msdb` Wenn die erste Datenbank in Datenbankspiegelungs-Monitor registriert wird. Die **dbm_monitor** -Rolle hat keine Mitglieder, bis ein Systemadministrator der Rolle Benutzer zuweist.|  
  
> [!IMPORTANT]  
>  Mitglieder der db_ssisadmin-Rolle und der dc_admin-Rolle können Ihre Berechtigungen möglicherweise auf sysadmin erhöhen. Diese Ausweitung von Berechtigungen ist möglich, da diese Rollen [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Pakete ändern können und [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Pakete von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe des sysadmin-Sicherheitskontexts des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agents ausgeführt werden können. Konfigurieren Sie als Schutz vor dieser Ausweitung von Berechtigungen beim Ausführen von Wartungsplänen, Datensammlungssätzen und anderen [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Paketen Aufträge des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agents, die Pakete ausführen, für die Verwendung eines Proxykontos mit einschränkten Berechtigungen, oder fügen Sie der db_ssisadmin-Rolle und der dc_admin-Rolle nur sysadmin-Mitglieder hinzu.  
  
## <a name="working-with-database-level-roles"></a>Arbeiten mit Rollen auf Datenbankebene  
 In der folgenden Tabelle werden die Befehle, Sichten und Funktionen zum Arbeiten mit Rollen auf Datenbankebene erklärt.  
  
|Funktion|type|BESCHREIBUNG|  
|-------------|----------|-----------------|  
|[sp_helpdbfixedrole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql)|Metadaten|Gibt eine Liste der festen Datenbankrollen zurück.|  
|[sp_dbfixedrolepermission &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql)|Metadaten|Zeigt die Berechtigungen einer festen Datenbankrolle an.|  
|[sp_helprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprole-transact-sql)|Metadaten|Gibt Informationen zu den Rollen in der aktuellen Datenbank zurück.|  
|[sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)|Metadaten|Gibt Informationen zu den Mitgliedern einer Rolle in der aktuellen Datenbank zurück.|  
|[sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)|Metadaten|Gibt eine Zeile für jedes Mitglied jeder Datenbankrolle zurück.|  
|[IS_MEMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/is-member-transact-sql)|Metadaten|Zeigt an, ob der aktuelle Benutzer ein Mitglied der angegebenen Microsoft Windows-Gruppe oder der Microsoft SQL Server-Datenbankrolle ist.|  
|[CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql)|Get-Help|Erstellt eine neue Datenbankrolle in der aktuellen Datenbank.|  
|[ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql)|Get-Help|Ändert den Namen einer Datenbankrolle.|  
|[DROP ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-role-transact-sql)|Get-Help|Entfernt eine Rolle aus der Datenbank.|  
|[sp_addrole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrole-transact-sql)|Get-Help|Erstellt eine neue Datenbankrolle in der aktuellen Datenbank.|  
|[sp_droprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprole-transact-sql)|Get-Help|Entfernt eine Datenbankrolle aus der aktuellen Datenbank.|  
|[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)|Get-Help|Fügt einer Datenbankrolle in der aktuellen Datenbank einen Datenbankbenutzer, eine Datenbankrolle, einen Windows-Anmeldenamen oder eine Windows-Gruppe hinzu.|  
|[sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)|Get-Help|Entfernt ein Sicherheitskonto aus einer SQL Serverrolle in der aktuellen Datenbank.|  
  
## <a name="public-database-role"></a>Datenbankrolle public  
 Jeder Datenbankbenutzer gehört der Datenbankrolle **public** an. Wenn einem Benutzer keine bestimmten Berechtigungen für ein sicherungsfähiges Objekt erteilt oder verweigert werden, erbt der Benutzer die Berechtigungen, die der Datenbankrolle **public** für dieses Objekt erteilt wurden.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql)  
  
 [Gespeicherte Sicherheitsprozeduren &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/security-stored-procedures-transact-sql)  
  
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql)  
  
 [Sichern von SQL Server](../securing-sql-server.md)  
  
 [sp_helprotect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprotect-transact-sql)  
  
  
