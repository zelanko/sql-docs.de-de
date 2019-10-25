---
title: Konfigurieren der flexiblen Failoverrichtlinie zum Steuern der Bedingungen für automatisches Failover (Always on-Verfügbarkeits Gruppen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 452d3ac4dae2164fa0fa172528ae398ea91fed31
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797752"
---
# <a name="configure-the-flexible-failover-policy-to-control-conditions-for-automatic-failover-always-on-availability-groups"></a>Konfigurieren der flexiblen Failoverrichtlinie zum Steuern der Bedingungen für ein automatisches Failover (AlwaysOn-Verfügbarkeitsgruppen)
  In diesem Thema wird beschrieben, wie die flexible Failoverrichtlinie für eine AlwaysOn-Verfügbarkeitsgruppe mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]konfiguriert wird. Eine flexible Failoverrichtlinie ermöglicht eine präzise Kontrolle über die Bedingungen, die ein automatisches Failover für eine Verfügbarkeitsgruppe verursachen. Durch eine Änderung der Fehlerbedingungen, die ein automatisches Failover und die Häufigkeit von Integritätsprüfungen auslösen, können Sie die Wahrscheinlichkeit für ein automatisches Failover erhöhen oder verringern, um das SLA für hohe Verfügbarkeit zu unterstützen.  
  
  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Limitations"></a> Einschränkungen beim automatischen Failover  
  
-   Damit ein automatisches Failover ausgeführt werden kann, müssen das aktuelle primäre Replikat und ein sekundäres Replikat für den Verfügbarkeitsmodus für synchrone Commits und automatischem Failover konfiguriert und das sekundäre Replikat mit dem primären Replikat synchronisiert sein.  
  
-   Wenn eine Verfügbarkeitsgruppe den Schwellenwert für WSFC-Fehler überschreitet, versucht der WSFC-Cluster nicht, ein automatisches Failover für die Verfügbarkeitsgruppe auszuführen. Außerdem verbleibt die WSFC-Ressourcengruppe der Verfügbarkeitsgruppe so lange in einem fehlerhaften Zustand, bis der Clusteradministrator die fehlerhafte Gruppe manuell online schaltet oder bis der Datenbankadministrator ein manuelles Failover der Verfügbarkeitsgruppe ausführt. Der *WSFC-Fehlerschwellenwert* ist als maximale Anzahl von Fehlern definiert, die während eines bestimmten Zeitraums für die Verfügbarkeitsgruppe unterstützt werden. Der Standardzeitraum beträgt sechs Stunden, und der Standardwert für die maximale Anzahl von Fehlern während dieses Zeitraums entspricht *n*-1, wobei *n* für die Anzahl der WSFC-Knoten steht. Um den Fehlerschwellenwert für eine angegebene Verfügbarkeitsgruppe zu ändern, verwenden Sie die WSFC Failover Manager Console.  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   Sie müssen mit der Serverinstanz verbunden sein, die das primäre Replikat hostet.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Berechtigungen  
  
|Aufgabe|Berechtigungen|  
|----------|-----------------|  
|Konfigurieren der flexiblen Failoverrichtlinie für eine neue Verfügbarkeitsgruppe|Erfordert die Mitgliedschaft in der festen **sysadmin** -Serverrolle und die CREATE AVAILABILITY GROUP-Serverberechtigung, ALTER ANY AVAILABILITY GROUP-Berechtigung oder CONTROL SERVER-Berechtigung.|  
|Ändern der Richtlinie einer vorhandenen Verfügbarkeitsgruppe|Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.|  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So konfigurieren Sie die flexible Failoverrichtlinie**  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, die das primäre Replikat hostet.  
  
