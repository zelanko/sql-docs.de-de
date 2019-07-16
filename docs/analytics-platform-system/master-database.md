---
title: Master-Datenbank – Parallel Data Warehouse | Microsoft-Dokumentation
description: Erfahren Sie, bis der master-Datenbank in Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 9f37c7a85baea3b41f6016a57e4f57579b427719
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960653"
---
# <a name="master-database---parallel-data-warehouse"></a>Master-Datenbank – Parallel Data Warehouse
Der SQL Server-PDW-master-Datenbank speichert die Anmeldeinformationen der Appliance auf Serverebene sowie der Datenbankkatalog. Es ist eine SQL Server-master-Datenbank, die sich auf dem steuerknoten befindet. Daher wird eine ähnliche Funktionalität in SQL Server PDW als Master für SQL Server bereitstellt.  
  
Weitere Informationen zu den Systemdatenbanken, finden Sie unter [Systemdatenbanken](system-databases.md).  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
Die folgende Liste beschreibt die Vorgänge, die Sie für die Masterdatenbank der SQL Server PDW nicht ausführen können.  
  
Sie *nicht möglich:*  
  
-   Führen Sie eine differenzielle Sicherung der Master.  
  
-   Erstellen von Benutzerobjekten in der Masterdatenbank.  
  
-   Ändern Sie die Sortierung der Master.  
  
-   Ändern Sie den Besitzer des Masters.  
  
-   Löschen oder Umbenennen von Master.  
  
-   Ändern Sie die Berechtigungen zum Master.  
  
-   Führen Sie **DBCC SHRINKLOG**.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Aufgabe|Beschreibung|  
|--------|---------------|  
|Erstellen Sie eine vollständige Sicherung der Master.|Beispiel:<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Weitere Informationen finden Sie unter [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md).|  
|Wiederherstellen der Masterdatenbank|Verwenden Sie zum Wiederherstellen des master-Datenbank die [Wiederherstellen der Master-Datenbank](restore-the-master-database.md) Seite im Konfigurations-Manager.|  
|Anzeigen von Datenbank-Kataloginformationen.|`SELECT * FROM master.sys.databases;`|  
|Zeigen Sie Informationen für eine systemweite Anmelde- und Berechtigungsprobleme.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
