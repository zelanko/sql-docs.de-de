---
title: Auftragseigenschaften – Neuer Auftrag (Seite „Benachrichtigungen“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5d1cc28e21235dfde9c1b7de00d9c97522bab2cc
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65095844"
---
# <a name="job-properties---new-job-notifications-page"></a>Auftragseigenschaften – Neuer Auftrag (Seite „Benachrichtigungen“)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Auf dieser Seite können Sie die Aktionen für den [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent festlegen, die bei Abschluss des Auftrags auszuführen sind.  
  
## <a name="options"></a>enthalten  
**E-Mail**  
Diese Option wird ausgewählt, um bei Abschluss des Auftrags eine E-Mail zu senden. Nachdem Sie die Option ausgewählt haben, müssen Sie den zu benachrichtigenden Operator und die Bedingung auswählen, durch die die Benachrichtigung ausgelöst wird: **Bei erfolgreicher Auftragsausführung**; **bei Auftragsfehler** oder **beim Abschluss des Auftrags**.  
  
**Page**  
Diese Option wird ausgewählt, um eine E-Mail an den Pager des Operators zu senden, wenn der Auftrag abgeschlossen ist. Nachdem Sie die Option ausgewählt haben, müssen Sie den zu benachrichtigenden Operator und die Bedingung angeben, durch die die Benachrichtigung ausgelöst wird: **Bei erfolgreicher Auftragsausführung**; **bei Auftragsfehler** oder **beim Abschluss des Auftrags**.  
  
**NET SEND**  
Diese Option wird ausgewählt, um einen Operator bei Abschluss des Auftrags über net send zu benachrichtigen. Nachdem Sie die Option ausgewählt haben, müssen Sie den zu benachrichtigenden Operator und die Bedingung angeben, durch die die Benachrichtigung ausgelöst wird: **Bei erfolgreicher Auftragsausführung**; **bei Auftragsfehler** oder **beim Abschluss des Auftrags**.  
  
**In das Windows-Anwendungsereignisprotokoll schreiben**  
Diese Option wird ausgewählt, um bei Abschluss des Auftrags einen Eintrag in das Anwendungsereignisprotokoll zu schreiben. Geben Sie nach Auswahl dieser Option die Bedingung an, durch die veranlasst wird, dass der Eintrag geschrieben wird: **Bei erfolgreicher Auftragsausführung**; **bei Auftragsfehler** oder **beim Abschluss des Auftrags**.  
  
**Auftrag automatisch löschen**  
Diese Option wird ausgewählt, um den Auftrag bei Abschluss zu löschen. Geben Sie nach Auswahl dieser Option die Bedingung an, durch die veranlasst wird, dass der Auftrag gelöscht wird: **Bei erfolgreicher Auftragsausführung**; **bei Auftragsfehler** oder **beim Abschluss des Auftrags**.  
  
## <a name="see-also"></a>Weitere Informationen  
[Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)  
[Vorgehensweise: Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails (SQL Server Management Studio)](https://msdn.microsoft.com/4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce)  
  
