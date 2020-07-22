---
title: ntext, text und image (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ntext_TSQL
- ntext
dev_langs:
- TSQL
helpviewer_keywords:
- text data type, about text data type
- text [SQL Server], data types
- ntext data type
- ntext data type, about ntext data type
- image data type, about image data type
ms.assetid: b0d8769c-7598-4f97-8162-ace5f182b5bc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95d3209fd08f08820966294b96b0fd11831e73ea
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555935"
---
# <a name="ntext-text-and-image-transact-sql"></a>ntext, text und image (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Datentypen fester und variabler Länge zum Speichern von großen Nicht-Unicode- und Unicode-Zeichendaten sowie Binärdaten. Unicode-Daten verwenden den UNICODE UCS-2-Zeichensatz.
  
>**WICHTIG!**  Die Datentypen **ntext**, **text** und **image** werden in einer zukünftigen Version von SQL Server entfernt. Vermeiden Sie die Verwendung dieser Datentypen bei neuen Entwicklungen, und planen Sie die Änderung von Anwendungen, in denen sie aktuell verwendet werden. Verwenden Sie stattdessen [nvarchar(max)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md), [varchar(max)](../../t-sql/data-types/char-and-varchar-transact-sql.md)und [varbinary(max)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md) .  
  
## <a name="arguments"></a>Argumente
**ntext**  
Unicode-Daten variabler Länge mit einer maximalen Zeichenfolgenlänge von 2^30 - 1 (1.073.741.823) Bytes. Die Speichergröße in Bytes ist doppelt so groß wie die eingegebene Zeichenfolgenlänge. Das ISO-Synonym für **ntext** lautet **national text**.
  
**text**  
Nicht-Unicode-Daten variabler Länge in der Codepage des Servers und mit einer maximalen Zeichenfolgenlänge von 2^31 - 1 (2.147.483.647). Auch wenn die Servercodepage Doppelbytezeichen verwendet, ist der Speicherplatz 2.147.483.647 Bytes groß. Abhängig von der Zeichenfolge kann die Speichergröße unter 2.147.483.647 Bytes liegen.
  
**image**  
Binärdaten variabler Länge von 0 bis 2^31-1 (2.147.483.647) Byte.
  
## <a name="remarks"></a>Bemerkungen  
Die folgenden Funktionen und Anweisungen können mit **ntext**, **text** oder **image**-Daten verwendet werden.
  
|Functions|Anweisungen|  
|---|---|
|[DATALENGTH &#40;Transact-SQL&#41;](../../t-sql/functions/datalength-transact-sql.md)|[READTEXT &#40;Transact-SQL&#41;](../../t-sql/queries/readtext-transact-sql.md)|  
|[PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)|[SET TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/statements/set-textsize-transact-sql.md)|  
|[SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)|[UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)|  
|[TEXTPTR &#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)|[WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)|  
|[TEXTVALID &#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)||  
  
## <a name="see-also"></a>Weitere Informationen
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Datentypkonvertierung &#40;Datenbank-Engine&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)

