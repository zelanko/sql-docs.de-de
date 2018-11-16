---
title: FREETEXTTABLE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- FREETEXTTABLE_TSQL
- FREETEXTTABLE
dev_langs:
- TSQL
helpviewer_keywords:
- search conditions [SQL Server], meaning matches
- meaning matches [full-text search]
- FREETEXTTABLE function (Transact-SQL)
- ranked results [full-text search]
- column searches [full-text search]
ms.assetid: 4523ae15-4260-40a7-a53c-8df15e1fee79
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 466954dd9909b860957bce6a292346bec4f4af9c
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657360"
---
# <a name="freetexttable-transact-sql"></a>FREETEXTTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ist eine Funktion der [FROM-Klausel](../../t-sql/queries/from-transact-sql.md) von einer [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT-Anweisung Ausführen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Volltextsuche Volltext-indizierte Spalten mit zeichenbasierten Datentypen. Diese Funktion gibt eine Tabelle mit 0 (null), einer oder mehreren Zeilen für alle Spalten mit Werten, die die Bedeutung und nicht nur dem genauen Wortlaut des Texts in der angegebenen entsprechen *Freetext_string*. Auf FREETEXTTABLE wird wie auf einen regulären Tabellennamen verwiesen.  
  
 FREETEXTTABLE eignet sich für unterschiedliche Arten von Spielen als das [FREETEXT &#40;Transact-SQL-&#41;](../../t-sql/queries/freetext-transact-sql.md),  
  
 Abfragen, die FREETEXTTABLE verwenden, geben für jede Zeile einen Relevanzrangfolgenwert (Relevance Ranking Value, RANK) und einen Volltextschlüssel (KEY) zurück.  
  
> [!NOTE]  
>  Informationen zu den Formen der Volltextsuche, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt werden, finden Sie unter [Abfragen mit Volltextsuche](../../relational-databases/search/query-with-full-text-search.md).  
  
(https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FREETEXTTABLE (table , { column_name | (column_list) | * }   
          , 'freetext_string'   
     [ , LANGUAGE language_term ]   
     [ , top_n_by_rank ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *table*  
 Der Name der Tabelle, die für Volltextabfragen markiert wurde. *Tabelle* oder *Ansicht*kann ein, zwei oder drei Datenbank-Objektnamen. Bei der Abfrage einer Sicht kann nur eine volltextindizierte Basistabelle verwendet werden.  
  
 *Tabelle* kann keinen Servernamen angeben und nicht in Abfragen auf Verbindungsservern verwendet werden.  
  
 *column_name*  
 Der Name einer oder mehrerer volltextindizierten Spalten der in der FROM-Klausel angegebenen Tabelle. Die Spalten können vom Typ **char**, **varchar**, **nchar**, **nvarchar**, **text**, **ntext**, **image**, **xml**, **varbinary** oder **varbinary(max)** sein.  
  
 *column_list*  
 Gibt an, dass verschiedene, durch Trennzeichen getrennte Spalten angegeben werden können. *column_list* muss in Klammern stehen. Sofern nicht *language_term* angegeben ist, muss die Sprache aller Spalten von *column_list* identisch sein.  
  
 \*  
 Gibt an, dass alle für die Volltextsuche registrierten Spalten nach dem angegebenen *freetext_string*-Wert durchsucht werden. Es sei denn, *Language_term* angegeben ist, wird die Sprache aller Volltext-indizierte Spalten in der Tabelle muss identisch sein.  
  
 *freetext_string*  
 Der Text, nach dem in *column_name* gesucht werden soll. Es kann hierbei ein beliebiger Text aus Wörtern, Ausdrücken und Sätzen eingegeben werden. Übereinstimmungen werden dann generiert, wenn ein Begriff oder Formen eines Begriffs im Volltextindex gefunden werden.  
  
 Im Gegensatz zu suchen, in der CONTAINS Suchbedingung, in und ein Schlüsselwort ist, bei der Verwendung in *Freetext_string* das Wort 'und' gilt als Füllwort oder [Stoppwort](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md), und werden verworfen.  
  
 Die Verwendung von WEIGHT, FORMSOF, Platzhaltern, NEAR und anderer Syntax ist nicht zulässig. Für *freetext_string* wird eine Worttrennung durchgeführt, und die Wörter werden auf den Stamm zurückgeführt und durchlaufen den Thesaurus.  
  
 LANGUAGE *language_term*  
 Die Sprache, deren Ressourcen für die Wörtertrennung, die Wortstammerkennung und den Thesaurus sowie die Entfernung von Stoppwörtern in der Abfrage verwendet werden. Dieser Parameter ist optional und kann als Zeichenfolge, ganze Zahl oder Hexadezimalwert entsprechend dem Gebietsschemabezeichner (Locale Identifier – LCID) einer Sprache angegeben werden. Wird *language_term* angegeben, wird die entsprechende Sprache auf alle Elemente der Suchbedingung angewendet. Wird kein Wert angegeben, wird die Volltextsprache der Spalte verwendet.  
  
 Wenn Dokumente anderer Sprachen zusammen als BLOBs (Binary Large Objects) in einer einzelnen Spalte gespeichert werden, legt der Gebietsschemabezeichner (LCID) eines bestimmten Dokuments die zur Indizierung seines Inhalts zu verwendende Sprache fest. Beim Abfragen einer solchen Spalte kann die Angabe von *LANGUAGE**language_term* die Wahrscheinlichkeit einer hohen Übereinstimmung steigern.  
  
 In Form einer Zeichenfolge entspricht *language_term* dem Wert der **alias**-Spalte in der [sys.syslanguages &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)-Kompatibilitätssicht.  Die Zeichenfolge muss in einfache Anführungszeichen gesetzt werden, z.B. '*language_term*'. In Form einer ganzen Zahl ist *language_term* der eigentliche Gebietsschemabezeichner, der die Sprache identifiziert. In Form eines Hexadezimalwerts ist *language_term* gleich 0x, gefolgt vom Hexadezimalwert des Gebietsschemabezeichners. Der Hexadezimalwert darf acht Ziffern nicht überschreiten, einschließlich führender Nullen.  
  
 Wird der Wert im Format Doppelbyte-Zeichensatz (Double-Byte Character Set, DBCS) angegeben, wird er von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Unicode konvertiert.  
  
 Ist die angegebene Sprache ungültig oder sind keine Ressourcen installiert, die dieser Sprache entsprechen, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Fehler zurück. Geben Sie 0x0 als *language_term* an, um neutrale Sprachressourcen zu verwenden.  
  
 *top_n_by_rank*  
 Gibt an, dass nur die *n*höchsten Rang entspricht in absteigender Reihenfolge zurückgegeben. Gilt nur, wenn ein Ganzzahlwert *n*, angegeben wird. Wenn *top_n_by_rank* mit anderen Parametern kombiniert wird, werden von der Abfrage möglicherweise weniger Zeilen zurückgegeben als die Anzahl von Zeilen, die mit allen Prädikaten übereinstimmen. *Top_n_by_rank* lässt sich die abfrageleistung zu erhöhen, indem Sie nur die relevantesten Treffer erneut aufrufen.  
  
## <a name="remarks"></a>Hinweise  
 Volltextprädikate und -funktionen gelten für eine einzelne Tabelle, die im FROM-Prädikat enthalten ist. Um eine Suche in mehreren Tabellen auszuführen, können Sie eine verknüpfte Tabelle in der FROM-Klausel verwenden, um in einem Resultset zu suchen, das aus mindestens zwei Tabellen erstellt wird.  
  
 FREETEXTTABLE verwendet die gleichen Suchbedingungen wie das FREETEXT-Prädikat.  
  
 Die zurückgegebene Tabelle besitzt wie CONTAINSTABLE, Spalten **Schlüssel** und **Rang**, die in der Abfrage und die entsprechenden Zeilen der Zeile Werte ranking verwiesen.  
  
## <a name="permissions"></a>Berechtigungen  
 FREETEXTTABLE kann nur von Benutzern aufgerufen werden, die entsprechende SELECT-Berechtigungen für die angegebene Tabelle oder die referenzierten Spalten der Tabelle besitzen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-simple-example"></a>A. Einfaches Beispiel  
 Im folgende Beispiel erstellt und füllt eine Tabelle zwei Spalten mit 3 Landkreise und Farben in ihren Flags. It erstellt und füllt einen Volltextkatalog und Index für die Tabelle. Die **FREETEXTTABLE** Syntax veranschaulicht.  
  
```  
CREATE TABLE Flags (Country nvarchar(30) NOT NULL, FlagColors varchar(200));  
CREATE UNIQUE CLUSTERED INDEX FlagKey ON Flags(Country);  
INSERT Flags VALUES ('France', 'Blue and White and Red');  
INSERT Flags VALUES ('Italy', 'Green and White and Red');  
INSERT Flags VALUES ('Tanzania', 'Green and Yellow and Black and Yellow and Blue');  
SELECT * FROM Flags;  
GO  
  
CREATE FULLTEXT CATALOG TestFTCat;  
CREATE FULLTEXT INDEX ON Flags(FlagColors) KEY INDEX FlagKey ON TestFTCat;  
GO   
  
SELECT * FROM Flags;  
SELECT * FROM FREETEXTTABLE (Flags, FlagColors, 'Blue');  
SELECT * FROM FREETEXTTABLE (Flags, FlagColors, 'Yellow');  
```  
  
### <a name="b-using-freetext-in-an-inner-join"></a>B. Verwenden von FREETEXT in einem INNER JOIN  
 Im folgenden Beispiel werden der Kategoriename und die Beschreibung aller Kategorien zurückgegeben, die sich auf `sweet`, `candy`, `bread`, `dry` oder `meat` beziehen.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Description  
    ,KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL   
    INNER JOIN FREETEXTTABLE(Production.ProductDescription,  
    Description,   
    'high level of performance') AS KEY_TBL  
ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY RANK DESC;  
GO  
```  
  
### <a name="c-specifying-language-and-highest-ranked-matches"></a>C. Angeben der Sprache und der höchsten Übereinstimmungen  
 Im folgenden Beispiel ist identisch, und zeigt die Verwendung von der `LANGUAGE` *Language_term* und *Top_n_by_rank* Parameter.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Description  
    ,KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL   
    INNER JOIN FREETEXTTABLE(Production.ProductDescription,  
    Description,   
    'high level of performance',  
    LANGUAGE N'English', 2) AS KEY_TBL  
ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY RANK DESC;  
GO  
```  
  
> [!NOTE]  
>  Die Sprache *Language_term* Paramete*r* ist nicht erforderlich, verwenden die *Top_n_by_rank* Parameter *.*  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte mit der Volltextsuche](../../relational-databases/search/get-started-with-full-text-search.md)   
 [Erstellen und Verwalten von Volltextkatalogen](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Erstellen und Verwalten von Volltextindizes](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [Abfragen mit Volltextsuche](../../relational-databases/search/query-with-full-text-search.md)   
 [Erstellen von Volltextsuchabfragen &#40;Visual Database Tools&#41;](https://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [Rowset-Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)   
 [Rang vorausberechnen (Serverkonfigurationsoption)](../../database-engine/configure-windows/precompute-rank-server-configuration-option.md)  
  
  
