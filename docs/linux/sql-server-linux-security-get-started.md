---
title: Erste Schritte mit SQL Server-Sicherheit unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die typischen Sicherheitsaktionen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.custom: sql-linux
ms.openlocfilehash: 6df990176c63efb6c42181d013a4e77c81f3c4b2
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083432"
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Exemplarische Vorgehensweise für die Sicherheitsfunktionen von SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Wenn Sie einen Linux-Benutzer, der in SQL Server neu ist sind, durchlaufen die folgenden Aufgaben Sie einige der Sicherheitsaufgaben. Diese sind nicht eindeutig oder speziell für Linux, aber es hilft, erhalten Sie eine Vorstellung von Bereichen, um weiter zu untersuchen. In jedem Beispiel wird ein Link in der ausführlichen Dokumentation für den entsprechenden Bereich bereitgestellt.

>  [!NOTE]
>  Die folgenden Beispiele verwenden die **AdventureWorks2014** -Beispieldatenbank. Anweisungen zum Abrufen und Installieren dieser Beispieldatenbank finden Sie [wiederherstellen eine SQL Server-Datenbank von Windows bis Linux](sql-server-linux-migrate-restore-database.md).


## <a name="create-a-login-and-a-database-user"></a>Erstellen Sie einen Anmeldenamen und Datenbankbenutzer 

Erteilen Sie anderen Zugriff auf SQL Server durch Erstellen eines Anmeldenamens in der master-Datenbank mithilfe der [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) Anweisung. Zum Beispiel:

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

>  [!NOTE]
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

Die erste Personen für die Verbindung mit einer Benutzerdatenbank werden den Administrator und Besitzer von Datenbankkonten. Jedoch diese Benutzer verfügen alle über die die Berechtigungen für die Datenbank verfügbar sind. Dies ist mehr Berechtigungen als die meisten Benutzer haben sollen. 

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

Weitere Informationen zu das Berechtigungssystem, finden Sie unter [erste Schritte mit Berechtigungen für die Datenbank-Engine](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).


## <a name="configure-row-level-security"></a>Konfigurieren der Sicherheit auf Zeilenebene  

[Sicherheit auf Zeilenebene](../relational-databases/security/row-level-security.md) ermöglicht es Ihnen, den Zugriff auf Zeilen in einer Datenbank, die basierend auf dem Benutzer, die Ausführung einer Abfrage einzuschränken. Dieses Feature ist nützlich für Szenarien, z. B. das sicherstellen, dass es sich bei Kunden nur ihre eigenen Daten zugreifen können oder dass Mitarbeiter nur auf Daten zugreifen können, die für ihre Abteilung relevant ist.   

Die folgenden Schritte führen, durch die Einrichtung von zwei Benutzer mit unterschiedlichen auf Zeilenebene Zugriff auf die `Sales.SalesOrderHeader` Tabelle. 

Erstellen Sie zwei Benutzerkonten, um die Sicherheit auf Zeilenebene zu testen:    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```   

Gewähren von Lesezugriff auf die `Sales.SalesOrderHeader` Tabelle, um beide Benutzer:    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;    
```   
   
Erstellen Sie eine neue Schema- und Inline-Tabellenwertfunktion. Die Funktion gibt 1, wenn eine Zeile in der `SalesPersonID` Spalte entspricht der ID eines eine `SalesPerson` Anmeldung oder wenn der Benutzer, die Ausführung der Abfrage der Manager-Benutzer ist.   
   
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

Erstellen Sie eine Sicherheitsrichtlinie für das Hinzufügen der Funktion als ein Filter und ein Block-Prädikat für die Tabelle ein:  

```
CREATE SECURITY POLICY SalesFilter   
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader,   
ADD BLOCK PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

Führen Sie die folgende Abfrage die `SalesOrderHeader` Tabelle wie jedes Benutzers. Überprüfen Sie, ob `SalesPerson280` nur ihre eigenen Verkäufe und die 95 Zeilen angezeigt werden. die `Manager` sehen, dass alle Zeilen in der Tabelle.  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
REVERT; 
 
EXECUTE AS USER = 'Manager';   
SELECT * FROM Sales.SalesOrderHeader;   
REVERT;   
```
 
Ändern Sie die Sicherheitsrichtlinie, um die Richtlinie zu deaktivieren.  Jetzt können sowohl Benutzer alle Zeilen zugreifen. 

```
ALTER SECURITY POLICY SalesFilter   
WITH (STATE = OFF);    
``` 


## <a name="enable-dynamic-data-masking"></a>Aktivieren Sie die dynamische datenmaskierung

[Die dynamische Datenmaskierung](../relational-databases/security/dynamic-data-masking.md) ermöglicht es Ihnen, die Offenlegung von sensiblen Daten für Benutzer von einer Anwendung, die durch das vollständig oder teilweise maskieren bestimmte Spalten beschränken. 

Verwenden einer `ALTER TABLE` -Anweisung eine Maskierungsfunktion zum Hinzufügen der `EmailAddress` -Spalte in der `Person.EmailAddress` Tabelle: 
 
```
USE AdventureWorks2014;
GO
ALTER TABLE Person.EmailAddress    
ALTER COLUMN EmailAddress    
ADD MASKED WITH (FUNCTION = 'email()');
``` 
 
Erstellen eines neuen Benutzers `TestUser` mit `SELECT` -Berechtigung für die Tabelle, führen Sie dann eine Abfrage als `TestUser` zum Anzeigen der maskierten Daten:   

