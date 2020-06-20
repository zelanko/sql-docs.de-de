---
title: Löschen eines Indexes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- dropping indexes
- indexes [SQL Server], dropping
- index deletions [SQL Server]
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4552ba701782e5790f95f54c0c1c66f82573f1e3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025620"
---
# <a name="delete-an-index"></a>Löschen eines Indexes
  In diesem Thema wird beschrieben, wie ein Index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]gelöscht wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So löschen Sie einen Index mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Indizes, die als Ergebnis einer PRIMARY KEY- oder UNIQUE-Einschränkung erstellt wurden, können mit dieser Methode nicht gelöscht werden. In diesem Fall muss die Einschränkung gelöscht werden. Verwenden Sie [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) mit der DROP CONSTRAINT-Klausel in [!INCLUDE[tsql](../../includes/tsql-md.md)], wenn Sie die Einschränkung und den entsprechenden Index entfernen möchten. Weitere Informationen finden Sie unter [Delete Primary Keys](../tables/delete-primary-keys.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung in der Tabelle oder Sicht. Über diese Berechtigungen verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** und die Mitglieder der festen Datenbankrollen **db_ddladmin** und **db_owner** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-an-index-by-using-object-explorer"></a>So löschen Sie einen Index mit dem Objekt-Explorer  
  
1.  Erweitern Sie im Objekt-Explorer die Datenbank mit der Tabelle, in der Sie einen Index löschen möchten.  
  
2.  Erweitern Sie den Ordner **Tabellen** .  
  
3.  Erweitern Sie die Tabelle, die den zu löschenden Index enthält.  
  
4.  Erweitern Sie den Ordner **Indizes** .  
  
5.  Klicken Sie mit der rechten Maustaste auf den Index, den Sie löschen möchten, und klicken Sie dann auf **Löschen**.  
  
6.  Überprüfen Sie im Dialogfeld **Objekt löschen** , ob sich der richtige Index im Raster **Zu löschendes Objekt** befindet, und klicken Sie auf **OK**.  
  
#### <a name="to-delete-an-index-using-table-designer"></a>So löschen Sie einen Index mit dem Tabellen-Designer  
  
1.  Erweitern Sie im Objekt-Explorer die Datenbank mit der Tabelle, in der Sie einen Index löschen möchten.  
  
2.  Erweitern Sie den Ordner **Tabellen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Tabelle, die den zu löschenden Index enthält, und klicken Sie auf Entwurf.  
  
4.  Klicken Sie im Menü **Tabellen-Designer** auf **Indizes/Schlüssel**.  
  
5.  Wählen Sie im Dialogfeld **Indizes/Schlüssel** den Index aus, den Sie löschen möchten.  
  
6.  Klicken Sie auf **Löschen**.  
  
7.  Klicken Sie auf **Schließen**.  
  
8.  Klicken Sie im Menü **Datei** auf **Save**_Tabellenname_.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-an-index"></a>So löschen Sie einen Index  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql).  
  
  
