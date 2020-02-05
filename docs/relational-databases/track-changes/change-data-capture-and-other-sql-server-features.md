---
title: Change Data Capture und andere SQL Server-Funktionen
ms.custom: seo-dt-2019
ms.date: 01/02/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], other SQL Server features and
ms.assetid: 7dfcb362-1904-4578-8274-da16681a960e
author: rothja
ms.author: jroth
ms.openlocfilehash: e29ad6de65172b08bb3f35aa89820ca817a9e1d3
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "74095299"
---
# <a name="change-data-capture-and-other-sql-server-features"></a>Change Data Capture und andere SQL Server-Funktionen
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie die folgenden Funktionen mit Change Data Capture interagieren:  
  
-   [Änderungsnachverfolgung](#ChangeTracking)  
  
-   [Spiegeln von Datenbanken](#DatabaseMirroring)  
  
-   [Transaktionsreplikation](#TransReplication)  
  
-   [Wiederherstellen oder Anfügen einer Datenbank, die für Change Data Capture aktiviert ist](#RestoreOrAttach)

-   [Eigenständige Datenbanken](#Contained)
  
##  <a name="ChangeTracking"></a> Änderungsnachverfolgung  
 Change Data Capture und die [Änderungsnachverfolgung](../../relational-databases/track-changes/about-change-tracking-sql-server.md) können für dieselbe Datenbank aktiviert werden. Dabei sind keine besonderen Aspekte zu berücksichtigen. Weitere Informationen finden Sie unter [Verwenden der Änderungsnachverfolgung &#40;SQL Server&#41;](../../relational-databases/track-changes/work-with-change-tracking-sql-server.md).  
  
##  <a name="DatabaseMirroring"></a> Datenbankspiegelung  
 Eine Datenbank, die für Change Data Capture aktiviert ist, kann gespiegelt werden. Um sicherzustellen, dass Erfassungen und Cleanups nach einem Failover automatisch durchgeführt werden, führen Sie folgende Schritte aus:  
  
1.  Stellen Sie sicher, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent auf der neuen Prinzipalserverinstanz ausgeführt wird.  
  
2.  Erstellen Sie den Erfassungs- und Cleanupauftrag in der neuen Prinzipaldatenbank (der vorherigen Spiegeldatenbank). Verwenden Sie zum Erstellen der Aufträge die gespeicherte [sp_cdc_add_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md) -Prozedur.  
  
 Um die aktuelle Konfiguration eines Cleanup- oder Erfassungsauftrags anzuzeigen, verwenden Sie die gespeicherte [sys.sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md) -Prozedur in der neuen Prinzipalserverinstanz. Für eine gegebene Datenbank heißt der Erfassungsauftrag cdc.*Datenbank\_name*\_capture und der Cleanupauftrag cdc.*Datenbank\_name*\_cleanup wobei *Datenbank_name* der Name der entsprechenden Datenbank ist.  
  
 Um die Konfiguration eines Auftrags zu ändern, verwenden Sie die gespeicherte [sys.sp_cdc_change_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md) -Prozedur.  
  
 Informationen zur Datenbankspiegelung finden Sie unter [ Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
##  <a name="TransReplication"></a> Transactional Replication  
 Change Data Capture und die Transaktionsreplikation können in einer Datenbank parallel vorhanden sein, allerdings wird die Auffüllung der Änderungstabellen anders behandelt, wenn beide Funktionen aktiviert sind. Change Data Capture und die Transaktionsreplikation verwenden immer dieselbe Prozedur, nämlich [sp_replcmds](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md), um die Änderungen aus dem Transaktionsprotokoll auszulesen. Wenn Change-Data-Capture allein aktiviert ist, ruft ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentauftrag die Prozedur **sp_replcmds**auf. Wenn für eine Datenbank beide Funktionen aktiviert sind, ruft der Protokolllese-Agent die Prozedur **sp_replcmds**auf. Dieser Agent füllt sowohl die Änderungstabellen als auch die Tabellen der Verteilungsdatenbank auf. Weitere Informationen finden Sie unter [Replication Log Reader Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md).  
  
 Angenommen, Change Data Capture ist für die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank aktiviert, und zwei Tabellen sind für die Erfassung aktiviert. Um die Änderungstabellen aufzufüllen, ruft der Capture-Auftrag **sp_replcmds**auf. Die Datenbank wird für die Transaktionsreplikation aktiviert, und eine Veröffentlichung wird erstellt. Anschließend wird der Protokolllese-Agent für die Datenbank erstellt, und der Erfassungsauftrag wird gelöscht. Der Protokolllese-Agent fährt fort, das Protokoll ab der letzten Protokollfolgenummer zu durchsuchen, für die ein Commit in die Änderungstabelle ausgeführt wurde. Auf diese Weise wird die Datenkonsistenz in den Änderungstabellen sichergestellt. Wenn die Transaktionsreplikation in dieser Datenbank deaktiviert wird, wird der Protokolllese-Agent entfernt und der Aufzeichnungsauftrag neu erstellt.  
  
> [!NOTE]  
>  Falls der Protokolllese-Agent sowohl für Change Data Capture als auch für die Transaktionsreplikation verwendet wird, werden die replizierten Änderungen zuerst in die Verteilungsdatenbank geschrieben. Anschließend werden erfasste Änderungen in die Änderungstabellen geschrieben. Der Commit wird für beide Vorgänge zusammen ausgeführt. Wenn beim Schreiben in die Verteilungsdatenbank eine Latenz auftritt, werden Änderungen in den Änderungstabellen auch erst nach dieser Latenzzeit angezeigt.  
  
 Die **proc exec** -Option der Transaktionsreplikation ist nicht verfügbar, wenn Change Data Capture aktiviert ist.  
  
##  <a name="RestoreOrAttach"></a> Wiederherstellen oder Anfügen einer Datenbank, die für Change Data Capture aktiviert ist  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet die folgende Logik, um zu ermitteln, ob Change Data Capture nach dem Wiederherstellen oder Anfügen einer Datenbank aktiviert bleibt:  
  
-   Wenn eine Datenbank auf demselben Server mit demselben Datenbanknamen wiederhergestellt wird, bleibt Change Data Capture aktiviert.  
  
-   Wenn eine Datenbank auf einem anderen Server wiederhergestellt wird, wird Change Data Capture standardmäßig deaktiviert, und alle zugehörigen Metadaten werden gelöscht.  
  
     Um Change-Data-Capture beizubehalten, verwenden Sie beim Wiederherstellen der Datenbank die **KEEP_CDC** -Option. Weitere Informationen zu dieser Option finden Sie unter [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md).  
  
-   Wenn eine Datenbank getrennt und an denselben Server oder einen anderen Server angefügt wird, bleibt Change Data Capture aktiviert.  
  
-   Wenn eine Datenbank mit der Option **KEEP_CDC** an eine andere Edition als die Standard oder Enterprise Edition angefügt oder dafür wiederhergestellt wird, wird der Vorgang blockiert, weil für Change-Data-Capture die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard oder Enterprise Edition erforderlich ist. Die Fehlermeldung 934 wird angezeigt:  
  
     `SQL Server cannot load database '%.*ls' because Change Data Capture is enabled. The currently installed edition of SQL Server does not support Change Data Capture. Either restore database without KEEP_CDC option, or upgrade the instance to one that supports Change Data Capture.`  
  
 Sie können [sys.sp_cdc_disable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md) verwenden, um Change Data Capture aus einer wiederhergestellten oder angefügten Datenbank zu entfernen.  
  
##  <a name="Contained"></a> Eigenständige Datenbanken  
 Change Data Capture wird in [enthaltenen Datenbanken](../../relational-databases/databases/contained-databases.md) nicht unterstützt.
  
## <a name="change-data-capture-and-always-on"></a>Change Data Capture und AlwaysOn  
 Bei Verwendung von AlwaysOn sollte die Änderungsenumeration auf dem sekundären Replikat erfolgen, um die Datenträgerlast auf dem primären Replikat zu verringern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten und Überwachen von Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
