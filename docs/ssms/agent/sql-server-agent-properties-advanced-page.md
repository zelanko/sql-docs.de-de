---
description: SQL Server-Agent-Eigenschaften (Seite Erweitert)
title: SQL Server-Agent-Eigenschaften (Seite Erweitert)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 96dcf5690bac961e08c222023e14d92b833cfff2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88318178"
---
# <a name="sql-server-agent-properties-advanced-page"></a>SQL Server-Agent-Eigenschaften (Seite Erweitert)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die erweiterten Eigenschaften des [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Diensts anzeigen und ändern.  
  
## <a name="options"></a>Optionen  
**SQL Server-Ereignisweiterleitung**  
Durch die Optionen in dieser Kategorie wird die Ereignisweiterleitung aktiviert und konfiguriert.  
  
**Ereignisse an anderen Server weiterleiten**  
Leitet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Ereignisse an einen anderen Server weiter.  
  
**Server**  
Wählen Sie den Namen des Servers aus, an den Ereignisse weitergeleitet werden sollen.  
  
**Ereignisse ohne Behandlung**  
Leitet nur Ereignisse ohne Behandlung an den angegebenen Server weiter. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent leitet nur Ereignisse weiter, auf die keine Warnung reagiert.  
  
**Alle Ereignisse**  
Leitet alle Ereignisse weiter. Wenn eine Warnung in der lokalen Instanz auf das Ereignis reagiert, leitet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Ereignis weiter und verarbeitet auch die Warnung.  
  
**Bei diesem Schweregrad des Ereignisses oder darüber**  
Leitet nur Ereignisse weiter, deren Schweregrad der angegebenen Ebene entspricht oder darüber liegt.  
  
**Bedingung für 'CPU im Leerlauf'**  
Durch die Optionen in dieser Kategorie werden die Bedingungen definiert, unter denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Aufträge ausführt, für die CPU-Leerlaufzeitpläne festgelegt sind.  
  
**Bedingung für 'CPU im Leerlauf' definieren**  
Definiert die Bedingungen, unter denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent die CPU als im Leerlauf befindlich betrachtet.  
  
**bei durchschnittlicher CPU-Nutzung unter**  
Prozentualer Wert der CPU-Nutzung, unter dem die CPU als im Leerlauf befindlich betrachtet wird.  
  
**und Verbleiben unterhalb dieser Stufe für**  
Die Zeitspanne, für die die durchschnittliche CPU-Nutzung unterhalb des angegebenen Wertes liegen muss, bevor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Aufträge dem CPU-Leerlaufzeitplan entsprechend ausführt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Anlegen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Verwalten von Ereignissen](../../ssms/agent/manage-events.md)  
  
