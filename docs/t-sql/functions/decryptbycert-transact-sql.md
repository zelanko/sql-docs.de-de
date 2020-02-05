---
title: DECRYPTBYCERT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DecryptByCert_TSQL
- DECRYPTBYCERT
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], decryption
- decryption [SQL Server], certificates
- DECRYPTBYCERT function
ms.assetid: 4950d787-40fa-4e26-bce8-2cb2ceca12fb
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9653e799a543dd95a7d6fb033e0a8d5b9a4484a8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71314532"
---
# <a name="decryptbycert-transact-sql"></a>DECRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion verwendet den privaten Schlüssel eines Zertifikats zum Entschlüsseln verschlüsselter Daten.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DecryptByCert ( certificate_ID , { 'ciphertext' | @ciphertext }   
    [ , { 'cert_password' | @cert_password } ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *certificate_ID*  
Die ID eines Zertifikats in der Datenbank. *certificate_ID* weist den Datentyp **int** auf.  
  
 *ciphertext*  
Die Datenzeichenfolge, die mithilfe des öffentlichen Schlüssels des Zertifikats verschlüsselt wurde.  
  
 @ciphertext  
Eine Variable vom Typ **varbinary**, die Daten enthält, die mit dem Zertifikat verschlüsselt wurden.  
  
 *cert_password*  
Das Kennwort, das zum Verschlüsseln des privaten Schlüssels des Zertifikats verwendet wurde. *cert_password* muss das Unicode-Datenformat aufweisen.  
  
 @cert_password  
Eine Variable vom Typ **nchar** oder **nvarchar**, die das Kennwort enthält, mit dem der private Schlüssel des Zertifikats verschlüsselt wurde. *\@cert_password* muss das Unicode-Datenformat aufweisen.  

## <a name="return-types"></a>Rückgabetypen  
**varbinary** mit einer maximalen Größe von 8.000 Byte.  
  
## <a name="remarks"></a>Bemerkungen  
Diese Funktion entschlüsselt Daten mithilfe des privaten Schlüssels eines Zertifikats. Kryptografische Umwandlungen, die asymmetrische Schlüssel verwenden, nehmen umfangreiche Ressourcen in Anspruch. Deshalb wird empfohlen, dass Entwickler die Verwendung von [ENCRYPTBYCERT](./encryptbycert-transact-sql.md) und DECRYPTBYCERT bei der routinemäßigen Verschlüsselung und Entschlüsselung von Benutzerdaten vermeiden.  

## <a name="permissions"></a>Berechtigungen  
`DECRYPTBYCERT` erfordert die CONTROL-Berechtigung für das Zertifikat.  
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel werden Zeilen aus `[AdventureWorks2012].[ProtectedData04]` ausgewählt, die als Daten markiert sind, die ursprünglich mit dem Zertifikat `JanainaCert02` verschlüsselt wurden. Im Beispiel wird zunächst der private Schlüssel des Zertifikats `JanainaCert02` mit dem Kennwort des Zertifikats `pGFD4bb925DGvbd2439587y` entschlüsselt. Dann wird der Chiffretext mit diesem privaten Schlüssel entschlüsselt. Die entschlüsselten Daten werden im Beispiel von **varbinary** in **nvarchar** konvertiert.  

```  
SELECT convert(nvarchar(max), DecryptByCert(Cert_Id('JanainaCert02'),  
    ProtectedData, N'pGFD4bb925DGvbd2439587y'))  
FROM [AdventureWorks2012].[ProtectedData04]   
WHERE Description   
    = N'data encrypted by certificate '' JanainaCert02''';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ENCRYPTBYCERT &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
