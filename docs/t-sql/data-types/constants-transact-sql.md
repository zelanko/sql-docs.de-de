---
description: Konstanten (Transact-SQL)
title: Konstanten (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/09/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- bit data type
- constants [SQL Server]
- scalar values
- money data type, constants
- binary [SQL Server], constants
- float data type
- Unicode [SQL Server], constants
- constants [Transact-SQL]
- integer constants
- decimal data type, constants
- character strings [SQL Server], constants
- positive values [SQL Server]
- formats [SQL Server], constants
- datetime data type [SQL Server]
- literals [SQL Server], constants
- real data type
- negative values
ms.assetid: 58ae3ff3-b1d5-41b2-9a2f-fc7ab8c83e0e
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b8b68b99fa522b69401eab47d54e40cdf8621c2
ms.sourcegitcommit: 780a81c02bc469c6e62a9c307e56a973239983b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90027281"
---
# <a name="constants-transact-sql"></a>Konstanten (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Eine Konstante, gelegentlich auch als Literal- oder Skalarwert bezeichnet, ist ein Symbol, das einen bestimmten Datenwert repräsentiert. Das Format einer Konstante ist abhängig vom Datentyp des Werts, den sie repräsentiert.
  
## <a name="character-string-constants"></a>Zeichenfolgenkonstanten
Zeichenfolgenkonstanten werden in einfache Anführungszeichen eingeschlossen und enthalten alphanumerische Zeichen (a-z, A-Z und 0-9) sowie Sonderzeichen, wie z. B. Ausrufezeichen (!), @-Zeichen und Nummernzeichen (#). Zeichenfolgenkonstanten wird die Standardsortierung der aktuellen Datenbank zugewiesen. Wenn die COLLATE-Klausel verwendet wird, erfolgt die Konvertierung in die Standardcodepage der Datenbank trotzdem noch vor der Konvertierung in die durch die COLLATE-Klausel angegebene Sortierung. Vom Benutzer eingegebene Zeichenfolgen werden durch die Codepage auf dem Computer ausgewertet und ggf. in die Standardcodepage der Datenbank übersetzt.

> [!NOTE]
> Wenn mithilfe der COLLATE-Klausel eine [UTF8-fähige Sortierung](../../relational-databases/collations/collation-and-unicode-support.md#utf8) angegeben wird, erfolgt die Konvertierung in die Standardcodepage der Datenbank trotzdem noch vor der Konvertierung in die von der COLLATE-Klausel angegebene Sortierung. Die Konvertierung erfolgt nicht direkt mit der angegebenen Unicode-fähigen Sortierung. Weitere Informationen finden Sie unter [Unicode-Zeichenfolgen](#unicode-strings).
  
Wurde für die QUOTED_IDENTIFIER-Option für eine Verbindung OFF festgelegt, können Zeichenfolgen auch in doppelte Anführungszeichen eingeschlossen werden; der Microsoft [OLE DB-Treiber für SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) und der [ODBC-Treiber für SQL Server](../../connect/odbc/download-odbc-driver-for-sql-server.md) verwenden jedoch automatisch `SET QUOTED_IDENTIFIER ON`. Es wird die Verwendung einfacher Anführungszeichen empfohlen.
  
Enthält eine in einfache Anführungszeichen eingeschlossene Zeichenfolge ein eingeschlossenes Anführungszeichen, muss das eingeschlossene Anführungszeichen durch zwei einfache Anführungszeichen ersetzt werden. Bei Zeichenfolgen, die in doppelten Anführungszeichen stehen, ist dies nicht erforderlich.
  
Nachfolgend finden Sie Beispiele für Zeichenfolgen:
  
```sql
'Cincinnati'  
'O''Brien'  
'Process X is 50% complete.'  
'The level for job_id: %d should be between %d and %d.'  
"O'Brien"  
```  
  
Leere Zeichenfolgen werden als zwei einzelne Anführungszeichen ohne Inhalt dargestellt. Im 6.x-Kompatibilitätsmodus wird eine leere Zeichenfolge als einzelnes Leerzeichen interpretiert.
  
Zeichenfolgenkonstanten unterstützen erweiterte [Sortierungen](../../relational-databases/collations/collation-and-unicode-support.md).
  
> [!NOTE]  
> Zeichenkonstanten, die größer sind als 8000 Bytes, werden als **varchar(max)-** Daten typisiert.  
  
## <a name="unicode-strings"></a>Unicode-Zeichenfolgen
Unicode-Zeichenfolgen besitzen ein ähnliches Format wie Zeichenfolgen, werden aber mit einem N-Bezeichner eingeleitet (N steht für Landessprache (National Language) im SQL-92-Standard). 

> [!IMPORTANT]  
> Das Präfix N muss ein Großbuchstabe sein. 

Beispielsweise ist `'Michél'` eine Zeichenkonstante, während `N'Michél'` eine Unicode-Konstante ist. Unicode-Konstanten werden als Unicode-Daten interpretiert und nicht mithilfe einer Codepage ausgewertet. Unicode-Konstanten verfügen über eine Sortierung. Diese Sortierung steuert in erster Linie Vergleiche und die Unterscheidung nach Groß- und Kleinschreibung. Unicode-Konstanten wird die Standardsortierung der aktuellen Datenbank zugewiesen. Wenn die COLLATE-Klausel verwendet wird, erfolgt die Konvertierung in die Standardsortierung der Datenbank trotzdem noch vor der Konvertierung in die durch die COLLATE-Klausel angegebene Sortierung. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md#storage_differences).
  
Unicode-Zeichenfolgenkonstanten unterstützen erweiterte Sortierungen.
  
> [!NOTE]  
> Unicode-Konstanten, die größer sind als 8000 Bytes, werden als **nvarchar(max)**-Daten typisiert.  
  
## <a name="binary-constants"></a>Binäre Konstanten
Binäre Konstanten besitzen das Präfix `0x` und bestehen aus einer Zeichenfolge von hexadezimalen Zahlen. Sie werden nicht in Anführungszeichen eingeschlossen.
  
Nachfolgend finden Sie Beispiele für Binärzeichenfolgen:
  
```sql
0xAE  
0x12Ef  
0x69048AEFDD010E  
0x  (empty binary string)  
```  
  
> [!NOTE]  
>  Binärkonstanten, die größer sind als 8000 Bytes, werden als **varbinary(max)**-Daten typisiert.  
  
## <a name="bit-constants"></a>bit-Konstanten
**bit**-Konstanten werden durch die Zahlen 0 oder 1 dargestellt und nicht in Anführungszeichen eingeschlossen. Wird eine größere Zahl als eins verwendet, wird diese in eins umgewandelt.
  
## <a name="datetime-constants"></a>datetime-Konstanten
**datetime**-Konstanten werden durch Datumszeichenfolgen in einem besonderen Format dargestellt und in einfache Anführungszeichen eingeschlossen.
  
Nachfolgend finden Sie Beispiele für **datetime**-Konstanten:
  
```sql
'December 5, 1985'  
'5 December, 1985'  
'851205'  
'12/5/98'  
```  
  
Beispiele für datetime-Konstanten sind:
  
```sql
'14:30:24'  
'04:24 PM'  
```  
  
## <a name="integer-constants"></a>integer-Konstanten
**integer**-Konstanten werden durch eine Zeichenfolge von Zahlen dargestellt, die nicht in Anführungszeichen eingeschlossen sind und keine Dezimaltrennzeichen enthalten. **integer**-Konstanten müssen ganze Zahlen sein und können keine Dezimalstellen enthalten.
  
Nachfolgend finden Sie Beispiele für **integer**-Konstanten:
  
```sql
1894  
2  
```  
  
## <a name="decimal-constants"></a>decimal-Konstanten
**decimal**-Konstanten werden durch eine Folge von Ziffern dargestellt, die nicht in Anführungszeichen eingeschlossen sind, und enthalten ein Dezimaltrennzeichen.
  
Nachfolgend finden Sie Beispiele für **decimal**-Konstanten:
  
```sql
1894.1204  
2.0  
```  
  
## <a name="float-and-real-constants"></a>float- und real-Konstanten
Für **float**- und **real**-Konstanten wird die wissenschaftliche Schreibweise verwendet.
  
Nachfolgend finden Sie Beispiele für **float**- oder **real**-Konstanten:
  
```sql
101.5E5  
0.5E-2  
```  
  
## <a name="money-constants"></a>money-Konstanten
**money**-Konstanten werden als Zeichenfolge von Zahlen mit einem optionalen Dezimaltrennzeichen und einem optionalen Währungssymbol als Präfix dargestellt. **money**-Konstanten werden nicht in Anführungszeichen eingeschlossen.
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erzwingt keine Gruppierungsregeln, wie etwa das Einfügen eines Kommas (,) nach jeder dritten Ziffer in Währungszeichenfolgen.
  
> [!NOTE]  
>  Kommas werden im angegebenen **money**-Literal ignoriert.  
  
Nachfolgend finden Sie Beispiele für **money**-Konstanten:
  
```sql
$12  
$542023.14  
```  
  
## <a name="uniqueidentifier-constants"></a>uniqueidentifier-Konstanten
**uniqueidentifier**-Konstanten sind eine Zeichenfolge, die eine GUID darstellt. Sie können entweder im Binär- oder Zeichenfolgenformat angegeben werden.
  
In den beiden folgenden Beispielen wird dieselbe GUID angegeben:
  
```sql
'6F9619FF-8B86-D011-B42D-00C04FC964FF'  
0xff19966f868b11d0b42d00c04fc964ff  
```  
  
## <a name="specifying-negative-and-positive-numbers"></a>Angeben von negativen und positiven Zahlen  
Um anzugeben, ob eine Zahl positiv oder negativ ist, wenden Sie einen der unären Operatoren **+** oder **-** auf eine numerische Konstante an. Dadurch wird ein numerischer Ausdruck erstellt, der den numerischen, vorzeichenbehafteten Wert darstellt. Numerische Konstanten werden auf einen positiven Wert gesetzt, wenn die unären Operatoren **+** oder **-** nicht angewendet werden.
  
**integer**-Ausdrücke mit Vorzeichen:  
  
```sql
+145345234
-2147483648
```
**decimal**-Ausdrücke mit Vorzeichen:  
  
```sql
+145345234.2234
-2147483648.10
```
  
**float**-Ausdrücke mit Vorzeichen:  
  
```sql
+123E-3
-12E5
```
  
**money**-Ausdrücke mit Vorzeichen:  
  
```sql
-$45.56
+$423456.99
```
  
## <a name="enhanced-collations"></a>Erweiterte Sortierungen  
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] unterstützt Zeichen- und Unicode-Zeichenfolgenkonstanten, die erweiterte Sortierungen unterstützen. Weitere Informationen finden Sie in der [COLLATE &#40;Transact-SQL&#41;](../../t-sql/statements/collations.md)-Klausel.
  
## <a name="see-also"></a>Weitere Informationen
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)
[Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md)  
[Rangfolge von Sortierungen](../../t-sql/statements/collation-precedence-transact-sql.md)    
  
