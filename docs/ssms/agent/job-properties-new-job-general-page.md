---
title: Auftragseigenschaften – Neuer Auftrag (Seite „Allgemein“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1ba6b2700ca49b1b649dae2b1c05320d8cf4a001
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47676128"
---
# <a name="job-properties---new-job-general-page"></a>Auftragseigenschaften – Neuer Auftrag (Seite „Allgemein“)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die allgemeinen Eigenschaften eines Agentauftrags in [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzeigen und ändern.  
  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)  
[Auftragskategorien – Auftragskategorien verwalten](../../ssms/agent/job-categories-manage-job-categories.md)  
  
