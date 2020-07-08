---
title: ENCRYPTBYCERT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYCERT
- ENCRYPTBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], encryption
- encryption [SQL Server], certificates
- ENCRYPTBYCERT function
ms.assetid: ab66441f-e2d2-4e3a-bcae-bcc09e12f3c1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b2a25f62b563a01aa9cafb522d9ea32ab0f32fc9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85682033"
---
# <a name="encryptbycert-transact-sql"></a>ENCRYPTBYCERT (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Verschlüsselt Daten mit dem öffentlichen Schlüssel eines Zertifikats.  
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
EncryptByCert ( certificate_ID , { 'cleartext' | @cleartext } )  
```  
  
## <a name="arguments"></a>Argumente  
_certificate\_ID_  
Die ID eines Zertifikats in der Datenbank. **int**.  
  
_Klartext_  
Eine Zeichenfolge mit Daten, die mit dem Zertifikat verschlüsselt werden.  
  
**\@cleartext**  
Eine Variable eines der folgenden Typen, die Daten enthalten, die mit dem öffentlichen Schlüssel des Zertifikats verschlüsselt werden:

* **nvarchar** 
* **char**
* **varchar**
* **binary** 
* **varbinary**
* **nchar**
  
## <a name="return-types"></a>Rückgabetypen  
**varbinary** mit einer maximalen Größe von 8.000 Bytes.  
  
## <a name="remarks"></a>Bemerkungen  
Diese Funktion verschlüsselt Daten mit dem öffentlichen Schlüssel des Zertifikats. Der verschlüsselte Text kann nur mit dem entsprechenden privaten Schlüssel entschlüsselt werden. Diese asymmetrischen Transformationen sind im Vergleich zum Verschlüsseln und Entschlüsseln mit einem symmetrischen Schlüssel kostenintensiv. Von der asymmetrischen Verschlüsselung wird daher abgeraten, wenn Sie große Datasets verwenden.
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel wird der in `@cleartext` gespeicherte Nur-Text mit dem Zertifikat mit dem Namen `JanainaCert02` verschlüsselt. Die verschlüsselten Daten werden in die `ProtectedData04`-Tabelle eingefügt.  
  
```  
INSERT INTO [AdventureWorks2012].[ProtectedData04]   
    VALUES ( N'Data encrypted by certificate ''Shipping04''',  
    EncryptByCert(Cert_ID('JanainaCert02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[DECRYPTBYCERT &#40;Transact-SQL&#41;](../../t-sql/functions/decryptbycert-transact-sql.md)   
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
[ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
[DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
[BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
[Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
