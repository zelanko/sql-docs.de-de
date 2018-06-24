---
title: SQL-DMO-Zuordnung zu SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 590f5396-98d5-485e-9b41-728c6ed7cb9d
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d99a665366fc9b5df9ff975d47cfa60dccaf4b4e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046972"
---
# <a name="sql-dmo-mapping-to-smo"></a>SQL-DMO-Zuordnung zu SMO
  SQL Distributed Management Objects (SQL-DMO) ist in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] nicht mehr enthalten, SQL-DMO-Anwendungen sollten für die Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) konvertiert werden. Das SMO-Objektmodell ähnelt SQL-DMO. Daher sind die meisten SQL-DMO-Objekte einem Objekt mit dem gleichen Namen in SMO zugeordnet. Einige SQL-DMO-Objekte wurden beim Übergang zu SMO jedoch geändert oder ganz gestrichen. In dieser Tabelle werden die empfohlenen Aktionen für SQL-DMO-Objekte aufgeführt, die nicht direkt nach SMO konvertiert wurden.  
  
|SQL-DMO-Objekt|Aktion in SMO|  
|---------------------|-------------------|  
|View2-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|AlertSystem-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|Application-Objekt|Entfernt|  
|Backup-Objekt und Backup2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Backup> und <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase> Objekte.|  
|BackupDevice-Objekt|<xref:Microsoft.SqlServer.Management.Smo.BackupDevice> Objekte|  
|BulkCopy-Objekt und BulkCopy2-Objekt|Entfernt und ersetzt durch <xref:Microsoft.SqlServer.Management.Smo.Transfer> Objekt.|  
|Category-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace. Ersetzen von <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCategory> Objekte.|  
|Check-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Check> Objekt|  
|Column-Objekt und Column2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Column> -Objekt.|  
|Configuration-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Configuration> und <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase> Objekte.|  
|ConfigValue-Objekt|<xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> -Objekt.|  
|Database-Objekt und Database2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Database> -Objekt.|  
|DatabaseRole-Objekt und DatabaseRole2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> -Objekt.|  
|DBFile-Objekt|<xref:Microsoft.SqlServer.Management.Smo.DataFile> -Objekt.|  
|DBOption-Objekt und DBOption2-Objekt|In das <xref:Microsoft.SqlServer.Management.Smo.DatabaseOptions>-Objekt verschoben|  
|Default-Objekt und Default2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Default> -Objekt.|  
|DistributionArticle-Objekt und DistributionArticle2-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|DistributionDatabase-Objekt und DistributionDatabase2-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|DistributionPublication-Objekt und DistributionPublication2-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|DistributionSubscription-Objekt und DistributionSubscription2-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|Distributor-Objekt und Distributor2-Objekt|Verschoben, um die <xref:Microsoft.SqlServer.Replication> Namespace.|  
|DRIDefault-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.ScriptingOptions> Objekt.|  
|FileGroup-Objekt und FileGroup2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.FileGroup> -Objekt.|  
|FullTextCatalog-Objekt und FullTextCatalog2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> und <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex> Objekte.|  
|Index-Objekt und Index2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Index> Objekt|  
|IntegratedSecurity-Objekt|Funktionalität in das <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt im <xref:Microsoft.SqlServer.Management.Common>-Namespace verschoben|  
|Job-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.Job> -Objekt. Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|JobFilter-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobFilter> -Objekt. Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|JobHistoryFilter-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobHistoryFilter> -Objekt. Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|JobSchedule-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> -Objekt. Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|JobServer-Objekt und JobServer2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> -Objekt. Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|JobStep-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> -Objekt. Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|Key-Objekt|<xref:Microsoft.SqlServer.Management.Smo.ForeignKey> und <xref:Microsoft.SqlServer.Management.Smo.Index> Objekte.|  
|LinkedServer-Objekt und LinkedServer2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.LinkedServer> -Objekt.|  
|LinkedServerLogin-Objekt|<xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> -Objekt.|  
|LogFile-Objekt|<xref:Microsoft.SqlServer.Management.Smo.LogFile> -Objekt.|  
|Login-Objekt und Login2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Login> -Objekt.|  
|MergeArticle-Objekt und MergeArticle2-Objekt|<xref:Microsoft.SqlServer.Replication.MergeArticle> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|MergeDynamicSnapshotJob-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|MergePublication-Objekt und MergePublication2-Objekt|<xref:Microsoft.SqlServer.Replication.MergePublication> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|MergePullSubscription-Objekt und MergePullSubscription2-Objekt|<xref:Microsoft.SqlServer.Replication.MergePullSubscription> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|MergeSubscription-Objekt|<xref:Microsoft.SqlServer.Replication.MergeSubscription> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|MergeSubsetFilter-Objekt|Verschoben `N:Microsoft.SqlServer.Replication` Namespace.|  
|NameList-Objekt|Entfernt Alternative Funktionalität im <xref:Microsoft.SqlServer.Management.Smo.Scripter> Objekt.|  
|Operator-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|Permission-Objekt und Permission2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.ServerPermission>, <xref:Microsoft.SqlServer.Management.Smo.DatabasePermission>, <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole>, und <xref:Microsoft.SqlServer.Management.Smo.ObjectPermission> Objekte.|  
|Property-Objekt|`Property` -Objekt.|  
|Publisher-Objekt und Publisher2-Objekt|<xref:Microsoft.SqlServer.Replication.ReplicationServer> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|QueryResults-Objekt und QueryResults2-Objekt|Ersetzt durch <xref:System.Data.DataTable> oder <xref:System.Data.DataSet> Systemobjekt.|  
|RegisteredServer-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|RegisteredSubscriber-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|Registry-Objekt und Registry2-Objekt|Entfernt|  
|RemoteLogin-Objekt|<xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt. In den gemeinsamen Namespace verschoben|  
|RemoteServer-Objekt und RemoteServer2-Objekt|<xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt. Verschoben <xref:Microsoft.SqlServer.Management.Common> Namespace.|  
|Replication-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|ReplicationDatabase-Objekt und ReplicationDatabase2-Objekt|<xref:Microsoft.SqlServer.Replication.ReplicationDatabase> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|ReplicationSecurity-Objekt|<xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt. Verschoben <xref:Microsoft.SqlServer.Management.Common> Namespace.|  
|ReplicationStoredProcedure-Objekt und ReplicationStoredProcedure2-Objekt|<xref:Microsoft.SqlServer.Replication.ReplicationStoredProcedure> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|ReplicationTable-Objekt und ReplicationTable2-Objekt|<xref:Microsoft.SqlServer.Replication.ReplicationTable> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|Restore-Objekt und Restore2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Restore> und <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase> Objekte.|  
|Rule-Objekt und Rule2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Rule> Objekt|  
|Schedule-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|ServerGroup-Objekt|Entfernt|  
|ServerRole-Objekt|<xref:Microsoft.SqlServer.Management.Smo.ServerRole> -Objekt.|  
|SQLObjectList-Objekt|<xref:Microsoft.SqlServer.Management.Smo.SqlSmoObject> Array.|  
|SQLServer-Objekt und SQLServer2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Server> -Objekt.|  
|StoredProcedure-Objekt und StoredProcedure2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> und <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> Objekte|  
|Subscriber-Objekt und Subscriber2-Objekt|Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|SystemDatatype-Objekt und SystemDataType2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.DataType> -Objekt.|  
|Table-Objekt und Table2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Table> -Objekt.|  
|TargetServer-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|TargetServerGroup-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|TransactionLog-Objekt|Funktionen, die verschoben werden, in der <xref:Microsoft.SqlServer.Management.Smo.Database> Objekt.|  
|TransArticle-Objekt und TransArticle2-Objekt|<xref:Microsoft.SqlServer.Replication.TransArticle> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|Transfer-Methode und Transfer2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Transfer> -Objekt.|  
|TransPublication-Objekt und TransPublication2-Objekt|<xref:Microsoft.SqlServer.Replication.TransPublication> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|TransPullSubscription-Objekt und TransPullSubscription2-Objekt|<xref:Microsoft.SqlServer.Replication.TransPullSubscription> -Objekt. Verschoben <xref:Microsoft.SqlServer.Replication> Namespace.|  
|Trigger-Objekt und Trigger2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Trigger> -Objekt.|  
|User-Objekt und User2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.User> -Objekt.|  
|UserDefinedDatatype-Objekt und UserDefinedDataType2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> -Objekt.|  
|UserDefinedFunction-Objekt|<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> und <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter> Objekte.|  
|View-Objekt und View2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.View> -Objekt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierungshandbuch für SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  