2.  Für eine neue Verfügbarkeitsgruppe verwenden Sie die [-Anweisung](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] . Verwenden Sie zum Ändern einer vorhandenen Verfügbarkeitsgruppe die [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung.  
  
    -   Um die Failover-Bedingungsebene festzulegen, verwenden Sie die Option FAILURE_CONDITION_LEVEL = *n* , wobei *n* für eine ganze Zahl zwischen 1 und 5 steht.  
  
         Beispielsweise wird mit der folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung die Fehlerbedingungsebene der vorhandenen Verfügbarkeitsgruppe `AG1`in Ebene 1 geändert:  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         Diese ganzzahligen Werte stehen in folgender Beziehung zu den Fehlerbedingungsebenen:  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] Wert|level|Automatisches Failover wird initiiert, wenn...|  
        |------------------------------|-----------|-------------------------------------------|  
        |1|1 (eins)|der Server ausfällt. Der SQL Server-Dienst wird aufgrund eines Failovers oder Neustarts beendet.|  
        |2|2 (zwei)|der Server nicht reagiert. Der Wert der Bedingungsebene wird unterschritten, der SQL Server-Dienst ist mit dem Cluster verbunden, und der Schwellenwert für das Timeout der Integritätsprüfung wird überschritten, oder das aktuelle primäre Replikat weist einen fehlerhaften Status auf.|  
        |3|3 (drei)|ein kritischer Serverfehler auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt ein interner kritischer Serverfehler auf.<br /><br /> Dies ist der Standardebene.|  
        |4|4 (vier)|ein mittelschwerer Serverfehler auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt ein mittelschwerer Serverfehler auf.|  
        |5|5 (fünf)|eine qualifizierte Fehlerbedingung auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt eine qualifizierte Fehlerbedingung auf.|  
  
         Weitere Informationen zu den Failover-Bedingungsebenen finden Sie unter [Flexible Failoverrichtlinie für automatisches Failover einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).  
  
    -   Um den Schwellenwert für das Timeout der Integritätsprüfung zu konfigurieren, verwenden Sie die Option HEALTH_CHECK_TIMEOUT = *n* , wobei *n* für eine ganze Zahl zwischen 15000 Millisekunden (15 Sekunden) und 4294967295 Millisekunden steht. Der Standardwert ist 30.000 Millisekunden (oder 30 Sekunden).  
  
         Mit der folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung wird z. B. der Schwellenwert für das Timeout der Integritätsprüfung einer vorhandenen Verfügbarkeitsgruppe mit dem Namen `AG1`in 60.000 Millisekunden (eine Minute) geändert.  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell  

### <a name="to-configure-the-flexible-failover-policy"></a>So konfigurieren Sie die flexible Failoverrichtlinie * *  
  
1.  Legen Sie den Standard (`cd`) auf die Serverinstanz fest, auf der das primäre Replikat gehostet wird.  
  
2.  Wenn Sie einer Verfügbarkeitsgruppe ein Verfügbarkeitsreplikat hinzufügen, verwenden Sie das `New-SqlAvailabilityGroup`-Cmdlet. Wenn Sie ein vorhandenes Verfügbarkeitsreplikat ändern, verwenden Sie das `Set-SqlAvailabilityGroup`-Cmdlet.  
  
    -   Um die Failover-Bedingungs Ebene festzulegen, verwenden Sie den `FailureConditionLevel`*Level* -Parameter, wobei *Level* einem der folgenden Werte entspricht:  
  
        |value|level|Automatisches Failover wird initiiert, wenn...|  
        |-----------|-----------|-------------------------------------------|  
        |`OnServerDown`|1 (eins)|der Server ausfällt. Der SQL Server-Dienst wird aufgrund eines Failovers oder Neustarts beendet.|  
        |`OnServerUnresponsive`|2 (zwei)|der Server nicht reagiert. Der Wert der Bedingungsebene wird unterschritten, der SQL Server-Dienst ist mit dem Cluster verbunden, und der Schwellenwert für das Timeout der Integritätsprüfung wird überschritten, oder das aktuelle primäre Replikat weist einen fehlerhaften Status auf.|  
        |`OnCriticalServerError`|3 (drei)|ein kritischer Serverfehler auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt ein interner kritischer Serverfehler auf.<br /><br /> Dies ist der Standardebene.|  
        |`OnModerateServerError`|4 (vier)|ein mittelschwerer Serverfehler auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt ein mittelschwerer Serverfehler auf.|  
        |`OnAnyQualifiedFailureConditions`|5 (fünf)|eine qualifizierte Fehlerbedingung auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt eine qualifizierte Fehlerbedingung auf.|  
  
         Weitere Informationen zu den Failover-Bedingungsebenen finden Sie unter [Flexible Failoverrichtlinie für automatisches Failover einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).  
  
         Beispielsweise wird mit dem folgenden Befehl die Fehlerbedingungsebene der vorhandenen Verfügbarkeitsgruppe `AG1`in Ebene 1 geändert.  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `
         -FailureConditionLevel OnServerDown  
        ```  
  
    -   Um den Schwellenwert für das Timeout der Integritätsprüfung festzulegen, verwenden Sie den Parameter `HealthCheckTimeout`*n* , wobei *n* für eine ganze Zahl zwischen 15000 Millisekunden (15 Sekunden) und 4294967295 Millisekunden steht. Der Standardwert ist 30000 Millisekunden (oder 30 Sekunden).  
  
         Mit dem folgenden Befehl wird z. B. der Schwellenwert für das Timeout der Integritätsprüfung der vorhandenen Verfügbarkeitsgruppe `AG1`in 120.000 Millisekunden (zwei Minuten) geändert.  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `
         -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Aufrufen der SQL Server PowerShell-Hilfe](../../../powershell/sql-server-powershell.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41; ](overview-of-always-on-availability-groups-sql-server.md)    
 [Verfügbarkeits Modi (AlwaysOn-Verfügbarkeitsgruppen)](availability-modes-always-on-availability-groups.md)    
 [Failover-und Failovermodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41; ](failover-and-failover-modes-always-on-availability-groups.md)    
 [Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)   
 [sp_server_diagnostics (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)  
