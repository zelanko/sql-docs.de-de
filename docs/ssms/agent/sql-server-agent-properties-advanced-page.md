---
title: SQL Server-Agent-Eigenschaften (Seite Erweitert)|Microsoft-Dokumente
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 35f4eaba0ff477e6577b4805a02db2c668f647ae
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42776342"
---
# <a name="sql-server-agent-properties-advanced-page"></a>SQL Server-Agent-Eigenschaften (Seite Erweitert)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die erweiterten Eigenschaften des [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Anlegen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Verwalten von Ereignissen](../../ssms/agent/manage-events.md)  
  
