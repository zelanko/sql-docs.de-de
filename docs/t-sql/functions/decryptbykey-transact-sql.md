---
title: DECRYPTBYKEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7f9e1e678fba7a2b2d24a85f4d57f1112b3d4cb8
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779476"
---
# <a name="decryptbykey-transact-sql"></a>DECRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion verwendet einen symmetrischen Schlüssel zum Entschlüsseln von Daten.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
  
## <a name="remarks"></a>Remarks  
`DECRYPTBYKEY` verwendet einen symmetrischen Schlüssel. Dieser symmetrische Schlüssel muss in der Datenbank bereits geöffnet sein. `DECRYPTBYKEY` lässt zu, dass mehrere Schlüssel gleichzeitig geöffnet sind. Der Schlüssel muss nicht unmittelbar vor dem Entschlüsseln von verschlüsseltem Text geöffnet werden.  
  
Die symmetrische Ver- und Entschlüsselung erfolgt in der Regel relativ schnell und eignet sich gut für Vorgänge, die große Datenmengen umfassen.  
  
## <a name="permissions"></a>Berechtigungen  
Dieser symmetrische Schlüssel muss in der aktuellen Sitzung bereits geöffnet sein. Weitere Informationen finden Sie unter [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-decrypting-by-using-a-symmetric-key"></a>A. Entschlüsseln mit einem symmetrischen Schlüssel  
In diesem Beispiel wird verschlüsselter Text mit einem symmetrischen Schlüssel entschlüsselt.  
  
```  
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
  
```  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Auswählen eines Verschlüsselungsalgorithmus](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  
