---
title: Erste Schritte mit SQL Server-Sicherheit unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die typischen Sicherheitsaktionen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.openlocfilehash: 655aebb0c07c812a7aa6c81e7c7033d85e8b7ce2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705204"
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Exemplarische Vorgehensweise für die Sicherheitsfunktionen von SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Wenn Sie einen Linux-Benutzer, der in SQL Server neu ist sind, durchlaufen die folgenden Aufgaben Sie einige der Sicherheitsaufgaben. Diese sind nicht eindeutig oder speziell für Linux, aber es hilft, erhalten Sie eine Vorstellung von Bereichen, um weiter zu untersuchen. In jedem Beispiel wird ein Link in der ausführlichen Dokumentation für den entsprechenden Bereich bereitgestellt.

> [!NOTE]
>  Die folgenden Beispiele verwenden die **AdventureWorks2014** -Beispieldatenbank. Anweisungen zum Abrufen und Installieren dieser Beispieldatenbank finden Sie [wiederherstellen eine SQL Server-Datenbank von Windows bis Linux](sql-server-linux-migrate-restore-database.md).


## <a name="create-a-login-and-a-database-user"></a>Erstellen Sie einen Anmeldenamen und Datenbankbenutzer 

Erteilen Sie anderen Zugriff auf SQL Server durch Erstellen eines Anmeldenamens in der master-Datenbank mithilfe der [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) Anweisung. Zum Beispiel:

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

> [!NOTE]
>  Verwenden Sie immer ein sicheres Kennwort ein, anstelle die Sternchen im vorherigen Befehl.

Anmeldungen können verbinden mit SQL Server und Zugriffsrechte (mit eingeschränkten Berechtigungen) für die master-Datenbank. Zum Verbinden mit einer Benutzerdatenbank benötigt eine Anmeldung eine entsprechende Identität auf Datenbankebene, dem Namen eines Datenbankbenutzers. Benutzer sind spezifisch für jede Datenbank, und müssen separat erstellt werden, in jeder Datenbank, um ihnen Zugriff gewähren. Im folgende Beispiel wird Sie in der AdventureWorks2014-Datenbank verschoben und verwendet dann die [CREATE USER](../t-sql/statements/create-user-transact-sql.md) -Anweisung zum Erstellen einer Benutzers namens Larry, das mit der Anmeldung mit dem Namen Larry verknüpft ist. Obwohl die Anmeldung und dem Benutzer verknüpft sind (die miteinander verknüpft sind), handelt es sich um verschiedene Objekte. Die Anmeldung ist ein Prinzip auf Serverebene. Der Benutzer ist ein Prinzipal auf Datenbankebene.

```
USE AdventureWorks2014;
GO
CREATE USER Larry;
GO
```

- Ein SQL Server-Administratorkonto kann auf eine beliebige Datenbank eine Verbindung herstellen und kann weitere Anmeldungen und Benutzern in einer beliebigen Datenbank erstellen.  
- Wenn ein Benutzer eine Datenbank erstellt, werden sie Besitzer der Datenbank, die mit dieser Datenbank herstellen kann. Datenbankbesitzer können weitere Benutzer zu erstellen.

Sie können später andere Anmeldungen um eine weitere Anmeldungen zu erstellen, durch die Erteilung Autorisieren der `ALTER ANY LOGIN` Berechtigung. Innerhalb einer Datenbank, Sie können andere Benutzer autorisieren, um weitere Benutzer zu erstellen, durch die Erteilung der `ALTER ANY USER` Berechtigung. Zum Beispiel:   

```
GRANT ALTER ANY LOGIN TO Larry;   
GO   
   
USE AdventureWorks2014;   
GO   
GRANT ALTER ANY USER TO Jerry;    
GO   
```

Der Anmeldename Larry kann nun weitere Anmeldungen erstellen, und der Benutzer Jerry können weitere Benutzer erstellen.


## <a name="granting-access-with-least-privileges"></a>Gewähren des Zugriffs mit geringstmöglichen Berechtigungen

