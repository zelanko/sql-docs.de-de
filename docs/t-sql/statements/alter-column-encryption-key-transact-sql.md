---
title: ALTER COLUMN ENCRYPTION KEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER COLUMN ENCRYPTION
- ALTER_COLUMN_ENCRYPTION_TSQL
- ALTER COLUMN ENCRYPTION KEY
- ALTER_COLUMN_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column encryption key, alter
- ALTER COLUMN ENCRYPTION KEY statement
ms.assetid: c79a220d-e178-4091-a330-c924cc0f0ae0
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: c06fb5b28e1c3ec5bd50b8922bcdf1e5d1b27ff7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "73594393"
---
# <a name="alter-column-encryption-key-transact-sql"></a>ALTER COLUMN ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Ändert durch das Hinzufügen oder Entfernen eines verschlüsselten Werts einen Spaltenverschlüsselungsschlüssel (Column encryption key, CEK) in einer Datenbank. Ein Spaltenverschlüsselungsschlüssel kann bis zu zwei Werte enthalten, was die Rotation des zugehörigen Spaltenhauptschlüssels ermöglicht. Ein Spaltenverschlüsselungsschlüssel wird beim Verschlüsseln von Spalten mit [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) oder [Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves.md) verwendet. Vor dem Hinzufügen eines Werts für den Spaltenverschlüsselungsschlüssel müssen Sie den Spaltenhauptschlüssel definieren, mit dem der Wert unter Verwendung von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder der [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md)-Anweisung verschlüsselt wurde.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
ALTER COLUMN ENCRYPTION KEY key_name   
    [ ADD | DROP ] VALUE   
    (  
        COLUMN_MASTER_KEY = column_master_key_name   
        [, ALGORITHM = 'algorithm_name' , ENCRYPTED_VALUE =  varbinary_literal ]   
    ) [;]  
