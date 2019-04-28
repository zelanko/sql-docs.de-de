---
title: Konfigurieren der Serverkonfigurationsoption „remote proc trans“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote proc trans option
- distributed transactions [SQL Server], enforcing
ms.assetid: cfbc6158-ab96-44b4-87eb-ea278c1b0c6b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 106f4ca8951200110349809065b35ba65a7f8411
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62811334"
---
# <a name="configure-the-remote-proc-trans-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption „remote proc trans“
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **remote proc trans** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert wird. Mit der Option **remote proc trans** können Sie die Aktionen einer Server-zu-Server-Prozedur über eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator-Transaktion (MS DTC) schützen.  
  
 Legen Sie den Wert von **remote proc trans** auf 1 fest, um eine von MS DTC koordinierte verteilte Transaktion zum Schutz der ACID-Eigenschaften (atomar, konsistent, isoliert und beständig) von Transaktionen bereitzustellen. Sitzungen, die nach dem Festlegen dieser Option auf 1 beginnen, erben die Konfigurationseinstellung als Standardeinstellung.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option „remote proc trans“ mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option "remote Proc Trans"](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Um diesen Wert festlegen zu können, müssen Remoteserververbindungen zulässig sein.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option wird aus Gründen der Kompatibilität mit früheren Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für Anwendungen bereitgestellt, die remote gespeicherte Prozeduren verwenden. Anstatt remote gespeicherte Prozeduren aufzurufen, sollten Sie verteilte Abfragen verwenden, die auf Verbindungsserver verweisen. Diese werden mithilfe von [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)definiert.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a>So konfigurieren Sie die Option „remote proc trans“  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den Knoten **Verbindungen** .  
  
3.  Aktivieren Sie unter **Remoteserververbindungen**das Kontrollkästchen **Verteilte Transaktionen für die Kommunikation zwischen Servern verlangen** .  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a>So konfigurieren Sie die Option „remote proc trans“  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `remote proc trans` auf `1`festzulegen.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote proc trans', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option "remote Proc Trans"  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Siehe auch  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
