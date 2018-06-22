---
title: Konfigurieren der HealthCheckTimeout-Eigenschafteneinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 6cd514ae1b9581a52e7dfdb382bc8fded757fb47
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059291"
---
# <a name="configure-healthchecktimeout-property-settings"></a>Konfigurieren der HealthCheckTimeout-Eigenschafteneinstellungen
  Die HealthCheckTimeout-Einstellung wird verwendet, um die Zeitdauer in Millisekunden angegeben, die die SQL Server-Ressourcen-DLL für die zurückgegebenen Informationen warten soll die [Sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) gespeicherte Prozedur, bevor gemeldet wird, die AlwaysOn-Failoverclusterinstanz (FCI) nicht reagiert. Änderungen am Timeoutwert werden unmittelbar wirksam; ein Neustart der SQL Server-Ressource ist nicht erforderlich.  
  
-   **Vorbereitungen:**  [Einschränkungen](#Limits), [Sicherheit](#Security)  
  
-   **So konfigurieren Sie die HeathCheckTimeout-Einstellung mit**  [PowerShell](#PowerShellProcedure), [Failovercluster-Manager](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Limits"></a> Einschränkungen  
 Der Standardwert für diese Eigenschaft ist 60.000 Millisekunden (60 Sekunden). Der Mindestwert ist 15.000 Millisekunden (15 Sekunden).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert ALTER SETTINGS- und VIEW SERVER STATE-Berechtigungen.  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
  
##### <a name="to-configure-healthchecktimeout-settings"></a>So konfigurieren Sie die HealthCheckTimeout-Einstellungen  
  
1.  Starten Sie eine erhöhte Windows PowerShell mittels **Als Administrator ausführen**.  
  
2.  Importieren Sie das `FailoverClusters`-Modul, um die Cluster-Cmdlets zu aktivieren.  
  
3.  Verwenden der `Get-ClusterResource` -Cmdlet zum Ermitteln der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Ressource, verwenden Sie dann `Set-ClusterParameter` Cmdlet, um die **HealthCheckTimeout** -Eigenschaft für die Failoverclusterinstanz.  
  
> [!TIP]  
>  Jedes Mal, wenn Sie ein neues PowerShell-Fenster öffnen, müssen Sie importieren die `FailoverClusters` Modul.  
  
### <a name="example-powershell"></a>Beispiel (PowerShell)  
 Im folgenden Beispiel wird die Einstellung HealthCheckTimeout auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource "`SQL Server (INST1)`" zu 60.000 Millisekunden geändert.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
  
```  
  
### <a name="related-content-powershell"></a>Verwandte Inhalte (PowerShell)  
  
-   [Clustering and High-Availability](http://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (Clustering und hohe Verfügbarkeit) (Failoverclustering und Netzwerklastenausgleichs-Teamblog)  
  
-   [Erste Schritte mit Windows PowerShell auf einem Failovercluster](http://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Clusterressourcenbefehle und entsprechende Windows PowerShell-Cmdlets](http://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> Verwenden des Failovercluster-Manager-Snap-Ins  
 **So konfigurieren Sie die HealthCheckTimeout-Einstellung**  
  
1.  Öffnen Sie des Failovercluster-Manager-Snap-In.  
  
2.  Erweitern Sie **Dienste und Anwendungen** , und wählen Sie den FCI aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die **SQL Server-Ressource** unter **Sonstige Ressourcen** , und wählen Sie im Kontextmenü **Eigenschaften** aus. Das Dialogfeld **Eigenschaften** der SQL Server-Ressource wird angezeigt.  
  
4.  Wählen Sie die Registerkarte **Eigenschaften** aus, geben Sie den gewünschten Wert für die **HealthCheckTimeout** -Eigenschaft ein, und klicken Sie dann auf **OK** , um die Änderung zu übernehmen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Mit der Anweisung [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] können Sie den HealthCheckTimeOut-Eigenschaftswert angeben.  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die Option HealthCheckTimeout auf 15.000 Millisekunden (15 Sekunden) festgelegt.  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Failoverrichtlinie für Failoverclusterinstanzen](failover-policy-for-failover-cluster-instances.md)  
  
  
