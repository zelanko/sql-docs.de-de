---
title: Löschen von Sichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-views
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a8ed1ad09f530575e94a61934f464ca3c2f2e6fa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149582"
---
# <a name="delete-views"></a>Löschen von Sichten
  Sie können Sichten in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] löschen, indem Sie Folgendes verwenden: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  

  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie eine Sicht löschen, werden die Definition der Sicht sowie weitere Informationen zur Sicht aus dem Systemkatalog entfernt. Alle Berechtigungen für die Sicht werden ebenfalls gelöscht.  
  
-   Eine mithilfe von `DROP TABLE` gelöschte Sicht in einer Tabelle muss explizit mit `DROP VIEW`gelöscht werden.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert entweder die ALTER-Berechtigung für SCHEMA oder die CONTROL-Berechtigung für OBJECT.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-view-from-a-database"></a>So löschen Sie eine Sicht aus einer Datenbank  
  
1.  Erweitern Sie im **Objekt-Explorer**die Datenbank mit der Sicht, die Sie löschen möchten, und erweitern Sie dann den Ordner **Sichten** .  
  
2.  Klicken Sie mit der rechten Maustaste auf die Sicht, die Sie löschen möchten, und klicken Sie auf **Löschen**.  
  
3.  Klicken Sie im Dialogfeld **Objekt löschen** auf **OK**.  
  
    > [!IMPORTANT]  
    >  Klicken Sie im Dialogfeld **Objekt löschen** auf **Abhängigkeiten anzeigen**, um das Dialogfeld ****Abhängigkeiten für Ansichtsname** zu öffnen. Es werden alle Objekte angezeigt, die von der Sicht abhängig sind, und alle Objekte, von denen die Sicht abhängig ist.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-view-from-a-database"></a>So löschen Sie eine Sicht aus einer Datenbank  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel wird die angegebene Sicht nur gelöscht, wenn die Sicht bereits vorhanden ist.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).  
  
  
