---
title: Sortierung und Unicode-Unterstützung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/18/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- binary collations [SQL Server]
- expression-level collations [SQL Server]
- Windows collations [SQL Server]
- globalization [SQL Server], about globalization
- supplementary character support
- code pages [SQL Server], about code pages
- collations [SQL Server], about collations
- Unicode [SQL Server], collations
- database-level collations [SQL Server]
- reading order
- column-level collations
- locales [SQL Server], about locales
- locales [SQL Server]
- code pages [SQL Server]
- SQL Server collations
- UTF-8
- UTF-16
- UTF8
- UTF16
- UCS2
- server-level collations [SQL Server]
ms.assetid: 92d34f48-fa2b-47c5-89d3-a4c39b0f39eb
author: pmasl
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 515e0501e86d81a34cd9e0f14d720ba3024b241c
ms.sourcegitcommit: 1c3f56deaa4c1ffbe5d7f75752ebe10447c3e7af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251092"
---
# <a name="collation-and-unicode-support"></a>Collation and Unicode Support
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Sortierungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bieten Sortierregeln und die Berücksichtigung von Groß-/Kleinschreibung und Akzenten für die Daten. Sortierungen, die mit Zeichendatentypen wie **char** und **varchar** verwendet werden, geben die Codeseite und die entsprechenden Zeichen vor, die für den jeweiligen Datentyp dargestellt werden können. Bei der Installation einer neuen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], bei der Wiederherstellung einer Datenbanksicherung oder bei der Verbindung von Servern mit Clientdatenbanken ist es wichtig, dass Sie die Gebietsschemaanforderungen, die Sortierreihenfolge und das Verhalten in Bezug auf die Groß-/Kleinschreibung und Akzente der Daten kennen, mit denen Sie arbeiten. Informationen zum Auflisten von Sortierungen, die in Ihrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz verfügbar sind, finden Sie unter [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md).    
    
Wenn Sie eine Sortierung für den Server, die Datenbank, die Spalte oder den Ausdruck auswählen, weisen Sie den Daten bestimmte Merkmale zu, die Auswirkungen auf die Ergebnisse vieler Datenbankvorgänge haben. Wenn Sie beispielsweise eine Abfrage mit `ORDER BY` erstellen, kann die Sortierreihenfolge des Resultsets von der Sortierung abhängen, die für die Datenbank gilt oder die in einer `COLLATE`-Klausel auf Ausdrucksebene der Abfrage vorgegeben ist.    
    
Zur optimalen Verwendung der Sortierungsunterstützung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist es erforderlich, die in diesem Thema beschriebenen Begriffe zu verstehen und zu wissen, wie sie mit den Eigenschaften der Daten in Zusammenhang stehen.    
    
##  <a name="Terms"></a> Sortierungsbegriffe    
    
