---
title: Zeitplan für Auftrag auswählen | Microsoft-Dokumentation
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
- sql13.ag.job.pickscheduleforjob.f1
helpviewer_keywords:
- Pick Schedule for Job dialog box
ms.assetid: 6de2025d-c25c-47b9-9a25-18c294935c15
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c561bb6100bb06318195f4c7a461056f35c65647
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38064658"
---
# <a name="pick-schedule-for-job"></a>Zeitplan für Auftrag auswählen
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Wählen Sie in diesem Dialogfeld einen vorhandenen Zeitplan für den Auftrag des [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Agents aus.  
  
## <a name="options"></a>Tastatur  
**Verfügbare Zeitpläne**  
Führt die verfügbaren Zeitpläne für diesen Auftrag auf. Weil ein Auftrag und ein Zeitplan denselben Besitzer haben müssen, enthält diese Liste nur Zeitpläne, die dem Besitzer des Auftrags gehören.  
  
**Name**  
Zeigt den Namen des Zeitplans an.  
  
**Enabled**  
Ausgewählt, wenn der Zeitplan aktiviert ist.  
  
**Beschreibung**  
Beschreibt die Bedingungen, unter denen der Zeitplan den Auftrag ausführt.  
  
**Aufträge im Zeitplan**  
Listet die Auftragsnummern auf, die an den Zeitplan angefügt sind. Wenn Sie auf eine Nummer klicken, zeigen Sie die Eigenschaften des Auftrags an.  
  
**Eigenschaften**  
Öffnet das Dialogfeld **Eigenschaften des Auftragszeitplans** , in dem Sie Informationen zum Zeitplan anzeigen können.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Anlegen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
  
