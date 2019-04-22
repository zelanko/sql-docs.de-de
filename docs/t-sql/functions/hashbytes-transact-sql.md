---
title: HASHBYTES (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HASHBYTES_TSQL
- HASHBYTES
dev_langs:
- TSQL
helpviewer_keywords:
- hash input
- HASHBYTES
ms.assetid: 0ea6a4d1-313e-4f70-b939-dd2cd570f6d6
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fb4a69420f4fc3ac7881b2798ef97fc0b202a31f
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59429386"
---
# <a name="hashbytes-transact-sql"></a>HASHBYTES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt den MD2-, MD4-, MD5-, SHA-, SHA1- oder SHA2-Hash der zugehörigen Eingabe in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
HASHBYTES ( '<algorithm>', { @input | 'input' } )  
  
<algorithm>::= MD2 | MD4 | MD5 | SHA | SHA1 | SHA2_256 | SHA2_512   
```  
  
## <a name="arguments"></a>Argumente  
 **'**\<algorithm>**'**  
 Identifiziert den für das Hashing der Eingabe zu verwendenden Hashalgorithmus. Dies ist ein erforderliches Argument ohne Standardwert. Die einfachen Anführungszeichen müssen eingegeben werden. Ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] gelten alle anderen Algorithmen als SHA2_256 und SHA2_512 als veraltet.  
  
 **@input**  
 Gibt eine Variable mit den Daten an, für die das Hashing ausgeführt werden soll. **@input** ist **varchar**, **nvarchar** oder **varbinary**.  
  
 **'** *input* **'**  
 Gibt einen Ausdruck an, der zu einer Zeichenfolge oder Binärzeichenfolge ausgewertet wird, für die das Hashing ausgeführt werden soll.  
  
 Die Ausgabe entspricht dem Algorithmusstandard: 128 Bits (16 Bytes) für MD2, MD4 und MD5; 160 Bits (20 Bytes) für SHA und SHA1; 256 Bits (32 Bytes) für SHA2_256 und 512 Bits (64 Bytes) für SHA2_512.  
  
**Gilt für** : [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Bei [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und früher sind zulässige Eingabewerte auf 8.000 Byte beschränkt.  
  
## <a name="return-value"></a>Rückgabewert  
 **varbinary** (maximal 8.000 Byte)  

## <a name="remarks"></a>Remarks  
Erwägen Sie die Verwendung von `CHECKSUM` oder `BINARY_CHECKSUM` als Alternativen zur Berechnung eines Hashwerts.

Die Algorithmen MD2, MD4, MD5, SHA und SHA1 sind ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] veraltet. Verwenden Sie stattdessen SHA2_256 oder SHA2_512. Ältere Algorithmen funktionieren weiterhin, lösen jedoch ein Ereignis aus, das auf die Veraltung hinweist.

## <a name="examples"></a>Beispiele  
### <a name="return-the-hash-of-a-variable"></a>Zurückgeben des Hashcodes einer Variablen  
 Im folgenden Beispiel wird der `SHA1`-Hash der in der `@HashThis`-Variablen gespeicherten **nvarchar**-Daten zurückgegeben.  
  
```sql  
DECLARE @HashThis nvarchar(4000);  
SET @HashThis = CONVERT(nvarchar(4000),'dslfdkjLK85kldhnv$n000#knf');  
SELECT HASHBYTES('SHA1', @HashThis);  
```  
  
### <a name="return-the-hash-of-a-table-column"></a>Zurückgeben des Hashcodes einer Tabellenspalte  
 Im folgenden Beispiel wird der SHA1-Hash der Werte in der Spalte `c1` der Tabelle `Test1` zurückgegeben.  
  
```sql  
CREATE TABLE dbo.Test1 (c1 nvarchar(50));  
INSERT dbo.Test1 VALUES ('This is a test.');  
INSERT dbo.Test1 VALUES ('This is test 2.');  
SELECT HASHBYTES('SHA1', c1) FROM dbo.Test1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------------------------------  
0x0E7AAB0B4FF0FD2DFB4F0233E2EE7A26CD08F173  
0xF643A82F948DEFB922B12E50B950CEE130A934D6  
  
(2 row(s) affected)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Auswählen eines Verschlüsselungsalgorithmus](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
[CHECKSUM_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/checksum-agg-transact-sql.md)  
[CHECKSUM &#40;Transact-SQL&#41;](../../t-sql/functions/checksum-transact-sql.md)  
[BINARY_CHECKSUM  &#40;Transact-SQL&#41;](../../t-sql/functions/binary-checksum-transact-sql.md)  
  