-   [Sortierung](#Collation_Defn) 

    - [Sortierungssätze](#Collation_sets)
    
    - [Sortierungsebenen](#Collation_levels)
    
-   [Gebietsschema](#Locale_Defn)    
    
-   [Codepage](#Code_Page_Defn)    
    
-   [Sortierreihenfolge](#Sort_Order_Defn)    
    
###  <a name="Collation_Defn"></a> Sortierung    
Eine Sortierung gibt die Bitmuster an, die die jeweiligen Zeichen in einem Datensatz darstellen. Sortierungen legen außerdem die Regeln fest, nach denen Daten sortiert und verglichen werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt das Speichern von Objekten mit verschiedenen Sortierungen in einer Datenbank. Bei Nicht-Unicode-Spalten gibt die Sortierungseinstellung die Codepage für die Daten und die Zeichen an, die dargestellt werden können. Daten, die zwischen Nicht-Unicode-Spalten verschoben werden, müssen jedoch von der Quellcodepage in die Zielcodepage konvertiert werden.    
    
[!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungsergebnisse können unterschiedlich sein, wenn die Anweisung im Kontext verschiedener Datenbanken ausgeführt wird, die jeweils andere Sortierungseinstellungen haben. Wenn möglich, sollte in Unternehmen eine standardisierte Sortierung verwendet werden. Auf diese Weise müssen Sie die Sortierung nicht explizit für jedes Zeichen oder jeden Unicode-Ausdruck angeben. Bei Objekten mit abweichenden Sortierungs- oder Codepageeinstellungen codieren Sie Ihre Abfragen so, dass diese den Regeln der Sortierungspriorität entsprechen. Weitere Informationen finden Sie unter [Rangfolge der Sortierungen (Transact-SQL)](../../t-sql/statements/collation-precedence-transact-sql.md).    
    
Die einer Sortierung zugeordneten Optionen sind die Berücksichtigung von Groß-/Kleinschreibung, Akzenten, Kana, Breite und Variierungsauswahlzeichen. [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] führt eine zusätzliche Option für die [UTF-8](https://www.wikipedia.org/wiki/UTF-8)-Codierung ein. Diese Optionen werden angegeben, indem sie an den Sortierungsnamen angefügt werden. Beispiel: Bei der Sortierung `Japanese_Bushu_Kakusu_100_CS_AS_KS_WS_UTF8` wird nach Groß-/Kleinschreibung, Akzent, Kana und Breite unterschieden, und die Sortierung verwendet die UTF-8-Codierung. Im Gegensatz dazu berücksichtigt die Sortierung `Japanese_Bushu_Kakusu_140_CI_AI_KS_WS_VSS` Groß-/Kleinschreibung und Akzente nicht, wohl aber Kana, Breite und Variierungsauswahlzeichen, und sie verwendet eine Nicht-Unicode-Codierung. In der folgenden Tabelle wird das den verschiedenen Optionen zugeordnete Verhalten beschrieben.    
    
|Option|und Beschreibung|    
|------------|-----------------|    
|Unterscheidung nach Groß-/Kleinschreibung (\_CS)|Unterscheidet zwischen Groß- und Kleinbuchstaben. Wenn diese Option ausgewählt ist, stehen Kleinbuchstaben in der Sortierreihenfolge vor ihren entsprechenden Großbuchstaben. Wenn diese Option nicht aktiviert wird, wird bei der Sortierung die Groß- und Kleinschreibung nicht berücksichtigt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] betrachtet also beim Sortieren die groß- und die kleingeschriebenen Versionen von Buchstaben als identisch. Sie können die Nichtunterscheidung nach Groß-/Kleinbuchstaben durch Angeben von „\_CI“ explizit auswählen.|    
|Unterscheidung nach Akzent (\_AS)|Unterscheidet zwischen Zeichen mit Akzent und Zeichen ohne Akzent. Beispielsweise ist 'a' nicht mit 'ấ' identisch. Wenn diese Option nicht aktiviert wird, wird bei der Sortierung nicht nach Akzent unterschieden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] betrachtet also beim Sortieren die Versionen von Buchstaben mit und ohne Akzent als identisch. Sie können die Nichtunterscheidung nach Akzent durch Angeben von „\_AI“ explizit auswählen.|    
|Unterscheidung nach Kana (\_KS)|Unterscheidet zwischen zwei japanischen Kana-Zeichen: Hiragana und Katakana. Wenn diese Option nicht aktiviert wird, wird bei der Sortierung Kana nicht beachtet. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] betrachtet also beim Sortieren Hiragana- und Katakana-Zeichen als identisch. Das Weglassen dieser Option ist die einzige Möglichkeit, die Nichtbeachtung von Kana anzugeben.|    
|Unterscheidung nach Breite (\_WS)|Unterscheidet zwischen Zeichen halber Breite und Zeichen normaler Breite. Wenn diese Option nicht ausgewählt ist, betrachtet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beim Sortieren die Darstellung in halber Breite und in normaler Breite desselben Zeichens als identisch. Das Weglassen dieser Option ist die einzige Möglichkeit, die Nichtbeachtung der Breite anzugeben.|    
|Mit Unterscheidung nach Variierungsauswahlzeichen (\_VSS)|Unterscheidet zwischen verschiedenen Variierungsauswahlzeichen für Ideogramme in den japanischen Sortierungen **Japanese_Bushu_Kakusu_140** und **Japanese_XJIS_140**, die in [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] eingeführt wurden. Eine Variierungssequenz besteht aus einem Basiszeichen plus einem ergänzenden Variierungsauswahlzeichen. Wenn diese \_VSS-Option nicht aktiviert ist, berücksichtigt die Sortierung die Variierung nicht, und das Variierungsauswahlzeichen wird im Vergleich nicht berücksichtigt. Das bedeutet, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeichen, die auf dem gleichen Basiszeichen aufbauen, aber verschiedene Variierungsauswahlzeichen aufweisen, für Sortierungszwecke als identisch betrachtet. Weitere Informationen enthält auch die [Unicode Ideographic Variation Database (Unicode-Datenbank der Ideogrammvariierungen)](https://www.unicode.org/reports/tr37/).<br/><br/> Variierungsauswahlzeichen unterstützende Sortierungen (\_VSS) werden in Indizes für die Volltextsuche nicht unterstützt. Indizes für die Volltextsuche unterstützen nur Optionen für die Unterscheidung nach Akzent (\_AS), Kana (\_KS) und Breite (\_WS). Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML- und CLR-Engines unterstützen keine Variierungsauswahlzeichen (\_VSS).|      
|Binär (\_BIN) <sup>1</sup>|Sortiert und vergleicht Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabellen basierend auf den für jedes Zeichen definierten Bitmustern. Die binäre Sortierreihenfolge unterscheidet nach Groß- und Kleinschreibung und nach Akzent. Die Option Binär ist zudem die schnellste Sortierreihenfolge. Weitere Informationen finden Sie im Abschnitt [Binäre Sortierungen](#Binary-collations) dieses Artikels.|      
|Binärcodepunkt (\_BIN2) <sup>1</sup> | Sortiert und vergleicht Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabellen basierend auf Unicode-Codepunkten für Unicode-Daten. Für Nicht-Unicode-Daten verwendet der Binär-Codepunkt Vergleiche, die mit binären Sortierungen identisch sind.<br/><br/> Der Vorteil beim Verwenden einer Binär-Codepunkt-Sortierreihenfolge liegt darin, dass in Anwendungen, die sortierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Daten vergleichen, eine Neusortierung der Daten nicht erforderlich ist. Folglich ermöglicht eine Binär-Codepunkt-Sortierreihenfolge eine einfachere Entwicklung von Anwendungen und eine Steigerung der Leistung. Weitere Informationen finden Sie im Abschnitt [Binäre Sortierungen](#Binary-collations) dieses Artikels.|
|UTF-8 (\_UTF8)|Ermöglicht das Speichern von mit UTF-8 codierten Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn diese Option nicht ausgewählt ist, verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Nicht-Unicode-Codierungsformat für die entsprechenden Datentypen. Weitere Informationen finden Sie im Abschnitt [Unterstützung für UTF-8](#utf8) dieses Artikels.| 

<sup>1</sup> Wenn „Binär“ oder der Binär-Codepunkt ausgewählt ist, sind die Optionen Unterscheidung nach Groß-/Kleinschreibung (\_CS), Unterscheidung nach Akzent (\_AS), Unterscheidung nach Kana (\_KS) und Unterscheidung nach Breite (\_WS) nicht verfügbar.      

#### <a name="examples-of-collation-options"></a>Beispiele für Sortierungsoptionen
Jede Sortierung setzt sich aus einer Kombination von Suffixen zur Festlegung der Unterscheidung nach Groß-/Kleinschreibung, Akzent, Breite oder Kana zusammen. Die folgenden Beispiele beschreiben das Verhalten der Sortierreihenfolge bei verschiedenen Suffixkombinationen.

|Suffix der Windows-Sortierung|Beschreibung der Sortierreihenfolge|
|------------|-----------------| 
|\_BIN <sup>1</sup>|Binäre Sortierung.|
|\_BIN2 <sup>1</sup> <sup>2</sup>|Binär-Codepunkt-Sortierreihenfolge.|
|\_CI_AI <sup>2</sup>|Keine Unterscheidung nach Groß-/Kleinschreibung, Akzent, Kana und Breite.|
|\_CI_AI_KS <sup>2</sup>|Keine Unterscheidung nach Groß-/Kleinschreibung, Akzent und Breite. Unterscheidung nach Kana.|
|\_CI_AI_KS_WS <sup>2</sup>|Keine Unterscheidung nach Groß-/Kleinschreibung und Akzent. Unterscheidung nach Kana und Breite|
|\_CI_AI_WS <sup>2</sup>|Keine Unterscheidung nach Groß-/Kleinschreibung, Akzent und Kana. Unterscheidung nach Breite.|
|\_CI_AS <sup>2</sup>|Keine Unterscheidung nach Groß-/Kleinschreibung, Kana und Breite. Unterscheidung nach Akzent.|
|\_CI_AS_KS <sup>2</sup>|Keine Unterscheidung nach Groß-/Kleinschreibung und Breite. Unterscheidung nach Akzent und Kana.|
|\_CI_AS_KS_WS <sup>2</sup>|Keine Unterscheidung nach Groß-/Kleinschreibung. Unterscheidung nach Akzent, Kana und Breite.|
|\_CI_AS_WS <sup>2</sup>|Keine Unterscheidung nach Groß-/Kleinschreibung und Kana. Unterscheidung nach Akzent und Breite.|
|\_CS_AI <sup>2</sup>|Keine Unterscheidung nach Akzent, Kana und Breite. Unterscheidung nach Groß-/Kleinschreibung.|
|\_CS_AI_KS <sup>2</sup>|Keine Unterscheidung nach Akzent und Breite. Unterscheidung nach Groß-/Kleinschreibung und Kana.|
|\_CS_AI_KS_WS <sup>2</sup>|Keine Unterscheidung nach Akzent. Unterscheidung nach Groß-/Kleinschreibung, Kana und Breite.|
|\_CS_AI_WS <sup>2</sup>|Keine Unterscheidung nach Akzent und Kana. Unterscheidung nach Groß-/Kleinschreibung und Breite.|
|\_CS_AS <sup>2</sup>|Keine Unterscheidung nach Kana und Breite. Unterscheidung nach Groß-/Kleinschreibung und Akzent.|
|\_CS_AS_KS <sup>2</sup>|Keine Unterscheidung nach Breite. Unterscheidung nach Groß-/Kleinschreibung, Akzent und Kana.|
|\_CS_AS_KS_WS <sup>2</sup>|Unterscheidung nach Groß-/Kleinschreibung, Akzent, Kana und Breite.|
|\_CS_AS_WS <sup>2</sup>|Keine Unterscheidung nach Kana. Unterscheidung nach Groß-/Kleinschreibung, Akzent und Breite.|

<sup>1</sup> Wenn „Binär“ oder der Binär-Codepunkt ausgewählt ist, sind die Optionen Unterscheidung nach Groß-/Kleinschreibung (\_CS), Unterscheidung nach Akzent (\_AS), Unterscheidung nach Kana (\_KS) und Unterscheidung nach Breite (\_WS) nicht verfügbar.    

<sup>2</sup> Durch Hinzufügen der UTF-8-Option (\_ UTF8) können Unicode-Daten mithilfe von UTF-8 codiert werden. Weitere Informationen finden Sie im Abschnitt [Unterstützung für UTF-8](#utf8) dieses Artikels. 

### <a name="Collation_sets"></a> Sortierungssätze

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt die folgenden Sortierungssätze:    

-  [Windows-Sortierreihenfolgen](#Windows-collations)

-  [Binäre Sortierungen](#Binary-collations)

-  [SQL Server-Sortierungen](#SQL-collations)
    
#### <a name="Windows-collations"></a> Windows-Sortierreihenfolgen    
Windows-Sortierungen definieren Regeln zum Speichern von Zeichendaten, die auf dem zugehörigen Windows-Systemgebietsschema basieren. Bei einer Windows-Sortierung wird der Vergleich der Nicht-Unicode-Daten implementiert, indem derselbe Algorithmus wie bei Unicode-Daten verwendet wird. Die grundlegenden Regeln für Windows-Sortierreihenfolgen geben an, welches Alphabet oder welche Sprache verwendet wird, wenn Wörterbuchsortierung angewendet wird. Zudem geben die Regeln die Codepage an, die zum Speichern von Nicht-Unicode-Zeichendaten verwendet wird. Sowohl die Unicode- als auch die Nicht-Unicode-Sortierung sind kompatibel mit Zeichenfolgenvergleichen in einer bestimmten Version von Windows. Dadurch wird die Konsistenz der Datentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht. Außerdem erhalten Entwickler so die Möglichkeit, Zeichenfolgen in ihren Anwendungen mithilfe der gleichen Regeln zu sortieren, die auch in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden. Weitere Informationen finden Sie unter [Name der Windows-Sortierung &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md).    
    
#### <a name="Binary-collations"></a> Binäre Sortierungen    
Binäre Sortierungen sortieren Daten basierend auf der Reihenfolge codierter Werte, die vom Gebietsschema und Datentyp definiert werden. Dabei wird die Groß- und Kleinschreibung beachtet. Eine binäre Sortierung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiert das zu verwendende Gebietsschema sowie die zu verwendende ANSI-Codepage. Dies erzwingt eine binäre Sortierreihenfolge. Da binäre Sortierungen relativ einfach sind, tragen sie dazu bei, die Anwendungsleistung zu verbessern. Bei Nicht-Unicode-Datentypen basieren Datenvergleiche auf den in der ANSI-Codepage definierten Codepunkten. Bei Unicode-Datentypen basieren Datenvergleiche auf den Unicode-Codepunkten. Bei binären Sortierungen von Unicode-Datentypen wird das Gebietsschema bei Datensortierungen nicht berücksichtigt. Beispielsweise führen **Latin_1_General_BIN** und **Japanese_BIN** bei Unicode-Daten zu den gleichen Sortierergebnissen. Weitere Informationen finden Sie unter [Name der Windows-Sortierung &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md).   
    
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gibt es zwei Arten von binären Sortierungen:

-  Frühere **BIN**-Sortierungen, die für Unicode-Daten einen unvollständigen Codepunkt-zu-Codepunkt-Vergleich ausführten. Die früheren binären Sortierungen verglichen die ersten Zeichen als WCHAR und die folgenden byteweise. In einer **BIN** -Sortierung wird nur der erste Buchstabe nach Codepunkt sortiert, die verbleibenden Zeichen werden entsprechend ihren Bytewerten sortiert.

-  Die neueren **BIN2**-Sortierungen, die den reinen Codepunkt-Vergleich implementieren. In einer **BIN2** -Sortierung werden alle Zeichen entsprechend ihren Codepunkten sortiert. Da die Intel Plattform eine Little-Endian-Architektur aufweist, werden Unicode-Zeichen immer mit vertauschten Bytes gespeichert.     
    
#### <a name="SQL-collations"></a> SQL Server-Sortierungen    
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sortierungen (SQL_\*) sind hinsichtlich der Sortierreihenfolge mit älteren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kompatibel. Die Wörterbuch-Sortierungsregeln für Nicht-Unicode-Daten sind nicht kompatibel mit den vom Betriebssystem Windows bereitgestellten Sortierroutinen. Das Sortieren von Unicode-Daten ist jedoch kompatibel mit einer bestimmten Version der Windows-Sortierregeln. Da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sortierungen unterschiedliche Vergleichsregeln für Nicht-Unicode- und Unicode-Daten verwenden, werden bei Vergleichen derselben Daten, je nach dem zugrunde liegenden Datentyp, unterschiedliche Ergebnisse angezeigt. Weitere Informationen finden Sie unter [Name der SQL Server-Sortierung &#40;Transact-SQL&#41;](../../t-sql/statements/sql-server-collation-name-transact-sql.md). 

Die Standardinstallationseinstellung wird während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups durch das Gebietsschema des Betriebssystems bestimmt. Die Sortierung auf Serverebene kann entweder während des Setups geändert werden, oder indem vor der Installation das Gebietsschema des Betriebssystems geändert wird. Die Standardsortierung wird auf die älteste verfügbare Version festgelegt, die den einzelnen Gebietsschemas jeweils zugeordnet ist. Der Grund hierfür ist die Abwärtskompatibilität. Deshalb ist dies nicht immer die empfohlene Sortierung. Um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen optimal zu können, ändern Sie die Standardinstallationseinstellungen für die Verwendung von Windows-Sortierungen. Beispielsweise ist für das Betriebssystem-Gebietsschema **Englisch (USA)** (Codepage 1252) die Standardsortierung während des Setups **SQL_Latin1_General_CP1_CI_AS**, welche in die nächste entsprechende Windows-Sortierung **Latin1_General_100_CI_AS_SC** geändert werden kann.
    
> [!NOTE]    
> Wenn Sie eine englischsprachige Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisieren, können Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sortierungen (SQL_\*) angeben, die mit vorhandenen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kompatibel sein sollen. Da die Standardsortierung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] während des Setups festgelegt wird, geben Sie unbedingt die Sortierungseinstellungen in den folgenden Fällen sorgfältig an:    
>     
> -   Der Anwendungscode ist abhängig vom Verhalten der vorherigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sortierungen.    
> -   Sie müssen Zeichendaten speichern, die mehrere Sprachen wiedergeben.    
    
### <a name="Collation_levels"></a> Sortierungsebenen
Das Festlegen von Sortierungen wird bei einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]für die folgenden Ebenen unterstützt:    

-  [Sortierungen auf Serverebene](#Server-level-collations)

-  [Sortierungen auf Datenbankebene](#Database-level-collations)

-  [Sortierungen auf Spaltenebene](#Column-level-collations)

-  [Sortierungen auf Ausdrucksebene](#Expression-level-collations)

#### <a name="Server-level-collations"></a> Sortierungen auf Serverebene   
Die Standardserversortierung wird während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups festgelegt und außerdem als Standardsortierung der Systemdatenbanken und aller Benutzerdatenbanken vorgegeben. 

In der folgenden Tabelle werden die standardmäßig verwendeten Sortierbezeichnungen angezeigt, die vom Gebietsschema des Betriebssystems bestimmt werden, einschließlich der entsprechenden Windows- und SQL-Sprachcode-IDs (LCID):

|Windows-Gebietsschema|Windows-LCID|SQL-LCID|Standardsortierung|
|---------------|---------|---------|---------------|
|Afrikaans (Südafrika)|0x0436|0x0409|Latin1_General_CI_AS|
|Albanisch (Albanien)|0x041c|0x041c|Albanian_CI_AS|
|Elsässisch (Frankreich)|0x0484|0x0409|Latin1_General_CI_AS|
|Amharisch (Äthiopien)|0x045e|0x0409|Latin1_General_CI_AS|
|Arabisch (Algerien)|0x1401|0x0401|Arabic_CI_AS|
|Arabisch (Bahrain)|0x3c01|0x0401|Arabic_CI_AS|
|Arabisch (Ägypten)|0x0c01|0x0401|Arabic_CI_AS|
|Arabisch (Irak)|0x0801|0x0401|Arabic_CI_AS|
|Arabisch (Jordanien)|0x2c01|0x0401|Arabic_CI_AS|
|Arabisch (Kuwait)|0x3401|0x0401|Arabic_CI_AS|
|Arabisch (Libanon)|0x3001|0x0401|Arabic_CI_AS|
|Arabisch (Libyen)|0x1001|0x0401|Arabic_CI_AS|
|Arabisch (Marokko)|0x1801|0x0401|Arabic_CI_AS|
|Arabisch (Oman)|0x2001|0x0401|Arabic_CI_AS|
|Arabisch (Katar)|0x4001|0x0401|Arabic_CI_AS|
|Arabisch (Saudi-Arabien)|0x0401|0x0401|Arabic_CI_AS|
|Arabisch (Syrien)|0x2801|0x0401|Arabic_CI_AS|
|Arabisch (Tunesien)|0x1c01|0x0401|Arabic_CI_AS|
|Arabisch (Vereinigte Arabische Emirate)|0x3801|0x0401|Arabic_CI_AS|
|Arabisch (Jemen)|0x2401|0x0401|Arabic_CI_AS|
|Armenisch (Armenien)|0x042b|0x0419|Latin1_General_CI_AS|
|Assamisch (Indien)|0x044d|0x044d|Auf Serverebene nicht verfügbar|
|Aserbaidschanisch (Aserbaidschan, kyrillisch)|0x082c|0x082c|Veraltet, auf Serverebene nicht verfügbar|
|Aserbaidschanisch (Aserbaidschan, lateinisch)|0x042c|0x042c|Veraltet, auf Serverebene nicht verfügbar|
|Baschkirisch (Russische Föderation)|0x046d|0x046d|Latin1_General_CI_AI|
|Baskisch (Baskisch)|0x042d|0x0409|Latin1_General_CI_AS|
|Belarussisch (Belarus)|0x0423|0x0419|Cyrillic_General_CI_AS|
|Bangla (Bangladesch)|0x0845|0x0445|Auf Serverebene nicht verfügbar|
|Bangla (Indien)|0x0445|0x0439|Auf Serverebene nicht verfügbar|
|Bosnisch (Bosnien und Herzegowina, kyrillisch)|0x201a|0x201a|Latin1_General_CI_AI|
|Bosnisch (Bosnien und Herzegowina, lateinisch)|0x141a|0x141a|Latin1_General_CI_AI|
|Bretonisch (Frankreich)|0x047e|0x047e|Latin1_General_CI_AI|
|Bulgarisch (Bulgarien)|0x0402|0x0419|Cyrillic_General_CI_AS|
|Katalanisch (Katalanisch)|0x0403|0x0409|Latin1_General_CI_AS|
|Chinesisch (Hongkong SAR, VR China)|0x0c04|0x0404|Chinese_Taiwan_Stroke_CI_AS|
|Chinesisch (Macao SAR)|0x1404|0x1404|Latin1_General_CI_AI|
|Chinesisch (Macau)|0x21404|0x21404|Latin1_General_CI_AI|
|Chinesisch (VRC)|0x0804|0x0804|Chinese_PRC_CI_AS|
|Chinesisch (VRC)|0x20804|0x20804|Chinese_PRC_Stroke_CI_AS|
|Chinesisch (Singapur)|0x1004|0x0804|Chinese_PRC_CI_AS|
|Chinesisch (Singapur)|0x21004|0x20804|Chinese_PRC_Stroke_CI_AS|
|Chinesisch (Taiwan)|0x30404|0x30404|Chinese_Taiwan_Bopomofo_CI_AS|
|Chinesisch (Taiwan)|0x0404|0x0404|Chinese_Taiwan_Stroke_CI_AS|
|Korsisch (Frankreich)|0x0483|0x0483|Latin1_General_CI_AI|
|Kroatisch (Bosnien und Herzegowina, lateinisch)|0x101a|0x041a|Croatian_CI_AS|
|Kroatisch (Kroatien)|0x041a|0x041a|Croatian_CI_AS|
|Tschechisch (Tschechische Republik)|0x0405|0x0405|Czech_CI_AS|
|Dänisch (Dänemark)|0x0406|0x0406|Danish_Norwegian_CI_AS|
|Dari (Afghanistan)|0x048c|0x048c|Latin1_General_CI_AI|
|Divehi (Malediven)|0x0465|0x0465|Auf Serverebene nicht verfügbar|
|Niederländisch (Belgien)|0x0813|0x0409|Latin1_General_CI_AS|
|Niederländisch (Niederlande)|0x0413|0x0409|Latin1_General_CI_AS|
|Englisch (Australien)|0x0c09|0x0409|Latin1_General_CI_AS|
|Englisch (Belize)|0x2809|0x0409|Latin1_General_CI_AS|
|Englisch (Kanada)|0x1009|0x0409|Latin1_General_CI_AS|
|Englisch (Karibik)|0x2409|0x0409|Latin1_General_CI_AS|
|Englisch (Indien)|0x4009|0x0409|Latin1_General_CI_AS|
|Englisch (Irland)|0x1809|0x0409|Latin1_General_CI_AS|
|Englisch (Jamaika)|0x2009|0x0409|Latin1_General_CI_AS|
|Englisch (Malaysia)|0x4409|0x0409|Latin1_General_CI_AS|
|Englisch (Neuseeland)|0x1409|0x0409|Latin1_General_CI_AS|
|Englisch (Philippinen)|0x3409|0x0409|Latin1_General_CI_AS|
|Englisch (Singapur)|0x4809|0x0409|Latin1_General_CI_AS|
|Englisch (Südafrika)|0x1c09|0x0409|Latin1_General_CI_AS|
|Englisch (Trinidad und Tobago)|0x2c09|0x0409|Latin1_General_CI_AS|
|Walisisch (Großbritannien)|0x0809|0x0409|Latin1_General_CI_AS|
|Englisch (USA)|0x0409|0x0409|SQL_Latin1_General_CP1_CI_AS|
|Englisch (Zimbabwe)|0x3009|0x0409|Latin1_General_CI_AS|
|Estnisch (Estland)|0x0425|0x0425|Estonian_CI_AS|
|Färöisch (Färöer-Inseln)|0x0438|0x0409|Latin1_General_CI_AS|
|Philippinisch (Philippinen)|0x0464|0x0409|Latin1_General_CI_AS|
|Finnisch (Finnland)|0x040b|0x040b|Finnish_Swedish_CI_AS|
|Französisch (Belgien)|0x080c|0x040c|French_CI_AS|
|Französisch (Kanada)|0x0c0c|0x040c|French_CI_AS|
|Französisch (Frankreich)|0x040c|0x040c|French_CI_AS|
|Französisch (Luxemburg)|0x140c|0x040c|French_CI_AS|
|Französisch (Monaco)|0x180c|0x040c|French_CI_AS|
|Französisch (Schweiz)|0x100c|0x040c|French_CI_AS|
|Friesisch (Niederlande)|0x0462|0x0462|Latin1_General_CI_AI|
|Galicisch (Spanien)|0x0456|0x0409|Latin1_General_CI_AS|
|Georgisch (Georgien)|0x10437|0x10437|Georgian_Modern_Sort_CI_AS|
|Georgisch (Georgien)|0x0437|0x0419|Latin1_General_CI_AS|
|Deutsch (Telefonbuchsortierung DIN)|0x10407|0x10407|German_PhoneBook_CI_AS|
|Deutsch (Österreich)|0x0c07|0x0409|Latin1_General_CI_AS|
|Deutsch (Deutschland)|0x0407|0x0409|Latin1_General_CI_AS|
|Deutsch (Liechtenstein)|0x1407|0x0409|Latin1_General_CI_AS|
|Deutsch (Luxemburg)|0x1007|0x0409|Latin1_General_CI_AS|
|Deutsch (Schweiz)|0x0807|0x0409|Latin1_General_CI_AS|
|Griechisch (Griechenland)|0x0408|0x0408|Greek_CI_AS|
|Grönländisch (Grönland)|0x046f|0x0406|Danish_Norwegian_CI_AS|
|Gujarati (Indien)|0x0447|0x0439|Auf Serverebene nicht verfügbar|
|Hausa (Nigeria, lateinisch)|0x0468|0x0409|Latin1_General_CI_AS|
|Hebräisch (Israel)|0x040d|0x040d|Hebrew_CI_AS|
|Hindi (Indien)|0x0439|0x0439|Auf Serverebene nicht verfügbar|
|Ungarisch (Ungarn)|0x040e|0x040e|Hungarian_CI_AS|
|Ungarisch (Technische Sortierung)|0x1040e|0x1040e|Hungarian_Technical_CI_AS|
|Isländisch (Island)|0x040f|0x040f|Icelandic_CI_AS|
|Igbo (Nigeria)|0x0470|0x0409|Latin1_General_CI_AS|
|Indonesisch (Indonesien)|0x0421|0x0409|Latin1_General_CI_AS|
|Inuktitut (Kanada, lateinisch)|0x085d|0x0409|Latin1_General_CI_AS|
|Inuktitut (Syllabics) Kanada|0x045d|0x045d|Latin1_General_CI_AI|
|Irisch (Irland)|0x083c|0x0409|Latin1_General_CI_AS|
|Italienisch (Italien)|0x0410|0x0409|Latin1_General_CI_AS|
|Italienisch (Schweiz)|0x0810|0x0409|Latin1_General_CI_AS|
|Japanisch (Japan XJIS)|0x0411|0x0411|Japanese_CI_AS|
|Japanisch (Japan)|0x040411|0x40411|Latin1_General_CI_AI|
|Kannada (Indien)|0x044b|0x0439|Auf Serverebene nicht verfügbar|
|Kasachisch (Kasachstan)|0x043f|0x043f|Kazakh_90_CI_AS|
|Khmer (Kambodscha)|0x0453|0x0453|Auf Serverebene nicht verfügbar|
|K'iche (Guatemala)|0x0486|0x0c0a|Modern_Spanish_CI_AS|
|Kinyarwanda (Ruanda)|0x0487|0x0409|Latin1_General_CI_AS|
|Konkani (Indien)|0x0457|0x0439|Auf Serverebene nicht verfügbar|
|Koreanisch (koreanische Wörterbuchsortierung)|0x0412|0x0412|Korean_Wansung_CI_AS|
|Kirgisisch (Kirgisistan)|0x0440|0x0419|Cyrillic_General_CI_AS|
|Lao (Volksrepublik Laos)|0x0454|0x0454|Auf Serverebene nicht verfügbar|
|Lettisch (Lettland)|0x0426|0x0426|Latvian_CI_AS|
|Litauisch (Litauen)|0x0427|0x0427|Lithuanian_CI_AS|
|Niedersorbisch (Deutschland)|0x082e|0x0409|Latin1_General_CI_AS|
|Luxemburgisch (Luxemburg)|0x046e|0x0409|Latin1_General_CI_AS|
|Mazedonisch (Mazedonien, FYROM)|0x042f|0x042f|Macedonian_FYROM_90_CI_AS|
|Malaiisch (Brunei Darussalam)|0x083e|0x0409|Latin1_General_CI_AS|
|Malaiisch (Malaysia)|0x043e|0x0409|Latin1_General_CI_AS|
|Malayalam (Indien)|0x044c|0x0439|Auf Serverebene nicht verfügbar|
|Maltesisch (Malta)|0x043a|0x043a|Latin1_General_CI_AI|
|Maori (Neuseeland)|0x0481|0x0481|Latin1_General_CI_AI|
|Mapudungun (Chile)|0x047a|0x047a|Latin1_General_CI_AI|
|Marathi (Indien)|0x044e|0x0439|Auf Serverebene nicht verfügbar|
|Mohawk (Kanada)|0x047c|0x047c|Latin1_General_CI_AI|
|Mongolisch (Mongolei)|0x0450|0x0419|Cyrillic_General_CI_AS|
|Mongolisch (VRC)|0x0850|0x0419|Cyrillic_General_CI_AS|
|Nepalesisch (Nepal)|0x0461|0x0461|Auf Serverebene nicht verfügbar|
|Norwegisch, Bokmål (Norwegen)|0x0414|0x0414|Latin1_General_CI_AI|
|Norwegisch (Nynorsk, Norwegen)|0x0814|0x0414|Latin1_General_CI_AI|
|Okzitanisch (Frankreich)|0x0482|0x040c|French_CI_AS|
|Oriya (Indien)|0x0448|0x0439|Auf Serverebene nicht verfügbar|
|Paschtu (Afghanistan)|0x0463|0x0463|Auf Serverebene nicht verfügbar|
|Persisch (Iran)|0x0429|0x0429|Latin1_General_CI_AI|
|Polnisch (Polen)|0x0415|0x0415|Polish_CI_AS|
|Portugiesisch (Brasilien)|0x0416|0x0409|Latin1_General_CI_AS|
|Portugiesisch (Portugal)|0x0816|0x0409|Latin1_General_CI_AS|
|Punjabi (Indien)|0x0446|0x0439|Auf Serverebene nicht verfügbar|
|Quechua (Bolivien)|0x046b|0x0409|Latin1_General_CI_AS|
|Quechua (Ecuador)|0x086b|0x0409|Latin1_General_CI_AS|
|Quechua (Peru)|0x0c6b|0x0409|Latin1_General_CI_AS|
|Rumänisch (Rumänien)|0x0418|0x0418|Romanian_CI_AS|
|Rätoromanisch (Schweiz)|0x0417|0x0417|Latin1_General_CI_AI|
|Russisch (Russische Föderation)|0x0419|0x0419|Cyrillic_General_CI_AS|
|Inari-Sami (Finnland)|0x243b|0x083b|Latin1_General_CI_AI|
|Lule-Sami (Norwegen)|0x103b|0x043b|Latin1_General_CI_AI|
|Lule-Sami (Schweden)|0x143b|0x083b|Latin1_General_CI_AI|
|Nord-Sami (Finnland)|0x0c3b|0x083b|Latin1_General_CI_AI|
|Nord-Sami (Norwegen)|0x043b|0x043b|Latin1_General_CI_AI|
|Nord-Sami (Schweden)|0x083b|0x083b|Latin1_General_CI_AI|
|Skolt-Sami (Finnland)|0x203b|0x083b|Latin1_General_CI_AI|
|Süd-Sami (Norwegen)|0x183b|0x043b|Latin1_General_CI_AI|
|Süd-Sami (Schweden)|0x1c3b|0x083b|Latin1_General_CI_AI|
|Sanskrit (Indien)|0x044f|0x0439|Auf Serverebene nicht verfügbar|
|Serbisch (Bosnien und Herzegowina, kyrillisch)|0x1c1a|0x0c1a|Latin1_General_CI_AI|
|Serbisch (Bosnien und Herzegowina, lateinisch)|0x181a|0x081a|Latin1_General_CI_AI|
|Serbisch (Serbien, kyrillisch)|0x0c1a|0x0c1a|Latin1_General_CI_AI|
|Serbisch (Serbien, lateinisch)|0x081a|0x081a|Latin1_General_CI_AI|
|Sesotho sa Leboa/Nord-Sotho (Südafrika)|0x046c|0x0409|Latin1_General_CI_AS|
|Setswana/Tswana (Südafrika)|0x0432|0x0409|Latin1_General_CI_AS|
|Sinhala (Sri Lanka)|0x045b|0x0439|Auf Serverebene nicht verfügbar|
|Slowakisch (Slowakei)|0x041b|0x041b|Slovak_CI_AS|
|Slowenisch (Slowenien)|0x0424|0x0424|Slovenian_CI_AS|
|Spanisch (Argentinien)|0x2c0a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Bolivien)|0x400a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Chile)|0x340a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Kolumbien)|0x240a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Costa Rica)|0x140a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Dominikanische Republik)|0x1c0a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Ecuador)|0x300a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (El Salvador)|0x440a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Guatemala)|0x100a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Honduras)|0x480a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Mexiko)|0x080a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Nicaragua)|0x4c0a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Panama)|0x180a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Paraguay)|0x3c0a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Peru)|0x280a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Puerto Rico)|0x500a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Spanien)|0x0c0a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Spanien, traditionelle Sortierung)|0x040a|0x040a|Traditional_Spanish_CI_AS|
|Spanisch (USA)|0x540a|0x0409|Latin1_General_CI_AS|
|Spanisch (Uruguay)|0x380a|0x0c0a|Modern_Spanish_CI_AS|
|Spanisch (Venezuela)|0x200a|0x0c0a|Modern_Spanish_CI_AS|
|Suaheli (Kenia)|0x0441|0x0409|Latin1_General_CI_AS|
|Schwedisch (Finnland)|0x081d|0x040b|Finnish_Swedish_CI_AS|
|Schwedisch (Schweden)|0x041d|0x040b|Finnish_Swedish_CI_AS|
|Syrisch (Syrien)|0x045a|0x045a|Auf Serverebene nicht verfügbar|
|Tadschikisch (Tadschikistan)|0x0428|0x0419|Cyrillic_General_CI_AS|
|Tamazight (Algerien, lateinisch)|0x085f|0x085f|Latin1_General_CI_AI|
|Tamil (Indien)|0x0449|0x0439|Auf Serverebene nicht verfügbar|
|Tatarisch (Russische Föderation)|0x0444|0x0444|Cyrillic_General_CI_AS|
|Telugu (Indien)|0x044a|0x0439|Auf Serverebene nicht verfügbar|
|Thai (Thailand)|0x041e|0x041e|Thai_CI_AS|
|Tibetisch (VRC)|0x0451|0x0451|Auf Serverebene nicht verfügbar|
|Türkisch (Türkei)|0x041f|0x041f|Turkish_CI_AS|
|Turkmenisch (Turkmenistan)|0x0442|0x0442|Latin1_General_CI_AI|
|Uighurisch (VRC)|0x0480|0x0480|Latin1_General_CI_AI|
|Ukrainisch (Ukraine)|0x0422|0x0422|Ukrainian_CI_AS|
|Obersorbisch (Deutschland)|0x042e|0x042e|Latin1_General_CI_AI|
|Urdu (Pakistan)|0x0420|0x0420|Latin1_General_CI_AI|
|Usbekisch (Usbekistan, kyrillisch)|0x0843|0x0419|Cyrillic_General_CI_AS|
|Usbekisch (Usbekistan, lateinisch)|0x0443|0x0443|Uzbek_Latin_90_CI_AS|
|Vietnamesisch (Vietnam)|0x042a|0x042a|Vietnamese_CI_AS|
|Walisisch (Großbritannien)|0x0452|0x0452|Latin1_General_CI_AI|
|Wolof (Senegal)|0x0488|0x040c|French_CI_AS|
|Xhosa/isiXhosa (Südafrika)|0x0434|0x0409|Latin1_General_CI_AS|
|Jakutisch (Russische Föderation)|0x0485|0x0485|Latin1_General_CI_AI|
|Yi (VRC)|0x0478|0x0409|Latin1_General_CI_AS|
|Yoruba (Nigeria)|0x046a|0x0409|Latin1_General_CI_AS|
|Zulu/isiZulu (Südafrika)|0x0435|0x0409|Latin1_General_CI_AS|