Die erste Personen für die Verbindung mit einer Benutzerdatenbank werden den Administrator und Besitzer von Datenbankkonten. Diese Benutzer haben jedoch die verfügbaren Berechtigungen für die Datenbank an. Dies ist mehr Berechtigungen als die meisten Benutzer haben sollen. 

Wenn Sie gerade die Schritte ersten, können Sie einige allgemeinen Kategorien von Berechtigungen zuweisen, indem Sie mithilfe der integrierten *festen Datenbankrollen*. Z. B. die `db_datareader` festen Datenbankrolle kann alle Tabellen in der Datenbank lesen, aber keine Änderungen vornehmen. Mitgliedschaft in einer festen Datenbankrolle zu gewähren, indem Sie mit der [ALTER ROLE](../t-sql/statements/alter-role-transact-sql.md) Anweisung. Im folgende Beispiel fügen Sie den Benutzer `Jerry` auf die `db_datareader` festen Datenbankrolle.   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

Eine Liste der festen Datenbankrollen, finden Sie unter [Datenbankrollen](../relational-databases/security/authentication-access/database-level-roles.md).

Später, wenn Sie eine genauere Zugriff auf Ihre Daten (empfohlen) konfigurieren möchten, erstellen eigene benutzerdefinierte Datenbankrollen mithilfe [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md) Anweisung. Weisen Sie klicken Sie dann bestimmte genau abgestufte Berechtigungen benutzerdefinierte Rollen zu.

Z. B. die folgenden Anweisungen erstellen eine Datenbankrolle mit dem Namen `Sales`, gewährt die `Sales` gruppieren Sie die Möglichkeit, finden Sie unter, aktualisieren und Löschen von Zeilen aus der `Orders` Tabelle und fügt dann den Benutzer `Jerry` auf die `Sales` Rolle.   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```   

For more information about the permission system, see [Getting Started with Database Engine Permissions](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).


## Configure row-level security  

[Row-Level Security](../relational-databases/security/row-level-security.md) enables you to restrict access to rows in a database based on the user executing a query. This feature is useful for scenarios like ensuring that customers can only access their own data or that workers can only access data that is pertinent to their department.   

The following steps walk through setting up two Users with different row-level access to the `Sales.SalesOrderHeader` table. 

Create two user accounts to test the row level security:    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```   

Grant read access on the `Sales.SalesOrderHeader` table to both users:    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;    
```   
   
Create a new schema and inline table-valued function. The function returns 1 when a row in the `SalesPersonID` column matches the ID of a `SalesPerson` login or if the user executing the query is the Manager user.   
   
```     
CREATE SCHEMA Security;   
GO   
   
CREATE FUNCTION Security.fn_securitypredicate(@SalesPersonID AS int)     
    RETURNS TABLE   
WITH SCHEMABINDING   
AS     
   RETURN SELECT 1 AS fn_securitypredicate_result    
WHERE ('SalesPerson' + CAST(@SalesPersonId as VARCHAR(16)) = USER_NAME())     
    OR (USER_NAME() = 'Manager');    
```   

Create a security policy adding the function as both a filter and a block predicate on the table:  

```
SECURITY-Richtlinie SalesFilter erstellen   
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader,   
BLOCK-Prädikat Security.fn_securitypredicate(SalesPersonID) hinzufügen    
  ON Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

Execute the following to query the `SalesOrderHeader` table as each user. Verify that `SalesPerson280` only sees the 95 rows from their own sales and that the `Manager` can see all the rows in the table.  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
ZURÜCKGESETZT. 
 
EXECUTE AS USER = "Manager";   
SELECT * FROM Sales.SalesOrderHeader;   
ZURÜCKGESETZT.   
```
 
Alter the security policy to disable the policy.  Now both users can access all rows. 

```
ALTER SECURITY POLICY SalesFilter   
MIT (STATE = OFF);    
``` 


## Enable dynamic data masking

[Dynamic Data Masking](../relational-databases/security/dynamic-data-masking.md) enables you to limit the exposure of sensitive data to users of an application by fully or partially masking certain columns. 

Use an `ALTER TABLE` statement to add a masking function to the `EmailAddress` column in the `Person.EmailAddress` table: 
 
```
Verwenden Sie die AdventureWorks2014; Wechseln Sie ALTER TABLE Person.EmailAddress     ALTER Spalte e-Mail-Adresse    
MASKIERTE hinzufügen mit (Funktion = ' email()');
``` 
 
Create a new user `TestUser` with `SELECT` permission on the table, then execute a query as `TestUser` to view the masked data:   

```  
Erstellen Sie Testbenutzer für Benutzer ohne Anmeldung   
GRANT SELECT ON Person.EmailAddress zu TestUser;    
 
