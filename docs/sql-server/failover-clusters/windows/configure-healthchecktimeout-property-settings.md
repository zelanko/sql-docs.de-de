---
title: Konfigurieren der HealthCheckTimeout-Eigenschafteneinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cfcb5d25b207af35e9a26b95b86997c803828f3f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002474"
---
# <a name="configure-healthchecktimeout-property-settings"></a>Konfigurieren der HealthCheckTimeout-Eigenschafteneinstellungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mit der HealthCheckTimeout-Einstellung wird die Zeitdauer in Millisekunden angegeben, die die Ressourcen-DLL für SQL Server auf Informationen warten soll, die von der gespeicherten Prozedur [sp_server_diagnostics](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) zurückgegeben werden, bevor gemeldet wird, dass die Always On-Failoverclusterinstanz (FCI) nicht reagiert. Änderungen am Timeoutwert werden unmittelbar wirksam; ein Neustart der SQL Server-Ressource ist nicht erforderlich.  
  
-   **Vorbereitungen:**  [Beschränkungen](#Limits), [Sicherheit](#Security)  
  
-   **So konfigurieren Sie die HeathCheckTimeout-Einstellung:**  [PowerShell](#PowerShellProcedure), [Failovercluster-Manager](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Limits"></a> Einschränkungen  
 Der Standardwert für diese Eigenschaft ist 30.000 Millisekunden (30 Sekunden). Der Mindestwert ist 15.000 Millisekunden (15 Sekunden).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert ALTER SETTINGS- und VIEW SERVER STATE-Berechtigungen.  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
  
##### <a name="to-configure-healthchecktimeout-settings"></a>So konfigurieren Sie die HealthCheckTimeout-Einstellungen  
  
1.  Starten Sie eine erhöhte Windows PowerShell mithilfe von **Als Administrator ausführen**.  
  
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
  
-   [Clustering and High-Availability](https://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (Clustering und hohe Verfügbarkeit) (Failoverclustering und Netzwerklastenausgleichs-Teamblog)  
  
-   [Erste Schritte mit Windows PowerShell auf einem Failovercluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Clusterressourcenbefehle und entsprechende Windows PowerShell-Cmdlets](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> Verwenden des Failovercluster-Manager-Snap-Ins  
 **So konfigurieren Sie die HealthCheckTimeout-Einstellung**  
  
1.  Öffnen Sie des Failovercluster-Manager-Snap-In.  
  
2.  Erweitern Sie **Dienste und Anwendungen** , und wählen Sie den FCI aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die **SQL Server-Ressource** unter **Sonstige Ressourcen** , und wählen Sie im Kontextmenü **Eigenschaften** aus. Das Dialogfeld **Eigenschaften** der SQL Server-Ressource wird angezeigt.  
  
4.  Wählen Sie die Registerkarte **Eigenschaften** aus, geben Sie den gewünschten Wert für die **HealthCheckTimeout** -Eigenschaft ein, und klicken Sie dann auf **OK** , um die Änderung zu übernehmen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Mit der Anweisung [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] können Sie den HealthCheckTimeOut-Eigenschaftswert angeben.  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die Option HealthCheckTimeout auf 15.000 Millisekunden (15 Sekunden) festgelegt.  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Failoverrichtlinie für Failoverclusterinstanzen](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
