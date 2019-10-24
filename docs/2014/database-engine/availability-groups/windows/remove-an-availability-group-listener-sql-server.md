---
title: Entfernen eines Verfügbarkeitsgruppenlisteners (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeaglistener.default.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 049296ff601296edbd990fe9ea70aef3efa8c44b
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72782857"
---
# <a name="remove-an-availability-group-listener-sql-server"></a>Entfernen eines Verfügbarkeitsgruppenlisteners (SQL Server)
  In diesem Thema wird beschrieben, wie ein Verfügbarkeitsgruppenlistener unter Verwendung von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]aus einer AlwaysOn-Verfügbarkeitsgruppe entfernt wird.  
  
-   **Vorbereitungen:**  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **Entfernen eines Listeners mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   Sie müssen mit der Serverinstanz verbunden sein, die das primäre Replikat hostet.  
  
###  <a name="Recommendations"></a> Empfehlungen  
 Bevor Sie einen Verfügbarkeitsgruppenlistener löschen, sollten Sie sicherstellen, dass er nicht von Anwendungen verwendet wird.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So entfernen Sie einen Verfügbarkeitsgruppenlistener**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Serverinstanz her, die das primäre Replikat hostet, und klicken Sie auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** und den Knoten **Verfügbarkeitsgruppen** .  
  
3.  Erweitern Sie den Knoten der Verfügbarkeitsgruppe, und erweitern Sie den Knoten **Verfügbarkeitsgruppenlistener** .  
  
4.  Klicken Sie mit der rechten Maustaste auf den Listener, und wählen Sie den Befehl **Löschen** aus.  
  
5.  Dadurch wird das Dialogfeld **Listener aus Verfügbarkeitsgruppe entfernen** geöffnet. Weitere Informationen finden Sie weiter unten in diesem Thema unter [Listener aus Verfügbarkeitsgruppe entfernen](#AgListenerPropertiesDialog).  
  
###  <a name="AgListenerPropertiesDialog"></a> Listener aus Verfügbarkeitsgruppe entfernen (Dialogfeld)  
 **Name**  
 Der Name des zu entfernenden Listeners.  
  
 **Ergebnis**  
 Zeigt einen Link an, entweder **Erfolgreich** oder **Fehler**, auf den Sie klicken können, um weitere Informationen zu erhalten.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So entfernen Sie einen Verfügbarkeitsgruppenlistener**  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, die das primäre Replikat hostet.  
  
2.  Verwenden Sie die [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) -Anweisung wie folgt:  
  
     Alter Availability Group *Gruppenname* Remove Listener **' *`dns_name`* '**  
  
     dabei ist *Gruppenname* der Name der Verfügbarkeitsgruppe und *DNS-Name* der DNS-Name des Verfügbarkeitsgruppenlisteners.  
  
     Im folgenden Beispiel wird der Listener der `AccountsAG` -Verfügbarkeitsgruppe gelöscht. Der DNS-Name lautet AccountsAG_Listener.  
  
    ```sql
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER 'AccountsAG_Listener';  
    ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
 **So entfernen Sie einen Verfügbarkeitsgruppenlistener**  
  
1.  Legen Sie den Standard (`cd`) auf die Serverinstanz fest, auf der das primäre Replikat gehostet wird.  
  
2.  Verwenden Sie das integrierte `Remove-Item`-Cmdlet, um einen Listener zu entfernen. Beispielsweise wird durch den folgenden Befehl der Listener `MyListener` aus einer Verfügbarkeitsgruppe namens `MyAg`entfernt.  
  
    ```powershell
    Remove-Item SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Anzeigen von Eigenschaften des Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41; ](overview-of-always-on-availability-groups-sql-server.md)    
 [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover (SQL Server)](../../listeners-client-connectivity-application-failover.md)  
