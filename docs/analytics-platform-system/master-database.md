---
title: Master-Datenbank
description: Weitere Informationen zur Master-Datenbank finden Sie unter Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 7bf3928bfb21d34d0f60e6c52be8dae43621e4bd
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766739"
---
# <a name="master-database---parallel-data-warehouse"></a>Master Datenbank-parallele Data Warehouse
In der SQL Server PDW Master-Datenbank werden Anmelde Informationen auf Geräteebene und der Daten Bank Katalog gespeichert. Es handelt sich um eine SQL Server Master-Datenbank, die sich auf dem Steuer Knoten befindet. Daher bietet es eine ähnliche Funktionalität wie SQL Server PDW, wie die Master-SQL Server bereitstellt.  
  
Weitere Informationen zu System Datenbanken finden Sie unter [System Datenbanken](system-databases.md).  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
In der folgenden Liste werden die Vorgänge beschrieben, die Sie für die SQL Server PDW Master-Datenbank nicht ausführen können.  
  
Folgendes ist *nicht möglich:*  
  
-   Führen Sie eine differenzielle Sicherung von Master aus.  
  
-   Erstellen Sie Benutzer Objekte in der Master-Domäne.  
  
-   Ändern Sie die Sortierung der Master-.  
  
-   Ändern Sie den Besitzer des Masters.  
  
-   Drop oder Rename Master.  
  
-   Ändern Sie die Berechtigungen für Master.  
  
-   Führen Sie **DBCC shrinklog**aus.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Aufgabe|Beschreibung|  
|--------|---------------|  
|Erstellen Sie eine vollständige Sicherung der Master-Datei.|Beispiel:<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Weitere Informationen finden Sie unter [Backup Database](../t-sql/statements/backup-transact-sql.md?view=aps-pdw-2016).|  
|Wiederherstellen der Masterdatenbank|Verwenden Sie zum Wiederherstellen der Master-Datenbank im Configuration Manager Tool die Seite [Master Datenbank wiederherstellen](restore-the-master-database.md) .|  
|Daten Bank Katalog Informationen anzeigen.|`SELECT * FROM master.sys.databases;`|  
|Systemweite Anmelde-und Berechtigungsinformationen anzeigen.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