> [!NOTE]
> Nur-Unicode-Sortierungen können während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups nicht ausgewählt werden, da sie nicht als Sortierungen auf Serverebene unterstützt werden.    
    
Nach dem Zuordnen einer Sortierung zum Server können Sie die Sortierung nur ändern, indem Sie alle Datenbankobjekte und -daten exportieren, die **master** -Datenbank erneut erstellen und alle Datenbankobjekte und -daten importieren. Statt die Standardsortierung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu ändern, können Sie die gewünschte Sortierung auch beim Erstellen einer neuen Datenbank oder Datenbankspalte angeben.    

Zum Abfragen der Serversortierung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden Sie die `SERVERPROPERTY`-Funktion:

```sql
SELECT CONVERT(varchar, SERVERPROPERTY('collation'));
```

Verwenden Sie die folgende integrierte `fn_helpcollations()`-Funktion, um alle verfügbaren Sortierungen vom Server abzufragen.

```sql
SELECT * FROM sys.fn_helpcollations();
```
    
#### <a name="Database-level-collations"></a> Sortierungen auf Datenbankebene    
Beim Anlegen oder Ändern einer Datenbank können Sie die Standardsortierung der Datenbank mithilfe der COLLATE-Klausel der CREATE DATABASE- oder ALTER DATABASE-Anweisung angeben. Wenn keine Sortierung angegeben wird, wird die Datenbank der Serversortierung zugeordnet.    
    
