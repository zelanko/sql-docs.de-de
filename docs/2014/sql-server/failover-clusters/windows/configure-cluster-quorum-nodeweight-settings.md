---
title: Konfigurieren von Cluster-Quorum-NodeWeight-Einstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: cb3fd9a6-39a2-4e9c-9157-619bf3db9951
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dfc31fa968952db56a64f93b180c2b88ec685725
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797605"
---
# <a name="configure-cluster-quorum-nodeweight-settings"></a>Konfigurieren von Cluster-Quorum-NodeWeight-Einstellungen
  In diesem Thema wird beschrieben, wie NodeWeight-Einstellungen für einen Elementknoten in einem Windows Server-Failoverclustering-Cluster konfiguriert werden. NodeWeight-Einstellungen werden während der Quorumabstimmung verwendet, um Notfallwiederherstellungs- und Multisubnetzszenarien für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] - und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanzen zu unterstützen.  
  
-   **Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)  
  
-   **Anzeigen von Quorum-NodeWeight-Einstellungen mit:** [Verwenden von PowerShell](#PowerShellProcedure), [Verwenden von Cluster.exe](#CommandPromptProcedure)  
  
-   [Verwandte Inhalte](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a>Voraussetzungen  
 Diese Funktion wird nur in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] oder höheren Versionen unterstützt.  
  
> [!IMPORTANT]  
>  Um NodeWeight-Einstellungen zu verwenden, muss der folgende Hotfix im WSFC-Cluster für alle Server übernommen werden:  
>   
>  [KB2494036](https://support.microsoft.com/kb/2494036): Ein Hotfix ist verfügbar, mit dem sich ein Clusterknoten konfigurieren lässt, der keine Quorumabstimmung in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] und in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]  
  
> [!TIP]  
>  Ist dieser Hotfix nicht installiert, geben die Beispiele in diesem Thema leere Werte oder NULL-Werte für NodeWeight zurück.  
  
###  <a name="Security"></a> Security  
 Der Benutzer muss einem Domänenkonto entsprechen, das Mitglied der lokalen Administratorgruppe an jedem Knoten des WSFC-Clusters ist.  
  
##  <a name="PowerShellProcedure"></a> Verwenden von PowerShell  
  
### <a name="to-configure-nodeweight-settings"></a>So konfigurieren Sie NodeWeight-Einstellungen
  
1.  Starten Sie eine erhöhte Windows PowerShell mithilfe von **Als Administrator ausführen**.  
  
2.  Importieren Sie das `FailoverClusters` -Modul, um Cluster-Cmdlets zu aktivieren.  
  
3.  Verwenden Sie das `Get-ClusterNode` -Objekt, um die `NodeWeight` -Eigenschaft für jeden Knoten im Cluster festzulegen.  
  
4.  Geben Sie die Clusterknoteneigenschaften in einem lesbaren Format aus.  
  
 Im folgenden Beispiel wird die NodeWeight-Einstellung geändert, um die Quorumabstimmung für den AlwaysOnSrv1-Knoten zu entfernen. Zudem werden die Einstellungen für alle Knoten im Cluster ausgegeben.
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv1"  
(Get-ClusterNode $node).NodeWeight = 0  
  
$cluster = (Get-ClusterNode $node).Cluster  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -property NodeName, State, NodeWeight  
```  
  
##  <a name="CommandPromptProcedure"></a> Verwenden von Cluster.exe  
  
> [!NOTE]  
>  Das Hilfsprogramm von cluster.exe ist in der [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] -Version veraltet.  Verwenden Sie PowerShell mit Failoverclustering für künftige Entwicklungen.  Das Hilfsprogramm von cluster.exe wird in der nächsten Version von Windows Server entfernt. Weitere Informationen finden Sie unter [Zuordnen von Cluster.exe-Befehlen zu Windows PowerShell-Cmdlets für Failovercluster](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).  
  
### <a name="to-configure-nodeweight-settings"></a>So konfigurieren Sie NodeWeight-Einstellungen
  
1.  Starten Sie mit **Als Administrator ausführen**eine Eingabeaufforderung mit erweiterten Berechtigungen.  
  
2.  Verwenden Sie **cluster.exe** , um `NodeWeight` -Werte festzulegen.  

 Im folgenden Beispiel wird der NodeWeight-Wert geändert, um die Quorumabstimmung des Knotens „AlwaysOnSrv1“ im Cluster „Cluster001“ zu entfernen.  
  
```cmd
cluster.exe Cluster001 node AlwaysOnSrv1 /prop NodeWeight=0  
```  
  
##  <a name="RelatedContent"></a>Verwandte Inhalte  
  
-   [Anzeigen von Ereignissen und Protokollen für einen Failovercluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)  
  
-   [Get-ClusterLog-Failovercluster-Cmdlet](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a>Siehe auch  
 [WSFC-Quorummodi und Abstimmungskonfiguration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md)   
 [Anzeigen von Cluster-Quorum-NodeWeight-Einstellungen](view-cluster-quorum-nodeweight-settings.md)   
 [Failovercluster-Cmdlets in Windows PowerShell, aufgelistet nach Taskfokus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)  
