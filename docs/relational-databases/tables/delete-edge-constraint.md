---
title: Löschen von Edgeeinschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing edge constraint
- deleting edge constraint, deleting connection constraint
- SQL Graph
- graph edge constraints
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3761d9e8507eb7051fe7a6cc39b83abfa091566d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774680"
---
# <a name="delete-edge-constraints"></a>Löschen von Edgeeinschränkungen
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Sie können eine Edgeeinschränkung in [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)] löschen. 
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So löschen Sie einen Primärschlüssel mit:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-an-edge-constraint"></a>Löschen einer Edgeeinschränkung
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Das Beispiel identifiziert zuerst den Namen der Edgeeinschränkung und löscht sie dann.  
  
    ```sql
    USE TEMPDB
    GO
    -- CREATE node and edge tables
    CREATE TABLE Customer
    (
        ID INTEGER PRIMARY KEY, 
        CustomerName VARCHAR(100)
    )
    AS NODE
    GO

    CREATE TABLE Product 
    (
        ID INTEGER PRIMARY KEY, 
        ProductName VARCHAR(100)
    ) AS NODE
    GO

    CREATE TABLE bought
    (
        PurchaseCount INT,
        CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
    )
    AS EDGE
    GO
    
    -- Return the name of edge constraint.
    SELECT name  
    FROM sys.edge_constraints  
    WHERE type = 'EC' AND parent_object_id = OBJECT_ID('bought');  
    GO  

    -- Delete the primary key constraint.  
    ALTER TABLE bought
    DROP CONSTRAINT EC_BOUGHT
    GO
    ```  
  
 Weitere Informationen finden Sie unter[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md), [sys.edge_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-edge-constraints-transact-sql.md) und [ssys.edge_constraint_clauses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-edge-constraint-clauses-transact-sql.md)
  
###  <a name="TsqlExample"></a>  