Sie können die Sortierung von Systemdatenbanken nur ändern, indem Sie die Sortierung für den Server ändern.    
    
Die Datenbanksortierung wird für alle Metadaten in der Datenbank verwendet und ist der Standard für alle Zeichenfolgenspalten, temporären Objekte, Variablennamen und anderen in der Datenbank verwendeten Zeichenfolgen. Wenn Sie die Sortierung einer Benutzerdatenbank ändern, treten möglicherweise Sortierungskonflikte auf, wenn Abfragen in der Datenbank auf temporäre Tabellen zugreifen. Temporäre Tabellen werden immer in der Systemdatenbank **tempdb** gespeichert, die die Sortierung für die Instanz verwendet. Abfragen, die Zeichendaten aus der Benutzerdatenbank und **tempdb** vergleichen, schlagen möglicherweise fehl, wenn die Sortierungen einen Konflikt beim Auswerten der Zeichendaten verursachen. Sie können dieses Problem umgehen, wenn Sie die COLLATE-Klausel in der Abfrage angeben. Weitere Informationen finden Sie unter [COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md).    

> [!NOTE]
> Sobald die Datenbank einmal in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] erstellt wurde, kann sie nicht mehr geändert werden.

Die Sortierung einer Benutzerdatenbank kann mithilfe einer `ALTER DATABASE`-Anweisung geändert werden, die folgendermaßen aussehen kann:

