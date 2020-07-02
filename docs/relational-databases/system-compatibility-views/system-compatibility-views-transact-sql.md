---
title: Systemkompatibilitäts-Sichten (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- compatibility views [SQL Server]
- system tables [SQL Server], compatibility views
- type IDs [SQL Server]
- system views [SQL Server], compatibility
- metadata [SQL Server], views
- backward compatibility [SQL Server], compatibility views
- compatibility [SQL Server], compatibility views
- backward compatibility [SQL Server], system tables
- compatibility [SQL Server], system tables
- user IDs [SQL Server]
ms.assetid: 8e4624f5-9d36-4ce7-9c9e-1fe010fa2122
author: rothja
ms.author: jroth
ms.openlocfilehash: 9eb123194e6ea69a6260f9eed4f02a07a9e819ed
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85652206"
---
# <a name="system-compatibility-views-transact-sql"></a>Systemkompatibilitäts-Sichten (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Viele der Systemtabellen aus früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind jetzt als eine Gruppe von Sichten implementiert worden. Diese Sichten werden als Kompatibilitätssichten bezeichnet und sollen ausschließlich für die Abwärtskompatibilität verwendet werden. Die Kompatibilitätssichten machen die gleichen Metadaten verfügbar wie in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Die Kompatibilitätssichten machen jedoch keine Metadaten bezüglich der in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher neu eingeführten Funktionen verfügbar. Wenn Sie also neue Funktionen, wie z. B. [!INCLUDE[ssSB](../../includes/sssb-md.md)] oder die Partitionierung, verwenden, müssen Sie Katalogsichten verwenden.  
  
 Ein weiterer Grund für ein Upgrade auf die Katalogsichten besteht darin, dass Kompatibilitätssichtspalten, in denen Benutzer-IDs und Typ-IDs gespeichert werden, evtl. NULL zurückgeben oder arithmetische Überläufe auslösen. Dies liegt daran, dass Sie mehr als 32.767 Benutzer, Gruppen und Rollen sowie 32.767 Datentypen erstellen können. Angenommen, Sie würden 32.768 Benutzer erstellen und folgende Abfrage ausführen: `SELECT * FROM sys.sysusers`. Wenn ARITHABORT auf ON festgelegt ist, schlägt die Abfrage aufgrund eines arithmetischen Überlauffehlers fehl. Wenn ARITHABORT auf OFF festgelegt ist, gibt die **UID** -Spalte NULL zurück.  
  
 Zur Vermeidung dieser Probleme wird die Verwendung der neuen Katalogsichten empfohlen, die die erhöhte Anzahl von Benutzer-IDs und Typ-IDs verarbeiten können. In der folgenden Tabelle sind die Spalten aufgeführt, bei denen es zu einem solchen Überlauf kommen kann.  
  
|Spaltenname|Kompatibilitätssicht|SQL Server 2005-Sicht|  
|-----------------|------------------------|--------------------------|  
|**xusertype**|**syscolumns**|**sys.columns**|  
|**usertype**|**syscolumns**|**sys.columns**|  
|**memberuid**|**sysmembers**|**sys.database_role_members**|  
|**groupuid**|**sysmembers**|**sys.database_role_members**|  
|**uid**|**sysobjects**|**sys.objects**|  
|**uid**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**GRANTOR**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**xusertype**|**systypes**|**sys.types**|  
|**uid**|**systypes**|**sys.types**|  
|**uid**|**sysusers**|**sys.database_principals**|  
|**altuid**|**sysusers**|**sys.database_principals**|  
|**gid**|**sysusers**|**sys.database_principals**|  
|**uid**|**syscacheobjects**|**sys.dm_exec_plan_attributes**|  
|**uid**|**sysprocesses**|**sys.dm_exec_requests**|  
  
 Wenn in einer Benutzerdatenbank auf Sie verwiesen wird, sind Systemtabellen, die in SQL Server 2000 (z. b. **syslanguages** oder **syscacheobjects**) als veraltet markiert wurden, nun an die Ansicht der Back Kompatibilität im **sys** -Schema gebunden. Da die SQL Server 2000-Systemtabellen für mehrere Versionen als veraltetet markiert wurden, wird diese Änderung nicht als wichtige Änderung eingestuft.  
  
 Beispiel: Wenn ein Benutzer eine Benutzertabelle namens " **syslanguages** " in einer Benutzerdatenbank erstellt, würde die-Anweisung in der-Datenbank in SQL Server 2008 `SELECT * from dbo.syslanguages;` die Werte aus der Benutzertabelle zurückgeben. Ab SQL Server 2012 werden Daten aus der Systemansicht **sys.sysSprachen**zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
