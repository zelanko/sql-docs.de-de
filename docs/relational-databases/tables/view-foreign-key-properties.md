---
title: Anzeigen von Fremdschlüsseleigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], attributes
- displaying foreign keys attributes
- viewing foreign keys attributes
ms.assetid: b0e57cb7-9b26-4b96-b76a-1f59f5f498c5
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f98435c4c8813d6cf5f9b9d3f451b9be0bb8f284
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129531"
---
# <a name="view-foreign-key-properties"></a>Anzeigen von Fremdschlüsseleigenschaften
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Sie können die Fremdschlüsselattribute einer Beziehung in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]anzeigen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So zeigen Sie die Fremdschlüsselattribute einer bestimmten Tabelle an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a>So zeigen Sie die Fremdschlüsselattribute einer Beziehung in einer bestimmten Tabelle an  
  
1.  Öffnen Sie den Tabellen-Designer für die Tabelle, in der der anzuzeigende Fremdschlüssel enthalten ist. Klicken Sie mit der rechten Maustaste in den Tabellen-Designer, und wählen Sie im Kontextmenü **Beziehungen** aus.  
  
2.  Wählen Sie im Dialogfeld **Fremdschlüsselbeziehungen** diejenige Beziehung aus, deren Eigenschaften Sie betrachten möchten.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 Wenn die Fremdschlüsselspalten mit einem Primärschlüssel verknüpft sind, werden die Primärschlüsselspalten in **Tabellen-Designer** durch ein Primärschlüsselsymbol gekennzeichnet, das im Zeilenselektor angezeigt wird.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a>So zeigen Sie die Fremdschlüsselattribute einer Beziehung in einer bestimmten Tabelle an  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel werden alle Fremdschlüssel und ihre Eigenschaften für die Tabelle `HumanResources.Employee` in der Beispieldatenbank zurückgegeben.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT   
        f.name AS foreign_key_name  
       ,OBJECT_NAME(f.parent_object_id) AS table_name  
       ,COL_NAME(fc.parent_object_id, fc.parent_column_id) AS constraint_column_name  
       ,OBJECT_NAME (f.referenced_object_id) AS referenced_object  
       ,COL_NAME(fc.referenced_object_id, fc.referenced_column_id) AS referenced_column_name  
       ,is_disabled  
       ,delete_referential_action_desc  
       ,update_referential_action_desc  
    FROM sys.foreign_keys AS f  
    INNER JOIN sys.foreign_key_columns AS fc   
       ON f.object_id = fc.constraint_object_id   
    WHERE f.parent_object_id = OBJECT_ID('HumanResources.Employee');  
    ```  
  
 Weitere Informationen finden Sie unter [sys.foreign_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md) und [sys.foreign_key_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