```sql
ALTER DATABASE myDB COLLATE Greek_CS_AI;
```

> [!IMPORTANT]
> Das Ändern der Sortierung auf Datenbankebene hat keinen Einfluss auf Sortierungen auf Spalten- oder Ausdrucksebene.

Die aktuelle Sortierung einer Datenbank kann mithilfe einer Anweisung abgerufen werden, die folgendermaßen aussehen kann:

```sql
SELECT CONVERT (VARCHAR(50), DATABASEPROPERTYEX('database_name','collation'));
```

#### <a name="Column-level-collations"></a> Sortierungen auf Spaltenebene    
Beim Erstellen oder Ändern einer Tabelle können Sie mithilfe der COLLATE-Klausel Sortierungen für alle Zeichenfolgenspalten angeben. Wenn keine Sortierung angegeben ist, wird der Spalte die Standardsortierung der Datenbank zugewiesen.    

Die Sortierung einer Spalte kann mithilfe einer `ALTER TABLE`-Anweisung geändert werden, die z. B. folgendermaßen aussehen kann:

```sql
ALTER TABLE myTable ALTER COLUMN mycol NVARCHAR(10) COLLATE Greek_CS_AI;
```
    
#### <a name="Expression-level-collations"></a> Sortierungen auf Ausdrucksebene    
Sortierungen auf Ausdrucksebene werden zum Zeitpunkt der Ausführung einer Anweisung festgelegt. Sie haben Auswirkungen auf die Art und Weise, wie ein Resultset zurückgegeben wird. Somit können die ORDER BY-Sortierergebnisse gebietsschemaspezifisch sein. Implementieren Sie mithilfe einer COLLATE-Klausel, die folgendermaßen aussehen kann, Sortierungen auf Ausdrucksebene:    
    
```sql    
SELECT name FROM customer ORDER BY name COLLATE Latin1_General_CS_AI;    
```    
    
###  <a name="Locale_Defn"></a> Gebietsschema    
Ein Gebietsschema ist ein Satz von Informationen, die einem Ort oder einer Kultur zugeordnet sind. Es kann Name und Bezeichner der gesprochenen Sprache, die Schrift, die zum Schreiben dieser Sprache verwendet wird, sowie kulturelle Konventionen enthalten. Sortierungen können einem oder mehreren Gebietsschemas zugeordnet sein. Weitere Informationen finden Sie unter [Von Microsoft zugewiesene Gebietsschemabezeichner (LCIDs)](https://msdn.microsoft.com/goglobal/bb964664.aspx).    
    
###  <a name="Code_Page_Defn"></a> Code Page    
 Eine Codepage ist ein geordneter Satz von Zeichen in einem vorgegebenen Skript, in dem ein numerischer Index, oder Codepunktwert, mit jedem Zeichen verbunden ist. Eine Codepage in Windows wird in der Regal als *Zeichensatz* oder *charset*bezeichnet. Codepages werden zur Unterstützung der Zeichensätze und Tastaturlayouts verschiedener Windows-Systemgebietsschemas verwendet.     
 
###  <a name="Sort_Order_Defn"></a> Sort Order    
 Die Sortierreihenfolge gibt an, wie Datenwerte sortiert werden. Dies wirkt sich auf die Ergebnisse des Datenvergleichs aus. Daten werden mithilfe von Sortierungen sortiert, die mit Indizes optimiert werden können.    
    
##  <a name="Unicode_Defn"></a> Unicode-Unterstützung    
Unicode ist ein Standard zum Zuordnen von Codepunkten zu Zeichen. Da dieser Standard entwickelt wurde, um alle Zeichen aus allen Sprachen der Welt zu unterstützen, besteht keine Notwendigkeit für unterschiedliche Codepages zur Handhabung der verschiedenen Zeichensätze.

### <a name="unicode-basics"></a>Grundlagen zu Unicode
Das Speichern von Daten in mehreren Sprachen innerhalb einer Datenbank ist schwierig zu verwalten, wenn nur Zeichendaten und Codepages verwendet werden. Es ist außerdem schwierig, eine Codepage für die Datenbank zu finden, die alle erforderlichen sprachenspezifischen Zeichen speichern kann. Weiterhin ist es schwierig, die ordnungsgemäße Übersetzung von Sonderzeichen sicherzustellen, die von Clients gelesen oder aktualisiert werden, die unterschiedliche Codepages ausführen. Datenbanken, die internationale Clients unterstützen, sollten immer Unicode-Datentypen anstelle von Nicht-Unicode-Datentypen verwenden.

Eine Datenbank für Kunden in Nordamerika muss z. B. drei Hauptsprachen verarbeiten:

-  Spanische Namen und Adressen für Mexiko.
-  Französische Namen und Adressen für Quebec.
-  Englische Namen und Adressen für den übrigen Teil Kanadas und die USA.

Wenn Sie nur Zeichenspalten und Codepages verwenden, müssen Sie bei der Installation einer Codepage für die Datenbank sicherstellen, dass diese Codepage die Zeichen der drei Sprachen verarbeiten kann. Weiterhin müssen Sie darauf achten, dass die ordnungsgemäße Übersetzung von Zeichen aus einer der Sprachen sichergestellt ist, wenn sie von Clients gelesen werden, auf denen eine Codepage für eine andere Sprache ausgeführt wird.
   
> [!NOTE]
> Die Codepages, die ein Client verwendet, werden durch die Einstellungen des Betriebssystems (OS) bestimmt. Verwenden Sie zum Festlegen von Clientcodepages unter Windows die Option **Ländereinstellungen** in der Systemsteuerung.    

Es ist schwierig, eine Codepage für Zeichendatentypen auszuwählen, die alle Zeichen unterstützt, die von einem weltweiten Publikum benötigt werden.
Die einfachste Möglichkeit, Zeichendaten in internationalen Datenbanken zu verwalten, besteht darin, immer einen Datentyp zu verwenden, der Unicode unterstützt. 

### <a name="unicode-data-types"></a>Unicode-Datentypen
Wenn Sie Zeichendaten speichern, die mehrere Sprachen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]widerspiegeln ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), verwenden Sie Unicode-Datentypen (**nchar**, **nvarchar** und **ntext**) anstelle von Nicht-Unicode-Datentypen (**char**, **varchar** und **text**). 

