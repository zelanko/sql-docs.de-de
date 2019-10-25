---
title: Offlineschalten einer Verfügbarkeitsgruppe (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], take offline
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c26994d15fabb24ecd73c201bcb63d301639f282
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797815"
---
# <a name="take-an-availability-group-offline-sql-server"></a>Offlineschalten einer Verfügbarkeitsgruppe (SQL Server)
  In diesem Thema wird beschrieben, wie eine AlwaysOn-Verfügbarkeitsgruppe über [!INCLUDE[tsql](../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] und höheren Versionen vom Status ONLINE zum Status OFFLINE gebracht wird. Es gibt keinen Datenverlust an Datenbanken mit synchronem Commit, da bei nicht vorgenommener Synchronisierung irgendeines Replikats mit synchronem Commit der OFFLINE-Vorgang einen Fehler auslöst und die Verfügbarkeitsgruppe ONLINE bleibt. Da die Verfügbarkeitsgruppe online bleibt, werden unsynchronisierte Datenbanken mit synchronem Commit vor möglichem Datenverlust geschützt. Nachdem eine Verfügbarkeitsgruppe offline geschaltet wurde, sind ihre Datenbanken für Clients nicht mehr verfügbar, und Sie können die Verfügbarkeitsgruppe nicht wieder online schalten. Schalten Sie daher eine Verfügbarkeitsgruppe nur offline, um die Verfügbarkeitsgruppenressourcen von einem WSFC-Cluster zu einem anderen zu migrieren.  
  
 Wenn während einer clusterübergreifenden Migration von [!INCLUDE[ssHADR](../includes/sshadr-md.md)]Anwendungen direkt eine Verbindung mit dem primären Replikat einer Verfügbarkeitsgruppe herstellen, muss die Verfügbarkeitsgruppe offline geschaltet werden. Die clusterübergreifende Migration von [!INCLUDE[ssHADR](../includes/sshadr-md.md)] unterstützt Betriebssystemupgrades mit minimaler Downtime von Verfügbarkeitsgruppen. Typischerweise wird die Kreuzclustermigration von [!INCLUDE[ssHADR](../includes/sshadr-md.md)] verwendet, um Betriebssysteme auf [!INCLUDE[win8](../includes/win8-md.md)] oder [!INCLUDE[win8srv](../includes/win8srv-md.md)]zu aktualisieren. Weitere Informationen finden Sie unter [Clusterübergreifende Migration von AlwaysOn-Verfügbarkeitsgruppen für Betriebssystemupgrade](https://msdn.microsoft.com/library/jj873730.aspx).  
  

  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
> [!CAUTION]  
>  Verwenden Sie die OFFLINE-Option nur für eine Kreuzclustermigration von Verfügbarkeitsgruppenressourcen.  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   Auf der Serverinstanz, auf der Sie den OFFLINE-Befehl eingeben, muss [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] oder höher (Enterprise Edition oder höher) ausgeführt werden.  
  
-   Die Verfügbarkeitsgruppe muss aktuell online sein.  
  
###  <a name="Recommendations"></a> Empfehlungen  
 Bevor Sie die Verfügbarkeitsgruppe offline schalten, löschen Sie den Verfügbarkeitsgruppenlistener oder die Listener. Weitere Informationen finden Sie unter [Entfernen eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)zu aktualisieren.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So schalten Sie eine Verfügbarkeitsgruppe offline**  
  
1.  Stellen Sie eine Verbindung zu einer Serverinstanz her, auf der ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe gehostet wird. Dieses Replikat kann das primäre Replikat oder ein sekundäres Replikat sein.  
  
2.  Verwenden Sie die [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) -Anweisung wie folgt:  
  
     ALTER AVAILABILITY GROUP *Gruppenname* OFFLINE  
  
     Dabei ist *group_name* der Name der Verfügbarkeitsgruppe.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `AccountsAG` -Verfügbarkeitsgruppe offline geschaltet.  
  
```sql
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="FollowUp"></a> Nachverfolgung: Nachdem die Verfügbarkeitsgruppe offline geschaltet wurde  
  
-   **Protokollieren eines OFFLINE-Vorgangs:**  Die Identität des WSFC-Knotens, in dem der OFFLINE-Vorgang initiiert wurde, wird sowohl im WSFC-Clusterprotokoll als auch in SQL ERRORLOG gespeichert.  
  
-   **Wenn Sie den Verfügbarkeitsgruppenlistener vor dem Offlineschalten der Gruppe nicht gelöscht haben:**  Wenn Sie die Verfügbarkeitsgruppe zu einem anderen WSFC-Cluster migrieren, löschen Sie den VNN und die VIP des Listener. Sie können sie entweder mit der Konsole der Failoverclusterverwaltung, dem PowerShell-Cmdlet [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) oder [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx)löschen. Beachten Sie, dass cluster.exe auf Windows 8 veraltet ist.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Entfernen eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [Ändern des HADR-Clusterkontexts der Serverinstanz &#40;SQL Server&#41;](availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Technische Artikel zu SQL Server 2012](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [SQL Server AlwaysOn-Teamblog: der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](availability-groups/windows/always-on-availability-groups-sql-server.md)  
