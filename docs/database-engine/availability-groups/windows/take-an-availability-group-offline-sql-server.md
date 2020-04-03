---
title: Offlineschalten einer Verfügbarkeitsgruppe (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], take offline
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d412a817a3e796e2ed85002ab11575b32e06ca91
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80216269"
---
# <a name="take-an-availability-group-offline-sql-server"></a>Offlineschalten einer Verfügbarkeitsgruppe (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie der Status einer Always On-Verfügbarkeitsgruppe mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] und höheren Versionen von ONLINE auf OFFLINE geändert wird. Es gibt keinen Datenverlust an Datenbanken mit synchronem Commit, da bei nicht vorgenommener Synchronisierung irgendeines Replikats mit synchronem Commit der OFFLINE-Vorgang einen Fehler auslöst und die Verfügbarkeitsgruppe ONLINE bleibt. Da die Verfügbarkeitsgruppe online bleibt, werden unsynchronisierte Datenbanken mit synchronem Commit vor möglichem Datenverlust geschützt. Nachdem eine Verfügbarkeitsgruppe offline geschaltet wurde, sind ihre Datenbanken für Clients nicht mehr verfügbar, und Sie können die Verfügbarkeitsgruppe nicht wieder online schalten. Schalten Sie daher eine Verfügbarkeitsgruppe nur offline, um die Verfügbarkeitsgruppenressourcen von einem WSFC-Cluster zu einem anderen zu migrieren.  
  
 Wenn während einer clusterübergreifenden Migration von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]Anwendungen direkt eine Verbindung mit dem primären Replikat einer Verfügbarkeitsgruppe herstellen, muss die Verfügbarkeitsgruppe offline geschaltet werden. Die clusterübergreifende Migration von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] unterstützt Betriebssystemupgrades mit minimaler Downtime von Verfügbarkeitsgruppen. Typischerweise wird die Kreuzclustermigration von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] verwendet, um Betriebssysteme auf [!INCLUDE[win8](../../../includes/win8-md.md)] oder [!INCLUDE[win8srv](../../../includes/win8srv-md.md)]zu aktualisieren. Weitere Informationen finden Sie unter [Lösungen mit hoher Verfügbarkeit (SQL Server)](https://msdn.microsoft.com/library/jj873730.aspx).  
  
  
> [!CAUTION]  
>  Verwenden Sie die Option OFFLINE für eine clusterübergreifende Migration von Verfügbarkeitsgruppenressourcen oder für ein Failover einer Verfügbarkeitsgruppe mit Leseskalierung.
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   Auf der Serverinstanz, auf der Sie den OFFLINE-Befehl eingeben, muss [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] oder höher (Enterprise Edition oder höher) ausgeführt werden.    
-   Die Verfügbarkeitsgruppe muss aktuell online sein.  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
 Bevor Sie die Verfügbarkeitsgruppe offline schalten, löschen Sie den Verfügbarkeitsgruppenlistener oder die Listener. Weitere Informationen finden Sie unter [Entfernen eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-an-availability-group-listener-sql-server.md)zu aktualisieren.  
  
##  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So schalten Sie eine Verfügbarkeitsgruppe offline**  
  
1.  Stellen Sie eine Verbindung zu einer Serverinstanz her, auf der ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe gehostet wird. Dieses Replikat kann das primäre Replikat oder ein sekundäres Replikat sein.  
  
2.  Verwenden Sie die [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) -Anweisung wie folgt:  
  
     ALTER AVAILABILITY GROUP *Gruppenname* OFFLINE  
  
     Dabei ist *Gruppenname* der Name der Verfügbarkeitsgruppe.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `AccountsAG` -Verfügbarkeitsgruppe offline geschaltet.  
  
```  
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="follow-up-after-the-availability-group-goes-offline"></a><a name="FollowUp"></a>Nächster Schritt: Nachdem die Verfügbarkeitsgruppe offline geschaltet wurde  
  
-   **Protokollieren eines OFFLINE-Vorgangs:**  Die Identität des WSFC-Knotens, in dem der OFFLINE-Vorgang initiiert wurde, wird sowohl im WSFC-Clusterprotokoll als auch in SQL ERRORLOG gespeichert.  
  
-   **Wenn Sie den Verfügbarkeitsgruppenlistener vor dem Offlineschalten der Gruppe nicht gelöscht haben:**  Wenn Sie die Verfügbarkeitsgruppe zu einem anderen WSFC-Cluster migrieren, löschen Sie den VNN und die VIP des Listeners. Sie können sie entweder mit der Konsole der Failoverclusterverwaltung, dem PowerShell-Cmdlet [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) oder [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx)löschen. Beachten Sie, dass cluster.exe auf Windows 8 veraltet ist.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Entfernen eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [Ändern des HADR-Clusterkontexts der Serverinstanz &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Technische Artikel zu SQL Server 2012](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [SQL Server Always On Team Blog: The official SQL Server Always On Team Blog (SQL Server Always On-Teamblog: Der offizielle SQL Server Always On-Teamblog)](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
