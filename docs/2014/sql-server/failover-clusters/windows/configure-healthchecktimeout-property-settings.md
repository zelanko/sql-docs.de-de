---
title: Konfigurieren der HealthCheckTimeout-Eigenschafteneinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4106de497a43404cb44606259d53beb1ed8f5a58
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "72797454"
---
# <a name="configure-healthchecktimeout-property-settings"></a>Konfigurieren der HealthCheckTimeout-Eigenschafteneinstellungen
  Mit der HealthCheckTimeout-Einstellung wird die Zeitdauer in Millisekunden angegeben, die die Ressourcen-DLL für SQL Server auf Informationen warten soll, die von der gespeicherten Prozedur [sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) zurückgegeben werden, bevor gemeldet wird, dass die AlwaysOn-Failoverclusterinstanz (FCI) nicht reagiert. Änderungen am Timeoutwert werden unmittelbar wirksam; ein Neustart der SQL Server-Ressource ist nicht erforderlich.  
  
-   **Vorbereitungen:**  [Einschränkungen](#Limits), [Sicherheit](#Security)  
  
-   **So konfigurieren Sie die HeathCheckTimeout-Einstellung mit**  [PowerShell](#PowerShellProcedure), [Failovercluster-Manager](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Limits"></a> Einschränkungen  
 Der Standardwert für diese Eigenschaft ist 60.000 Millisekunden (60 Sekunden). Der Mindestwert ist 15.000 Millisekunden (15 Sekunden).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert ALTER SETTINGS- und VIEW SERVER STATE-Berechtigungen.  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell  
  
### <a name="to-configure-healthchecktimeout-settings"></a>So konfigurieren Sie die HealthCheckTimeout-Einstellungen  
  
1.  Starten Sie eine erhöhte Windows PowerShell mittels **Als Administrator ausführen**.  
  
2.  Importieren Sie das `FailoverClusters`-Modul, um die Cluster-Cmdlets zu aktivieren.  
  
3.  Verwenden Sie `Get-ClusterResource` das Cmdlet, um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Ressource zu suchen `Set-ClusterParameter` , und legen Sie dann mit dem Cmdlet die **healthchecktimeout** -Eigenschaft für die Failoverclusterinstanz fest.  
  
> [!TIP]  
>  Bei jedem Öffnen eines neuen PowerShell-Fensters müssen Sie das `FailoverClusters`-Modul importieren.  

 Im folgenden Beispiel wird die Einstellung HealthCheckTimeout auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource "`SQL Server (INST1)`" zu 60.000 Millisekunden geändert.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
```  
  
### <a name="related-content-powershell"></a>Verwandte Inhalte (PowerShell)  
  
-   [Clustering and High-Availability](https://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (Clustering und hohe Verfügbarkeit) (Failoverclustering und Netzwerklastenausgleichs-Teamblog)  
  
-   [Erste Schritte mit Windows PowerShell auf einem Failovercluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Clusterressourcenbefehle und entsprechende Windows PowerShell-Cmdlets](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> Verwenden des Failovercluster-Manager-Snap-Ins  
 **So konfigurieren Sie die HealthCheckTimeout-Einstellung**  
  
1.  Öffnen Sie des Failovercluster-Manager-Snap-In.  
  
2.  Erweitern Sie **Dienste und Anwendungen** , und wählen Sie den FCI aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die **SQL Server-Ressource** unter **Sonstige Ressourcen** , und wählen Sie im Kontextmenü **Eigenschaften** aus. Das Dialogfeld **Eigenschaften** der SQL Server-Ressource wird angezeigt.  
  
4.  Wählen Sie die Registerkarte **Eigenschaften** aus, geben Sie den gewünschten Wert für die **HealthCheckTimeout** -Eigenschaft ein, und klicken Sie dann auf **OK** , um die Änderung zu übernehmen.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Mithilfe der [Alter Server Configuration](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung können Sie den healthchecktimeout-Eigenschafts Wert angeben.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die Option HealthCheckTimeout auf 15.000 Millisekunden (15 Sekunden) festgelegt.  
  
```sql
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Failoverrichtlinie für Failoverclusterinstanzen](failover-policy-for-failover-cluster-instances.md)  
