---
title: Umbenennen einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/02/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], renaming
- renaming databases
ms.assetid: 44c69d35-abcb-4da3-9370-5e0bc9a28496
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a2cfe01b4df32e0966084866a67cea4bfd57bc11
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "72907429"
---
# <a name="rename-a-database"></a>Umbenennen einer Datenbank

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In diesem Artikel wird beschrieben, wie eine benutzerdefinierte Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder Azure SQL-Datenbank mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)] umbenannt wird. Der Name der Datenbank kann alle Zeichen enthalten, die den Regeln für Bezeichner entsprechen.  
  
## <a name="in-this-topic"></a>In diesem Thema
  
- Vorbereitungen  
  
     [Einschränkungen](#limitations-and-restrictions)  
  
     [Security](#security)  
  
- So benennen Sie eine Datenbank um mit:  
  
     [SQL Server Management Studio](#rename-a-database-using-sql-server-management-studio)  
  
     [Transact-SQL](#rename-a-database-using-transact-sql)  
  
- **Nachverfolgung:**  [Nach dem Umbenennen einer Datenbank](#backup-after-renaming-a-database)  

> [!NOTE]
> Um eine Datenbank in Azure SQL Data Warehouse oder Parallel Data Warehouse umzubenennen, verwenden Sie die Anweisung [RENAME (Transact-SQL)](../../t-sql/statements/rename-transact-sql.md).
  
## <a name="before-you-begin"></a>Vorbereitungen
  
### <a name="limitations-and-restrictions"></a>Einschränkungen  
  
- Systemdatenbanken können nicht umbenannt werden.
- Der Name der Datenbank kann nicht geändert werden, während andere Benutzer auf die Datenbank zugreifen. 
  - In SQL Server können Sie den Einzelbenutzermodus für eine Datenbank festlegen, um offene Verbindungen zu schließen. Weitere Informationen finden Sie unter [Festlegen des Einzelbenutzermodus für eine Datenbank](../../relational-databases/databases/set-a-database-to-single-user-mode.md).
  - Sie müssen in Azure SQL-Datenbank sicherstellen, dass keine andere Benutzer über eine offene Verbindung zur Datenbank verfügen, die Sie umbenennen möchten.
  
### <a name="security"></a>Sicherheit  
  
#### <a name="permissions"></a>Berechtigungen

Erfordert die ALTER-Berechtigung für die Datenbank.  
  
## <a name="rename-a-database-using-sql-server-management-studio"></a>Umbenennen einer Datenbank mit SQL Server Management Studio

Verwenden Sie die folgenden Schritte zum Umbenennen einer Instanz von SQL Server oder Azure SQL-Datenbank mit SQL Server Management Studio.

  
1. Stellen Sie im **Objekt-Explorer** eine Verbindung zu Ihrer SQL-Instanz her.  
  
2. Stellen Sie sicher, dass keine offenen Verbindungen zur Datenbank bestehen. Wenn Sie SQL Server verwenden, können Sie [den Einzelbenutzermodus für die Datenbank festlegen](../../relational-databases/databases/set-a-database-to-single-user-mode.md), um alle offenen Verbindungen zu schließen und zu verhindern, dass andere Benutzer eine Verbindung herstellen, während Sie den Namen der Datenbank ändern.  
  
3. Erweitern Sie im Objekt-Explorer **Datenbanken**, klicken Sie mit der rechten Maustaste auf die Datenbank, die umbenannt werden soll, und klicken Sie anschließend auf **Umbenennen**.  
  
4. Geben Sie den neuen Datenbanknamen ein, und klicken Sie dann auf **OK**.  
  
5. Handelt es sich bei der Datenbank um die Standarddatenbank, können Sie sie optional nach dem Umbenennen zurücksetzen. Informationen hierzu finden Sie im Abschnitt [Zurücksetzen der Standarddatenbank nach dem Umbenennen](#reset-your-default-database-after-rename).

## <a name="rename-a-database-using-transact-sql"></a>Umbenennen einer Datenbank mit Transact-SQL  
  
### <a name="to-rename-a-sql-server-database-by-placing-it-in-single-user-mode"></a>So benennen Sie eine SQL Server-Datenbank um, indem Sie den Einzelbenutzermodus festlegen

Verwenden Sie die folgenden Schritte, um eine SQL Server-Datenbank in SQL Server Management Studio mit T-SQL umzubenennen. Dazu gehören die Schritte zum Festlegen des Einzelbenutzermodus für die Datenbank sowie das erneute Festlegen des Mehrbenutzermodus für die Datenbank, nachdem sie umbenannt wurde.
  
1. Stellen Sie für Ihre Instanz eine Verbindung zur `master`-Datenbank her.  
2. Öffnen Sie ein Abfragefenster.  
3. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird der Name der Datenbank `MyTestDatabase` in `MyTestDatabaseCopy`geändert.
  
   ```sql
   USE master;  
   GO  
   ALTER DATABASE MyTestDatabase SET SINGLE_USER WITH ROLLBACK IMMEDIATE
   GO
   ALTER DATABASE MyTestDatabase MODIFY NAME = MyTestDatabaseCopy ;
   GO  
   ALTER DATABASE MyTestDatabaseCopy SET MULTI_USER
   GO
   ```  

4. Handelt es sich bei der Datenbank um die Standarddatenbank, können Sie sie optional nach dem Umbenennen zurücksetzen. Informationen hierzu finden Sie im Abschnitt [Zurücksetzen der Standarddatenbank nach dem Umbenennen](#reset-your-default-database-after-rename).

### <a name="to-rename-an-azure-sql-database-database"></a>So benennen Sie eine Datenbank in Azure SQL-Datenbank um

Verwenden Sie die folgenden Schritte zum Umbenennen einer Instanz von Azure SQL-Datenbank mit T-SQL in SQL Server Management Studio.
  
1. Stellen Sie für Ihre Instanz eine Verbindung zur `master`-Datenbank her.  
2. Öffnen Sie ein Abfragefenster.
3. Stellen Sie sicher, dass niemand die Datenbank verwendet.
4. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird der Name der Datenbank `MyTestDatabase` in `MyTestDatabaseCopy`geändert.
  
   ```sql
   ALTER DATABASE MyTestDatabase MODIFY NAME = MyTestDatabaseCopy ;
   ```  

## <a name="backup-after-renaming-a-database"></a>Sicherung nach dem Umbenennen einer Datenbank  

Sichern Sie die `master`-Datenbank, nachdem Sie eine Datenbank in SQL Server umbenennen. Dies ist in Azure SQL-Datenbank nicht erforderlich, da Sicherungen automatisch erstellt werden.  
  
## <a name="reset-your-default-database-after-rename"></a>Zurücksetzen der Standarddatenbank nach dem Umbenennen

Wurde die Datenbank, die Sie umbenennen, als Standarddatenbank festgelegt, setzen Sie die Standardeinstellung mit dem folgenden Befehl auf die umbenannte Datenbank zurück:


```sql
USE [master]
GO
ALTER LOGIN [your-login] WITH DEFAULT_DATABASE=[new-database-name]
GO
```


## <a name="see-also"></a>Weitere Informationen

- [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)
- [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md)  
