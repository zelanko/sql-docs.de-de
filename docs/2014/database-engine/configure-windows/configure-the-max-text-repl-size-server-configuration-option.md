---
title: Konfigurieren der Serverkonfigurationsoption „max text repl size“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- max text repl size option
ms.assetid: 3056cf64-621d-4996-9162-3913f6bc6d5b
caps.latest.revision: 35
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 78f0bd4fd322294c4c3a1d15efeaac64ca19e8c0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149957"
---
# <a name="configure-the-max-text-repl-size-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption max text repl size
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **Max. Textgröße für Replikation** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert wird. Die **Max. Textgröße** Option gibt die maximale Größe (in Bytes) der `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, `xml`, und `image` Daten, die hinzugefügt werden können einer replizierten oder aufgezeichneten Spalte in einer einzelnen INSERT-, Update-, WRITETEXT- oder UPDATETEXT-Anweisung. Der Standardwert ist 65536 Byte. Der Wert -1 gibt an, dass mit Ausnahme der durch den Datentyp auferlegten Größenbegrenzung keine Begrenzung der Größe gilt.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Max. Textgröße für Replikation mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option „max text repl size“](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Diese Option gilt für die Transaktionsreplikation und Change Data Capture. Wenn ein Server sowohl für die Transaktionsreplikation als auch für Change Data Capture konfiguriert ist, gilt der angegebene Wert für beide Funktionen. Diese Option gilt nicht für die Momentaufnahmereplikation und die Mergereplikation.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a>So konfigurieren Sie die Option Max. Textgröße für Replikation  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften**aus.  
  
2.  Klicken Sie auf den **Erweitert** -Knoten.  
  
3.  Geben Sie unter **Verschiedenes**für die Option **Max. Textgröße für Replikation** den gewünschten Wert an.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a>So konfigurieren Sie die Option Max. Textgröße für Replikation  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um die Option `max text repl size` auf `-1`festzulegen.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;   
RECONFIGURE ;   
GO  
EXEC sp_configure 'max text repl size', -1 ;   
GO  
RECONFIGURE;   
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="FollowUp"></a> Nachverfolgung: Nach dem Konfigurieren der Option Max. Textgröße für Replikation  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationsfunktionen und -tasks](../../relational-databases/replication/replication-features-and-tasks.md)   
 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql)   
 [UPDATETEXT (Transact-SQL)](/sql/t-sql/queries/updatetext-transact-sql)   
 [WRITETEXT (Transact-SQL)](/sql/t-sql/queries/writetext-transact-sql)  
  
  
