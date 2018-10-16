---
title: COMPRESS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f5bca48c2aa30bf1a3616076c61d06f69dc5dab2
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49168954"
---
# <a name="compress-transact-sql"></a>COMPRESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Diese Funktion komprimiert den Eingabeausdruck mit dem GZIP-Algorithmus. Die Funktion gibt ein Bytearray vom Typ **varbinary(max)** zurück.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
COMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Argumente  
*expression*  
Ein

* **binary(***n***)**
* **char(***n***)**
* **nchar(***n***)**
* **nvarchar(max)**
* **nvarchar(***n***)**
* **varbinary(max)**
* **varbinary(***n***)**
* **varchar(max)**

oder

* **varchar(***n***)**

expression. Weitere Informationen finden Sie unter [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="return-types"></a>Rückgabetypen
**varbinary(max)** stellt den komprimierten Inhalt der Eingabe dar.
  
## <a name="remarks"></a>Remarks  
Komprimierte Daten können nicht indiziert werden.
  
Die `COMPRESS`-Funktion komprimiert die Ausdrucksdaten der Eingabe. Sie müssen diese Funktion aufrufen, damit jeder Datenabschnitt komprimiert wird. Weitere Informationen zu automatischer Datenkomprimierung während der Speicherung auf Zeilen- oder Seitenebene finden Sie unter [Datenkomprimierung](../../relational-databases/data-compression/data-compression.md).
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-compress-data-during-the-table-insert"></a>A. Komprimieren von Daten beim Einfügen einer Tabelle  
Dieses Beispiel zeigt, wie Daten aus einer Tabelle komprimiert werden können, die in einer Tabelle enthalten sind:
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>B. Archivieren einer komprimierten Version von gelöschten Zeilen  
Diese Anweisung löscht zunächst ältere Spielerdaten aus der `player`-Tabelle. Die Datensätze werden dann in der `inactivePlayer`-Tabelle in einem komprimierten Format gespeichert, um Speicherplatz zu sparen.
  
```sql
DELETE player  
WHERE datemodified < @startOfYear  
OUTPUT id, name, surname datemodifier, COMPRESS(info)   
INTO dbo.inactivePlayers ;  
```  
  
## <a name="see-also"></a>Siehe auch
[String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/string-functions-transact-sql.md)  
[DECOMPRESS &#40;Transact-SQL&#41;](../../t-sql/functions/decompress-transact-sql.md)
  
  
