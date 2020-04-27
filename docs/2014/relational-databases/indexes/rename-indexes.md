---
title: Umbenennen von Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- renaming indexes
- index names [SQL Server]
- indexes [SQL Server], renaming
ms.assetid: d3d612a1-ea1b-4d99-85d2-0a2ad54f4b0e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 744e7a10c9c4dcd776d58b6234749f2be5aa1479
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63036219"
---
# <a name="rename-indexes"></a>Umbenennen von Indizes
  In diesem Thema wird beschrieben, wie ein Index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]umbenannt wird. Wenn Sie einen Index umbenennen, wird der aktuelle Name des Indexes durch den neuen Namen ersetzt, den Sie bereitstellen. Der angegebene Name muss innerhalb der Tabelle oder Sicht eindeutig sein. So können z.B. zwei Tabellen über einen Index mit dem Namen **XPK_1**verfügen; innerhalb derselben Tabelle können jedoch nicht zwei Indizes mit dem Namen **XPK_1**verwendet werden. Sie können keinen Index mit dem gleichen Namen erstellen, den ein vorhandener deaktivierter Index aufweist. Das Umbenennen eines Indexes bewirkt nicht, dass der Index neu erstellt wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So benennen Sie einen Index um mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Wenn Sie eine PRIMARY KEY- oder eine UNIQUE-Einschränkung für eine Tabelle erstellen, wird für die Tabelle automatisch ein Index erstellt, der denselben Namen wie die Einschränkung erhält. Da Indexnamen innerhalb der Tabelle eindeutig sein müssen, können Sie keinen Index erstellen oder umbenennen, wenn dieser anschließend denselben Namen wie eine vorhandene PRIMARY KEY- oder UNIQUE-Einschränkung für die Tabelle verwendet.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für den Index.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-rename-an-index-by-using-the-table-designer"></a>So benennen Sie einen Index mit dem Tabellen-Designer um  
  
1.  Klicken Sie im Objekt-Explorer auf das Pluszeichen, um die Datenbank zu erweitern, die die Tabelle enthält, in der Sie einen Index umbenennen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Tabellen** zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Tabelle, für die Sie einen Index umbenennen möchten, und wählen Sie **Entwurf**.  
  
4.  Klicken Sie im Menü **Tabellen-Designer** auf **Indizes/Schlüssel**.  
  
5.  Wählen Sie im Textfeld **Ausgewählter Primärschlüssel/eindeutiger Schlüssel oder Index** den Index aus, den Sie umbenennen möchten.  
  
6.  Klicken Sie im Raster auf **Name** , und geben Sie in das Textfeld einen neuen Namen ein.  
  
7.  Klicken Sie auf **Schließen**.  
  
8.  Klicken Sie im Menü **Datei** auf **Speichern**_table_name_.  
  
#### <a name="to-rename-an-index-by-using-object-explorer"></a>So benennen Sie einen Index mit dem Objekt-Explorer um  
  
1.  Klicken Sie im Objekt-Explorer auf das Pluszeichen, um die Datenbank zu erweitern, die die Tabelle enthält, in der Sie einen Index umbenennen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Tabellen** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um die Tabelle zu erweitern, für die Sie einen Index umbenennen möchten.  
  
4.  Klicken Sie auf das Pluszeichen, um den Ordner **Indizes** zu erweitern.  
  
5.  Klicken Sie mit der rechten Maustaste auf den Index, den Sie umbenennen möchten, und wählen Sie **Umbenennen**.  
  
6.  Geben Sie den neuen Namen des Indexes ein, und drücken Sie die EINGABETASTE.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-rename-an-index"></a>So benennen Sie einen Index um  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Renames the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table to IX_VendorID.   
  
    EXEC sp_rename N'Purchasing.ProductVendor.IX_ProductVendor_VendorID', N'IX_VendorID', N'INDEX';   
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).  
  
  