> [!NOTE]
> Die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] kann bei Unicode-Datentypen bis zu 65.535 Zeichen mit UCS-2 oder den gesamten Unicode-Bereich (1.114.111 Zeichen) darstellen, wenn ergänzende Zeichen verwendet werden. Weitere Informationen zum Aktivieren der ergänzenden Zeichen finden Sie unter [Ergänzende Zeichen](#Supplementary_Characters).

Alternativ dazu gilt ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] Folgendes: Wenn eine für UTF-8 aktivierte Sortierung (\_UTF8) verwendet wird, werden Datentypen, die zuvor kein Unicode waren (**char** und **varchar**) zu Unicode-Datentypen (UTF-8). [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] ändert das Verhalten der bereits vorhandenen Unicode-UTF-16-Datentypen (**nchar**, **nvarchar** und **ntext**) nicht. Weitere Informationen finden Sie unter [Speicherunterschiede zwischen UTF-8 und UTF-16](#storage_differences).

### <a name="unicode-considerations"></a>Weitere Überlegungen
Nicht-Unicode-Datentypen verfügen über umfassende Einschränkungen. Das liegt daran, dass ein Nicht-Unicode-Computer auf die Verwendung einer einzelnen Codepage beschränkt ist. Es kann sein, dass Sie mit Unicode eine bessere Systemleistung erzielen, da weniger Codepagekonvertierungen erforderlich sind. Unicode-Sortierungen müssen auf der Datenbank-, Spalten- oder Ausdrucksebene einzeln ausgewählt werden, weil sie auf Serverebene nicht unterstützt werden.    

Wenn Sie Daten von einem Server auf einen Client verschieben, wird die Serversortierung von älteren Clienttreibern möglicherweise nicht erkannt. Dies kann passieren, wenn Sie Daten von einem Unicode-Server auf einen Nicht-Unicode-Client verschieben. Die beste Möglichkeit, dieses Problem zu beheben, besteht in einem Update des Clientbetriebssystems, wobei die zugrunde liegenden Systemsortierungen aktualisiert werden. Wenn auf dem Client Datenbankclient-Software installiert ist, sollten Sie ein Serviceupdate der Datenbankclient-Software in Erwägung ziehen.    
    
> [!TIP]
> Sie können auch versuchen, eine andere Sortierung für die Daten auf dem Server zu verwenden. Wählen Sie eine Sortierung aus, die einer Codepage auf dem Client zugeordnet werden kann.    
Um die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) verfügbaren UTF-16-Sortierungen zum Verbessern der Suche nach und Sortierung von einigen Unicode-Zeichen (nur Windows-Sortierungen) zu verwenden, können Sie eine der Sortierungen mit ergänzenden Zeichen (\_SC) oder eine der Version 140-Sortierungen auswählen.    
 
Um die in [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] verfügbaren UTF-8-Sortierungen zum Verbessern der Suche nach und Sortieren von einigen Unicode-Zeichen (nur Windows-Sortierungen) zu verwenden, müssen Sie für die UTF-8-Codierung aktivierte Sammlungen (\_UTF8) auswählen.
 
-   Das UTF8-Flag kann auf folgende Sortierungen angewendet werden:    
    -   Sortierungen von Version 90 
        > [!NOTE]
        > Nur wenn in dieser Version bereits Sortierungen mit ergänzenden Zeichen (\_SC) oder Variierungsauswahlzeichen (\_VSS) vorhanden sind.
    -   Sortierungen von Version 100    
    -   Sortierungen der Version 140   
    -   Die binäre Sortierung BIN2<sup>1</sup>
    
-   Das UTF8-Flag kann auf folgende Sortierungen nicht angewendet werden:    
    -   Sortierungen der Version 90, die keine ergänzenden Zeichen (\_SC) oder Variierungsauswahlzeichen (\_VSS) unterstützen    
    -   Die binären Sortierungen BIN und BIN2 <sup>2</sup>    
    -   Die SQL\_*-Sortierungen  
    
