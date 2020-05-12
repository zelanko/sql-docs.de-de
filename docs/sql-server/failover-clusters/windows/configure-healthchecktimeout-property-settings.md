---
title: Konfigurieren von HealthCheckTimeout für eine Verfügbarkeitsgruppe
description: Konfigurieren Sie HealthCheckTimeout für eine Always On-Verfügbarkeitsgruppe, um anzugeben, wie lange die SQL Server-Ressourcen-DLL warten soll, bevor sie meldet, dass die Verfügbarkeitsgruppe nicht reagiert.
ms.custom: seo-lt-2019
ms.date: 03/09/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3baf48a747db8dfdc9fb18387ac92dd0c53b4c8
ms.sourcegitcommit: 5a9ec5e28543f106bf9e7aa30dd0a726bb750e25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2020
ms.locfileid: "82925117"
---
# <a name="configure-healthchecktimeout-property-settings"></a>Konfigurieren der HealthCheckTimeout-Eigenschafteneinstellungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mit der HealthCheckTimeout-Einstellung wird die Zeitdauer in Millisekunden angegeben, die die Ressourcen-DLL für SQL Server auf Informationen warten soll, die von der gespeicherten Prozedur [sp_server_diagnostics](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) zurückgegeben werden, bevor gemeldet wird, dass die Always On-Failoverclusterinstanz (FCI) nicht reagiert. Änderungen am Timeoutwert werden unmittelbar wirksam; ein Neustart der SQL Server-Ressource ist nicht erforderlich.  
  
-   **Vorbereitungen:**  [Beschränkungen](#Limits), [Sicherheit](#Security)  
  
-   **So konfigurieren Sie die HeathCheckTimeout-Einstellung:**  [PowerShell](#PowerShellProcedure), [Failovercluster-Manager](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Limits"></a> Einschränkungen  
 Der Standardwert für diese Eigenschaft ist 30.000 Millisekunden (30 Sekunden). Der Mindestwert ist 15.000 Millisekunden (15 Sekunden).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert ALTER SETTINGS- und VIEW SERVER STATE-Berechtigungen.  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell  
  
##### <a name="to-configure-healthchecktimeout-settings"></a>So konfigurieren Sie die HealthCheckTimeout-Einstellungen  
  
1.  Starten Sie eine erhöhte Windows PowerShell mittels **Als Administrator ausführen**.  
  
2.  Importieren Sie das **FailoverClusters** -Modul, um die Cluster-Cmdlets zu aktivieren.  
  
3.  Verwenden Sie das **Get-ClusterResource** -Cmdlet, um die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource zu suchen, und verwenden Sie anschließend das **Set-ClusterParameter** -Cmdlet, um die **HealthCheckTimeout** -Eigenschaft für die Failoverclusterinstanz festzulegen.  
  
> [!TIP]  
>  Bei jedem Öffnen eines neuen PowerShell-Fensters müssen Sie das **FailoverClusters** -Modul importieren.  
  
### <a name="example-powershell"></a>Beispiel (PowerShell)  
 Im folgenden Beispiel wird die Einstellung HealthCheckTimeout auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource "`SQL Server (INST1)`" zu 60.000 Millisekunden geändert.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
  
```  
  
### <a name="related-content-powershell"></a>Verwandte Inhalte (PowerShell)  
  
-   [Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Clustering und hohe Verfügbarkeit) (Failoverclustering und Netzwerklastenausgleichs-Teamblog)  
  
-   [Erste Schritte mit Windows PowerShell auf einem Failovercluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Clusterressourcenbefehle und entsprechende Windows PowerShell-Cmdlets](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> Verwenden des Failovercluster-Manager-Snap-Ins  
 **So konfigurieren Sie die HealthCheckTimeout-Einstellung**  
  
1.  Öffnen Sie des Failovercluster-Manager-Snap-In.  
  
2.  Erweitern Sie **Dienste und Anwendungen** , und wählen Sie den FCI aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die **SQL Server-Ressource** unter **Sonstige Ressourcen** , und wählen Sie im Kontextmenü **Eigenschaften** aus. Das Dialogfeld **Eigenschaften** der SQL Server-Ressource wird angezeigt.  
  
4.  Wählen Sie die Registerkarte **Eigenschaften** aus, geben Sie den gewünschten Wert für die **HealthCheckTimeout** -Eigenschaft ein, und klicken Sie dann auf **OK** , um die Änderung zu übernehmen.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Mit der Anweisung [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] können Sie den HealthCheckTimeOut-Eigenschaftswert angeben.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die Option HealthCheckTimeout auf 15.000 Millisekunden (15 Sekunden) festgelegt.  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
