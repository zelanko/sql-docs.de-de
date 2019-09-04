---
title: DECRYPTBYKEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DecryptByKey_TSQL
- DECRYPTBYKEY
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], DecryptByKey function
- decryption [SQL Server], keys
- decryption [SQL Server], symmetric keys
- DECRYPTBYKEY function
ms.assetid: 6edf121f-ac62-4dae-90e6-6938f32603c9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 76bb0b64f0a3405a20b9b05c8cb1e18d6ab242a3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118938"
---
# <a name="decryptbykey-transact-sql"></a>DECRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion verwendet einen symmetrischen Schlüssel zum Entschlüsseln von Daten.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql
  
DecryptByKey ( { 'ciphertext' | @ciphertext }   
    [ , add_authenticator, { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Argumente  
*ciphertext*  
Eine Variable vom Typ **varbinary**, die Daten enthält, die mit dem Schlüssel verschlüsselt wurden.  
  
**@ciphertext**  
Eine Variable vom Typ **varbinary**, die Daten enthält, die mit dem Schlüssel verschlüsselt wurden.  
  
 *add_authenticator*  
Gibt an, ob durch den ursprünglichen Verschlüsselungsprozess ein Authentifikator zusammen mit dem Klartext einbezogen und verschlüsselt wurde. Muss mit dem Wert übereinstimmen, der während der Datenverschlüsselung an [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) übergeben wurde. *add_authenticator* verfügt über einen **int**-Datentyp.  
  
 *authenticator*  
Die Daten, die als Grundlage für die Generierung des Authentifikators verwendet werden. Diese müssen mit dem Wert übereinstimmen, der für [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) bereitgestellt wurde. *authenticator* verfügt über einen **sysname**-Datentyp.  

**@authenticator**  
Eine Variable, die Daten für die Generierung durch den Authentifikator enthält. Diese müssen mit dem Wert übereinstimmen, der für [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) bereitgestellt wurde. *@authenticator* verfügt über einen **sysname**-Datentyp.  

## <a name="return-types"></a>Rückgabetypen  
**varbinary** mit einer maximalen Größe von 8.000 Byte. `DECRYPTBYKEY` gibt NULL zurück, wenn der für die Datenverschlüsselung verwendete symmetrische Schlüssel nicht geöffnet ist oder wenn *ciphertext* den Wert NULL aufweist.  
  
## <a name="remarks"></a>Bemerkungen  
`DECRYPTBYKEY` verwendet einen symmetrischen Schlüssel. Dieser symmetrische Schlüssel muss in der Datenbank bereits geöffnet sein. `DECRYPTBYKEY` lässt zu, dass mehrere Schlüssel gleichzeitig geöffnet sind. Der Schlüssel muss nicht unmittelbar vor dem Entschlüsseln von verschlüsseltem Text geöffnet werden.  
  
Die symmetrische Ver- und Entschlüsselung erfolgt in der Regel relativ schnell und eignet sich gut für Vorgänge, die große Datenmengen umfassen.  

Der `DECRYPTBYKEY`-Aufruf muss im Kontext der Datenbank mit dem Verschlüsselungsschlüssel erfolgen. Stellen Sie dies sicher, indem Sie `DECRYPTBYKEY` aus einem Objekt (z.B. einer Sicht, einer gespeicherten Prozedur oder einer Funktion) aufrufen, das sich in der Datenbank befindet. 
  
## <a name="permissions"></a>Berechtigungen  
Dieser symmetrische Schlüssel muss in der aktuellen Sitzung bereits geöffnet sein. Weitere Informationen finden Sie unter [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-decrypting-by-using-a-symmetric-key"></a>A. Entschlüsseln mit einem symmetrischen Schlüssel  
In diesem Beispiel wird verschlüsselter Text mit einem symmetrischen Schlüssel entschlüsselt.  
  
```sql  
-- First, open the symmetric key with which to decrypt the data.  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
GO  
  
-- Now list the original ID, the encrypted ID, and the   
-- decrypted ciphertext. If the decryption worked, the original  
-- and the decrypted ID will match.  
SELECT NationalIDNumber, EncryptedNationalID   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalID))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-decrypting-by-using-a-symmetric-key-and-an-authenticating-hash"></a>B. Entschlüsseln mit einem symmetrischen Schlüssel und einem Authentifizierungshash  
In diesem Beispiel werden Daten entschlüsselt, die ursprünglich zusammen mit einem Authentifikator verschlüsselt wurden.  
  
```sql  
-- First, open the symmetric key with which to decrypt the data  
OPEN SYMMETRIC KEY CreditCards_Key11  
   DECRYPTION BY CERTIFICATE Sales09;  
GO  
  
-- Now list the original card number, the encrypted card number,  
-- and the decrypted ciphertext. If the decryption worked,   
-- the original number will match the decrypted number.  
SELECT CardNumber, CardNumber_Encrypted   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByKey(CardNumber_Encrypted, 1 ,   
    HashBytes('SHA1', CONVERT(varbinary, CreditCardID))))   
    AS 'Decrypted card number' FROM Sales.CreditCard;  
GO  
  
```  

### <a name="c-fail-to-decrypt-when-not-in-the-context-of-database-with-key"></a>C. Fehler beim Entschlüsseln, wenn nicht im Kontext der Datenbank mit dem Schlüssel
Das folgende Beispiel zeigt, dass `DECRYPTBYKEY` im Kontext der Datenbank mit dem Schlüssel ausgeführt werden muss. Die Zeile wird nicht entschlüsselt, wenn `DECRYPTBYKEY` in der Master-Datenbank ausgeführt wird. Das Ergebnis ist NULL. 

```sql
-- Create the database
CREATE DATABASE TestingDecryptByKey
GO

USE [TestingDecryptByKey]

-- Create the table and view
CREATE TABLE TestingDecryptByKey.dbo.Test(val VARBINARY(8000) NOT NULL);
GO
CREATE VIEW dbo.TestView AS SELECT CAST(DecryptByKey(val) AS VARCHAR(30)) AS DecryptedVal FROM TestingDecryptByKey.dbo.Test;
GO

-- Create the key, and certificate
USE TestingDecryptByKey;
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'ItIsreallyLong1AndSecured!Passsword#';
CREATE CERTIFICATE TestEncryptionCertificate WITH SUBJECT = 'TestEncryption';
CREATE SYMMETRIC KEY TestEncryptSymmmetricKey WITH ALGORITHM = AES_256, IDENTITY_VALUE = 'It is place for test',
KEY_SOURCE = 'It is source for test' ENCRYPTION BY CERTIFICATE TestEncryptionCertificate;

-- Insert rows into the table
DECLARE @var VARBINARY(8000), @Val VARCHAR(30);
SELECT @Val = '000-123-4567';
OPEN SYMMETRIC KEY TestEncryptSymmmetricKey DECRYPTION BY CERTIFICATE TestEncryptionCertificate;
SELECT @var = EncryptByKey(Key_GUID('TestEncryptSymmmetricKey'), @Val);
SELECT CAST(DecryptByKey(@var) AS VARCHAR(30)), @Val;
INSERT INTO dbo.Test VALUES(@var);
GO

-- Switch to master
USE [Master];
GO

-- Results show the date inserted
SELECT DecryptedVal FROM TestingDecryptByKey.dbo.TestView;

-- Results are NULL because we are not in the context of the TestingDecryptByKey Database
SELECT CAST(DecryptByKey(val) AS VARCHAR(30)) AS DecryptedVal FROM TestingDecryptByKey.dbo.Test;
GO

-- Clean up resources
USE TestingDecryptByKey;

DROP SYMMETRIC KEY TestEncryptSymmmetricKey REMOVE PROVIDER KEY;
DROP CERTIFICATE TestEncryptionCertificate;

Use [Master]
DROP DATABASE TestingDecryptByKey;
GO
```

  
## <a name="see-also"></a>Weitere Informationen  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Auswählen eines Verschlüsselungsalgorithmus](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  
