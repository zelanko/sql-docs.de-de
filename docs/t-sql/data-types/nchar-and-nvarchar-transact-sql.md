---
title: nchar und nvarchar (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/19/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8a8baa16e2b2d7e22bfd3d4045ff77483e198aec
ms.sourcegitcommit: 67261229b93f54f9b3096890b200d1aa0cc884ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68354591"
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar und nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Dieser Artikel beschreibt Zeichendatentypen, die entweder über eine feste Größe – **nchar** – oder über eine variable Größe – **nvarchar** – verfügen. Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] gilt Folgendes: Wenn eine Sortierung mit aktivierten [zusätzlichen Zeichen](../../relational-databases/collations/collation-and-unicode-support.md#Supplementary_Characters) verwendet wird, speichern diese Datentypen den gesamten Bereich der [Unicodezeichendaten](../../relational-databases/collations/collation-and-unicode-support.md#Unicode_Defn) und verwenden die Zeichencodierung [UTF-16](https://www.wikipedia.org/wiki/UTF-16). Wenn eine Sortierung ohne aktivierte zusätzliche Zeichen angegeben ist, speichern diese Datentypen nur die Teilmenge der Zeichendaten, die von der [UCS-2](https://www.wikipedia.org/wiki/Universal_Coded_Character_Set#Encoding_forms)-Zeichencodierung unterstützt werden.
  
## <a name="arguments"></a>Argumente  
**nchar** [ ( n ) ]  
Zeichenfolgendaten mit fester Größe. *n* definiert die Zeichenfolgengröße in Bytepaaren und muss ein Wert zwischen 1 und 4.000 sein. Die Speichergröße beträgt zweimal *n* Byte. Für die [UCS-2](https://www.wikipedia.org/wiki/UTF-16#U+0000_to_U+D7FF_and_U+E000_to_U+FFFF)-Codierung beträgt die Speichergröße zweimal *n* Byte, und die Anzahl von Zeichen, die gespeichert werden können, ist ebenfalls *n*. Für die UTF-16-Codierung ist die Speichergröße noch zweimal *n* Byte, aber die Anzahl von Zeichen, die gespeichert werden können, ist ggf. kleiner als *n*, da zusätzliche Zeichen zwei Bytepaare verwenden (auch [Ersatzzeichenpaar](https://www.wikipedia.org/wiki/UTF-16#U+010000_to_U+10FFFF) genannt). Die ISO-Synonyme für **nchar** lauten **national char** und **national character**.
  
**nvarchar** [ ( n | **max** ) ]  
Zeichenfolgendaten mit variabler Größe. *n* definiert die Zeichenfolgengröße in Bytepaaren und kann ein Wert zwischen 1 und 4.000 sein. **max** gibt an, dass die maximale Speichergröße 2^30-1 Zeichen (2 GB) beträgt. Die Speichergröße beträgt zweimal *n* Byte + 2 Byte. Für die [UCS-2](https://www.wikipedia.org/wiki/UTF-16#U+0000_to_U+D7FF_and_U+E000_to_U+FFFF)-Codierung beträgt die Speichergröße zweimal *n* Byte + 2 Byte, und die Anzahl von Zeichen, die gespeichert werden können, ist ebenfalls *n*. Für die UTF-16-Codierung ist die Speichergröße noch zweimal *n* Byte + 2 Byte, aber die Anzahl von Zeichen, die gespeichert werden können, ist ggf. kleiner als *n*, da zusätzliche Zeichen zwei Bytepaare verwenden (auch [Ersatzzeichenpaar](https://www.wikipedia.org/wiki/UTF-16#U+010000_to_U+10FFFF) genannt). Die ISO-Synonyme für **nvarchar** lauten **national char varying** und **national character varying**.
  
## <a name="remarks"></a>Bemerkungen  
Ein gängiges Missverständnis besteht darin, dass das *n* in [NCHAR(*n*) und NVARCHAR(*n*)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md) die Anzahl von Zeichen definiert. Das *n* in [NCHAR(*n*) und NVARCHAR(*n*)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md) definiert jedoch die Zeichenfolgenlänge in **Bytepaaren** (0-4.000). *n* definiert niemals die Anzahl von Zeichen, die gespeichert werden können. Dies ähnelt der Definition von [CHAR(*n*) und VARCHAR(*n*)](../../t-sql/data-types/char-and-varchar-transact-sql.md).   
Das Missverständnis entsteht, da bei der Verwendung von Zeichen, die im Unicode-Bereich 0-65.535 definiert sind, ein Zeichen pro Bytepaar gespeichert werden kann. In höheren Unicode-Bereichen (65.536-1.114.111) verwendet ein Zeichen möglicherweise aber zwei Bytepaare. In einer als NCHAR(10) definierten Spalte kann [!INCLUDE[ssde_md](../../includes/ssde_md.md)] beispielsweise 10 Zeichen speichern, die ein Bytepaar verwenden (Unicode-Bereich 0-65.535), jedoch weniger als 10 Zeichen bei Verwendung von zwei Bytepaaren (Unicode-Bereich 65.536-1.114.111). Weitere Informationen zum Unicode-Speicher und -Zeichenbereichen finden Sie unter [Speicherunterschiede zwischen UTF-8 und UTF-16](../../relational-databases/collations/collation-and-unicode-support.md#storage_differences).     

Wenn *n* in einer Datendefinitions- oder Variablendeklarationsanweisung nicht angegeben ist, beträgt die Standardlänge 1. Wenn *n* in der CAST-Funktion nicht angegeben ist, beträgt die Standardlänge 30.

Wenn Sie **nchar** oder **nvarchar** verwenden, wird Folgendes empfohlen:
- Verwenden Sie **nchar**, wenn die Dateneinträge einer Spalte jeweils gleich lang sind.  
- Verwenden Sie **nvarchar**, wenn sich die Dateneinträge einer Spalte in ihrer Größe erheblich unterscheiden.  
- Verwenden Sie **nvarchar(max)** , wenn die Dateneinträge einer Spalte unterschiedlich lang sind, und die Zeichenfolgenlänge 4.000 Bytepaare überschreitet.  
  
**sysname** ist ein vom System bereitgestellter benutzerdefinierter Datentyp, der funktional **nvarchar(128)** entspricht, außer dass er keine NULL-Werte zulässt. **sysname** wird zum Verweisen auf Datenbankobjektnamen verwendet.
  
Objekten, die **nchar** or **nvarchar** verwenden, wird die Standardsortierung der Datenbank zugewiesen, es sei denn, mithilfe der COLLATE-Klausel wird eine bestimmte Sortierung zugewiesen.
  
SET ANSI_PADDING hat für **nchar** und **nvarchar** immer den Wert ON. SET ANSI_PADDING OFF gilt nicht für die Datentypen **nchar** oder **nvarchar**.
  
Stellen Sie einer Unicode-Zeichenfolgenkonstanten den Buchstaben „N“ voran, um UCS-2- oder UTF-16-Eingabe zu markieren, je nachdem, ob eine Sortierung mit zusätzlichen Zeichen verwendet wird. Ohne das Präfix „N“ wird die Zeichenfolge in die Standardcodepage der Datenbank konvertiert, die einige Zeichen ggf. nicht erkennt. Ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] gilt Folgendes: Wenn eine Sortierung mit aktiviertem UTF-8 verwendet wird, kann die Standardcodepage einen UNICODE UTF-8-Zeichensatz speichern. 
 
> [!NOTE]  
> Geht einer Zeichenfolgenkonstante der Buchstabe „N“ voraus, gibt die implizite Konvertierung eine UCS-2- oder UTF-16-Zeichenfolge zurück, wenn die Konstante, die konvertiert werden soll, die maximale Länge für den Datentyp für „nvarchar“-Zeichenfolgen (4.000) nicht überschreitet. Andernfalls hat die implizite Konvertierung einen hohen „nvarchar(max)“-Wert zur Folge.
  
> [!WARNING]  
> Jede **varchar(max)** - oder **nvarchar(max)** -Spalte, die ungleich NULL ist, erfordert 24 Byte an zusätzlicher fester Zuteilung, die während eines Sortiervorgangs hinsichtlich des Zeilenlimits von 8.060 Byte gelten. Diese zusätzlichen Byte können zur Erstellung einer impliziten Beschränkung der Anzahl der **varchar(max)** - oder **nvarchar(max)** -Spalten führen, die ungleich NULL sind. Beim Erstellen der Tabelle (außerhalb der üblichen Warnung darüber, dass die maximale Zeilengröße das zulässige Maximum von 8.060 Byte überschreitet) oder beim Einfügen der Daten wird kein spezieller Fehler ausgegeben. Diese umfangreiche Zeilengröße kann Fehler verursachen (z.B. Fehler 512), die Benutzer während einiger normaler Vorgänge möglicherweise nicht vorhersehen können.  Die Aktualisierung eines gruppierten Indexschlüssels und Teile des vollständigen Spaltensatzes stellen zwei Beispiele für Vorgänge dieser Art dar.
  
## <a name="converting-character-data"></a>Konvertieren von Zeichendaten  
Informationen zum Konvertieren von Zeichendaten finden Sie unter [char und varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
## <a name="see-also"></a>Siehe auch
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)    
[Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md)     
[Einzelbyte- und Mehrbyte-Zeichensätze](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets)  
  
