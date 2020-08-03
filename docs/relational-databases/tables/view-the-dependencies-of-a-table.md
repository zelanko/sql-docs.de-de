---
title: Anzeigen der Abhängigkeiten einer Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table dependencies [SQL Server]
- dependencies [SQL Server], tables
- displaying dependences
- viewing dependencies
ms.assetid: c4351ef5-e7d0-46e7-8367-88695e9974f8
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dd39db91c0ee2e6e71ed351fa39dae66921e0207
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394647"
---
# <a name="view-the-dependencies-of-a-table"></a>Anzeigen der Abhängigkeiten einer Tabelle
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa-pdw.md)]

  Sie können die Abhängigkeiten einer Tabelle in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)] anzeigen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So zeigen Sie die Abhängigkeiten einer Tabelle mit folgenden Elementen an:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die VIEW DEFINITION-Berechtigung für die Datenbank und die SELECT-Berechtigung für sys.sql_expression_dependencies für die Datenbank. Standardmäßig wird die SELECT-Berechtigung nur Mitgliedern der festen Datenbankrolle db_owner gewährt. Wenn einem anderen Benutzer die SELECT-Berechtigung und die VIEW DEFINITION-Berechtigung erteilt werden, kann dieser Berechtigte alle Abhängigkeiten in der Datenbank anzeigen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-the-objects-on-which-a-table-depends"></a>So zeigen Sie die Objekte an, von denen eine Tabelle abhängt  
  
1.  Erweitern Sie im **Objekt-Explorer**den Ordner **Datenbanken**, erweitern Sie eine Datenbank, und erweitern Sie dann **Tabellen**.  
  
2.  Klicken Sie mit der rechten Maustaste auf eine Tabelle, und klicken Sie dann auf **Abhängigkeiten anzeigen**.  
  
3.  Wählen Sie im Dialogfeld **Objektabhängigkeiten** _\<object name\>_ entweder **Objekte, die von**  abhängig sind _\<object name\>_ oder **Objekte, von denen** _\<object name\>_ **abhängt** aus.  
  
4.  Wählen Sie im Raster **Abhängigkeiten** ein Objekt aus. Der Objekttyp (z.B. „Trigger“ oder „Gespeicherte Prozedur“) wird im Feld **Typ** angezeigt.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-the-objects-that-depend-on-a-table"></a>So zeigen Sie die Objekte an, die von einer Tabelle abhängen  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');   
    GO  
  
    ```  
  
#### <a name="to-view-the-dependencies-of-a-table"></a>So zeigen Sie die Abhängigkeiten einer Tabelle an  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Im folgenden Beispiel werden die Objekte, die von der Tabelle `Production.Product`abhängen, zurückgegeben. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referenced_id = OBJECT_ID(N'Production.Product');   
    GO  
  
    ```  
  
 Weitere Informationen finden Sie unter [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md).  
  
  
