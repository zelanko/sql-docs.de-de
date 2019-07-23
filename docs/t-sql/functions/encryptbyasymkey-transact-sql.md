---
title: ENCRYPTBYASYMKEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYASYMKEY
- ENCRYPTBYASYMKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTBYASYMKEY function
- encryption [SQL Server], asymmetric keys
- asymmetric keys [SQL Server], ENCRYPTBYASYMKEY function
ms.assetid: 86bb2588-ab13-4db2-8f3c-42c9f572a67b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a9c0128fab05a83720bd7f4eedd8d2e200c62450
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135890"
---
# <a name="encryptbyasymkey-transact-sql"></a>ENCRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion verschlüsselt Daten mit einem asymmetrischen Schlüssel.  
  
 ![Artikellinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Article link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
EncryptByAsymKey ( Asym_Key_ID , { 'plaintext' | @plaintext } )  
```  
  
## <a name="arguments"></a>Argumente  
*asym_key_ID*  
Die ID eines asymmetrischen Schlüssels in der Datenbank. *asym_Key_ID* weist den Datentyp **int** auf.  
  
*Klartext*  
Eine Zeichenfolge von Daten, die `ENCRYPTBYASYMKEY` mit dem asymmetrischen Schlüssel verschlüsselt. *Klartext* kann die Datentypen
 
+ **binary**
+ **char**
+ **nchar**
+ **nvarchar**
+ **varbinary**
  
oder
  
+ **varchar**
 
aufweisen.  
  
**@plaintext**  
Eine Variable, die einen Wert enthält, der von `ENCRYPTBYASYMKEY` mit dem asymmetrischen Schlüssel verschlüsselt wird. **@plaintext** kann die Datentypen
  
+ **binary**
+ **char**
+ **nchar**
+ **nvarchar**
+ **varbinary**
  
oder
  
+ **varchar**
 
aufweisen.  
  
## <a name="return-types"></a>Rückgabetypen  
**varbinary** mit einer maximalen Größe von 8.000 Byte.  
  
## <a name="remarks"></a>Remarks  
Verschlüsselungs- und Entschlüsselungsvorgänge, die asymmetrische Schlüssel verwenden, verwenden viele Ressourcen und werden deshalb kostspielig, verglichen mit der Verschlüsselung und Entschlüsselung mit einem symmetrischen Schlüssel. Es wird empfohlen, dass Entwickler asymmetrische Schlüssel für Verschlüsselungs- und Entschlüsselungsvorgänge auf großen Datasets vermeiden, z.B. bei Benutzerdaten in Datenbanktabellen. Stattdessen sollten Entwickler die Daten zunächst mit einem starken symmetrischen Schlüssel verschlüsseln und dann diesen symmetrischen Schlüssel mit einem asymmetrischen Schlüssel verschlüsseln.  
  
`ENCRYPTBYASYMKEY` gibt je nach Algorithmus **NULL** zurück, wenn die Eingabe eine bestimmte Anzahl von Bytes überschreitet. Die spezifischen Grenzwerte:

+ Ein 512-Bit-RSA-Schlüssel kann bis zu 53 Bytes verschlüsseln
+ Ein 1024-Bit-Schlüssel kann bis zu 117 Bytes verschlüsseln
+ Ein 2048-Bit-Schlüssel kann bis zu 245 Bytes verschlüsseln

Sowohl Zertifikate als auch asymmetrische Schlüssel dienen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Wrapper für RSA-Schlüssel.  
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird der in `@cleartext` gespeicherte Text mit dem asymmetrischen Schlüssel `JanainaAsymKey02` verschlüsselt. Due Anweisung fügt die verschlüsselten Daten in die Tabelle `ProtectedData04` ein.  
  
```  
INSERT INTO AdventureWorks2012.Sales.ProtectedData04   
    VALUES( N'Data encrypted by asymmetric key ''JanainaAsymKey02''',  
    EncryptByAsymKey(AsymKey_ID('JanainaAsymKey02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DECRYPTBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/decryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  