---
title: XML-Formatdateien (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], XML format files
- bulk importing [SQL Server], format files
- XML format files [SQL Server]
ms.assetid: 69024aad-eeea-4187-8fea-b49bc2359849
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cc1e8de30fa582898ef8516b9767dec14c4fa81
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050464"
---
# <a name="xml-format-files-sql-server"></a>XML-Formatdateien (SQL Server)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] stellt ein XML-Schema bereit, das die Syntax für das Schreiben von *XML-Formatdateien* definiert, die zum Übertragen von Daten in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle per Massenimport verwendet werden. XML-Formatdateien müssen sich an dieses Schema halten, das in XSDL (XML Schema Definition Language) definiert ist. XML-Formatdateien werden nur unterstützt, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tools zusammen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client installiert werden.  
  
 Eine XML-Formatdatei kann mit dem Befehl **bcp**, einer BULK INSERT-Anweisung oder einer INSERT ... SELECT \* FROM OPENROWSET(BULK...)-Anweisung verwendet werden. Mithilfe des **bcp** -Befehls können Sie automatisch eine XML-Formatdatei für eine Tabelle generieren. Weitere Informationen finden Sie unter [bcp Utility](../../tools/bcp-utility.md).  
  
> [!NOTE]  
>  Zwei Typen von Formatdateien werden zum Massenexportieren und -importieren unterstützt: *Nicht-XML-Formatdateien* und *XML-Formatdateien*. XML-Formatdateien bieten eine flexible und leistungsfähige Alternative zu Nicht-XML-Formatdateien. Informationen zu Nicht-XML-Formatdateien finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  

  
##  <a name="benefits-of-xml-format-files"></a><a name="BenefitsOfXmlFFs"></a> Vorteile von XML-Formatdateien  
  
-   XML-Formatdateien sind selbstbeschreibend, wodurch das Lesen, Erstellen und Erweitern erleichtert wird. Sie können vom Benutzer gelesen werden, sodass dieser nachvollziehen kann, wie Daten bei Massenvorgängen interpretiert werden.  
  
-   XML-Formatdateien enthalten die Datentypen von Zielspalten.  Die XML-Codierung enthält eine klare Beschreibung der Datentypen und Datenelemente der Datendatei sowie der Zuordnung zwischen den Datenelementen und den Tabellenspalten.  
  
     Dies ermöglicht die Trennung zwischen der Darstellungsweise von Daten in den Datendateien und der Zuordnung des betreffenden Datentyps für jedes Feld in der Datei. Wenn z. B. eine Datendatei eine Zeichendarstellung der Daten enthält, geht der entsprechende SQL-Spaltentyp verloren.  
  
-   Eine XML-Formatdatei ermöglicht das Laden eines Felds aus einer Datendatei, das einen einzigen LOB-Datentyp (Large Object) enthält.  
  
-   Eine XML-Formatdatei kann erweitert werden und bleibt dennoch mit früheren Versionen kompatibel. Darüber hinaus erleichtert die Übersichtlichkeit der XML-Codierung die Erstellung mehrerer Formatdateien für eine bestimmte Datendatei. Dies ist von Nutzen, wenn Sie alle oder einige Datenfelder den Spalten in verschiedenen Tabellen oder Sichten zuordnen müssen.  
  
-   Die XML-Syntax einer Formatdatei ist unabhängig von der Richtung des Vorgangs, die Syntax ist also für Massenexport und Massenimport identisch.  
  
-   Sie können XML-Formatdateien verwenden, um Massenimporte von Daten in Tabellen bzw. nicht partitionierte Sichten oder Massenexporte von Daten auszuführen.  
  
-   Bei einer OPENROWSET (BULK...)-Funktion ist die Angabe einer Zieltabelle optional. Das liegt daran, dass die Funktion die XML-Formatdatei zum Lesen von Daten aus einer Datendatei benötigt.  
  
    > [!NOTE]  
    >  Beim **bcp** -Befehl und der BULK INSERT-Anweisung ist eine Zieltabelle erforderlich, die mithilfe der Zieltabellenspalten die Typkonvertierung durchführt.  
  
##  <a name="structure-of-xml-format-files"></a><a name="StructureOfXmlFFs"></a> Struktur von XML-Formatdateien  
 XML-Formatdateien definieren, ebenso wie Nicht-XML-Formatdateien, das Format und die Struktur der Datenfelder in einer Datendatei und ordnen diese Datenfelder den Spalten in einer einzigen Zieltabelle zu.  
  
 Eine XML-Format Datei besteht aus zwei Haupt \<RECORD> Komponenten \<ROW> :  
  
