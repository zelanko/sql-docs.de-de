---
description: Deaktivieren von Fremdschlüsseleinschränkungen mit INSERT- und UPDATE-Anweisungen
title: Deaktivieren von Fremdschlüsseleinschränkungen in INSERT- und UPDATE-Anweisungen
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
- UPDATE statement [SQL Server], foreign key constraints
- INSERT statement [SQL Server], foreign key constraints
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d68a5689d31d5db0e4221e4fc58ec5d724ee4fdf
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96130885"
---
# <a name="disable-foreign-key-constraints-with-insert-and-update-statements"></a>Deaktivieren von Fremdschlüsseleinschränkungen mit INSERT- und UPDATE-Anweisungen
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa-pdw.md)]

  Sie können eine Fremdschlüsseleinschränkung während der Durchführung von INSERT- und UPDATE-Transaktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]deaktivieren. Verwenden Sie diese Option, wenn Sie wissen, dass neue Daten nicht gegen die vorhandene Einschränkung verstoßen, oder wenn die Einschränkung nur für die bereits in der Datenbank vorhandenen Daten gilt.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So deaktivieren Sie eine Fremdschlüsseleinschränkung für INSERT- und UPDATE-Anweisungen mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Sobald diese Einschränkungen deaktiviert worden sind, wird die Spalte bei Einfügungen oder Updates nicht mehr bezüglich der Einschränkungsbedingungen überprüft.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a>So deaktivieren Sie eine Fremdschlüsseleinschränkung für die Anweisungen INSERT und UPDATE  
  
1.  Erweitern Sie im **Objekt-Explorer** die Tabelle mit der Einschränkung, und erweitern Sie dann den Ordner **Schlüssel** .  
  
2.  Klicken Sie mit der rechten Maustaste auf die Einschränkung, und wählen Sie anschließend **Ändern** aus.  
  
3.  Klicken Sie im Raster unter dem **Tabellen-Designer** auf **Fremdschlüsseleinschränkung erzwingen** , und wählen Sie im Dropdownmenü **Nein** aus.  
  
4.  Klicken Sie auf **Schließen**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a>So deaktivieren Sie eine Fremdschlüsseleinschränkung für die Anweisungen INSERT und UPDATE  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie die folgenden Beispiele, fügen Sie sie in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
