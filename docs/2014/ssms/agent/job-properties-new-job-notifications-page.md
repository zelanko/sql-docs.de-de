---
title: 'Auftragseigenschaften: Neuer Auftrag (Seite "Benachrichtigungen") | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10cee6f0d5bf62178c71d25b8eb5682c22bbbe3b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52797687"
---
# <a name="job-properties-new-job-notifications-page"></a>Auftragseigenschaften: Neuer Auftrag (Seite "Benachrichtigungen")
  Auf dieser Seite können Sie die Aktionen für den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent festlegen, die bei Abschluss des Auftrags auszuführen sind.  
  
## <a name="options"></a>Optionen  
 **E-Mail**  
 Diese Option wird ausgewählt, um bei Abschluss des Auftrags eine E-Mail zu senden. Wählen Sie nach Auswahl dieser Option an, die den zu benachrichtigenden Operator und die Bedingung, die die Benachrichtigung ausgelöst wird: **Bei erfolgreicher auftragsausführung**; **Bei Fehlschlagen des Auftrags**; oder **beim Abschluss des Auftrags**.  
  
 **Seite**  
 Diese Option wird ausgewählt, um eine E-Mail an den Pager des Operators zu senden, wenn der Auftrag abgeschlossen ist. Geben Sie nach Auswahl dieser Option den zu benachrichtigenden Operator und die Bedingung, die die Benachrichtigung ausgelöst wird: **Bei erfolgreicher auftragsausführung**; **Bei Fehlschlagen des Auftrags**; oder **beim Abschluss des Auftrags**.  
  
 **NET SEND**  
 Diese Option wird ausgewählt, um einen Operator bei Abschluss des Auftrags über net send zu benachrichtigen. Geben Sie nach Auswahl dieser Option den zu benachrichtigenden Operator und die Bedingung, die die Benachrichtigung ausgelöst wird: **Bei erfolgreicher auftragsausführung**; **Bei Fehlschlagen des Auftrags**; oder **beim Abschluss des Auftrags**.  
  
 **In das Windows-Anwendungsereignisprotokoll schreiben**  
 Diese Option wird ausgewählt, um bei Abschluss des Auftrags einen Eintrag in das Anwendungsereignisprotokoll zu schreiben. Geben Sie nach Auswahl dieser Option die Bedingung, die die zu schreibenden Eintrags bewirkt: **Bei erfolgreicher auftragsausführung**; **Bei Fehlschlagen des Auftrags**; oder **beim Abschluss des Auftrags**.  
  
 **Auftrag automatisch löschen**  
 Diese Option wird ausgewählt, um den Auftrag bei Abschluss zu löschen. Geben Sie nach Auswahl dieser Option die Bedingung, die der Auftrag gelöscht auslösen: **Bei erfolgreicher auftragsausführung**; **Bei Fehlschlagen des Auftrags**; oder **beim Abschluss des Auftrags**.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Aufträgen](implement-jobs.md)   
 [Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  
