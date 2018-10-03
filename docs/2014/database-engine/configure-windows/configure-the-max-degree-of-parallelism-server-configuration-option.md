---
title: Konfigurieren der Serverkonfigurationsoption „Max. Grad an Parallelität“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 336c34d5fa04f09ea907c7ce61620d7ae034a9fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201770"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Max. Grad an Parallelität
  In diesem Thema wird beschrieben, wie so konfigurieren Sie die `max degree of parallelism` Serverkonfigurationsoption in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]. Wenn eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Computer mit mehreren Mikroprozessoren oder CPUs ausgeführt wird, wird der am besten geeignete Grad an Parallelität erkannt, also die Anzahl an Prozessoren, die für die Ausführung einer einzigen Anweisung eingesetzt werden. Dies gilt für die einzelnen Ausführungen paralleler Pläne. Sie können mithilfe der `max degree of parallelism`-Option die Anzahl der Prozessoren beschränken, die für die Ausführung paralleler Pläne verwendet werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] berücksichtigt die Ausführung paralleler Pläne für Abfragen, Data Definition Language (DDL) Indexvorgänge und statische und keysetgesteuerte cursorauffüllung.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Max. Grad an Parallelität option verwenden:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**[nach dem Konfigurieren der Max. Grad an Parallelität (Option)  ](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn die Option Affinity Mask nicht auf den Standardwert festgelegt ist, steht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Systemen mit symmetrischem Multiprocessing (SMP) möglicherweise nur eine beschränkte Anzahl an Prozessoren zur Verfügung.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   Um den Server für die Ermittlung des maximalen Parallelitätsgrads zu aktivieren, legen Sie diese Option auf den Standardwert 0 fest. Durch das Festlegen des maximalen Parallelitätsgrads auf 0 kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle verfügbaren Prozessoren verwenden (bis maximal 64 Prozessoren). Legen Sie `max degree of parallelism` auf 1 fest, um das Generieren paralleler Pläne zu unterdrücken. Legen Sie den Wert auf eine Zahl von 1 bis 32.767 fest, um die maximale Anzahl von Prozessorkernen anzugeben, die von einer einzelnen Abfrageausführung verwendet werden können. Wenn ein Wert angegeben wird, der über der Anzahl der verfügbaren Prozessoren liegt, wird die tatsächliche Anzahl der Prozessoren verwendet. Verfügt der Computer nur über einen Prozessor, wird der Wert von `max degree of parallelism` ignoriert.  
  
-   In Abfragen kann der Wert "Max. Grad an Parallelität" überschrieben werden; geben Sie hierzu den Abfragehinweis MAXDOP in der Abfrageanweisung an. Weitere Informationen finden Sie unter [Abfragehinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).  
  
-   Indizierungsoperationen, bei denen ein Index erstellt oder neu aufgebaut wird bzw. an deren Ende ein gruppierter Index steht, können ressourcenintensiv sein. In Indizierungsoperationen kann der Wert "Max. Grad an Parallelität" überschrieben werden; geben Sie hierzu die Indexoption MAXDOP in der Indexanweisung an. Der Wert MAXDOP wird zur Ausführungszeit auf die Anweisung angewendet und wird nicht in den Metadaten für den Index gespeichert. Weitere Informationen finden Sie unter [Konfigurieren von Parallelindexvorgängen](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
-   Neben Abfragen und Indexoperationen steuert diese Option auch die Parallelität von DBCC CHECKTABLE, DBCC CHECKDB und DBCC CHECKFILEGROUP. Sie können Pläne für die parallele Ausführung für diese Anweisungen deaktivieren, und zwar mithilfe des Ablaufverfolgungsflags 2528. Weitere Informationen finden Sie unter [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>So konfigurieren Sie die Option Max. Grad an Parallelität  
  
1.  Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften**aus.  
  
2.  Klicken Sie auf den **Erweitert** -Knoten.  
  
3.  Wählen Sie im Feld **Max. Grad an Parallelität** die maximale Anzahl der Prozessoren aus, die bei der Ausführung paralleler Pläne verwendet werden sollen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>So konfigurieren Sie die Option Max. Grad an Parallelität  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um die Option `max degree of parallelism` auf `8`festzulegen.  
  
```tsql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 8;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="FollowUp"></a> Nachverfolgung: Nach dem Konfigurieren der Option Max. Grad an Parallelität  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Siehe auch  
 [Affinitätsmaske (Serverkonfigurationsoption)](affinity-mask-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DBCC CHECKTABLE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)   
 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [DBCC CHECKFILEGROUP (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql)   
 [Konfigurieren von Parallelindexvorgängen](../../relational-databases/indexes/configure-parallel-index-operations.md)   
 [Abfragehinweise (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)   
 [Festlegen von Indexoptionen](../../relational-databases/indexes/set-index-options.md)  
  
  
