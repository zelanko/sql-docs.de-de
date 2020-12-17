---
description: Auftragseigenschaften – Neuer Auftrag (Seite „Allgemein“)
title: Auftragseigenschaften – Neuer Auftrag (Seite „Allgemein“)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 992a0ecbc8ec36ce88ca44490d04a6354828a116
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97408886"
---
# <a name="job-properties---new-job-general-page"></a>Auftragseigenschaften – Neuer Auftrag (Seite „Allgemein“)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die allgemeinen Eigenschaften eines [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agentauftrags anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
**Name**  
Ändern Sie den Namen des Auftrags.  
  
**Besitzer**  
Wählen Sie den Besitzer für den Auftrag aus.  
  
**Kategorie**  
Wählen Sie die Auftragskategorie für den Auftrag aus.  
  
**...**  
Zeigt die Aufträge in der ausgewählten Kategorie an.  
  
**Beschreibung**  
Ändern Sie die Beschreibung des Auftrags.  
  
**Enabled**  
Aktivieren Sie den Auftrag. Wenn der Auftrag nicht aktiviert ist, wird er nicht als Antwort auf einen Zeitplan oder eine Warnung ausgeführt. Sie können den Auftrag jedoch weiterhin mithilfe der gespeicherten Prozedur **sp_start_job** starten.  
  
**Quelle**  
Zeigt den Masterserver für den Auftrag an. Nur auf der Seite **Auftragseigenschaften– Allgemein** verfügbar.  
  
**Erstellt**  
Zeigt das Datum und die Uhrzeit der Auftragserstellung an. Nur auf der Seite **Auftragseigenschaften– Allgemein** verfügbar.  
  
**Zuletzt geändert**  
Zeigt das Datum und die Uhrzeit der letzten Änderung des Auftrags an. Nur auf der Seite **Auftragseigenschaften– Allgemein** verfügbar.  
  
**Zuletzt ausgeführt**  
Zeigt das Datum und die Uhrzeit des Starts der letzten Ausführung des Auftrags an. Nur auf der Seite **Auftragseigenschaften– Allgemein** verfügbar.  
  
**Auftragsverlauf anzeigen**  
Zeigt den Auftragsverlauf für den Auftrag an. Nur auf der Seite **Auftragseigenschaften– Allgemein** verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
[Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)  
[Auftragskategorien – Auftragskategorien verwalten](../../ssms/agent/job-categories-manage-job-categories.md)  
