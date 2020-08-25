---
description: Erstellen von Unique-Einschränkungen
title: Erstellen von Unique-Einschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- UNIQUE_TSQL
helpviewer_keywords:
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], creating
- constraints [SQL Server], unique
ms.assetid: a86f9d6f-f242-43be-b65d-b3435b71b62a
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c641b2562fa15f17bcb6ce235529916ca70a2a52
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646320"
---
# <a name="create-unique-constraints"></a>Erstellen von Unique-Einschränkungen

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine UNIQUE-Einschränkung in [!INCLUDE[tsql](../../includes/tsql-md.md)] erstellen, um sicherzustellen, dass in bestimmte Spalten, die nicht zum Primärschlüssel gehören, Werte nicht mehrfach eingegeben werden können. Durch die Erstellung einer UNIQUE-Einschränkung wird automatisch ein entsprechender eindeutiger Index erstellt.  
  
> [!NOTE]    
> Unter [Primärschlüssel, Fremdschlüssel und eindeutiger Schlüssel in SQL Analytics](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-table-constraints) finden Sie weitere Informationen zu UNIQUE-Einschränkungen in Azure Synapse Analytics.
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So erstellen Sie eine UNIQUE-Einschränkung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-unique-constraint"></a>So erstellen Sie eine UNIQUE-Einschränkung  
  
1.  Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle, der Sie eine UNIQUE-Einschränkung hinzufügen möchten, und klicken Sie auf **Entwerfen**.  
  
2.  Klicken Sie im Menü **Tabellen-Designer** auf **Indizes/Schlüssel**.  
  
3.  Klicken Sie im Dialogfeld **Indizes/Schlüssel** auf **Hinzufügen**.  
  
4.  Klicken Sie im Datenblattbereich unter **Allgemein**auf **Typ** , und wählen Sie im Dropdown-Listenfeld rechts neben der Eigenschaft den Eintrag **Eindeutiger Schlüssel** aus.  
  
5.  Klicken Sie im Menü **Datei** auf _Tabellenname_**speichern**.  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-unique-constraint"></a>So erstellen Sie eine UNIQUE-Einschränkung  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel wird die Tabelle `TransactionHistoryArchive4` angelegt und eine UNIQUE-Einschränkung für die Spalte `TransactionID`erstellt.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive4  
     (  
       TransactionID int NOT NULL,   
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)   
    );   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-on-an-existing-table"></a>So erstellen Sie eine UNIQUE-Einschränkung für eine vorhandene Tabelle  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel werden eine UNIQUE-Einschränkung für die Spalten `PasswordHash` und `PasswordSalt` in der Tabelle `Person.Password`erstellt.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    ALTER TABLE Person.Password   
    ADD CONSTRAINT AK_Password UNIQUE (PasswordHash, PasswordSalt);   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-in-an-new-table"></a>So erstellen Sie eine UNIQUE-Einschränkung für eine neue Tabelle  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel wird eine Tabelle erstellt und dann wird eine UNIQUE-Einschränkung für die Spalte `TransactionID`definiert.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive2  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)  
    );  
    GO  
  
    ```  
  
     Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md), [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md) und [table_constraint &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-table-constraint-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
