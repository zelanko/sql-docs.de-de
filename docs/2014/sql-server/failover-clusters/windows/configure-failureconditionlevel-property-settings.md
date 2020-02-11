---
title: Konfigurieren von FailureConditionLevel-Eigenschafteneinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 87ed68cc3540075e0fd5d357182d709394f44455
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72797500"
---
# <a name="configure-failureconditionlevel-property-settings"></a>Konfigurieren von FailureConditionLevel-Eigenschafteneinstellungen
  Mit der FailureConditionLevel-Eigenschaft können Sie die Bedingungen für einen Failover oder Neustart der AlwaysOn-Failoverclusterinstanz (FCI) festlegen. Änderungen an dieser Eigenschaft werden unmittelbar übernommen, ohne dass ein Neustart des Windows Server-Failoverclusterdiensts (WSFC) oder der FCI-Ressource erforderlich ist.  
  
-   Vorbereitungen **:**[failureconditionlevel-Eigenschaften Einstellungen](#Restrictions), [Sicherheit](#Security)    
  
-   So **Konfigurieren Sie die failureconditionlevel-Eigenschafts Einstellungen mithilfe von,** [PowerShell](#PowerShellProcedure), [Failovercluster-Manager](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a>Failureconditionlevel-Eigenschaften Einstellungen  
 Die Fehlerbedingungen werden auf einer ansteigenden Skala festgelegt. Auf der Ebene 1-5 enthält jede Ebene die Bedingungen der vorherigen Ebenen sowie die eigenen Bedingungen. Dies bedeutet, dass die Wahrscheinlichkeit eines Failovers oder Neustarts mit jeder Ebene zunimmt.  Weitere Informationen finden Sie im Abschnitt "Bestimmen von Fehlern" des Themas [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) .  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert ALTER SETTINGS- und VIEW SERVER STATE-Berechtigungen.  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
  
### <a name="to-configure-failureconditionlevel-settings"></a>So konfigurieren Sie die FailureConditionLevel-Einstellungen  
  
1.  Starten Sie eine erhöhte Windows PowerShell mittels **Als Administrator ausführen**.  
  
2.  Importieren Sie das `FailoverClusters`-Modul, um die Cluster-Cmdlets zu aktivieren.  
  
3.  Verwenden Sie `Get-ClusterResource` das Cmdlet, um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Ressource zu suchen `Set-ClusterParameter` , und verwenden Sie dann das Cmdlet, um die **failureconditionlevel** -Eigenschaft für eine Failoverclusterinstanz festzulegen.  
  
> [!TIP]  
>  Bei jedem Öffnen eines neuen PowerShell-Fensters müssen Sie das `FailoverClusters`-Modul importieren.  

 Im folgenden Beispiel wird die FailureConditionLevel-Einstellung auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource "`SQL Server (INST1)`" in "Failover oder Neustart bei wichtigen Serverfehlern" geändert.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3
```  
  
### <a name="related-content-powershell"></a>Verwandte Inhalte (PowerShell)  
  
-   [Clustering und hohe Verfügbarkeit](https://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (Failoverclustering und Netzwerk Lastenausgleich-Teamblog)  
  
-   [Ersten Schritte mit Windows PowerShell auf einem Failovercluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Cluster Ressourcen Befehle und entsprechende Windows PowerShell-Cmdlets](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a>Verwenden des Snap-Ins "Failovercluster-Manager"  

### <a name="to-configure-failureconditionlevel-property-settings"></a>So konfigurieren Sie failureconditionlevel-Eigenschaften Einstellungen
  
1.  Öffnen Sie des Failovercluster-Manager-Snap-In.  
  
2.  Erweitern Sie **Dienste und Anwendungen** , und wählen Sie den FCI aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die **SQL Server-Ressource** unter **Sonstige Ressourcen**, und wählen Sie im Kontextmenü **Eigenschaften** aus. Das Dialogfeld **Eigenschaften** der SQL Server-Ressource wird angezeigt.  
  
4.  Wählen Sie die Registerkarte **Eigenschaften** aus, geben Sie den gewünschten Wert für die **FailureConditionLevel** -Eigenschaft ein, und klicken Sie dann auf **OK** , um die Änderung zu übernehmen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  

### <a name="to-configure-failureconditionlevel-property-settings"></a>So konfigurieren Sie failureconditionlevel-Eigenschaften Einstellungen
  
 Mithilfe der [Alter Server Configuration](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung können Sie den failureconditionlevel-Eigenschafts Wert angeben.  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die FailureConditionLevel-Eigenschaft auf 0 gesetzt. Dadurch wird angegeben, dass bei einer Fehlerbedingung nicht automatisch ein Failover oder Neustart ausgelöst wird.  
  
```sql
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_server_diagnostics &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)   
 [Failoverrichtlinie für Failoverclusterinstanzen](failover-policy-for-failover-cluster-instances.md)  
