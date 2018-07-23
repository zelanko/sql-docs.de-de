---
title: Abfragen von Servern | Microsoft-Dokumentation
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
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c2e7ded81d62f01ec739cd02358410bbae299451
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981852"
---
# <a name="poll-servers"></a>Abfragen von Servern
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Wenn die Multiserververwaltung implementiert ist, stellen die Zielserver regelmäßig eine Verbindung mit dem Masterserver her, um Informationen zu ausgeführten Aufträgen hochzuladen und neue Aufträge herunterzuladen. Der Vorgang der Verbindungsherstellung mit dem Masterserver wird als *Serverabruf* bezeichnet und findet in regelmäßigen *Abrufintervallen*statt.  
  
## <a name="polling-intervals"></a>Abrufintervalle  
Das Abrufintervall (standardmäßig eine Minute) steuert, wie oft der Zielserver eine Verbindung mit dem Masterserver herstellt, um Anweisungen herunterzuladen und die Ergebnisse der Auftragsausführung hochzuladen.  
  
Wenn ein Zielserver den Masterserver abruft, liest er die dem Zielserver zugewiesenen Vorgänge aus der **sysdownloadlist** -Tabelle in der **msdb** -Datenbank. Diese Operationen steuern Multiserveraufträge sowie verschiedene Aspekte des Verhaltens eines Zielservers. Dazu gehören beispielsweise das Löschen, Einfügen oder Starten eines Auftrags und das Aktualisieren des Abrufintervalls eines Zielservers.  
  
Vorgänge werden in der **sysdownloadlist** -Tabelle auf eine der folgenden Arten bereitgestellt:  
  
-   Explizit durch Verwenden der gespeicherten Prozedur **sp_post_msx_operation** .  
  
-   Implizit durch Verwenden anderer gespeicherter Auftragsprozeduren.  
  
Wenn Sie gespeicherte Auftragsprozeduren zum Ändern von Multiserver-Auftragszeitplänen oder Multiserverauftragsschritten bzw. von SQL-DMO-Objekten (SQL Distributed Management Objects) zum Steuern von Multiserveraufträgen verwenden, geben Sie den folgenden Befehl nach dem Ändern der Multiserverauftragsschritte oder Multiserver-Auftragszeitpläne aus:  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Durch die Ausgabe dieses Befehls bleiben die Zielserver mit der aktuellen Auftragsdefinition synchronisiert.  
  
Es ist nicht notwendig, Vorgänge explizit bereitzustellen, wenn Sie folgende Elemente verwenden:  
  
-   Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] zum Steuern von Multiserveraufträgen.  
  
-   Gespeicherte Auftragsprozeduren, die weder Auftragszeitpläne noch Auftragsschritte ändern.  
  
**So erzwingen Sie, dass ein Zielserver den Masterserver abruft**  
  
-   [SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Verwalten von Ereignissen](../../ssms/agent/manage-events.md)  
  