-   \<RECORD>Beschreibt die Daten, die in der Datendatei gespeichert werden.  
  
     Jedes- \<RECORD> Element enthält einen Satz von einem oder mehreren- \<FIELD> Elementen. Diese Elemente entsprechen den Feldern in der Datendatei. Die Basissyntax lautet wie folgt:  
  
     \<RECORD>  
  
     \<FIELD .../>[ ... *n* ]  
  
     \</RECORD>  
  
     Jedes \<FIELD> Element beschreibt den Inhalt eines bestimmten Daten Felds. Ein Feld kann jeweils nur einer Spalte in der Tabelle zugeordnet werden. Nicht alle Felder müssen Spalten zugeordnet werden.  
  
     Ein Feld in einer Datendatei kann eine feste bzw. variable Länge aufweisen oder durch Zeichen abgeschlossen sein. Ein *Feldwert* kann als ein Zeichen (mit Einzelbytedarstellung), als ein Doppelbytezeichen (mit Unicode-Doppelbytedarstellung), als ein systemeigenes Datenbankformat oder als ein Dateiname dargestellt werden. Wird ein Feldwert als Dateiname dargestellt, verweist der Dateiname auf die Datei, die den Wert einer BLOB-Spalte in der Zieltabelle enthält.  
  
-   \<ROW>Beschreibt, wie Daten Zeilen aus einer Datendatei erstellt werden, wenn die Daten aus der Datei in eine-Tabelle importiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Ein- \<ROW> Element enthält eine Reihe von- \<COLUMN> Elementen. Diese Elemente entsprechen den Tabellenspalten. Die Basissyntax lautet wie folgt:  
  
     \<ROW>  
  
     \<COLUMN .../>[ ... *n* ]  
  
     \</ROW>  
  
     Jedes \<COLUMN> Element kann nur einem Feld in der Datendatei zugeordnet werden. Die Reihenfolge der \<COLUMN> Elemente im- \<ROW> Element definiert die Reihenfolge, in der Sie vom Massen Vorgang zurückgegeben werden. Die XML-Format Datei weist jedem \<COLUMN> Element einen lokalen Namen zu, der keine Beziehung zur Spalte in der Ziel Tabelle eines Massen Import Vorgangs aufweist.  
  
##  <a name="schema-syntax-for-xml-format-files"></a><a name="SchemaSyntax"></a> Schemasyntax für XML-Formatdateien  
 Dieser Abschnitt enthält eine Zusammenfassung der Elemente und Attribute des XML-Schemas für XML-Formatdateien. Die Syntax einer Formatdatei ist unabhängig von der Richtung des Vorgangs, die Syntax ist also für Massenexport und Massenimport identisch. In diesem Abschnitt wird auch erläutert, wie der Massen Import das \<ROW> -Element und das- \<COLUMN> Element verwendet und wie der xsi: Type-Wert eines Elements in ein Dataset eingefügt wird.  
  
 Unter [Beispiele für XML-Formatdateien](#SampleXmlFFs)weiter unten in diesem Thema können Sie die Syntax mit tatsächlichen XML-Formatdateien vergleichen.  
  
> [!NOTE]  
>  Sie können eine Formatdatei so ändern, dass Sie einen Massenimport von einer Datendatei durchführen können, in der die Anzahl und/oder Reihenfolge der Felder von der Anzahl und/oder Reihenfolge der Tabellenspalten abweicht. Weitere Informationen finden Sie unter [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)erforderlich.  
  
  
  
###  <a name="basic-syntax-of-the-xml-schema"></a><a name="BasicSyntax"></a> Basissyntax des XML-Schemas  
 Diese Syntax Anweisungen zeigen nur die Elemente ( \<BCPFORMAT> , \<RECORD> , \<FIELD> , \<ROW> und \<COLUMN> ) sowie deren grundlegende Attribute an.  
  
 \<BCPFORMAT ...>  
  
 \<RECORD>  
  
 \<FIELD ID = "*fieldID*" xsi:type = "*fieldType*" [...]  
  
 />  
  
 \</RECORD>  
  
 \<ROW>  
  
 \<COLUMN SOURCE = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]  
  
 />  
  
 \</ROW>  
  
 \</BCPFORMAT>  
  
