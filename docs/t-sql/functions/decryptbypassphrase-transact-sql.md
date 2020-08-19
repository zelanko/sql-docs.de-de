---
description: DECRYPTBYPASSPHRASE (Transact-SQL)
title: DECRYPTBYPASSPHRASE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DECRYPTBYPASSPHRASE
- DECRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- decryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], DECRYPTBYPASSPHRASE function
- DECRYPTBYPASSPHRASE function
ms.assetid: ca34b5cd-07b3-4dca-b66a-ed8c6a826c95
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b183d118a9b09bd4bb35f122ae1c1986148fe9df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417396"
---
# <a name="decryptbypassphrase-transact-sql"></a>DECRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Diese Funktion entschlüsselt Daten, die ursprünglich mit einer Passphrase verschlüsselt wurden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
DecryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *passphrase*  
Die Passphrase, die zum Generieren des Entschlüsselungsschlüssels verwendet wird.  
  
 @passphrase  
Eine Variable vom Typ **char**, **nchar**, **nvarchar** oder **varchar**, die die Passphrase enthält, die zum Generieren des Entschlüsselungsschlüssels verwendet wird.  
  
'*ciphertext*'  
Die Zeichenfolge der Daten, die mit dem Schlüssel verschlüsselt wurden. *ciphertext* verfügt über einen **varbinary**-Datentyp.  
 
@ciphertext  
Eine Variable vom Typ **varbinary**, die Daten enthält, die mit dem Schlüssel verschlüsselt wurden. Die *\@ciphertext*-Variable verfügt über eine maximale Größe von 8.000 Bytes.  
  
*add_authenticator*  
Gibt an, ob durch den ursprünglichen Verschlüsselungsprozess ein Authentifikator zusammen mit dem Klartext einbezogen und verschlüsselt wurde. *add_authenticator* weist den Wert 1 auf, wenn im Verschlüsselungsprozess ein Authentifikator verwendet wurde. *add_authenticator* verfügt über einen **int**-Datentyp.  
  
@add_authenticator  
Eine Variable, die angibt, ob durch den ursprünglichen Verschlüsselungsprozess ein Authentifikator zusammen mit dem Klartext einbezogen, und verschlüsselt, wurde. *\@add_authenticator* weist den Wert 1 auf, wenn im Verschlüsselungsprozess ein Authentifikator verwendet wurde. *\@add_authenticator* weist den Datentyp **int** auf.  

*authenticator*  
Die Daten, die als Grundlage für die Generierung des Authentifikators verwendet werden. *authenticator* verfügt über einen **sysname**-Datentyp.  
  
@authenticator  
Eine Variable, die Daten enthält, die als Grundlage für die Generierung der Authentifikatoren verwendet wurden. *\@authenticator* weist den Datentyp **sysname** auf.  
  
## <a name="return-types"></a>Rückgabetypen  
**varbinary** mit einer maximalen Größe von 8.000 Byte.  
  
## <a name="remarks"></a>Bemerkungen  
`DECRYPTBYPASSPHRASE` erfordert keine Berechtigungen für die Ausführung. `DECRYPTBYPASSPHRASE` gibt NULL zurück, wenn die falsche Passphrase oder falsche Authentifikatorinformationen übergeben werden.  
  
`DECRYPTBYPASSPHRASE` verwendet die Passphrase zum Generieren eines Entschlüsselungsschlüssels. Der Entschlüsselungsschlüssel bleibt nicht erhalten.  
  
Wenn zum Zeitpunkt der Verschlüsselung des Chiffretexts ein Authentifikator enthalten war, muss `DECRYPTBYPASSPHRASE` denselben Authentifikator für den Entschlüsselungsprozess erhalten. Wenn der für den Entschlüsselungsprozess angegebene Authentifikatorwert nicht mit dem Authentifikatorwert übereinstimmt, der ursprünglich zum Verschlüsseln der Daten verwendet wurde, schlägt der `DECRYPTBYPASSPHRASE`-Vorgang fehl.  
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird der unter [EncryptByPassPhrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md) aktualisierte Datensatz entschlüsselt.  
  
```  
USE AdventureWorks2012;  
-- Get the passphrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
= 'A little learning is a dangerous thing!';  
  
-- Decrypt the encrypted record.  
SELECT CardNumber, CardNumber_EncryptedbyPassphrase   
    AS 'Encrypted card number', CONVERT(varchar,  
    DecryptByPassphrase(@PassphraseEnteredByUser, CardNumber_EncryptedbyPassphrase, 1   
    , CONVERT(varbinary, CreditCardID)))  
    AS 'Decrypted card number' FROM Sales.CreditCard   
    WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswählen eines Verschlüsselungsalgorithmus](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
  
  
