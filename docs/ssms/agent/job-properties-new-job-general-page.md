---
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
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e089aa61b1c55d5761ba28db840171c1cc28dfb3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75242294"
---
# <a name="job-properties---new-job-general-page"></a>Auftragseigenschaften – Neuer Auftrag (Seite „Allgemein“)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

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
  
**Aktiviert**  
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
  