EXECUTE AS USER = 'TestUser';   
SELECT EmailAddressID, EmailAddress FROM Person.EmailAddress;       
ZURÜCKGESETZT.    
```
 
Verify that the masking function changes the email address in the first record from:
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## Enable Transparent Data Encryption

One threat to your database is the risk that someone will steal the database files off of your hard-drive. This could happen with an intrusion that gets elevated access to your system, through the actions of a problem employee, or by theft of the computer containing the files (such as a laptop).

Transparent Data Encryption (TDE) encrypts the data files as they are stored on the hard drive. The master database of the SQL Server database engine has the encryption key, so that the database engine can manipulate the data. The database files cannot be read without access to the key. High-level administrators can manage, backup, and recreate the key, so the database can be moved, but only by selected people. When TDE is configured, the `tempdb` database is also automatically encrypted. 

Since the Database Engine can read the data, Transparent Data Encryption does not protect against unauthorized access by administrators of the computer who can directly read memory, or access SQL Server through an administrator account.

### Configure TDE

- Create a master key
- Create or obtain a certificate protected by the master key
- Create a database encryption key and protect it by the certificate
- Set the database to use encryption

Configuring TDE requires `CONTROL` permission on the master database and `CONTROL` permission on the user database. Typically an administrator configures TDE. 

The following example illustrates encrypting and decrypting the `AdventureWorks2014` database using a certificate installed on the server named `MyServerCert`.


```
USE master;  
GO  

ERSTELLEN VON HAUPTSCHLÜSSEL-VERSCHLÜSSELUNG DURCH DAS KENNWORT = ' ***';  
GO  

Erstellen des Zertifikats MyServerCert mit Betreff = 'Meine Datenbankzertifikat für Datenverschlüsselungsschlüssel';  
GO  

USE AdventureWorks2014;   GO
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
Verschlüsselung von SERVER-Zertifikat MyServerCert  
GO
  
ALTER DATABASE AdventureWorks2014  
SET-VERSCHLÜSSELUNG AUF;   
```

To remove TDE, execute `ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

The encryption and decryption operations are scheduled on background threads by SQL Server. You can view the status of these operations using the catalog views and dynamic management views in the list that appears later in this topic.   

> [!WARNING]
>  Backup files of databases that have TDE enabled are also encrypted by using the database encryption key. As a result, when you restore these backups, the certificate protecting the database encryption key must be available. This means that in addition to backing up the database, you have to make sure that you maintain backups of the server certificates to prevent data loss. Data loss will result if the certificate is no longer available. For more information, see [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  

For more information about TDE, see [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md).   


## Configure backup encryption
SQL Server has the ability to encrypt the data while creating a backup. By specifying the encryption algorithm and the encryptor (a certificate or asymmetric key) when creating a backup, you can create an encrypted backup file.    
  
> [!WARNING]  
>  It is very important to back up the certificate or asymmetric key, and preferably to a different location than the backup file it was used to encrypt. Without the certificate or asymmetric key, you cannot restore the backup, rendering the backup file unusable. 
 
 
The following example creates a certificate, and then creates a backup protected by the certificate.
```
Verwenden Sie Master;   Wechseln   erstellen Zertifikat BackupEncryptCert   mit Betreff = 'Datenbanksicherungen';   Wechseln SICHERUNGSDATENBANK [AdventureWorks2014]   auf den Datenträger N'/var/opt/mssql/backups/AdventureWorks2014.bak ='  
mit  
  KOMPRIMIERUNG  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVERZERTIFIKAT BackupEncryptCert =  
   ),  
  STATS = 10  
GO  
```

For more information, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).


## Next steps

For more information about the security features of SQL Server, see [Security Center for SQL Server Database Engine and Azure SQL Database](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).
