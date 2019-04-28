---
title: Externes Datenbank-E-Mail-Programm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- external programs [Database Mail]
- DatabaseMail90.exe
- Database Mail [SQL Server], external programs
ms.assetid: bc124164-eb6e-4b7f-bf66-98a3113d02f7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c617e4f7c069a869935fa4ed83d28c02d0b0b9a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917641"
---
# <a name="database-mail-external-program"></a>Externes Datenbank-E-Mail-Programm
  Die ausführbare Datei für das externe Datenbank-E-Mail-Programm ist **DatabaseMail.exe**und ist im Verzeichnis **MSSQL\Binn** der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installation gespeichert. Datenbank-E-Mail verwendet die Service Broker-Aktivierung, um das externe Programm zu starten, wenn E-Mail-Nachrichten zur Verarbeitung vorhanden sind. Datenbank-E-Mail startet eine Instanz des externen Programms. Das externe Programm wird im Sicherheitskontext des Dienstkontos für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt.  
  
 **In diesem Thema:**  
  
-   [Konzepte des externen Datenbank-E-Mail-Programms](#ComponentsAndConcepts)  
  
-   [Tasks, die sich auf die Konfiguration des externe Datenbank-E-Mail-Programms beziehen](#RelatedTasks)  
  
##  <a name="ComponentsAndConcepts"></a> Konzepte des externen Datenbank-E-Mail-Programms  
 Wenn das externe Programm gestartet wird, stellt das Programm mithilfe der Windows-Authentifizierung eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her und beginnt mit der Verarbeitung von E-Mail-Nachrichten. Wenn keine zu sendenden Nachrichten für den angegebenen Timeoutzeitraum vorhanden sind, wird das Programm beendet. Mithilfe des Assistenten zum Konfigurieren von Datenbank-E-Mail oder der gespeicherten Prozeduren von Datenbank-E-Mail können Sie konfigurieren, nach welcher Wartezeit das Programm beendet wird. Weitere Informationen finden Sie unter [sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)ausgeführt.  
  
 Das externe Programm speichert Informationen in Systemtabellen in der **msdb** -Datenbank. Falls das externe Programm nicht mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kommunizieren kann, protokolliert das Programm Fehler im Microsoft Windows-Anwendungsereignisprotokoll. Eine zusätzliche Meldungsprotokollierung ist verfügbar, wenn der Protokolliergrad im Dialogfeld **Systemparameter konfigurieren** des **Assistenten zum Konfigurieren von Datenbank-E-Mail** auf **Ausführlich**festgelegt wird.  
  
 Beachten Sie, dass das externe Programm aus Gründen der Effizienz Konto- und Profilinformationen zwischenspeichert. Deshalb kann es sein, dass Konfigurationsänderungen an Konten und Profilen erst nach ein paar Minuten im externen Programm angezeigt werden.  
  
##  <a name="RelatedTasks"></a> Tasks, die sich auf die Konfiguration des externe Datenbank-E-Mail-Programms beziehen  
  
|Konfigurationstask|Themenlink|  
|------------------------|----------------|  
|Geben Sie die Zeit für das externe Programm vor dem Beenden an.|[sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [Datenbank-E-Mail-Protokoll und -Überwachung](database-mail-log-and-audits.md)   
 [Datenbank-E-Mail](database-mail.md)  
  
  
