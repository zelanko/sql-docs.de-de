---
title: Datentypen (Transact-SQL) | Microsoft-Dokumentation
description: In diesem Artikel werden die verschiedenen Datentypen zusammengefasst, die in SQL Server verfügbar sind.
ms.date: 09/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system data types [SQL Server]
- data types [SQL Server]
- data types [SQL Server], about data types
ms.assetid: a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 33374865afeda8b6aac3c1f0423574a4fa1ac593
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248558"
---
# <a name="data-types-transact-sql"></a>Datentypen (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügt jede Spalte, jede lokale Variable, jeder Ausdruck und jeder Parameter einen entsprechenden Datentyp. Ein Datentyp ist ein Attribut, das für das jeweilige Objekt angibt, welchen Typ von Daten ein Objekt aufnehmen kann: Ganzzahlige Daten, Zeichendaten, Währungsdaten, Datums- und Uhrzeitdaten, binäre Zeichenfolgen usw.
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt eine Reihe von Systemdatentypen zur Verfügung, die alle Typen von Daten definieren, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden können. Sie können auch Ihre eigenen Datentypen in [!INCLUDE[tsql](../../includes/tsql-md.md)] oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] definieren. Aliasdatentypen basieren auf den vom System bereitgestellten Datentypen. Weitere Informationen zu Aliasdatentypen finden Sie unter [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md). Benutzerdefinierte Typen erhalten ihre Merkmale von den Methoden und Operatoren einer Klasse, die Sie mithilfe einer der von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] unterstützten Programmiersprachen erstellen.
  
Wenn zwei Ausdrücke, die unterschiedliche Datentypen, Sortierungen, Genauigkeiten, Dezimalstellen oder Längen haben, durch einen Operator kombiniert werden, wird das Ergebnis durch Folgendes bestimmt:
-   Der Datentyp des Ergebnisses wird bestimmt, indem die Regeln zur Rangfolge der Datentypen auf die Eingabeausdrücke angewendet werden. Weitere Informationen finden Sie unter [Rangfolge der Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
-   Wenn der Ergebniswert vom Datentyp **char**, **varchar**, **text**, **nchar**, **nvarchar** oder **ntext** ist, wird die Sortierung des Ergebnisses durch die Regeln zur Sortierungsrangfolge bestimmt. Weitere Informationen finden Sie unter [Rangfolge von Sortierungen &#40;Transact-SQL&#41;](../../t-sql/statements/collation-precedence-transact-sql.md).  
-   Die Genauigkeit, die Dezimalstellen und die Länge des Ergebniswertes hängen von der Genauigkeit, den Dezimalstellen und der Länge der Eingabeausdrücke ab. Weitere Informationen finden Sie unter [Genauigkeit, Dezimalstellen und Länge &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Datentypsynonyme für die ISO-Kompatibilität bereit. Weitere Informationen finden Sie unter [Data Type Synonyms &#40;Transact-SQL&#41; (Synonyme für Datentypen &#40;Transact-SQL&#41;)](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
## <a name="data-type-categories"></a>Datentypkategorien
Datentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind nach den folgenden Kategorien organisiert:
  
:::row:::
    :::column:::
        Genaue numerische Werte
    :::column-end:::
    :::column:::
        Unicode-Zeichenfolgen
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        Ungefähre numerische Werte
    :::column-end:::
    :::column:::
        Binärzeichenfolgen
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        Datum und Uhrzeit
    :::column-end:::
    :::column:::
        Andere Datentypen
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        Zeichenfolgen
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
 
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind einige Datentypen aufgrund ihrer Speichermerkmale als den folgenden Gruppen zugehörig definiert:
-   Datentypen für große Werte: **varchar(max)** und **nvarchar(max)**  
-   Datentypen für große Objekte: **text**, **ntext**, **image**, **varbinary(max)** und **xml**  
  
    > [!NOTE]  
    >  „sp_help“ gibt –1 als Länge für Datentypen mit hohen Werten und **xml**-Datentypen zurück.  
  
### <a name="exact-numerics"></a>Genaue numerische Werte
  
:::row:::
    :::column:::
        [bigint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)
    :::column-end:::
    :::column:::
        [numeric](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [bit](../../t-sql/data-types/bit-transact-sql.md)
    :::column-end:::
    :::column:::
        [smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [decimal](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)
    :::column-end:::
    :::column:::
        [smallmoney](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)
    :::column-end:::
    :::column:::
        [tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [money](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

### <a name="approximate-numerics"></a>Ungefähre numerische Werte
  
:::row:::
    :::column:::
        [float](../../t-sql/data-types/float-and-real-transact-sql.md)
    :::column-end:::
    :::column:::
        [real](../../t-sql/data-types/float-and-real-transact-sql.md)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

### <a name="date-and-time"></a>Datum und Uhrzeit
  
:::row:::
    :::column:::
        [date](../../t-sql/data-types/date-transact-sql.md)
    :::column-end:::
    :::column:::
        [datetimeoffset](../../t-sql/data-types/datetimeoffset-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [datetime2](../../t-sql/data-types/datetime2-transact-sql.md)
    :::column-end:::
    :::column:::
        [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [datetime](../../t-sql/data-types/datetime-transact-sql.md)
    :::column-end:::
    :::column:::
        [time](../../t-sql/data-types/time-transact-sql.md)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
  
### <a name="character-strings"></a>Zeichenfolgen
  
:::row:::
    :::column:::
        [char](../../t-sql/data-types/char-and-varchar-transact-sql.md)
    :::column-end:::
    :::column:::
        [varchar](../../t-sql/data-types/char-and-varchar-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [text](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
 
### <a name="unicode-character-strings"></a>Unicode-Zeichenfolgen
  
:::row:::
    :::column:::
        [nchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)
    :::column-end:::
    :::column:::
        [nvarchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [ntext](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
  

### <a name="binary-strings"></a>Binärzeichenfolgen
  
:::row:::
    :::column:::
        [binary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)
    :::column-end:::
    :::column:::
        [varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [image](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

### <a name="other-data-types"></a>Andere Datentypen

:::row:::
    :::column:::
        [Cursor](../../t-sql/data-types/cursor-transact-sql.md)
    :::column-end:::
    :::column:::
        [rowversion](../../t-sql/data-types/rowversion-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [hierarchyid](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
    :::column-end:::
    :::column:::
        [uniqueidentifier](../../t-sql/data-types/uniqueidentifier-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [sql_variant](../../t-sql/data-types/sql-variant-transact-sql.md)
    :::column-end:::
    :::column:::
        [xml](../../t-sql/xml/xml-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [Räumliche Geometrietypen](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md) 
    :::column-end:::
    :::column:::
        [Räumliche Geografietypen](../../t-sql/spatial-geography/spatial-types-geography.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [Tabelle](../../t-sql/data-types/table-transact-sql.md) 
    :::column-end:::
    :::column:::
         
    :::column-end:::
:::row-end:::

  
## <a name="see-also"></a>Weitere Informationen
[CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)
[EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)  
[Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Functions &#40;Transact-SQL&#41; (Funktionen (Transact-SQL))](../../t-sql/functions/functions.md)  
[LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)  
[sp_droptype &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)  
[sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)  
[sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)
  
  