```  
CREATE USER TestUser WITHOUT LOGIN;   
GRANT SELECT ON Person.EmailAddress TO TestUser;    
 
EXECUTE AS USER = 'TestUser';   
SELECT EmailAddressID, EmailAddress FROM Person.EmailAddress;       
REVERT;    
```
 
Stellen Sie sicher, dass die Maskierungsfunktion ändert, die e-Mail-Adresse im ersten Datensatz aus:
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## <a name="enable-transparent-data-encryption"></a>Aktivieren der transparenten Datenverschlüsselung

Eine Bedrohung für Ihre Datenbank ist das Risiko, dass ein Benutzer die Datenbankdateien auf der Festplatte stehlen wird. Dies kann auf einen Eindringversuch passieren, die erhöhte Zugriffsrechte auf Ihrem System durch die Aktionen eines Mitarbeiters Problem oder Diebstahl des Computers mit den Dateien (z. B. einem Laptop) abruft.

Transparent Data Encryption (TDE) verschlüsselt die Datendateien an, wie sie auf der Festplatte gespeichert werden. Die master-Datenbank der SQL Server-Datenbank-Engine hat den Verschlüsselungsschlüssel, damit die Datenbank-Engine die Daten bearbeiten kann. Die Datenbankdateien können nicht ohne Zugriff auf den Schlüssel nicht gelesen werden. Auf hoher Ebene Administratoren können verwalten "," Sicherung und den Schlüssel neu erstellen, damit die Datenbank verschoben werden kann, aber nur von ausgewählten Personen. Wenn TDE dafür konfiguriert ist, die `tempdb` Datenbank werden auch automatisch verschlüsselt. 

Da die Datenbank-Engine die Daten lesen kann, schützt Transparent Data Encryption nicht vor nicht autorisiertem Zugriff, die Administratoren von dem Computer, die direkt Arbeitsspeicher gelesen werden können, oder Zugriff auf SQL Server über ein Administratorkonto.

### <a name="configure-tde"></a>Konfigurieren von TDE

- Erstellen Sie einen Hauptschlüssel
- Erstellen oder beziehen Sie ein vom Hauptschlüssel geschütztes Zertifikat
- Erstellen Sie einen Verschlüsselungsschlüssel für die Datenbank, und schützen Sie ihn durch das Zertifikat
- Legen Sie fest, dass für die Datenbank Verschlüsselung verwendet wird

Konfigurieren von TDE erfordert `CONTROL` -Berechtigung für die master-Datenbank und `CONTROL` -Berechtigung für die Benutzerdatenbank. Ein Administrator konfiguriert in der Regel TDE. 

Im folgenden Beispiel wird die Verschlüsselung und Entschlüsselung der `AdventureWorks2014` -Datenbank gezeigt, wobei ein auf dem Server `MyServerCert`installiertes Zertifikat verwendet wird.


```
USE master;  
GO  

CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**********';  
GO  

CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My Database Encryption Key Certificate';  
GO  

USE AdventureWorks2014;  
GO
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO
  
ALTER DATABASE AdventureWorks2014  
SET ENCRYPTION ON;   
```

Um TDE zu entfernen, führen `ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

Die Ver- und Entschlüsselung-Vorgänge werden von SQL Server in Hintergrundthreads geplant. Sie können den Status dieser Vorgänge mithilfe der in der Liste weiter unten in diesem Thema genannten Katalogsichten und dynamischen Verwaltungssichten anzeigen.   

>  [!WARNING]
>  Sicherungsdateien von Datenbanken, für die TDE aktiviert wurde, werden ebenfalls mithilfe des Verschlüsselungsschlüssels für die Datenbank verschlüsselt. Darum muss bei der Wiederherstellung dieser Sicherungen das Zertifikat, das zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet wurde, verfügbar sein. Dies bedeutet, dass Sie zusätzlich zur Sicherung der Datenbank auch Sicherungskopien der Serverzertifikate aufbewahren müssen, um einem Datenverlust vorzubeugen. Ist das Zertifikat nicht mehr verfügbar, kann es zu einem Datenverlust kommen. Weitere Informationen finden Sie unter [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  

Weitere Informationen zu TDE finden Sie unter [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md).   


## <a name="configure-backup-encryption"></a>Verschlüsseln von Sicherungen konfigurieren
SQL Server bietet die Möglichkeit, die Daten beim Erstellen einer Sicherung zu verschlüsseln. Durch Angeben des Verschlüsselungsalgorithmus und die Verschlüsselungsmethode (Zertifikat oder asymmetrischer Schlüssel) Wenn Sie eine Sicherung zu erstellen, können Sie eine verschlüsselte Sicherungsdatei erstellen.    
  
> [!WARNING]  
>  Es ist sehr wichtig, das Zertifikat oder den asymmetrischen Schlüssel zu sichern – vorzugsweise an einem anderen Speicherort als die Sicherungsdatei, die zum Verschlüsseln verwendet wurde. Ohne das Zertifikat oder den asymmetrischen Schlüssel können Sie keine Sicherung wiederherstellen, sodass die Sicherungsdatei unbrauchbar ist. 
 
 
Im folgende Beispiel wird ein Zertifikat erstellt, und klicken Sie dann eine Sicherung durch das Zertifikat geschützt.
```
USE master;  
GO  
CREATE CERTIFICATE BackupEncryptCert   
   WITH SUBJECT = 'Database backups';  
GO 
BACKUP DATABASE [AdventureWorks2014]  
TO DISK = N'/var/opt/mssql/backups/AdventureWorks2014.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
```

Weitere Informationen finden Sie unter [Sicherungsverschlüsselung](../relational-databases/backup-restore/backup-encryption.md).


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den Sicherheitsfunktionen von SQL Server finden Sie unter [Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).
