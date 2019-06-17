---
title: SQL-DMO-Zuordnung zu SMO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 590f5396-98d5-485e-9b41-728c6ed7cb9d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a6273032f88807291bfc7024f1abcdbd1440073
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62780680"
---
# <a name="sql-dmo-mapping-to-smo"></a>SQL-DMO-Zuordnung zu SMO
  SQL Distributed Management Objects (SQL-DMO) ist in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]nicht mehr enthalten, SQL-DMO-Anwendungen sollten für die Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) konvertiert werden. Das SMO-Objektmodell ähnelt SQL-DMO. Daher sind die meisten SQL-DMO-Objekte einem Objekt mit dem gleichen Namen in SMO zugeordnet. Einige SQL-DMO-Objekte wurden beim Übergang zu SMO jedoch geändert oder ganz gestrichen. In dieser Tabelle werden die empfohlenen Aktionen für SQL-DMO-Objekte aufgeführt, die nicht direkt nach SMO konvertiert wurden.  
  
|SQL-DMO-Objekt|Aktion in SMO|  
|---------------------|-------------------|  
|View2-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|AlertSystem-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace.|  
|Application-Objekt|Entfernt|  
|Backup-Objekt und Backup2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Backup>-Objekt und <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>-Objekt|  
|BackupDevice-Objekt|<xref:Microsoft.SqlServer.Management.Smo.BackupDevice> Objekte|  
|BulkCopy-Objekt und BulkCopy2-Objekt|Entfernt und durch das <xref:Microsoft.SqlServer.Management.Smo.Transfer>-Objekt ersetzt|  
|Category-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.Agent> Namespace. Durch das <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCategory>-, <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCategory>-Objekt und <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCategory>-Objekt ersetzt|  
|Check-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Check> Objekt|  
|Column-Objekt und Column2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Column>-Objekt|  
|Configuration-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Configuration>-Objekt und <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase>-Objekt|  
|ConfigValue-Objekt|<xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>-Objekt|  
|Database-Objekt und Database2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Database>-Objekt|  
|DatabaseRole-Objekt und DatabaseRole2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.DatabaseRole>-Objekt|  
|DBFile-Objekt|<xref:Microsoft.SqlServer.Management.Smo.DataFile>-Objekt|  
|DBOption-Objekt und DBOption2-Objekt|In das <xref:Microsoft.SqlServer.Management.Smo.DatabaseOptions>-Objekt verschoben|  
|Default-Objekt und Default2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Default>-Objekt|  
|DistributionArticle-Objekt und DistributionArticle2-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|DistributionDatabase-Objekt und DistributionDatabase2-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|DistributionPublication-Objekt und DistributionPublication2-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|DistributionSubscription-Objekt und DistributionSubscription2-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|Distributor-Objekt und Distributor2-Objekt|Verschoben werden, um die <xref:Microsoft.SqlServer.Replication> Namespace.|  
|DRIDefault-Objekt|Verschoben <xref:Microsoft.SqlServer.Management.Smo.ScriptingOptions> Objekt.|  
|FileGroup-Objekt und FileGroup2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.FileGroup>-Objekt|  
|FullTextCatalog-Objekt und FullTextCatalog2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog>-Objekt und <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex>-Objekt|  
|Index-Objekt und Index2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Index> Objekt|  
|IntegratedSecurity-Objekt|Funktionalität in das <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt im <xref:Microsoft.SqlServer.Management.Common>-Namespace verschoben|  
|Job-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.Job>-Objekt In den <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace verschoben|  
|JobFilter-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobFilter>-Objekt In den <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace verschoben|  
|JobHistoryFilter-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobHistoryFilter>-Objekt In den <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace verschoben|  
|JobSchedule-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule>-Objekt In den <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace verschoben|  
|JobServer-Objekt und JobServer2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer>-Objekt In den <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace verschoben|  
|JobStep-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep>-Objekt In den <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace verschoben|  
|Key-Objekt|<xref:Microsoft.SqlServer.Management.Smo.ForeignKey>-Objekt und <xref:Microsoft.SqlServer.Management.Smo.Index>-Objekt|  
|LinkedServer-Objekt und LinkedServer2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.LinkedServer>-Objekt|  
|LinkedServerLogin-Objekt|<xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>-Objekt|  
|LogFile-Objekt|<xref:Microsoft.SqlServer.Management.Smo.LogFile>-Objekt|  
|Login-Objekt und Login2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Login>-Objekt|  
|MergeArticle-Objekt und MergeArticle2-Objekt|<xref:Microsoft.SqlServer.Replication.MergeArticle>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|MergeDynamicSnapshotJob-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|MergePublication-Objekt und MergePublication2-Objekt|<xref:Microsoft.SqlServer.Replication.MergePublication>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|MergePullSubscription-Objekt und MergePullSubscription2-Objekt|<xref:Microsoft.SqlServer.Replication.MergePullSubscription>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|MergeSubscription-Objekt|<xref:Microsoft.SqlServer.Replication.MergeSubscription>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|MergeSubsetFilter-Objekt|In den `N:Microsoft.SqlServer.Replication`-Namespace verschoben|  
|NameList-Objekt|Entfernt Alternative Funktionalität im <xref:Microsoft.SqlServer.Management.Smo.Scripter>-Objekt|  
|Operator-Objekt|In den <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace verschoben|  
|Permission-Objekt und Permission2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.ServerPermission>-Objekt, <xref:Microsoft.SqlServer.Management.Smo.DatabasePermission>-Objekt <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> und <xref:Microsoft.SqlServer.Management.Smo.ObjectPermission>-Objekt|  
|Property-Objekt|`Property`-Objekt|  
|Publisher-Objekt und Publisher2-Objekt|<xref:Microsoft.SqlServer.Replication.ReplicationServer>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|QueryResults-Objekt und QueryResults2-Objekt|Durch das <xref:System.Data.DataTable>-Objekt oder das <xref:System.Data.DataSet>-Systemobjekt ersetzt|  
|RegisteredServer-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|RegisteredSubscriber-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|Registry-Objekt und Registry2-Objekt|Entfernt|  
|RemoteLogin-Objekt|<xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt In den gemeinsamen Namespace verschoben|  
|RemoteServer-Objekt und RemoteServer2-Objekt|<xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt In den <xref:Microsoft.SqlServer.Management.Common>-Namespace verschoben|  
|Replication-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|ReplicationDatabase-Objekt und ReplicationDatabase2-Objekt|<xref:Microsoft.SqlServer.Replication.ReplicationDatabase>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|ReplicationSecurity-Objekt|<xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt In den <xref:Microsoft.SqlServer.Management.Common>-Namespace verschoben|  
|ReplicationStoredProcedure-Objekt und ReplicationStoredProcedure2-Objekt|<xref:Microsoft.SqlServer.Replication.ReplicationStoredProcedure>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|ReplicationTable-Objekt und ReplicationTable2-Objekt|<xref:Microsoft.SqlServer.Replication.ReplicationTable>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|Restore-Objekt und Restore2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Restore>-Objekt und <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>-Objekt|  
|Rule-Objekt und Rule2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Rule> Objekt|  
|Schedule-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|ServerGroup-Objekt|Entfernt|  
|ServerRole-Objekt|<xref:Microsoft.SqlServer.Management.Smo.ServerRole>-Objekt|  
|SQLObjectList-Objekt|<xref:Microsoft.SqlServer.Management.Smo.SqlSmoObject> Array.|  
|SQLServer-Objekt und SQLServer2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt|  
|StoredProcedure-Objekt und StoredProcedure2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> und <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> Objekte|  
|Subscriber-Objekt und Subscriber2-Objekt|In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|SystemDatatype-Objekt und SystemDataType2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.DataType>-Objekt|  
|Table-Objekt und Table2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Table>-Objekt|  
|TargetServer-Objekt|In den <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace verschoben|  
|TargetServerGroup-Objekt|In den <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace verschoben|  
|TransactionLog-Objekt|Funktionalität in das <xref:Microsoft.SqlServer.Management.Smo.Database>-Objekt verschoben|  
|TransArticle-Objekt und TransArticle2-Objekt|<xref:Microsoft.SqlServer.Replication.TransArticle>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|Transfer-Methode und Transfer2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Transfer>-Objekt|  
|TransPublication-Objekt und TransPublication2-Objekt|<xref:Microsoft.SqlServer.Replication.TransPublication>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|TransPullSubscription-Objekt und TransPullSubscription2-Objekt|<xref:Microsoft.SqlServer.Replication.TransPullSubscription>-Objekt In den <xref:Microsoft.SqlServer.Replication>-Namespace verschoben|  
|Trigger-Objekt und Trigger2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.Trigger>-Objekt|  
|User-Objekt und User2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.User>-Objekt|  
|UserDefinedDatatype-Objekt und UserDefinedDataType2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>-Objekt|  
|UserDefinedFunction-Objekt|<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>-Objekt und <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>-Objekt|  
|View-Objekt und View2-Objekt|<xref:Microsoft.SqlServer.Management.Smo.View>-Objekt|  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierungshandbuch für SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