```  
  
## <a name="arguments"></a>Argumente  
 *key_name*  
 Der Spaltenverschlüsselungsschlüssel, den Sie verändern möchten.  
  
 *column_master_key_name*  
 Gibt den Namen des benutzerdefinierten Spaltenhauptschlüssels (custom column master key, CMK) an, der zur Verschlüsselung des CEK verwendet wird.  
  
 *algorithm_name*  
 Der Name des Verschlüsselungsalgorithmus, der zum Verschlüsseln des Werts verwendet wird. Der Algorithmus für die Systemanbieter muss auf **RSA_OAEP** festgelegt sein Dieses Argument ist ungültig, wenn ein Spaltenverschlüsselungsschlüssel entfernt wird.  
  
 *varbinary_literal*  
 Der CEK-BLOB, der mit dem angegebenen Masterverschlüsselungsschlüssel verschlüsselt wird. Dieses Argument ist ungültig, wenn ein Spaltenverschlüsselungsschlüssel entfernt wird.  
  
> [!WARNING]  
>  Verwenden Sie diese Anweisung nie mit CEK-Werten im Klartext. Hierdurch wird die Wirksamkeit des Features beeinträchtigt.  
  
## <a name="remarks"></a>Bemerkungen  
In der Regel wird ein CEK nur mit einem verschlüsselten Wert erstellt. Wenn der aktuelle CMK rotiert, also mit dem neuen CMK ersetzt werden muss, können Sie einen neuen CEK-Wert hinzufügen, der mit dem neuen CMK verschlüsselt wird. Dieser Workflow stellt sicher, dass Clientanwendungen auf Daten zugreifen können, die mit dem Spaltenverschlüsselungsschlüssel verschlüsselt wurden, während der neue Spaltenhauptschlüssel den Clientanwendungen zur Verfügung gestellt wird. Ein Treiber, für den Always Encrypted aktiviert ist, kann in einer Clientanwendung, die keinen Zugriff auf den neuen Hauptschlüssel hat, zum Zugriff auf vertrauliche Daten den CEK-Wert verwenden, der mit dem alten CMK verschlüsselt wurde. Von Always Encrypted unterstützte Verschlüsselungsalgorithmen erfordern einen Klartextwert von 256 Bit. 
 
Es wird empfohlen, Tools wie SQL Server Management Studio (SSMS) oder PowerShell zu verwenden, um Spaltenhauptschlüssel zu rotieren. Weitere Informationen finden Sie unter [Rotieren von Always Encrypted-Schlüsseln mithilfe von SQL Server Management Studio](../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-ssms.md) und [Rotieren von Always Encrypted-Schlüsseln mithilfe von PowerShell](../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md).

Ein verschlüsselter Wert soll mit einem Schlüsselspeicheranbieter erstellt werden, der den Schlüsselspeicher mit dem CMK enthält.  

 Spaltenhauptschlüssel werden aus folgenden Gründen rotiert:
- Complianceanforderungen erfordern möglicherweise eine regelmäßige Rotation der Schlüssel.
- Ein Spaltenhauptschlüssel ist gefährdet und muss aus Sicherheitsgründen rotiert werden.
- Die Freigabe von Spaltenverschlüsselungsschlüsseln mit einer Secure Enclave auf der Serverseite soll aktiviert oder deaktiviert werden. Wenn Ihr aktueller Spaltenhauptschlüssel keine Enclave-Berechnungen unterstützt (also nicht mit der ENCLAVE_COMPUTATIONS-Eigenschaft definiert wurde) und Sie Enclave-Berechnungen in Spalten aktivieren möchten, die mit einem Spaltenverschlüsselungsschlüssel geschützt sind, der von Ihrem Spaltenhauptschlüssel verschlüsselt wird, müssen Sie den Spaltenhauptschlüssel durch den neuen Schlüssel mit der ENCLAVE_COMPUTATIONS-Eigenschaft ersetzen. [Übersicht über die Schlüsselverwaltung für Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md) und [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md).

Mit [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md), [sys.column_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md) und [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md) können Sie sich Informationen zu CEKs anzeigen lassen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **ALTER ANY COLUMN ENCRYPTION KEY**-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-adding-a-column-encryption-key-value"></a>A. Hinzufügen eines Spaltenverschlüsselungsschlüsselwerts  
 Im folgenden Beispiel wird ein CEK mit der Bezeichnung `MyCEK` verändert.  
  
```sql  
ALTER COLUMN ENCRYPTION KEY MyCEK  
ADD VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK2,   
    ALGORITHM = 'RSA_OAEP',   
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E00740075007300650072002F006D0079002F0064006500650063006200660034006100340031003000380034006200350033003200360066003200630062006200350030003600380065003900620061003000320030003600610037003800310066001DDA6134C3B73A90D349C8905782DD819B428162CF5B051639BA46EC69A7C8C8F81591A92C395711493B25DCBCCC57836E5B9F17A0713E840721D098F3F8E023ABCDFE2F6D8CC4339FC8F88630ED9EBADA5CA8EEAFA84164C1095B12AE161EABC1DF778C07F07D413AF1ED900F578FC00894BEE705EAC60F4A5090BBE09885D2EFE1C915F7B4C581D9CE3FDAB78ACF4829F85752E9FC985DEB8773889EE4A1945BD554724803A6F5DC0A2CD5EFE001ABED8D61E8449E4FAA9E4DD392DA8D292ECC6EB149E843E395CDE0F98D04940A28C4B05F747149B34A0BAEC04FFF3E304C84AF1FF81225E615B5F94E334378A0A888EF88F4E79F66CB377E3C21964AACB5049C08435FE84EEEF39D20A665C17E04898914A85B3DE23D56575EBC682D154F4F15C37723E04974DB370180A9A579BC84F6BC9B5E7C223E5CBEE721E57EE07EFDCC0A3257BBEBF9ADFFB00DBF7EF682EC1C4C47451438F90B4CF8DA709940F72CFDC91C6EB4E37B4ED7E2385B1FF71B28A1D2669FBEB18EA89F9D391D2FDDEA0ED362E6A591AC64EF4AE31CA8766C259ECB77D01A7F5C36B8418F91C1BEADDD4491C80F0016B66421B4B788C55127135DA2FA625FB7FD195FB40D90A6C67328602ECAF3EC4F5894BFD84A99EB4753BE0D22E0D4DE6A0ADFEDC80EB1B556749B4A8AD00E73B329C95827AB91C0256347E85E3C5FD6726D0E1FE82C925D3DF4A9  
);  
GO  
  
```  
  
### <a name="b-dropping-a-column-encryption-key-value"></a>B. Entfernen eines Spaltenverschlüsselungsschlüsselwerts  
 Im folgenden Beispiel wird ein CEK mit der Bezeichnung `MyCEK` verändert, indem ein Wert entfernt wird.  
  
```sql  
ALTER COLUMN ENCRYPTION KEY MyCEK  
DROP VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK  
);  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Always Encrypted &#40;Datenbank-Engine&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Übersicht über die Schlüsselverwaltung für Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   
  
  