> [!NOTE]  
>  Weitere Attribute, die dem Wert von xsi: Type in einem-Element oder einem-Element zugeordnet sind, werden weiter unten \<FIELD> \<COLUMN> in diesem Thema beschrieben.  
  

  
####  <a name="schema-elements"></a><a name="SchemaElements"></a> Schema-Elemente  
 In diesem Abschnitt werden die Funktionen aller Elemente dargestellt, die das XML-Schema für XML-Formatdateien definiert. Die Attribute werden in separaten Abschnitten weiter unten in diesem Thema beschrieben.  
  
 \<BCPFORMAT>  
 Ist das Element der Formatdatei, das die Datensatzstruktur einer bestimmten Datendatei und ihre Übereinstimmung mit den Spalten einer Tabellenzeile in einer Tabelle definiert.  
  
 \<RECORD .../>  
 Definiert ein komplexes Element, das ein oder mehrere- \<FIELD> Elemente enthält. Die Reihenfolge, in der die Felder in der Formatdatei deklariert werden, entspricht der Reihenfolge, in der diese Felder in der Datendatei angezeigt werden.  
  
 \<FIELD .../>  
 Definiert ein Feld in der Datendatei, das Daten enthält.  
  
 Die Attribute dieses Elements werden unter [Attribute des- \<FIELD> Elements](#AttrOfFieldElement)weiter unten in diesem Thema erläutert.  
  
 \<ROW .../>  
 Definiert ein komplexes Element, das ein oder mehrere- \<COLUMN> Elemente enthält. Die Reihenfolge der \<COLUMN> Elemente ist unabhängig von der Reihenfolge der \<FIELD> Elemente in einer Daten Satz Definition. Stattdessen bestimmt die Reihenfolge der \<COLUMN> Elemente in einer Format Datei die Spaltenreihenfolge des resultierenden Rowsets. Datenfelder werden in der Reihenfolge geladen, in der die entsprechenden \<COLUMN> Elemente im- \<COLUMN> Element deklariert werden.  
  
 Weitere Informationen finden Sie weiter unten in diesem Thema unter Verwendung [des- \<ROW> Elements durch den Massen Import](#HowUsesROW).  
  
 \<COLUMN>  
 Definiert eine Spalte als Element ( \<COLUMN> ). Jedes- \<COLUMN> Element entspricht einem- \<FIELD> Element (dessen ID im Source-Attribut des-Elements angegeben ist \<COLUMN> ).  
  
 Die Attribute dieses Elements werden unter [Attribute des- \<COLUMN> Elements](#AttrOfColumnElement)weiter unten in diesem Thema erläutert. Siehe auch, [wie der Massen Import das- \<COLUMN> Element verwendet](#HowUsesColumn), weiter unten in diesem Thema.  
  
 \</BCPFORMAT>  
 Ist erforderlich, um die Formatdatei zu beenden.  
  
####  <a name="attributes-of-the-field-element"></a><a name="AttrOfFieldElement"></a>Attribute des \<FIELD> Elements  
 In diesem Abschnitt werden die Attribute des- \<FIELD> Elements beschrieben, die in der folgenden Schema Syntax zusammengefasst sind:  
  
 <FIELD  
  
 ID **= " *`fieldID`* "**  
  
 xsi **:** Type **= " *`fieldType`* "**  
  
 [ LENGTH **="*`n`*"** ]  
  
 [PREFIX_LENGTH **= " *`p`* "** ]  
  
 [max_length **= " *`m`* "** ]  
  
 [Sortierung **= " *`collationName`* "** ]  
  
 [Terminator **= " *`terminator`* "** ]  
  
 />  
  
 Jedes \<FIELD> Element ist unabhängig von den anderen. Ein Feld wird anhand der folgenden Attribute beschrieben:  
  
|FIELD-Attribut|BESCHREIBUNG|Optional /<br /><br /> Erforderlich|  
|---------------------|-----------------|------------------------------|  
|ID **= " *`fieldID`* "**|Gibt den logischen Namen des Felds in der Datendatei an. Die ID eines Felds ist der Schlüssel, mit dem auf das Feld verwiesen wird.<br /><br /> <Feld-ID **= " *`fieldID`* "**/> wird <Spalten Quelle **= " *`fieldID`* "** zugeordnet./>|Erforderlich|  
|xsi: Type **= " *`fieldType`* "**|Dies ist ein (als Attribut verwendetes) XML-Konstrukt, das den Typ der Instanz des Elements identifiziert. Der Wert von *fieldType* bestimmt, welche der optionalen Attribute (unten) in einer bestimmten Instanz erforderlich sind.|Erforderlich (abhängig vom Datentyp)|  
|Length **= " *`n`* "**|Dieses Attribut definiert die Länge für eine Instanz mit einem Datentyp fester Länge.<br /><br /> Der Wert von *n* muss eine positive ganze Zahl sein.|Optional, sofern nicht für den xsi:type-Wert erforderlich|  
|PREFIX_LENGTH **= " *`p`* "**|Dieses Attribut definiert die Präfixlänge für eine binäre Datendarstellung. Bei dem PREFIX_LENGTH-Wert, *p*, muss es sich um eine der folgenden Zahlen handeln: 1, 2, 4 oder 8.|Optional, sofern nicht für den xsi:type-Wert erforderlich|  
|max_length **= " *`m`* "**|Dieses Attribut gibt die maximale Anzahl an Byte an, die in einem bestimmten Feld gespeichert werden kann. Ohne eine Zieltabelle ist die maximale Spaltenlänge nicht bekannt. Das MAX_LENGTH-Attribut beschränkt die maximale Länge einer Ausgabezeichenspalte sowie den Speicherplatz, der dem Spaltenwert zugewiesen ist. Dies ist vor allem bei Verwendung der BULK-Option der OPENROWSET-Funktion in einer SELECT FROM-Klausel nützlich.<br /><br /> Der Wert von *m* muss eine positive ganze Zahl sein. Standardmäßig beträgt die maximale Länge 8000 Zeichen für eine **char** -Spalte und 4000 Zeichen für eine **nchar** -Spalte.|Optional|  
|Collations **= " *`collationName`* "**|COLLATION ist nur für Zeichenfelder zulässig. Eine Liste der SQL-Sortierungsnamen finden Sie unter [SQL Server-Sortierungsname &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql).|Optional|  
|Terminator **= " *`terminator`* "**|Dieses Attribut gibt das Abschlusszeichen eines Datenfelds an. Als Abschlusszeichen kann jedes beliebige Zeichen verwendet werden. Es muss sich jedoch um ein eindeutiges Zeichen handeln, das nicht Teil der Daten ist.<br /><br /> Standardmäßig wird das Tabstoppzeichen (dargestellt als \t) als Abschlusszeichen verwendet. Um eine Absatzmarke darzustellen, verwenden Sie \r\n.|Wird nur mit einem xsi:type von Zeichendaten verwendet, die dieses Attribut erfordern.|  
  
#####  <a name="xsitype-values-of-the-field-element"></a><a name="XsiTypeValuesOfFIELD"></a>Xsi: Type-Werte des \<FIELD> Elements  
 Der xsi:type-Wert ist ein (als Attribut verwendetes) XML-Konstrukt, das den Datentyp für eine Instanz eines Elements identifiziert. Weitere Informationen finden Sie unter "Einfügen des xsi:type-Werts in ein Dataset" weiter unten in diesem Abschnitt.  
  
 Der xsi: Type-Wert des- \<FIELD> Elements unterstützt die folgenden Datentypen.  
  
|\<FIELD>xsi: Type-Werte|Erforderliche(s) XML-Attribut(e)<br /><br /> für Datentyp|Optionale(s) XML-Attribut(e)<br /><br /> für Datentyp|  
|-------------------------------|---------------------------------------------------|---------------------------------------------------|  
|**NativeFixed**|`LENGTH`|Keine.|  
|**NativePrefix**|`PREFIX_LENGTH`|MAX_LENGTH|  
|**CharFixed**|`LENGTH`|COLLATION|  
|**NCharFixed**|`LENGTH`|COLLATION|  
|**CharPrefix**|`PREFIX_LENGTH`|MAX_LENGTH, COLLATION|  
|**NCharPrefix**|`PREFIX_LENGTH`|MAX_LENGTH, COLLATION|  
|**CharTerm**|`TERMINATOR`|MAX_LENGTH, COLLATION|  
|**NCharTerm**|`TERMINATOR`|MAX_LENGTH, COLLATION|  
  
 Weitere Informationen zu [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
####  <a name="attributes-of-the-column-element"></a><a name="AttrOfColumnElement"></a>Attribute des \<COLUMN> Elements  
 In diesem Abschnitt werden die Attribute des- \<COLUMN> Elements beschrieben, die in der folgenden Schema Syntax zusammengefasst sind:  
  
 \<COLUMN  
  
 SOURCE = "*fieldID*"  
  
 NAME = "*columnName*"  
  
 xsi:type = "*columnType*"  
  
 [ LENGTH = "*n*" ]  
  
 [ PRECISION = "*n*" ]  
  
 [ SCALE = "*value*" ]  
  
 [ NULLABLE = { "YES"  
  
 "NO" } ]  
  
 />  
  
 Ein Feld wird mithilfe der folgenden Attribute einer Spalte in der Zieltabelle zugeordnet:  
  
|COLUMN-Attribut|BESCHREIBUNG|Optional /<br /><br /> Erforderlich|  
|----------------------|-----------------|------------------------------|  
|Quelle **= " *`fieldID`* "**|Gibt die ID des Felds an, das der Spalte zugeordnet wird.<br /><br /> <Spalten Quelle **= " *`fieldID`* "**/> wird <Feld-ID **= " *`fieldID`* "** zugeordnet./>|Erforderlich|  
|NAME = "*columnName*"|Gibt den Namen der Spalte im Rowset an, die durch die Formatdatei dargestellt wird. Dieser Spaltenname wird verwendet, um die Spalte im Resultset zu identifizieren; er muss nicht dem in der Zieltabelle verwendeten Spaltennamen entsprechen.|Erforderlich|  
|xsi **:** Type **= " *`ColumnType`* "**|Dies ist ein (als Attribut verwendetes) XML-Konstrukt, das den Datentyp der Instanz des Elements identifiziert. Der Wert von *ColumnType* bestimmt, welche der optionalen Attribute (unten) in einer bestimmten Instanz erforderlich sind.<br /><br /> Hinweis: die möglichen Werte von *ColumnType* und den zugehörigen Attributen werden in der nächsten Tabelle aufgeführt.|Optional|  
|Length **= " *`n`* "**|Definiert die Länge für eine Instanz mit einem Datentyp fester Länge. LENGTH wird nur verwendet, wenn es sich bei xsi:type um einen Zeichenfolgen-Datentyp handelt.<br /><br /> Der Wert von *n* muss eine positive ganze Zahl sein.|Optional (nur verfügbar, wenn xsi:type ein Zeichenfolgen-Datentyp ist)|  
|PRECISION **="*`n`*"**|Gibt die Anzahl der Stellen einer Zahl an. Beispielsweise hat die Zahl 123,45 eine Genauigkeit von 5.<br /><br /> Der Wert muss eine positive ganze Zahl sein.|Optional (nur verfügbar, wenn xsi:type ein Datentyp mit variablen Zahlen ist)|  
|Skalieren **= " *`int`* "**|Gibt die Anzahl der Stellen rechts vom Dezimaltrennzeichen einer Zahl an. Beispielsweise verfügt die Zahl 123,45 über 2 Dezimalstellen.<br /><br /> Der Wert muss eine ganze Zahl sein.|Optional (nur verfügbar, wenn xsi:type ein Datentyp mit variablen Zahlen ist)|  
|NULLABLE **=** { **"** YES **"**<br /><br /> **"** NO **"** }|Gibt an, ob eine Spalte NULL-Werte verarbeiten kann. Dieses Attribut ist unabhängig von FIELDS. Falls die Spalte jedoch nicht NULLABLE ist und für ein Feld NULL (d. h. kein Wert) angegeben wurde, tritt ein Laufzeitfehler auf.<br /><br /> Das NULLABLE-Attribut wird nur verwendet, wenn Sie eine einfache SELECT FROM OPENROWSET (BULK...)-Anweisung ausführen.|Optional (verfügbar für jeden beliebigen Datentyp)|  
  
#####  <a name="xsitype-values-of-the-column-element"></a><a name="XsiTypeValuesOfCOLUMN"></a>Xsi: Type-Werte des \<COLUMN> Elements  
 Der xsi:type-Wert ist ein (als Attribut verwendetes) XML-Konstrukt, das den Datentyp für eine Instanz eines Elements identifiziert. Weitere Informationen finden Sie unter "Einfügen des xsi:type-Werts in ein Dataset" weiter unten in diesem Abschnitt.  
  
 Das- \<COLUMN> Element unterstützt systemeigene SQL-Datentypen wie folgt:  
  
|Typkategorie|\<COLUMN>Datentypen|Erforderliche(s) XML-Attribut(e)<br /><br /> für Datentyp|Optionale(s) XML-Attribut(e)<br /><br /> für Datentyp|  
|-------------------|---------------------------|---------------------------------------------------|---------------------------------------------------|  
|Korrigiert|`SQLBIT`, `SQLTINYINT`, `SQLSMALLINT`, `SQLINT`, `SQLBIGINT`, `SQLFLT4`, `SQLFLT8`, `SQLDATETIME`, `SQLDATETIM4`, `SQLDATETIM8`, `SQLMONEY`, `SQLMONEY4`, `SQLVARIANT` und `SQLUNIQUEID`|Keine.|NULLABLE|  
|Variable Zahl|`SQLDECIMAL` und `SQLNUMERIC`|Keine.|NULLABLE, PRECISION, SCALE|  
|LOB|`SQLIMAGE`, `CharLOB`, `SQLTEXT` und `SQLUDT`|Keine.|NULLABLE|  
|Character LOB|`SQLNTEXT`|Keine.|NULLABLE|  
|Binäre Zeichenfolge|`SQLBINARY` und `SQLVARYBIN`|Keine.|NULLABLE, LENGTH|  
|Zeichenfolge|`SQLCHAR`, `SQLVARYCHAR`, `SQLNCHAR` und `SQLNVARCHAR`|Keine.|NULLABLE, LENGTH|  
  
> [!IMPORTANT]  
>  Verwenden Sie in der Formatdatei einen der folgenden Datentypen für den Massenexport oder -import von SQLXML-Daten: SQLCHAR oder SQLVARYCHAR (die Daten werden in der Clientcodepage oder in der Codepage, die durch die Sortierung impliziert wird, gesendet), SQLNCHAR oder SQLNVARCHAR (die Daten werden als Unicode gesendet) oder SQLBINARY oder SQLVARYBIN (die Daten werden ohne Konvertierung gesendet).  
  
 Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
###  <a name="how-bulk-import-uses-the-row-element"></a><a name="HowUsesROW"></a>Verwendung des-Elements durch den Massen Import \<ROW>  
 Das- \<ROW> Element wird in einigen Kontexten ignoriert. Ob \<ROW> sich das Element auf einen Massen Import Vorgang auswirkt, hängt davon ab, wie der Vorgang durchgeführt wird:  
  
-   Befehl **bcp**  
  
     Wenn Daten in eine Ziel Tabelle geladen werden, ignoriert **bcp** die \<ROW> Komponente. Stattdessen lädt **bcp** die Daten auf der Grundlage der Spaltentypen der Zieltabelle.  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen (BULK INSERT und der OPENROWSET-Massenrowsetanbieter)  
  
     Beim Massen Importieren von Daten in eine Tabelle [!INCLUDE[tsql](../../../includes/tsql-md.md)] verwenden-Anweisungen die- \<ROW> Komponente, um das Eingaberowset zu generieren. Darüber hinaus [!INCLUDE[tsql](../../../includes/tsql-md.md)] führen-Anweisungen geeignete Typkonvertierungen basierend auf den Spaltentypen aus, \<ROW> die unter und der entsprechenden Spalte in der Ziel Tabelle angegeben sind. Besteht eine Nichtübereinstimmung zwischen den Spaltentypen, die in der Formatdatei und in der Zieltabelle angegeben sind, wird eine zusätzliche Typkonvertierung durchgeführt. Aufgrund dieser zusätzlichen Typkonvertierung kann es zu einer Diskrepanz (d. h. einem Genauigkeitsverlust) im Verhalten von BULK INSERT bzw. des OPENROWSET-Massenrowsetanbieters verglichen mit **bcp**kommen.  
  
     Mithilfe der Informationen im- \<ROW> Element kann eine Zeile erstellt werden, ohne dass zusätzliche Informationen erforderlich sind. Aus diesem Grund können Sie ein Rowset mithilfe einer SELECT-Anweisung generieren (SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*).  
  
    > [!NOTE]  
    >  Die OPENROWSET BULK-Klausel erfordert eine Formatdatei (beachten Sie, dass eine Konvertierung vom Datentyp des Felds in den Datentyp der Spalte nur mit einer XML-Formatdatei möglich ist).  
  
###  <a name="how-bulk-import-uses-the-column-element"></a><a name="HowUsesColumn"></a>Verwendung des-Elements durch den Massen Import \<COLUMN>  
 Für den Massen Import von Daten in eine Tabelle ordnen die \<COLUMN> Elemente in einer Format Datei einem Tabellen Spalten ein Datendatei Feld zu, indem Folgendes angegeben wird:  
  
-   Die Position jedes Felds innerhalb einer Zeile in der Datendatei.  
  
-   Der Spaltentyp, der verwendet wird, um den Felddatentyp in den gewünschten Spaltendatentyp zu konvertieren.  
  
 Falls einem Feld keine Spalte zugeordnet ist, wird das Feld nicht in die generierte(n) Zeile(n) kopiert. Dieses Verhalten ermöglicht, dass eine Datendatei Zeilen mit unterschiedlichen Spalten (in verschiedenen Tabellen) generieren kann.  
  
 Ebenso ordnet für den Massen Export von Daten aus einer Tabelle jede \<COLUMN> in der Format Datei die Spalte aus der Eingabe Tabellenzeile dem entsprechenden Feld in der Ausgabe Datendatei zu.  
  
###  <a name="putting-the-xsitype-value-into-a-data-set"></a><a name="PutXsiTypeValueIntoDataSet"></a> Einfügen des xsi:type-Werts in ein Dataset  
 Wird ein XML-Dokument durch die XSD-Sprache (XML Schema Definition) überprüft, wird der xsi:type-Wert nicht in das Dataset eingefügt. Sie können die xsi:type-Informationen jedoch in das Dataset einfügen, indem Sie die XML-Formatdatei in ein XML-Dokument laden (z. B. `myDoc`), wie durch den folgenden Codeausschnitt veranschaulicht:  
  
```  
...;  
myDoc.LoadXml(xmlFormat);  
XmlNodeList ColumnList = myDoc.GetElementsByTagName("COLUMN");  
for(int i=0;i<ColumnList.Count;i++)  
{  
   Console.Write("COLUMN: xsi:type=" +ColumnList[i].Attributes["type",  
      "http://www.w3.org/2001/XMLSchema-instance"].Value+"\n");  
}  
```  
  
##  <a name="sample-xml-format-files"></a><a name="SampleXmlFFs"></a> Beispiele für XML-Formatdateien  
 Dieser Abschnitt enthält Informationen zum Verwenden von XML-Formatdateien in verschiedenen Situationen, u. a. ein [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] -Beispiel.  
  
> [!NOTE]  
>  In den Datendateien, die in den folgenden Beispielen gezeigt werden, steht `<tab>` für ein Tabstoppzeichen in einer Datendatei, und `<return>` steht für einen Wagenrücklauf.  
  

  
> [!NOTE]  
>  Informationen zum Erstellen einer Formatdatei finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
###  <a name="a-ordering-character-data-fields-the-same-as-table-columns"></a><a name="OrderCharFieldsSameAsCols"></a> A. Gleiches Anordnen von Zeichendatenfeldern und Tabellenspalten  
 Das folgende Beispiel zeigt eine XML-Formatdatei, die eine Datendatei beschreibt, in der drei Felder mit Zeichendaten enthalten sind. Die Formatdatei ordnet die Datendatei einer Tabelle zu, die drei Spalten enthält. Die Datenfelder entsprechen den Spalten der Tabelle eins zu eins.  
  
 **Tabelle (Zeile):** Person (Age int, FirstName varchar(20), LastName varchar(30))  
  
 **Datendatei (Datensatz):** Alter \<tab> FirstName \<tab> LastName\<return>  
  
 Die folgende XML-Formatdatei liest aus der Datendatei in die Tabelle.  
  
 Im `<RECORD>` -Element stellt die Formatdatei die Datenwerte in allen drei Feldern als Zeichendaten dar. Für jedes Feld gibt das `TERMINATOR` -Attribut das Abschlusszeichen an, das dem Datenwert folgt.  
  
 Die Datenfelder entsprechen den Spalten der Tabelle eins zu eins. Im `<ROW>` -Element ordnet die Formatdatei die `Age` -Spalte dem ersten Feld, die `FirstName` -Spalte dem zweiten Feld und die `LastName` -Spalte dem dritten Feld zu.  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>   
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="2" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="3" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  Ein entsprechendes [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] Beispiel finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
###  <a name="b-ordering-data-fields-and-table-columns-differently"></a><a name="OrderFieldsAndColsDifferently"></a> B. Unterschiedliches Anordnen von Datenfeldern und Tabellenspalten  
 Das folgende Beispiel zeigt eine XML-Formatdatei, die eine Datendatei beschreibt, in der drei Felder mit Zeichendaten enthalten sind. Die Formatdatei ordnet die Datendatei einer Tabelle zu, die drei Spalten enthält, die anders angeordnet sind als die Felder der Datendatei.  
  
 **Tabelle (Zeile):** Person (Age int, FirstName varchar(20), LastName varchar(30))  
  
 **Datendatei** (Datensatz): Age \<tab> LastName \<tab> FirstName\<return>  
  
 Im `<RECORD>` -Element stellt die Formatdatei die Datenwerte in allen drei Feldern als Zeichendaten dar.  
  
 Im `<ROW>` -Element ordnet die Formatdatei die `Age` -Spalte dem ersten Feld, die `FirstName` -Spalte dem dritten Feld und die `LastName` -Spalte dem zweiten Feld zu.  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="2" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  Ein entsprechendes [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] Beispiel finden Sie unter [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md).  
  
### <a name="c-omitting-a-data-field"></a>C. Auslassen eines Datenfelds  
 Das folgende Beispiel zeigt eine XML-Formatdatei, die eine Datendatei beschreibt, in der vier Felder mit Zeichendaten enthalten sind. Die Formatdatei ordnet die Datendatei einer Tabelle zu, die drei Spalten enthält. Das zweite Datenfeld entspricht keiner Tabellenspalte.  
  
 **Tabelle (Zeile):** Person (Age int, FirstName varchar(20), LastName varchar(30))  
  
 **Datendatei (Datensatz):** Alters Mitarbeiter-ID \<tab> \<tab> FirstName \<tab> LastName\<return>  
  
 Im `<RECORD>` -Element stellt die Formatdatei die Datenwerte in allen vier Feldern als Zeichendaten dar. Für jedes Feld gibt das TERMINATOR-Attribut das Abschlusszeichen an, das dem Datenwert folgt.  
  
 Im `<ROW>` -Element ordnet die Formatdatei die `Age` -Spalte dem ersten Feld, die `FirstName` -Spalte dem dritten Feld und die `LastName` -Spalte dem vierten Feld zu.  
  
```  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="10"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="4" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  Ein entsprechendes [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] Beispiel finden Sie unter [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md).  
  
###  <a name="d-mapping-field-xsitype-to-column-xsitype"></a><a name="MapXSItype"></a> D. Zuordnung \<FIELD> von xsi: Type zu \<COLUMN> xsi: Type  
 Das folgende Beispiel zeigt verschiedene Typen von Feldern und ihre Zuordnungen zu Spalten.  
  
```  
<?xml version = "1.0"?>  
<BCPFORMAT  
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   <RECORD>  
      <FIELD xsi:type="CharTerm" ID="C1" TERMINATOR="\t"   
            MAX_LENGTH="4"/>  
      <FIELD xsi:type="CharFixed" ID="C2" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="CharPrefix" ID="C3" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharTerm" ID="C4" TERMINATOR="\t"   
         MAX_LENGTH="4"/>  
      <FIELD xsi:type="NCharFixed" ID="C5" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharPrefix" ID="C6" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NativeFixed" ID="C7" LENGTH="4"/>  
   </RECORD>  
   <ROW>  
      <COLUMN SOURCE="C1" NAME="Age" xsi:type="SQLTINYINT"/>  
      <COLUMN SOURCE="C2" NAME="FirstName" xsi:type="SQLVARYCHAR"   
      LENGTH="16" NULLABLE="NO"/>  
      <COLUMN SOURCE="C3" NAME="LastName" />  
      <COLUMN SOURCE="C4" NAME="Salary" xsi:type="SQLMONEY"/>  
      <COLUMN SOURCE="C5" NAME="Picture" xsi:type="SQLIMAGE"/>  
      <COLUMN SOURCE="C6" NAME="Bio" xsi:type="SQLTEXT"/>  
      <COLUMN SOURCE="C7" NAME="Interest"xsi:type="SQLDECIMAL"   
      PRECISION="5" SCALE="3"/>  
   </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="e-mapping-xml-data-to-a-table"></a><a name="MapXMLDataToTbl"></a> E. Zuordnen von XML-Daten zu einer Tabelle  
 Im folgenden Beispiel wird eine leere zweispaltige Tabelle (`t_xml`) erstellt, in der die erste Spalte dem `int` -Datentyp und die zweite Spalte dem `xml` -Datentyp zugeordnet ist.  
  
```  
CREATE TABLE t_xml (c1 int, c2 xml)  
```  
  
 Die folgende XML-Formatdatei lädt eine Datendatei in die `t_xml`-Tabelle.  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" PREFIX_LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="8"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="c1" xsi:type="SQLINT"/>  
  <COLUMN SOURCE="2" NAME="c2" xsi:type="SQLNCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="f-importing-fixed-length-or-fixed-width-fields"></a><a name="ImportFixedFields"></a> F. Importieren von Feldern mit fester Länge oder fester Breite  
 Im folgenden Beispiel werden Felder mit einer festen Länge bzw. Breite von jeweils `10` und `6` Zeichen beschrieben. Die Formatdatei stellt diese Feldlängen bzw. -breiten als `LENGTH="10"` und `LENGTH="6"`dar. Jede Zeile der Datendatei endet mit einer Kombination von Wagenrücklauf/Zeilenvorschub, {CR}{LF}, was in der Formatdatei als `TERMINATOR="\r\n"`dargestellt wird.  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT  
       xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"  
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharFixed" LENGTH="10"/>  
    <FIELD ID="2" xsi:type="CharFixed" LENGTH="6"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="C1" xsi:type="SQLINT" />  
    <COLUMN SOURCE="2" NAME="C2" xsi:type="SQLINT" />  
  </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="additional-examples"></a><a name="AdditionalExamples"></a> Zusätzliche Beispiele  
 Die folgenden Themen enthalten weitere Beispiele sowohl für Nicht-XML-Dateien als auch für XML-Formatdateien:  
  
-   [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
 Keine.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Massenimport und -export von Daten &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md)   
 [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
