---
title: Verwenden von AlwaysOn-Richtlinien zum Anzeigen des Zustands einer verfügbarkeitsgruppe (SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 12a183718ee13915fd6236caf943fea03819e723
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62812976"
---
# <a name="use-alwayson-policies-to-view-the-health-of-an-availability-group-sql-server"></a>Verwenden von AlwaysOn-Richtlinien zum Anzeigen des Zustands einer Verfügbarkeitsgruppe (SQL Server)
  In diesem Thema wird beschrieben, wie der Betriebsstatus einer AlwaysOn-Verfügbarkeitsgruppe in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] mithilfe einer AlwaysOn-Richtlinie in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]bzw. mit PowerShell geändert wird. Weitere Informationen zu AlwaysOn-richtlinienbasierte Verwaltung, finden Sie unter [AlwaysOn-Richtlinien für Betriebsprobleme mit AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
> [!IMPORTANT]  
>  Für AlwaysOn-Richtlinien werden die Kategorienamen als IDs verwendet. Durch die Änderung des Namens einer AlwaysOn-Kategorie wird die Funktion zur Integritätsüberprüfung unterbrochen. Daher sollten die Namen der AlwaysOn-Kategorie nicht geändert werden.  
  

  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert CONNECT-, VIEW SERVER STATE- und VIEW ANY DEFINITION-Berechtigungen.  
  
##  <a name="SSMSProcedure"></a> Verwenden des AlwaysOn-Dashboards  
 **Um das AlwaysOn-Dashboard zu öffnen.**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Serverinstanz her, die eines der Verfügbarkeitsreplikate hostet. Verwenden Sie zum Anzeigen von Informationen zu allen Verfügbarkeitsreplikaten in einer Verfügbarkeitsgruppe die Serverinstanz, die das primäre Replikat hostet.  
  
2.  Klicken Sie auf den Servernamen, um die Serverstruktur zu erweitern.  
  
3.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** .  
  
     Klicken Sie entweder mit der rechten Maustaste auf den Knoten **Verfügbarkeitsgruppen**, oder erweitern Sie diesen Knoten, und klicken Sie mit der rechten Maustaste auf eine bestimmte Verfügbarkeitsgruppe.  
  
4.  Wählen Sie den Befehl **Dashboard anzeigen** aus.  
  
 Informationen zur Verwendung des AlwaysOn-Dashboards finden Sie unter [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
 **Verwenden von AlwaysOn-Richtlinien zum Anzeigen des Zustands einer verfügbarkeitsgruppe**  
  
1.  Legen Sie den Standardwert (`cd`) auf eine Serverinstanz fest, auf der eines der Verfügbarkeitsreplikate gehostet wird. Verwenden Sie zum Anzeigen von Informationen zu allen Verfügbarkeitsreplikaten in einer Verfügbarkeitsgruppe die Serverinstanz, die das primäre Replikat hostet.  
  
2.  Verwenden Sie die folgenden Cmdlets:  
  
     `Test-SqlAvailabilityGroup`  
     Bewertet die Integrität einer Verfügbarkeitsgruppe durch die Auswertung der Richtlinien der richtlinienbasierten SQL Server-Verwaltung. Sie müssen über CONNECT-, VIEW SERVER STATE- und VIEW ANY DEFINITION-Berechtigungen verfügen, um dieses Cmdlet auszuführen.  
  
     Beispielsweise werden durch den folgenden Befehl alle Verfügbarkeitsgruppen im „Error“-Zustand auf der Serverinstanz angezeigt `Computer\Instance`.  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups |
        Test-SqlAvailabilityGroup |
        Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     `Test-SqlAvailabilityReplica`  
     Bewertet die Integrität von Verfügbarkeitsreplikaten durch die Auswertung der Richtlinien der richtlinienbasierten SQL Server-Verwaltung. Sie müssen über CONNECT-, VIEW SERVER STATE- und VIEW ANY DEFINITION-Berechtigungen verfügen, um dieses Cmdlet auszuführen.  
  
     Durch den folgenden Befehl werden beispielsweise die Integrität des Verfügbarkeitsreplikats `MyReplica` in der Verfügbarkeitsgruppe `MyAg` ausgewertet und eine kurze Zusammenfassung ausgegeben.  
  
    ```powershell
    Test-SqlAvailabilityReplica `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     `Test-SqlDatabaseReplicaState`  
     Bewertet die Integrität einer Verfügbarkeitsdatenbank für alle hinzugefügten Verfügbarkeitsreplikate durch die Auswertung der Richtlinien der richtlinienbasierten SQL Server-Verwaltung.  
  
     Durch den folgenden Befehl werden beispielsweise die Integrität aller Verfügbarkeitsdatenbanken in der Verfügbarkeitsgruppe `MyAg` ausgewertet und eine kurze Zusammenfassung für jede Datenbank ausgegeben.  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates |
        Test-SqlDatabaseReplicaState  
    ```  
  
     Diese Cmdlets akzeptieren die folgenden Optionen:  
  
    |Option|Description|  
    |------------|-----------------|  
    |`AllowUserPolicies`|Führt in den AlwaysOn-Richtlinienkategorien gefundene Benutzerrichtlinien aus.|  
    |`InputObject`|Eine Auflistung von Objekten, die abhängig vom verwendeten Cmdlet den Status von Verfügbarkeitsgruppen, Verfügbarkeitsreplikaten oder Verfügbarkeitsdatenbanken darstellen. Das Cmdlet berechnet die Integrität der angegebenen Objekte.|  
    |`NoRefresh`|Wenn dieser Parameter festgelegt wird, werden die vom `-Path`-Parameter oder `-InputObject`-Parameter angegebenen Objekte nicht manuell vom Cmdlet aktualisiert.|  
    |`Path`|Abhängig vom verwendeten Cmdlet der Pfad zur Verfügbarkeitsgruppe, zu den Verfügbarkeitsreplikaten oder zum Status des Datenbankreplikatclusters. Dies ist ein optionaler Parameter. Wird dieser Parameter nicht angegeben, wird der Wert standardmäßig auf den aktuellen Arbeitsstandort festgelegt.|  
    |`ShowPolicyDetails`|Zeigt das Ergebnis aller von diesem Cmdlet ausgeführten Richtlinienauswertungen an. Das Cmdlet gibt ein Objekt pro Richtlinienauswertung aus. Dieses Objekt verfügt über Felder, in denen die Ergebnisse der Auswertung beschrieben werden, z. B. ob die Richtlinie eingehalten wurde sowie den Richtliniennamen und die Kategorie.|  
  
     Durch den folgenden `Test-SqlAvailabilityGroup`-Befehl wird beispielsweise der `-ShowPolicyDetails`-Parameter angegeben, um das Ergebnis aller Richtlinienauswertungen anzuzeigen, die von diesem Cmdlet für die einzelnen Richtlinien der richtlinienbasierten Verwaltung ausgeführt wurden, die für die Verfügbarkeitsgruppe `MyAg` ausgeführt wurden.  
  
    ```powershell
    Test-SqlAvailabilityGroup `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName `  
    -ShowPolicyDetails  
    ```  
  
    > [!NOTE]  
    >  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
 **SQL Server Always on Team Blogs: Überwachung von AlwaysOn-Zustands mit PowerShell:**  
  
-   [Teil 1: Basic Cmdlet Overview (Überwachen der Always On-Integrität mit PowerShell – Teil 1: Übersicht über grundlegende Cmdlets)](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-1.aspx)  
  
-   [Teil 2: Advanced Cmdlet Usage (Überwachen der Always On-Integrität mit PowerShell – Teil 2: Verwendung erweiterter Cmdlets)](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-2.aspx)  
  
-   [Teil 3: A Simple Monitoring Application (Überwachen der Always On-Integrität mit PowerShell – Teil 3: Eine einfache Überwachungsanwendung)](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/monitoring-alwayson-health-with-powershell-part-3.aspx)  
  
-   [Teil 4: Integration with SQL Server Agent (Überwachen der Always On-Integrität mit PowerShell – Teil 4: Integration in SQL Server-Agent)](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwaltung einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)   
 [Überwachen von Verfügbarkeitsgruppen (SQL Server)](monitoring-of-availability-groups-sql-server.md)   
 [AlwaysOn-Richtlinien für Betriebsprobleme mit AlwaysOn-Verfügbarkeitsgruppen (SQLServer)](always-on-policies-for-operational-issues-always-on-availability.md) 
  
  
