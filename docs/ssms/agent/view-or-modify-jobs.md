---
title: Anzeigen oder Ändern von Aufträgen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 93a81e3cc2dc7990c2bbf0207e72d258923eae66
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75257538"
---
# <a name="view-or-modify-jobs"></a>Anzeigen oder Ändern von Aufträgen
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Jeden Auftrag, den Sie erstellt haben, können Sie anzeigen. Nachdem Sie einen Auftrag ausgeführt haben, können Sie auch den Auftragsverlauf anzeigen. Auf diese Weise erfahren Sie, wann der Auftrag ausgeführt wurde, den Status des Auftrags insgesamt sowie den Status jedes Auftragsschritts. Sie sehen, ob bei dem Auftrag in der Vergangenheit jemals ein Fehler aufgetreten ist, wann der Auftrag zuletzt erfolgreich ausgeführt wurde sowie welche Ausgabe bei jeder Ausführung des Auftrags erstellt wurde. Mitglieder der festen Serverrolle **sysadmin** können jeden Auftrag anzeigen oder ändern, unabhängig vom Besitzer.  
  
> [!NOTE]  
> Ein Auftrag muss mindestens einmal ausgeführt worden sein, damit ein Auftragsverlauf vorhanden ist. Sie können die Gesamtgröße des Auftragsverlaufsprotokolls und die Größe pro Auftrag begrenzen.  
  
Schließlich können Sie einen Auftrag an neue Anforderungen anpassen. Sie können Folgendes ändern:  
  
-   Benachrichtigungsoptionen  
  
-   Zeitpläne  
  
-   Auftragsschritte  
  
-   Besitz  
  
-   Auftragskategorie  
  
-   Zielserver (ausschließlich bei Multiserveraufträgen)  
  
Wenn Sie Änderungen an Multiserveraufträgen vornehmen, müssen Sie die Änderungen der Downloadliste bereitstellen, damit die Zielserver den aktualisierten Auftrag herunterladen können. Um sicherzustellen, dass die Zielserver über die aktuellsten Auftragsdefinitionen verfügen, führen Sie nach dem Aktualisieren des Multiserverauftrags wie folgt eine INSERT-Anweisung aus:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Weitere Informationen finden Sie unter [sp_purge_jobhistory (Transact-SQL)](https://msdn.microsoft.com/237f9bad-636d-4262-9bfb-66c034a43e88).  
  
Mitglieder der festen Serverrolle **sysadmin** können die Definition oder den Verlauf jedes Auftrags anzeigen und können jeden Auftrag ändern.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Beschreibt, wie [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträge angezeigt werden.|[Anzeigen eines Auftrags](../../ssms/agent/view-a-job.md)|  
|Beschreibt, wie das Auftragsverlaufsprotokoll des [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents angezeigt wird.|[Anzeigen des Auftragsverlaufs](../../ssms/agent/view-the-job-history.md)|  
|Beschreibt, wie der Inhalt des Auftragsverlaufsprotokolls des [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents gelöscht wird.|[Löschen des Auftragsverlaufsprotokolls](../../ssms/agent/clear-the-job-history-log.md)|  
|Beschreibt, wie Größenbeschränkungen für Auftragsverlaufsprotokolle des [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents festgelegt werden.|[Resize the Job History Log](../../ssms/agent/resize-the-job-history-log.md)|  
|Beschreibt, wie die Eigenschaften von [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträgen geändert werden.|[Ändern eines Auftrags](../../ssms/agent/modify-a-job.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
[sysjobhistory](../../relational-databases/system-tables/dbo-sysjobhistory-transact-sql.md)  
  
