---
title: CRYPT_GEN_RANDOM (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CRYPT_GEN_RANDOM_TSQL
- CRYPT_GEN_RANDOM
dev_langs:
- TSQL
helpviewer_keywords:
- CRYPT_GEN_RANDOM function
ms.assetid: b74bd9d4-758e-4b94-89a0-76dcda6d8c42
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 70df8f06eb1561dd186d5be643a5863ffab5981a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68026452"
---
# <a name="crypt_gen_random-transact-sql"></a>CRYPT_GEN_RANDOM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt eine von der Crypto API (CAPI) generierte Kryptografie-Zufallszahl aus. `CRYPT_GEN_RANDOM` gibt eine hexadezimale Zahl mit der Länge einer angegebenen Anzahl Bytes zurück.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
CRYPT_GEN_RANDOM ( length [ , seed ] )   
```  
  
## <a name="arguments"></a>Argumente  
*length*  
Die Länge der Zahl in Bytes, die von `CRYPT_GEN_RANDOM` erstellt wird. Das *length*-Argument weist einen **int**Datentyp und einen Wertebereich zwischen 1 und 8000 auf. `CRYPT_GEN_RANDOM` gibt NULL für einen **int**-Wert außerhalb dieses Bereichs zurück. 
  
*seed*  
Eine optionale Hexadezimalzahl für die Verwendung als zufälliger Ausgangswert. Die Länge von *seed* muss mit dem Wert des *length*-Arguments übereinstimmen. Das *seed*-Argument weist den Datentyp **varbinary(8000)** auf.
  
## <a name="returned-types"></a>Rückgabetypen  
**varbinary(8000)**
  
## <a name="permissions"></a>Berechtigungen  
Diese Funktion ist öffentlich und erfordert keine besonderen Berechtigungen.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-generating-a-random-number"></a>A. Generieren einer Zufallszahl  
In diesem Beispiel wird eine Zufallszahl von 50 Byte Länge generiert:
  
```sql
SELECT CRYPT_GEN_RANDOM(50) ;  
```  
  
In diesem Beispiel wird mithilfe eines Seeds von 4 Byte eine Zufallszahl von 4 Byte Länge generiert:
  
```sql
SELECT CRYPT_GEN_RANDOM(4, 0x25F18060) ;  
```  
  
## <a name="see-also"></a>Weitere Informationen
[RAND &#40;Transact-SQL&#41;](../../t-sql/functions/rand-transact-sql.md)
  
  