<sup>1</sup> Ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.3. [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 3.0 hat die Sortierung **UTF8_BIN2** durch **Latin1_General_100_BIN2_UTF8** ersetzt.        
<sup>2</sup> Bis [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.3.    
    
Zum Abwägen der Vor- und Nachteile von Unicode- und Nicht-Unicode-Datentypen müssen Sie das Szenario testen und die Leistungsunterschiede in Ihrer Umgebung messen. Es ist ratsam, die Sortierung zu standardisieren, die für die Systeme in Ihrem Unternehmen verwendet wird, und so weit wie möglich Unicode-Server und -Clients bereitzustellen.    
    
In vielen Fällen interagiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit anderen Servern oder Clients, und Ihr Unternehmen verwendet möglicherweise mehrere Standards für den Datenzugriff zwischen Anwendungen und Serverinstanzen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clients stellen einen der beiden Haupttypen dar:    
    
-   **Unicode-Clients** , die OLE DB und Open Database Connectivity (ODBC) Version 3.7 oder höher verwenden.    
-   **Nicht-Unicode-Clients** , die DB Library und ODBC Version 3.6 oder früher verwenden.    
    
Die folgende Tabelle enthält Informationen zur Verwendung mehrsprachiger Daten mit verschiedenen Kombinationen von Unicode- und Nicht-Unicode-Servern.    
    
|Server|Client|Vorteile oder Beschränkungen|    
|------------|------------|-----------------------------|    
|Unicode|Unicode|Da Unicode-Daten im gesamten System verwendet werden, verfügt dieses Szenario über die beste Systemleistung und den besten Schutz vor Beschädigung der abgerufenen Daten. Dies ist der Fall bei ActiveX Data Objects (ADO), OLE DB und ODBC Version 3.7 oder höher.|    
|Unicode|Nicht-Unicode|In diesem Szenario sind Einschränkungen oder Fehler beim Verschieben von Daten auf einen Clientcomputer möglich. Dies gilt besonders für Verbindungen zwischen einem Server, auf dem ein neueres Betriebssystem ausgeführt wird, und einem Client, auf dem eine ältere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oder ein älteres Betriebssystem installiert ist. Die Unicode-Daten auf dem Server versuchen, eine Zuordnung zu einer entsprechenden Codeseite auf dem Nicht-Unicode-Client zu erstellen, um die Daten zu konvertieren.|    
|Nicht-Unicode|Unicode|Dies ist keine günstige Konfiguration bei der Verwendung mehrsprachiger Daten Sie sind nicht in der Lage, Unicode-Daten auf den Nicht-Unicode-Server zu schreiben. Es ist wahrscheinlich, dass Probleme auftreten, wenn Daten an Server gesendet werden, die von der Codepage des Servers nicht erfasst werden.|    
|Nicht-Unicode|Nicht-Unicode|Dieses Szenario ist bei mehrsprachigen Daten mit zahlreichen Beschränkungen verbunden. Sie können nur eine Codepage verwenden.|    
    
##  <a name="Supplementary_Characters"></a> Ergänzende Zeichen    
Das Unicode Consortium hat jedem Zeichen einen eindeutigen Codepunkt zugeordnet, der einem Wert im Bereich 000000 bis 10FFFF entspricht. Die am häufigsten verwendeten Zeichen haben Codepunktwerte im Bereich von 000000 bis 00FFFFFF (65.535 Zeichen), die in ein 8-Bit- oder 16-Bit-Wort im Arbeitsspeicher und auf dem Datenträger passen. Dieser Bereich wird in der Regel als der Basic Multilingual Plane (BMP) festgelegt. 

Aber das Unicode Consortium hat 16 zusätzliche „Ebenen“ von Zeichen eingerichtet, die jeweils genauso groß sind wie die BMP. Diese Definition ermöglicht es Unicode, das Potential für 1.114.112 Zeichen (d.h. 2<sup>16</sup> * 17 Zeichen) innerhalb des Codepunktbereichs 000000 bis 10FFFFFF darzustellen. Zeichen mit Codepunktwerten größer als 00FFFFFF erfordern zwei bis vier aufeinanderfolgende 8-Bit-Wörter (UTF-8) oder zwei aufeinanderfolgende 16-Bit-Wörter (UTF-16). Diese Zeichen, die sich außerhalb der BMP befinden, werden als *ergänzende Zeichen*bezeichnet, und die zusätzlichen aufeinanderfolgenden 8-Bit- oder 16-Bit-Wörter werden als *Ersatzzeichenpaare*bezeichnet. Weitere Informationen zur ergänzende Zeichen, Ersatzzeichen und Ersatzzeichenpaaren finden Sie im [Unicode-Standard](http://www.unicode.org/standard/standard.html).    

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Datentypen wie **nchar** und **nvarchar** bereit, um Unicode-Daten im BMP-Bereich (000000 bis 00FFFF) zu speichern, die die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] mit UCS-2 kodiert. 

[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] hat eine neue Familie von Sortierungen mit ergänzenden Zeichen (\_SC) eingeführt, die mit den Datentypen **nchar**, **nvarchar** und **sql_variant** verwendet werden können, um den gesamten Unicode-Zeichenbereich (000000 bis 10FFFF) darzustellen. Beispiel: `Latin1_General_100_CI_AS_SC`, oder bei Verwenden einer japanischen Sortierung `Japanese_Bushu_Kakusu_100_CI_AS_SC`. 
 
[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] erweitert die Unterstützung für ergänzende Zeichen mit den neuen UTF-8-aktivierten Sortierungen ([\_UTF8](#utf8)) auf die Datentypen **char** und **varchar**. Diese können auch den vollständigen Unicode-Zeichenbereich darstellen.   

> [!NOTE]
> Ab [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterstützen alle neuen **\_140**-Sortierungen automatisch ergänzende Zeichen.

Bei Verwendung ergänzender Zeichen:    
    
-   Ergänzende Zeichen können bei Sortier- und Vergleichsvorgängen für Sortierungsversionen ab 90 verwendet werden.    
-   Alle Sortierungen von Version 100 unterstützen die linguistische Sortierung mit ergänzenden Zeichen.    
-   Ergänzende Zeichen werden für die Verwendung in Metadaten, beispielsweise in Namen von Datenbankobjekten, nicht unterstützt.    
-   Datenbanken, die Sammlungen mit zusätzlichen Zeichen (\_SC) enthalten, können nicht für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Replikation verwendet werden. Das liegt daran, dass manche der Systemtabellen und gespeicherten Prozeduren, die für die Replikation erstellt wurden, den Legacydatentyp **ntext** verwenden, der keine zusätzlichen Zeichen unterstützt.  

-   Das SC-Flag kann in folgenden Versionen angewendet werden:    
    -   Sortierungen von Version 90    
    -   Sortierungen von Version 100    
    
-   Das SC-Flag kann nicht auf folgende Versionen angewendet werden:    
    -   Nicht versionierte Windows-Sortierungen der Version 80    
    -   Die binären Sortierungen BIN und BIN2    
    -   Die SQL\*-Sortierungen    
    -   Sortierungen von Version 140 (diese benötigen kein SC-Flag, da sie ergänzende Zeichen bereits unterstützen)    
    
In der folgenden Tabelle wird das Verhalten einiger Zeichenfolgenfunktionen und Zeichenfolgenoperatoren verglichen, wenn diese ergänzende Zeichen mit und ohne SCA-Sortierung (supplementary character-aware) verwenden:    
    
|Zeichenfolgenfunktion oder Operator|Mit SCA-Sortierung|Ohne SCA-Sortierung|    
|---------------------------------|--------------------------|-----------------------------|    
|[CHARINDEX](../../t-sql/functions/charindex-transact-sql.md)<br /><br /> [LEN](../../t-sql/functions/len-transact-sql.md)<br /><br /> [PATINDEX](../../t-sql/functions/patindex-transact-sql.md)|Das UTF-16-Ersatzzeichenpaar wird als einzelner Codepunkt betrachtet.|Das UTF-16-Ersatzzeichenpaar wird als zwei Codepunkte betrachtet.|    
|[LEFT](../../t-sql/functions/left-transact-sql.md)<br /><br /> [REPLACE](../../t-sql/functions/replace-transact-sql.md)<br /><br /> [REVERSE](../../t-sql/functions/reverse-transact-sql.md)<br /><br /> [RIGHT](../../t-sql/functions/right-transact-sql.md)<br /><br /> [SUBSTRING](../../t-sql/functions/substring-transact-sql.md)<br /><br /> [STUFF](../../t-sql/functions/stuff-transact-sql.md)|Diese Funktionen behandeln jedes Ersatzzeichenpaar als einzelnen Codepunkt und funktionieren wie erwartet.|Diese Funktionen können Ersatzzeichenpaare möglicherweise aufteilen und zu unerwarteten Ergebnissen führen.|    
|[NCHAR](../../t-sql/functions/nchar-transact-sql.md)|Gibt das Zeichen zurück, das dem angegebenen Unicode-Codepunktwert im Bereich 0 zu 0x10FFFF entspricht. Wenn der angegebene Wert im Bereich 0 bis 0xFFFF liegt, wird nur ein Zeichen zurückgegeben. Bei höheren Werten wird das entsprechende Ersatzzeichenpaar zurückgegeben.|Ein Wert größer als 0xFFFF gibt anstelle des entsprechenden Ersatzzeichens NULL zurück.|    
|[UNICODE](../../t-sql/functions/unicode-transact-sql.md)|Gibt einen UTF-16-Codepunkt im Bereich 0 bis 0x10FFFF zurück.|Gibt einen UCS-2-Codepunkt im Bereich 0 bis 0xFFFF zurück.|    
|[Einzelnes zu suchendes Zeichen](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)<br /><br /> [Platzhalterzeichen - nicht zu suchende(s) Zeichen](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)|Ergänzende Zeichen werden für alle Platzhaltervorgänge unterstützt.|Ergänzende Zeichen werden für diese Platzhaltervorgänge nicht unterstützt. Andere Platzhalteroperatoren werden unterstützt.|    
    
## <a name="GB18030"></a> GB18030-Unterstützung    
GB18030 ist ein separater Standard, der in der Volksrepublik China zur Codierung von chinesischen Schriftzeichen verwendet wird. In GB18030 können Zeichen 1, 2 oder 4 Bytes lang sein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet Unterstützung für GB18030-codierte Zeichen, indem diese erkannt werden, wenn Sie den Server von einer clientseitigen Anwendung erreichen, und in systemeigene Unicode-Zeichen konvertiert und als solche gespeichert werden. Nach ihrer Speicherung im Server werden diese Zeichen in allen nachfolgenden Operationen als Unicode-Zeichen behandelt. 

Sie können eine beliebige chinesische Sortierung verwenden. Empfohlen wird die aktuelle Version 100. Alle \_100-Ebenen-Sortierungen unterstützen die linguistische Sortierung mit GB18030-Zeichen. Wenn die Daten ergänzende Zeichen (Ersatzpaare) enthalten, können Sie Such- und Sortiervorgänge mithilfe der in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verfügbaren SC-Sortierungen optimieren.    

> [!NOTE]
> Stellen Sie sicher, dass Ihre Clienttools wie z. B.[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] die Schriftart Dengxian verwenden, um Zeichenfolgen mit GB18030-codierten Zeichen richtig anzuzeigen.
    
## <a name="Complex_script"></a> Unterstützung komplexer Skripts    
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann das Eingeben, Speichern, Ändern und Anzeigen komplexer Skripts unterstützen. Zu komplexen Skripts gehören folgende Typen:    
    
-   Skripts, die sowohl die Kombination von Text von rechts nach links und Text von links nach rechts enthalten, als auch die Kombination von arabischem und englischem Text.    
-   Skripts, deren Zeichen die Form abhängig von ihrer Position ändern, oder abhängig davon, ob sie mit anderen Zeichen kombiniert werden, wie beispielsweise arabische, indische und thailändische Zeichen.    
-   Sprachen, wie beispielsweise Thailändisch, die ein internes Wörterbuch zum Erkennen von Wörtern erfordern, da keine Abstände zwischen den Wörtern vorhanden sind.    
    
Datenbankanwendungen, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interagieren, müssen über Steuerelemente verfügen, die komplexe Skripts unterstützen. Standardmäßige Windows-Formularsteuerelemente, die in verwaltetem Code erstellt werden, sind für komplexe Skripts aktiviert.    

## <a name="Japanese_Collations"></a> Japanische Sortierungen, die in  [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]
 
Ab [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] werden neue japanische Sortierungsfamilien unterstützt, bei denen es sich um Permutationen verschiedener Optionen (\_CS, \_AS, \_KS, \_WS, \_VSS) handelt. 

Um diese Sortierungen aufzulisten, können Sie die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] abfragen:      

```sql 
SELECT Name, Description FROM fn_helpcollations()  
WHERE Name LIKE 'Japanese_Bushu_Kakusu_140%' OR Name LIKE 'Japanese_XJIS_140%'
``` 

Alle neuen Sortierungen verfügen über integrierte Unterstützung für ergänzende Zeichen, sodass keine der neuen **\_140**-Sortierungen das SC-Flag besitzt (oder benötigt).

Diese Sortierungen werden in Indizes der [!INCLUDE[ssde_md](../../includes/ssde_md.md)], in für den Arbeitsspeicher optimierten Tabellen, in Columnstore-Indizes und in nativ kompilierten Modulen unterstützt.

<a name="ctp23"></a>

## <a name="utf8"></a> Unterstützung für UTF-8
Mit [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] wird die vollständige Unterstützung für die weit verbreitete Zeichencodierung UTF-8 als Import- oder Exportcodierung oder als Sortierung für Zeichenfolgedaten auf Datenbank- und Spaltenebene eingeführt. UTF-8 ist für die Datentypen **char** and **varchar** zulässig und ist bei der Erstellung oder Änderung einer Objektsortierung in eine Sortierung mit dem Suffix `UTF8` aktiviert. Beispiel: **LATIN1_GENERAL_100_CI_AS_SC** in **LATIN1_GENERAL_100_CI_AS_SC_UTF8**. 

Die in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] eingeführte UTF-8-Codierung ist nur für Windows-Sortierungen verfügbar, die Sonderzeichen unterstützen. **nchar** und **nvarchar** ermöglichen nur die UCS-2- oder UTF-16-Codierung und bleiben unverändert.

### <a name="storage_differences"></a> Speicherunterschiede zwischen UTF-8 und UTF-16
Das Unicode Consortium hat jedem Zeichen einen eindeutigen Codepunkt zugeordnet, der einem Wert im Bereich 000000 bis 10FFFF entspricht. Mit [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] stehen sowohl UTF-8- als auch UTF-16-Codierungen zur Darstellung des gesamten Bereichs zur Verfügung:    
-  Bei der UTF-8-Codierung benötigen Zeichen im ASCII-Bereich (000000 - 00007F) 1 Bytes, die Codepunkte 000080 bis 0007FF 2 Byte, die Codepunkte 000800 bis 00FFFF 3 Bytes und die Codepunkte 0010000 bis 0010FFFFFF 4 Bytes. 
-  Bei der UTF-16-Codierung benötigen die Codepunkte 000000 bis 00FFFFFF 2 Bytes und die Codepunkte 0010000 bis 0010FFFF 4 Bytes. 

Die folgende Tabelle zeigt die Codierungsspeicherplatz in Bytes für jeden Zeichenbereich und jeden Codierungstyp:

|Codebereich (hexadezimal)|Codebereich (dezimal)|Speicherplatz in Bytes <sup>1</sup> mit UTF-8|Speicherplatz in Bytes <sup>1</sup> mit UTF-16|    
|---------------------------------|---------------------------------|--------------------------|-----------------------------|   
|000000 – 00007F|0 - 127|1|2|
|000080 – 00009F<br />0000A0 – 0003FF<br />000400 – 0007FF|128 – 159<br />160 – 1.023<br />1\.024 – 2.047|2|2|
|000800 – 003FFF<br />004000 – 00FFFF|2\.048 - 16.383<br />16.384 – 65.535|3|2|
|010000 – 03FFFF <sup>2</sup><br /><br />040000 – 10FFFF <sup>2</sup>|65.536 – 262.143 <sup>2</sup><br /><br />262.144 – 1.114.111 <sup>2</sup>|4|4|

<sup>1</sup> Die Speicherbytes beziehen sich auf die codierte Bytelänge, nicht auf die jeweilige Datentypgröße beim Speichern auf dem Datenträger. Weitere Informationen zu den Speichergrößen auf dem Datenträger finden Sie unter [nchar und nvarchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md) und [char und varchar](../../t-sql/data-types/char-and-varchar-transact-sql.md).

<sup>2</sup> Codepunktbereich für [ergänzende Zeichen](#Supplementary_Characters).

> [!TIP]   
> Üblicherweise denkt man in [CHAR(*n*) und VARCHAR(*n*)](../../t-sql/data-types/char-and-varchar-transact-sql.md) oder in [NCHAR(*n*) und NVARCHAR(*n*)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md), wobei *n* für die Anzahl von Zeichen steht. Dies liegt daran, dass in einem Beispiel einer CHAR(10)-Spalte mithilfe einer Sortierung wie „Latin1_General_100_CI_AI“ 10 ASCII-Zeichen im Bereich 0-127 gespeichert werden können, da jedes Zeichen in diesem Bereich nur 1 Byte verwendet.    
> In [CHAR(*n*) und VARCHAR(*n*)](../../t-sql/data-types/char-and-varchar-transact-sql.md) steht *n* jedoch für die Zeichenfolgenlänge in **Byte** (0-8.000), wobei das *n* in [NCHAR(*n*) und NVARCHAR(*n*)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md) für die Zeichenfolgenlänge in **Bytepaaren** (0-4.000) steht. *n* definiert niemals die Anzahl von Zeichen, die gespeichert werden können.

Wie bereits erwähnt, kann die Wahl der geeigneten Unicode-Codierung und des geeigneten Datentyps je nach verwendetem Zeichensatz zu erheblichen Einsparungen beim Speicherplatz führen oder den aktuellen Speicherbedarf erhöhen. Wenn Sie beispielsweise eine lateinische Sortierung verwenden, bei der UTF-8 aktiviert ist, z. B. „Latin1_General_100_CI_AI_SC_UTF8“, speichert eine `CHAR(10)`-Spalte 10 Byte und kann 10 ASCII-Zeichen im Bereich 0-127 enthalten, jedoch nur 5 Zeichen im Bereich 128-2047 und nur 3 Zeichen im Bereich 2048-65535. Im Vergleich dazu kann eine `NCHAR(10)`-Spalte 10 Zeichen im Bereich 0-65535 enthalten, da sie 10 Bytepaare (20 Byte) speichert.  

Bevor Sie entscheiden, ob Sie die UTF-8- oder UTF-16-Codierung für eine Datenbank oder Spalte verwenden möchten, sollten Sie die Verteilung der gespeicherten Zeichenfolgendaten berücksichtigen:
-  Wenn diese sich hauptsächlich im ASCII-Bereich 0-127 befinden (z. B. Englisch), dann benötigt jedes Zeichen 1 Byte mit UTF-8 und 2 Byte mit UTF-16. Die Verwendung von UTF-8 hat Speichervorteile. Die Änderung eines vorhandenen Spaltendatentyps mit ASCII-Zeichen im Bereich 0-127 von `NCHAR(10)` in `CHAR(10)` mit einer UTF-8-fähigen Sortierung führt beispielsweise zu einer Verringerung der Speicheranforderungen um 50 %. Diese Verringerung ist darauf zurückzuführen, dass `NCHAR(10)` 20 Byte für den Speicher erfordert, wohingegen `CHAR(10)` 10 Byte für die Darstellung der gleichen Unicode-Zeichenfolge erfordert.    
-  Oberhalb des ASCII-Bereichs benötigen fast alle lateinischen Schriftzeichen sowie Griechisch, Kyrillisch, Koptisch, Armenisch, Hebräisch, Arabisch, Syrisch, Tāna und N'Ko jeweils 2 Byte pro Zeichen in UTF-8 und UTF-16. In diesen Fällen gibt es für vergleichbare Datentypen keine signifikanten Speicherunterschiede (z.B. zwischen der Verwendung von **char** oder **nchar**).
-  Wenn es sich hauptsächlich um ostasiatische Schriftzeichen handelt (z.B. Koreanisch, Chinesisch und Japanisch), dann benötigt jedes Zeichen 3 Byte mit UTF-8 und 2 Byte mit UTF-16. Die Verwendung von UTF-16 hat Speichervorteile. 
-  Zeichen im Bereich von 010000 bis 10FFFFFF benötigen jeweils 4 Byte in UTF-8 und UTF-16. In diesen Fällen gibt es keine Speicherunterschiede für vergleichbare Datentypen (z.B. zwischen der Verwendung von **char** oder **nchar**).

Weitere Überlegungen zur finden Sie unter [Schreiben internationaler Transact-SQL-Anweisungen](../../relational-databases/collations/write-international-transact-sql-statements.md).

##  <a name="Related_Tasks"></a> Verwandte Aufgaben    
    
|Task|Thema|    
|----------|-----------|    
|Beschreibt, wie die Sortierung der Instanz von SQL Server festgelegt oder geändert wird.|[Festlegen oder Ändern der Serversortierung](../../relational-databases/collations/set-or-change-the-server-collation.md)|    
|Beschreibt, wie die Sortierung einer Benutzerdatenbank festgelegt oder geändert wird.|[Festlegen oder Ändern der Datenbanksortierung](../../relational-databases/collations/set-or-change-the-database-collation.md)|    
|Beschreibt, wie die Sortierung einer Spalte in der Datenbank festgelegt oder geändert wird.|[Festlegen oder Ändern der Spaltensortierung](../../relational-databases/collations/set-or-change-the-column-collation.md)|    
|Beschreibt, wie Sortierungsinformationen auf Server-, Datenbank- oder Spaltenebene zurückgegeben werden.|[Anzeigen von Sortierungsinformationen](../../relational-databases/collations/view-collation-information.md)|    
|Beschreibt, wie Transact-SQL-Anweisungen geschrieben werden, die die Übertragung von einer Sprache in eine andere verbessern, oder wie mehrere Sprachen einfacher unterstützt werden.|[Schreiben internationaler Transact-SQL-Anweisungen](../../relational-databases/collations/write-international-transact-sql-statements.md)|    
|Beschreibt, wie die Sprache von Fehlermeldungen und die bevorzugte Verwendungs- und Anzeigeweise von Datums-, Zeit-, und Währungsdaten geändert werden.|[Festlegen einer Sitzungssprache](../../relational-databases/collations/set-a-session-language.md)|    
    
##  <a name="Related_Content"></a> Verwandte Inhalte    
[Bewährte Methoden für die Sortierungsänderung bei SQL Server](https://go.microsoft.com/fwlink/?LinkId=113891)    
[Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)        
[Schreiben internationaler Transact-SQL-Anweisungen](../../relational-databases/collations/write-international-transact-sql-statements.md)     
[Bewährte Methode in SQL Server für die Migration zu Unicode](https://go.microsoft.com/fwlink/?LinkId=113890) – wird nicht mehr angeboten   
[Website des Unicode Consortium](https://go.microsoft.com/fwlink/?LinkId=48619)   
[Unicode-Standard](http://www.unicode.org/standard/standard.html)     
[UTF-8-Unterstützung im OLE DB-Treiber für SQL Server](../../connect/oledb/features/utf-8-support-in-oledb-driver-for-sql-server.md)      
[SQL Server-Sortierungsname &#40;Transact-SQL&#41;](../../t-sql/statements/sql-server-collation-name-transact-sql.md)        
[Name der Windows-Sortierung &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md)     
Blog [Einführung von UTF-8-Unterstützung für SQL Server](https://techcommunity.microsoft.com/t5/SQL-Server/Introducing-UTF-8-support-for-SQL-Server/ba-p/734928)       
    
## <a name="see-also"></a>Weitere Informationen    
[Contained Database Collations](../../relational-databases/databases/contained-database-collations.md)     
[Auswählen einer Sprache beim Erstellen eines Volltextindex](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)     
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)    
    
 
