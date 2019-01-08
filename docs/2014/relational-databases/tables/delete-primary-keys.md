---
title: Löschen von Primärschlüsseln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing primary keys
- deleting primary keys
- primary keys [SQL Server], deleting
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 690b52fceb74269501880565bab65b020206fa61
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52814532"
---
# <a name="delete-primary-keys"></a>Löschen von Primärschlüsseln
  Sie können einen Primärschlüssel mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[tsql](../../includes/tsql-md.md)]löschen (DROP). Wenn der Primärschlüssel gelöscht wird, wird auch der zugehörige Index gelöscht.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So löschen Sie einen Primärschlüssel mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-delete-a-primary-key-constraint-using-object-explorer"></a>So löschen Sie eine PRIMARY KEY-Einschränkung mit Objekt-Explorer  
  
1.  Erweitern Sie im Objekt-Explorer die Tabelle, die den Primärschlüssel enthält, und erweitern Sie dann **Schlüssel**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Schlüssel, und klicken Sie dann auf **Löschen**.  
  
3.  Überprüfen Sie im Dialogfeld **Objekt löschen** , ob der richtige Schlüssel angegeben worden ist, und klicken Sie auf **OK**.  
  
#### <a name="to-delete-a-primary-key-constraint-using-table-designer"></a>So löschen Sie eine PRIMARY KEY-Einschränkung mit dem Tabellen-Designer  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle mit dem Primärschlüssel, und klicken Sie dann auf **Entwerfen**.  
  
2.  Klicken Sie in der Tabelle mit der rechten Maustaste auf die Zeile mit dem Primärschlüssel, und wählen Sie **Primärschlüssel entfernen** aus, um die Einstellung zu deaktivieren.  
  
    > [!NOTE]  
    >  Schließen Sie die Tabelle, ohne die Änderungen zu speichern, um diese Aktion rückgängig zu machen. Das Löschen eines Primärschlüssels lässt sich nicht rückgängig machen, ohne dass auch alle anderen Änderungen an der Tabelle aufgehoben werden.  
  
3.  Klicken Sie im Menü **Datei** auf **Speichern**_table name_.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-primary-key-constraint"></a>So löschen Sie einen Primärschlüssel  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel wird zuerst der Name der Primärschlüsseleinschränkung identifiziert, und dann wird die Einschränkung gelöscht.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) und [sys.key_constraints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)  
  
###  <a name="TsqlExample"></a>  
