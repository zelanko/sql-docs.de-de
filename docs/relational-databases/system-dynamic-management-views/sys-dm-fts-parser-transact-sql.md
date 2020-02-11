---
title: sys. dm_fts_parser (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_parser_TSQL
- dm_fts_parser
- dm_fts_parser_TSQL
- sys.dm_fts_parser
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_parser dynamic management function
- troubleshooting [SQL Server], full-text search
ms.assetid: 2736d376-fb9d-4b28-93ef-472b7a27623a
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: fa60c1785e0740dde4bc6b3755dea36db8a5a21a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900917"
---
# <a name="sysdm_fts_parser-transact-sql"></a>sys.dm_fts_parser (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt das endgültige Tokenisierungsergebnis zurück, nachdem eine bestimmte Kombination aus [Wörter](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)Trennung, [Thesaurus](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)und [Stopp Liste](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md) auf eine Eingabe der Abfrage Zeichenfolge angewendet wurde. Das Tokenisierungsergebnis entspricht der Ausgabe der Volltext-Engine für die angegebene Abfragezeichenfolge.  
  
 sys.dm_fts_parser ist eine dynamische Verwaltungsfunktion.  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.dm_fts_parser('query_string', lcid, stoplist_id, accent_sensitivity)  
```  
  
## <a name="arguments"></a>Argumente  
 *query_string*  
 Die zu analysierende Abfrage. *QUERY_STRING* kann eine Zeichen folgen Kette sein, die Syntax Unterstützung [enthält](../../t-sql/queries/contains-transact-sql.md) . Sie können z. B. Flexionsformen, einen Thesaurus und logische Operatoren einschließen.  
  
 *LCID*  
 Gebiets Schema Bezeichner (Locale Identifier, LCID) der Wörter Trennung, der zum *QUERY_STRING der*verwendet werden soll.  
  
 *stoplist_id*  
 ID der Stopp Liste, sofern vorhanden, die von der durch *LCID*identifizierten Wörter Trennung verwendet werden soll. *stoplist_id* ist vom Datentyp **int**. Wenn Sie ' NULL ' angeben, wird keine Stopp Liste verwendet. Wenn Sie 0 angeben, wird die Systemstoppliste STOPLIST verwendet.  
  
 Eine Stopplisten-ID ist innerhalb der Datenbank eindeutig. Verwenden Sie die [sys. fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md) -Katalog Sicht, um die Stopp Listen-ID für einen Volltextindex für eine bestimmte Tabelle abzurufen.  
  
 *accent_sensitivity*  
 Boolescher Wert, mit dem gesteuert wird, ob diakritische Zeichen bei der Volltextsuche berücksichtigt werden. *accent_sensitivity* ist vom **Bit**und weist einen der folgenden Werte auf:  
  
|value|Akzent ist...|  
|-----------|----------------------------|  
|0|Keine Beachtung von Groß-/Kleinschreibung<br /><br /> Wörter wie "Café" und "Café" werden identisch behandelt.|  
|1|Sensibel<br /><br /> Wörter wie "Café" und "Café" werden anders behandelt.|  
  
> [!NOTE]  
>  Um die [!INCLUDE[tsql](../../includes/tsql-md.md)] aktuelle Einstellung dieses Werts für einen voll Text Katalog anzuzeigen, führen Sie die folgende Anweisung aus: `SELECT fulltextcatalogproperty('` *Catalog_Name*`', 'AccentSensitivity');`.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|Schlüsselwort (keyword)|**varbinary (128)**|Die hexadezimale Darstellung eines gegebenen Schlüsselworts, das von einer Wörtertrennung zurückgegeben wurde. Diese Darstellung wird zum Speichern des Schlüsselworts im Volltextindex verwendet. Dieser Wert ist nicht Menschen lesbar, aber es ist hilfreich, ein bestimmtes Schlüsselwort mit der Ausgabe zu verknüpfen, die von anderen dynamischen Verwaltungs Sichten zurückgegeben wird, die den Inhalt eines voll Text Indexes zurückgeben, wie z [. b. sys. dm_fts_index_keywords](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md) und [sys. dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md).<br /><br /> **Hinweis:** OxFF stellt das Sonderzeichen dar, das das Ende einer Datei oder eines Datasets angibt.|  
|group_id|**int**|Enthält einen ganzzahligen Wert, mit dem die logische Gruppe unterschieden werden kann, aus der ein gegebener Begriff generiert wurde. Beispiel: Mit '`Server AND DB OR FORMSOF(THESAURUS, DB)"`' werden die folgenden group_id-Werte auf Englisch ausgegeben:<br /><br /> 1: Server<br />2: DB<br />3: DB|  
|phrase_id|**int**|Enthält einen ganzzahligen Wert, der zur Unterscheidung der Fälle dient, in denen alternative Formen für zusammengesetzte Wörter (z. B. "full-text") von der Wörtertrennung ausgegeben werden. Wenn zusammengesetzte Wörter vorhanden sind (z. B. 'multi-millon'), gibt die Wörtertrennung u. U. alternative Formen aus. Diese alternativen Formen (Ausdrücke) müssen in einigen Fällen unterschieden werden.<br /><br /> Beispiel: Mit '`multi-million`' werden die folgenden phrase_id-Werte auf Englisch ausgegeben:<br /><br /> 1 für`multi`<br />1 für`million`<br />2 für`multimillion`|  
|occurrence|**int**|Gibt die Reihenfolge der einzelnen Begriffe im Analyseergebnis an. Beispiel: Für den Ausdruck "`SQL Server query processor`" enthält die Spalte occurrence die folgenden Vorkommenwerte auf Englisch:<br /><br /> 1 für`SQL`<br />2 für`Server`<br />3 für`query`<br />4 für`processor`|  
|special_term|**nvarchar(4000)**|Enthält Informationen über die Eigenschaften des Begriffs, der von der Wörtertrennung ausgegeben wird. Hierbei gibt es folgende Möglichkeiten:<br /><br /> Genaue Übereinstimmung<br /><br /> Noise word (Füllwort)<br /><br /> End of Sentence (Ende des Satzes)<br /><br /> End of paragraph (Ende des Absatzes)<br /><br /> End of Chapter (Ende des Kapitels)|  
|display_term|**nvarchar(4000)**|Enthält die Klartextform des Schlüsselworts. Wie bei den Funktionen für den Zugriff auf den Inhalt des Volltextindexes stimmt der angezeigte Begriff aufgrund der Denormalisierungsgrenze u. U. nicht mit dem ursprünglichen Begriff überein. In der Regel ist er jedoch so genau, dass Sie ihn anhand der ursprünglichen Eingabe identifizieren können.|  
|expansion_type|**int**|Enthält Informationen über die Beschaffenheit der Erweiterung eines gegebenen Begriffs. Hierbei gibt es folgende Möglichkeiten:<br /><br /> 0 = einzelnes Wort, Schreibweise<br /><br /> 2 = Flexionserweiterung<br /><br /> 4 = Thesauruserweiterung/-ersetzung<br /><br /> Nehmen Sie beispielsweise an, dass der Thesaurus "run" als Erweiterung von `jog` definiert:<br /><br /> `<expansion>`<br /><br /> `<sub>run</sub>`<br /><br /> `<sub>jog</sub>`<br /><br /> `</expansion>`<br /><br /> Der Begriff `FORMSOF (FREETEXT, run)` generiert die folgende Ausgabe:<br /><br /> 
  `run` (expansion_type=0)<br /><br /> 
  `runs` (expansion_type=2)<br /><br /> 
  `running` (expansion_type=2)<br /><br /> 
  `ran` (expansion_type=2)<br /><br /> 
  `jog` (expansion_type=4)|  
|source_term|**nvarchar(4000)**|Der Begriff bzw. der Ausdruck, auf dessen Basis ein gegebener Begriff generiert wurde. Beispiel: Aus der Abfrage von '"`word breakers" AND stemmers'` ergeben sich die folgenden source_term-Werte auf Englisch:<br /><br /> `word breakers`für den display_term`word`<br />`word breakers`für den display_term`breakers`<br />`stemmers`für den display_term`stemmers`|  
  
## <a name="remarks"></a>Bemerkungen  
 **sys. dm_fts_parser** unterstützt die Syntax und Features von voll Text Prädikaten, wie z. b. " [enthält](../../t-sql/queries/contains-transact-sql.md) " und "frei [Text](../../t-sql/queries/freetext-transact-sql.md)", sowie Funktionen wie " [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) " und " [fretexfähige](../../relational-databases/system-functions/freetexttable-transact-sql.md)".  
  
## <a name="using-unicode-for-parsing-special-characters"></a>Verwenden von Unicode zum Analysieren von Sonderzeichen  
 Wenn Sie eine Abfrage Zeichenfolge analysieren, verwendet **sys. dm_fts_parser** die Sortierung der Datenbank, mit der Sie verbunden sind, es sei denn, Sie geben die Abfrage Zeichenfolge als Unicode an. Daher kann die Ausgabe für eine nicht-Unicode-Zeichenfolge, die Sonderzeichen enthält, wie z. b. "ü" oder "ç", abhängig von der Sortierung der Datenbank unerwartet ausfallen. Um eine Abfrage Zeichenfolge unabhängig von der Daten Bank Sortierung zu verarbeiten, stellen `N`Sie die Zeichenfolge `N'`mit dem Präfix *QUERY_STRING*`'`.  
  
 Weitere Informationen finden Sie unter "C. Anzeigen der Ausgabe einer Zeichenfolge mit Sonderzeichen" später in diesem Thema.  
  
## <a name="when-to-use-sysdm_fts_parser"></a>Verwendung von 'sys.dm_fts_parser'  
 **sys. dm_fts_parser** kann für Debuggingzwecke sehr leistungsstark sein. Die wichtigsten Verwendungsszenarios sind:  
  
-   Verdeutlichung der Funktionsweise der Wörtertrennung bei einer gegebenen Eingabe  
  
     Wenn bei einer Abfrage unerwartete Ergebnisse zurückgegeben werden, kann dies an der Analyse und Trennung der Daten durch die Wörtertrennung liegen. Mit sys.dm_fts_parser können Sie das Ergebnis ermitteln, das eine Wörtertrennung an den Volltextindex übergibt. Außerdem können Sie sehen, bei welchen Begriffen es sich um Stoppwörter handelt, die im Volltextindex nicht gesucht werden. Ob ein Begriff ein Stoppwort für eine bestimmte Sprache ist, hängt davon ab, ob es sich in der durch den *stoplist_id* Wert angegebenen Stopp Liste befindet, die in der Funktion deklariert ist.  
  
     Beachten Sie auch die Einstellung für die Unterscheidung nach Akzent, die dem Benutzer ermöglicht, unter Berücksichtigung dieser Einstellung zu ermitteln, wie die Wörtertrennung die Eingabe analysiert.  
  
-   Verdeutlichung der Funktionsweise der Wortstammerkennung bei einer gegebenen Eingabe  
  
     Sie können ermitteln, wie ein Abfrageausdruck und seine Stammformen von der Wörtertrennung und der Wortstammerkennung analysiert werden, indem Sie eine CONTAINS- oder eine CONTAINSTABLE-Abfrage mit der folgenden FORMSOF-Klausel angeben:  
  
    ```  
    FORMSOF( INFLECTIONAL, query_term )  
    ```  
  
     Anhand der Ergebnisse können Sie sehen, welche Begriffe an den Volltextindex übergeben werden.  
  
-   Verdeutlichung der Erweiterung bzw. Ersetzung der gesamten oder eines Teils der Eingabe durch den Thesaurus  
  
     Sie können auch Folgendes angeben:  
  
    ```  
    FORMSOF( THESAURUS, query_term )  
    ```  
  
     Die Ergebnisse dieser Abfrage veranschaulichen die Interaktion der Wörtertrennung und des Thesaurus für den Abfrageausdruck. Sie können den Ausdruck oder die Ersetzungen im Thesaurus anzeigen und die resultierende Abfrage identifizieren, die tatsächlich für den Volltextindex verwendet wird.  
  
     Der Benutzer kann auch Folgendes angeben:  
  
    ```  
    FORMSOF( FREETEXT, query_term )  
    ```  
  
     Die Flexions- und Thesaurusfunktionen werden automatisch ausgeführt.  
  
 Des Weiteren ist sys.dm_fts_parser eine nützliche Hilfe, um viele andere Probleme bei Volltextabfragen zu verstehen und zu beheben.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** und die Zugriffsrechte auf die angegebene Stopp Liste.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-the-output-of-a-given-word-breaker-for-a-keyword-or-phrase"></a>A. Anzeigen der Ausgabe einer angegebenen Wörtertrennung für ein Schlüsselwort oder einen Ausdruck  
 Für die Ausgabe des folgenden Beispiels wurden die Wörtertrennung für Englisch mit der LCID 1033 und keine Stoppliste auf die folgende Abfragezeichenfolge angewendet:  
  
 `The Microsoft business analysis`  
  
 Die Unterscheidung nach Akzent ist deaktiviert.  
  
```sql
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis" ', 1033, 0, 0);  
```  
  
### <a name="b-displaying-the-output-of-a-given-word-breaker-in-the-context-of-stoplist-filtering"></a>B. Anzeigen der Ausgabe einer angegebenen Wörtertrennung im Kontext der Stopplistenfilterung  
 Für die Ausgabe des folgenden Beispiels wurden die Wörtertrennung für Englisch mit der LCID 1033 und eine Stoppliste für Englisch mit der ID 77 auf die folgende Abfragezeichenfolge angewendet:  
  
 `"The Microsoft business analysis" OR "MS revenue"`  
  
 Die Unterscheidung nach Akzent ist deaktiviert.  
  
```sql
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis"  OR " MS revenue" ', 1033, 77, 0);  
```  
  
### <a name="c-displaying-the-output-of-a-string-that-contains-special-characters"></a>C. Anzeigen der Ausgabe einer Zeichenfolge mit Sonderzeichen  
 Im folgenden Beispiel wird Unicode verwendet, um die folgende französische Zeichenfolge zu analysieren:  
  
 `français`  
  
 Das Beispiel gibt die LCID für die französische Sprache, `1036`, und die ID einer benutzerdefinierten Stoppliste, `5` an. Die Unterscheidung nach Akzent ist aktiviert.  
  
```sql
SELECT * FROM sys.dm_fts_parser(N'français', 1036, 5, 1);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten und Funktionen für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Voll Text Suche](../../relational-databases/search/full-text-search.md)   
 [Konfigurieren und Verwalten von Wörter Trennungen und Wort Stamm Erkennungen für die Suche](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Konfigurieren und Verwalten von Thesaurusdateien für die voll Text Suche](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Abfragen mit voll Text Suche](../../relational-databases/search/query-with-full-text-search.md)   
 [Abfragen mit voll Text Suche](../../relational-databases/search/query-with-full-text-search.md)   
 [Sicherungsfähige Elemente](../../relational-databases/security/securables.md)  
  
  
