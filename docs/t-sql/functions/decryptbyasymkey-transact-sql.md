---
title: DECRYPTBYASYMKEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DECRYPTBYASYMKEY
- DECRYPTBYASYMKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], DECRYPTBYASYMKEY function
- DECRYPTBYASYMKEY function
- decryption [SQL Server], asymmetric keys
ms.assetid: d9ebcd30-f01c-4cfe-b95e-ffe6ea13788b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3a46b3f19bc676b0b8e9f86db684328940b6e520
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65945560"
---
# <a name="decryptbyasymkey-transact-sql"></a>DECRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion verwendet einen asymmetrischen Schlüssel zum Entschlüsseln verschlüsselter Daten.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DecryptByAsymKey (Asym_Key_ID , { 'ciphertext' | @ciphertext }   
    [ , 'Asym_Key_Password' ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Asym_Key_ID*  
Die ID eines asymmetrischen Schlüssels in der Datenbank. *Asym_Key_ID* weist den Datentyp **int** auf.  
  
 *ciphertext*  
Die Zeichenfolge der Daten, die mit dem asymmetrischen Schlüssel verschlüsselt wurden.  
  
 @ciphertext  
Eine Variable vom Typ **varbinary**, die Daten enthält, die mit dem asymmetrischen Schlüssel verschlüsselt wurden.  
  
 *Asym_Key_Password*  
Das Kennwort, mit dem der asymmetrische Schlüssel in der Datenbank verschlüsselt wurde.  
  
## <a name="return-types"></a>Rückgabetypen  
**varbinary** mit einer maximalen Größe von 8.000 Byte.  
  
## <a name="remarks"></a>Remarks  
Im Vergleich zur symmetrischen Verschlüsselung/Entschlüsselung ist die Verschlüsselung/Entschlüsselung mit asymmetrischen Schlüsseln kostspielig. Wenn Sie mit großen Datasets arbeiten (z.B. in Tabellen gespeicherte Benutzerdaten), wird empfohlen, dass Entwickler die Verschlüsselung/Entschlüsselung mit asymmetrischen Schlüsseln vermeiden.  
  
## <a name="permissions"></a>Berechtigungen  
`DECRYPTBYASYMKEY` erfordert die CONTROL-Berechtigung für den asymmetrischen Schlüssel.  
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel wird Chiffretext entschlüsselt, der ursprünglich mit dem asymmetrischen Schlüssel `JanainaAsymKey02` verschlüsselt wurde. Dieser asymmetrische Schlüssel ist in `AdventureWorks2012.ProtectedData04` gespeichert. Im Beispiel wurden die zurückgegebenen Daten mit dem asymmetrischen Schlüssel `JanainaAsymKey02` entschlüsselt. Im Beispiel wurde das Kennwort `pGFD4bb925DGvbd2439587y` verwendet, um diesen asymmetrischen Schlüssel zu entschlüsseln. Im Beispiel wurde der zurückgegebenen Klartext in den Typ **nvarchar** konvertiert.  
  
```  
SELECT CONVERT(nvarchar(max),  
    DecryptByAsymKey( AsymKey_Id('JanainaAsymKey02'),   
    ProtectedData, N'pGFD4bb925DGvbd2439587y' ))   
AS DecryptedData   
FROM [AdventureWorks2012].[Sales].[ProtectedData04]   
WHERE Description = N'encrypted by asym key''JanainaAsymKey02''';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [Auswählen eines Verschlüsselungsalgorithmus](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
