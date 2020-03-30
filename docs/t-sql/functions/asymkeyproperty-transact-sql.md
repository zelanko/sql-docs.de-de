---
title: ASYMKEYPROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ASYMKEYPROPERTY_TSQL
- ASYMKEYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASYMKEYPROPERTY
ms.assetid: a30581f2-e1b1-4996-93e6-527ff96b7c42
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: de7e95ab26102c0b3bbe1e33c57ae9491a5b9a2c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "65945887"
---
# <a name="asymkeyproperty-transact-sql"></a>ASYMKEYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt die Eigenschaften eines asymmetrischen Schlüssels zurück.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
ASYMKEYPROPERTY (Key_ID , 'algorithm_desc' | 'string_sid' | 'sid')  
```  
  
## <a name="arguments"></a>Argumente  
*Key_ID*  
Die Key_ID eines asymmetrischen Schlüssels in der Datenbank. Wenn Sie nur den Schlüsselnamen kennen, verwenden Sie ASYMKEY_ID, um die KEY_ID zu finden. *Key_ID* weist den Datentyp **int** auf.
  
**‚** algorithm_desc **’**  
Gibt an, dass die Ausgabe die Algorithmusbeschreibung des asymmetrischen Schlüssels zurückgibt. Nur verfügbar für aus einem EKM-Modul erstellte asymmetrische Schlüssel.
  
**‚** string_sid **’**  
Gibt an, dass die Ausgabe die SID des asymmetrischen Schlüssels im **nvarchar()** -Format zurückgibt.
  
**'** sid **'**  
Gibt an, dass die Ausgabe die SID des asymmetrischen Schlüssels im Binärformat zurückgibt.
  
## <a name="return-types"></a>Rückgabetypen  
**sql_variant**
  
## <a name="permissions"></a>Berechtigungen  
Erfordert mindestens eine passende Berechtigung für den asymmetrischen Schlüssel, und dem Aufrufer darf die VIEW-Berechtigung für den asymmetrischen Schlüssel nicht verweigert worden sein. Weitere Informationen zu Berechtigungen für asymmetrische Schlüssel finden Sie unter [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md).
  
## <a name="examples"></a>Beispiele  
Das folgende Beispiel gibt die Eigenschaften des asymmetrischen Schlüssels mit der Key_ID 256 zurück.
  
```sql
SELECT   
ASYMKEYPROPERTY(256, 'algorithm_desc') AS Algorithm,  
ASYMKEYPROPERTY(256, 'string_sid') AS String_SID,  
ASYMKEYPROPERTY(256, 'sid') AS SID ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen
[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
[ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)  
[DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)  
[SIGNBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/signbyasymkey-transact-sql.md)  
[VERIFYSIGNEDBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/verifysignedbyasymkey-transact-sql.md)  
[Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)  
[sys.asymmetric_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md)  
[Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)  
[ASYMKEY_ID &#40;Transact-SQL&#41;](../../t-sql/functions/asymkey-id-transact-sql.md)  
[SYMKEYPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/symkeyproperty-transact-sql.md)
  
  
