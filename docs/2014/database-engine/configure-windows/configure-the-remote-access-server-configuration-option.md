---
title: Konfigurieren der Serverkonfigurationsoption „Remotezugriff“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], stored procedure execution
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e499315b2807245a34d3ec4fe7d7616e98b76512
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62811354"
---
# <a name="configure-the-remote-access-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Remotezugriff
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **Remotezugriff** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert wird. Mithilfe der Option **Remotezugriff** können Sie die Ausführung gespeicherter Prozeduren von lokalen Servern oder Remoteservern steuern, auf denen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden. Der Standardwert für diese Option ist 1. Damit wird die Berechtigung zum Ausführen lokal gespeicherter Prozeduren von Remoteservern aus oder zum Ausführen remote gespeicherter Prozeduren vom lokalen Server aus erteilt. Legen Sie die Option auf 0 fest, um zu verhindern, dass lokal gespeicherte Prozeduren von einem Remoteserver aus ausgeführt werden oder dass remote gespeicherte Prozeduren auf dem lokalen Server ausgeführt werden können.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Verwenden Sie stattdessen [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So konfigurieren Sie die Option Remotezugriff mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option Remotezugriff](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Die Option **Remotezugriff** gilt nur für Server, die mithilfe von [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)hinzugefügt wurden, und wird aus Gründen der Abwärtskompatibilität bereitgestellt.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-access-option"></a>So konfigurieren Sie die Option Remotezugriff  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den Knoten **Verbindungen** .  
  
3.  Aktivieren oder deaktivieren Sie unter **Remoteserververbindungen**das Kontrollkästchen **Remoteverbindungen mit diesem Server zulassen** .  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-remote-access-option"></a>So konfigurieren Sie die Option Remotezugriff  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `remote access` auf `0`festzulegen.  
  
```sql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option Remotezugriff  
 Diese Einstellung wird erst wirksam, wenn Sie SQL Server neu starten.  
  
## <a name="see-also"></a>Siehe auch  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
