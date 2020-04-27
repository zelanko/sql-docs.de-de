---
title: Konfigurieren der Serverkonfigurationsoption „Kostenbeschränkung der Abfragekontrolle“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], time to execute
- query governor cost limit option [SQL Server]
- time [SQL Server], query run time
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 758c2b42d09e120bf0621bcdedf26b93f130b39f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62786804"
---
# <a name="configure-the-query-governor-cost-limit-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Kostenbeschränkung der Abfragekontrolle
  In diesem Thema wird beschrieben, wie `query governor cost limit` die Server Konfigurationsoption [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in mithilfe [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] von [!INCLUDE[tsql](../../includes/tsql-md.md)]oder konfiguriert wird. Die Kostenbeschränkungsoption der Abfragekontrolle legt ein Höchstlimit für den Zeitraum an, in dem eine Abfrage ausgeführt werden kann. Die Abfragekosten beziehen sich auf eine geschätzte Zeit in Sekunden, die für das Ausführen einer Abfrage bei einer bestimmten Hardwarekonfiguration benötigt wird. Der Standardwert für diese Option ist 0, mit dem die Abfragekontrolle deaktiviert wird. Alle Abfragen können dann ohne zeitliche Begrenzung ausgeführt werden. Wenn Sie einen nicht negativen Wert ungleich Null angeben, lässt die Abfragekontrolle die Ausführung von Abfragen nicht zu, deren geschätzte Kosten über diesem Wert liegen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Kostenbeschränkung der Abfragekontrolle mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option „Kostenbeschränkung der Abfragekontrolle“](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   Wenn Sie den Wert der Option Kostenbeschränkung der Abfragekontrolle jeweils für eine Verbindung ändern möchten, können Sie dazu die [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) -Anweisung verwenden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a>So konfigurieren Sie die Option Kostenbeschränkung der Abfragekontrolle  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf die Seite **Verbindungen** .  
  
3.  Aktivieren bzw. deaktivieren Sie das Kontrollkästchen **Abfragekontrolle verwenden, um Abfragen mit langer Ausführungszeit zu verhindern** .  
  
     Wenn Sie dieses Kontrollkästchen aktivieren, geben Sie in das untere Feld einen positiven Wert ein, der von der Abfragekontrolle verwendet wird, um das Ausführen von Abfragen nicht zuzulassen, deren Ausführungszeiten diesen Wert überschreiten.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a>So konfigurieren Sie die Option Kostenbeschränkung der Abfragekontrolle  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `query governor cost limit` auf `120` Sekunden festzulegen.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query governor cost limit', 120 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="follow-up-after-you-configure-the-query-governor-cost-limit-option"></a><a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option „Kostenbeschränkung der Abfragekontrolle“  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
