---
title: Löschen von Unique-Einschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- UNIQUE constraints [SQL Server], deleting
- constraints [SQL Server], deleting
- deleting constraints
- constraints [SQL Server], unique
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1b96ee1324f58163057144497dbaac28d5824e5d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225200"
---
# <a name="delete-unique-constraints"></a>Löschen von Unique-Einschränkungen
  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine UNIQUE-Einschränkung in [!INCLUDE[tsql](../../includes/tsql-md.md)]löschen. Wenn eine Unique-Einschränkung gelöscht wird, werden die Forderung nach Eindeutigkeit für die Werte, die in die Spalte oder Spaltenkombination im Einschränkungsausdruck eingegeben werden, und der zugehörige eindeutige index entfernt.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So löschen Sie eine Unique-Einschränkung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-unique-constraint-using-object-explorer"></a>So löschen Sie eine UNIQUE-Einschränkung im Objekt-Explorer  
  
1.  Erweitern Sie im Objekt-Explorer die Tabelle, die die eindeutige Einschränkung enthält, und dann erweitern Sie **Einschränkungen**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Schlüssel, und klicken Sie dann auf **Löschen**.  
  
3.  Überprüfen Sie im Dialogfeld **Objekt löschen** , ob der richtige Schlüssel angegeben worden ist, und klicken Sie auf **OK**.  
  
#### <a name="to-delete-a-unique-constraint-using-table-designer"></a>So löschen Sie eine eindeutige Einschränkung mit dem Tabellen-Designer  
  
1.  Klicken Sie im **Objekt-Explorer** mit der rechten Maustaste auf die Tabelle mit der UNIQUE-Einschränkung, und klicken Sie dann auf **Entwerfen**.  
  
2.  Klicken Sie im Menü **Tabellen-Designer** auf **Indizes/Schlüssel**.  
  
3.  Wählen Sie im Dialogfeld **Indizes/Schlüssel** in der Liste **Ausgewählter Primärschlüssel/eindeutiger Schlüssel und Index** den eindeutigen Schlüssel aus.  
  
4.  Klicken Sie auf **Löschen**.  
  
5.  Klicken Sie im Menü **Datei** auf **Speichern** > *Tabellenname*.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-unique-constraint"></a>So löschen Sie eine Unique-Einschränkung  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Return the name of unique constraint.  
    SELECT name  
    FROM sys.objects  
    WHERE type = 'UQ' AND OBJECT_NAME(parent_object_id) = N' DocExc';  
    GO  
    -- Delete the unique constraint.  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT UNQ_ColumnB_DocExc;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) und [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).  
  
###  <a name="TsqlExample"></a>  
