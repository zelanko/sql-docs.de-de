---
title: Definieren der Serialisierung von XML-Daten | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Regeln für die Serialisierung von Daten in SQL Server.
ms.custom: ''
ms.date: 12/07/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- entitization rules [XML in SQL Server]
- serialization
- reparsing serialized XML structures
- encoding [XML in SQL Server]
- XML [SQL Server], serialization
- xml data type [SQL Server], serialization
- typed XML
ms.assetid: 42b0b5a4-bdd6-4a60-b451-c87f14758d4b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 67201804cc1f93a9595ff46c02a57da7ea6e6109
ms.sourcegitcommit: 68063a1857f40487e6a2028de25990728419e3a7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96749702"
---
# <a name="define-the-serialization-of-xml-data"></a>Definieren der Serialisierung von XML-Daten
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Beim expliziten oder impliziten Umwandeln des XML-Datentyps in eine SQL-Zeichenfolge oder einen Binärtyp wird der Inhalt des XML-Datentyps entsprechend der in diesem Thema beschriebenen Regeln serialisiert.  
  
## <a name="serialization-encoding"></a>Serialisierungscodierung  
 Wenn der SQL-Zieltyp VARBINARY ist, erfolgt die Serialisierung des Ergebnisses in UTF-16 mit einer UTF-16-Markierung für die Bytereihenfolge am Anfang, jedoch ohne eine XML-Deklaration. Wenn der Zieltyp zu klein ist, wird ein Fehler ausgelöst.  
  
 Beispiel:  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARBINARY(MAX))  
```  
  
 Dies ist das Ergebnis:  
  
```console
0xFFFE3C0094032F003E00  
```  
  
 Wenn der SQL-Zieltyp NVARCHAR oder NCHAR ist, erfolgt die Serialisierung des Ergebnisses in UTF-16 ohne die Markierung für die Bytereihenfolge am Anfang und ohne eine XML-Deklaration. Wenn der Zieltyp zu klein ist, wird ein Fehler ausgelöst.  
  
 Beispiel:  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as NVARCHAR(MAX))  
```  
  
 Dies ist das Ergebnis:  
  
```console
<Δ/>  
```  
  
 Wenn der SQL-Zieltyp VARCHAR oder CHAR ist, erfolgt die Serialisierung des Ergebnisses in der Codierung, die der Codepage der Datenbanksortierung entspricht, ohne Markierung zur Bytereihenfolge oder XML-Deklaration. Wenn der Zieltyp zu klein ist oder der Wert nicht zur Codeseite der Zielsortierung zugeordnet werden kann, wird ein Fehler ausgelöst.  
  
 Beispiel:  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARCHAR(MAX))  
```  
  
 Das kann zu einem Fehler führen, wenn die Codeseite der aktuellen Sortierung das Unicode-Zeichen Δ nicht darstellen kann oder es in einer speziellen Codierung dargestellt.  
  
 Beim Zurückgeben der XML-Ergebnisse an die Clientseite werden die Daten in UTF-16-Codierung gesendet. Der clientseitige Anbieter macht die Daten dann entsprechend seinen API-Regeln verfügbar.  
  
## <a name="serialization-of-the-xml-structures"></a>Serialisierung der XML-Strukturen  
 Der Inhalt eines **xml** -Datentyps wird auf die herkömmliche Art und Weise serialisiert. Das heißt konkret, dass Elementknoten dem Elementmarkup zugeordnet und Textknoten dem Textinhalt zugeordnet werden. Die Umstände, unter denen die Zeichen in Entitäten geändert werden, und die Modalitäten beim Serialisieren von atomaren Werten werden in den folgenden Abschnitten beschrieben.  
  
## <a name="entitization-of-xml-characters-during-serialization"></a>Ändern von XML-Zeichen in Entitäten bei der Serialisierung  
 Jede serialisierte XML-Struktur muss in der Lage sein, neu analysiert zu werden. Deshalb müssen einige Zeichen so serialisiert werden, dass sie in eine Entität geändert werden, damit die Roundtripfähigkeit der Zeichen in der gesamten Normalisierungsphase des XML-Parsers erhalten bleibt. Allerdings müssen einige Zeichen so in Entitäten geändert werden, dass das Dokument wohlgeformt ist und somit analysiert werden kann. Im Folgenden sind die bei der Serialisierung geltenden Regeln für das Ändern in Entitäten aufgeführt:  
  
-   Die Zeichen „&“, und „\<, and >“ werden immer in die Entitäten `&amp;`, `&lt;` oder `&gt;` geändert, wenn sie in einem Attributwert oder Elementinhalt auftreten.  
  
-   Da SQL Server ein Anführungszeichen (U+0022) zum Einschließen von Attributwerten verwendet, wird das Anführungszeichen in Attributwerten bei der Änderung in Entitäten zu `&quot;`.  
  
-   Ein Ersatzpaar wird beim Ändern in Entitäten zu einem einzelnen numerischen Zeichenverweis, wenn die Umwandlung nur auf dem Server erfolgt. So wird z. B. das Ersatzpaar U+D800 U+DF00 durch das Ändern in Entitäten zum numerischen Zeichenverweis `&#x00010300;`.  
  
-   Um zu verhindern, dass ein Tabstopp (U+0009) und ein Zeilenvorschub (LF, U+000A) beim Analysieren normalisiert werden, werden sie beim Ändern in Entitäten innerhalb von Attributwerten zu ihren numerischen Zeichenverweisen `&#x9;` bzw. `&#xA;`.  
  
-   Um zu verhindern, dass ein Wagenrücklauf (CR, U+000D) beim Analysieren normalisiert wird, wird er beim Ändern in Entitäten sowohl innerhalb von Attributwerten als auch in Elementinhalt zu seinem numerischen Zeichenverweis `&#xD;`.  
  
-   Um Textknoten zu schützen, die ausschließlich Leerzeichen enthalten, wird eines der Leerzeichen – zumeist das letzte – beim Ändern in Entitäten zu dessen numerischem Zeichenverweis. Auf diese Weise bleibt der Leerzeichentextknoten beim Neuanalysieren erhalten, und zwar unabhängig von der Einstellung zur Handhabung von Leerzeichen beim Analysieren.  
  
 Beispiel:  
  
```sql
declare @u NVARCHAR(50)  
set @u = N'<a a="  
    '+NCHAR(0xD800)+NCHAR(0xDF00)+N'>">   '+NCHAR(0xA)+N'</a>'  
select CAST(CONVERT(XML,@u,1) as NVARCHAR(50))  
```  
  
 Dies ist das Ergebnis:  
  
```console
<a a="  
    𐌀>">     
</a>  
```  
  
 Wenn Sie die letzte Leerzeichenschutzregel nicht anwenden wollen, können Sie die explizite CONVERT-Option 1 beim Umwandeln von **xml** in einen Zeichenfolgen- oder Binärtyp verwenden. Sie können z. B. folgende Aktionen ausführen, um das Ändern in Entitäten zu vermeiden:  
  
```sql
select CONVERT(NVARCHAR(50), CONVERT(XML, '<a>   </a>', 1), 1)  
```  
  
 Beachten Sie, dass die [query()-Methode (xml-Datentyp)](../../t-sql/xml/query-method-xml-data-type.md) eine xml-Datentypinstanz ergibt. Deshalb wird jedes Ergebnis der **query()** -Methode, das in einen Zeichenfolgen- oder Binärtyp umgewandelt wird, entsprechend den zuvor beschriebenen Regeln in Entitäten geändert. Wenn Sie Zeichenfolgenwerte erhalten wollen, die nicht in Entitäten geändert wurden, sollten Sie stattdessen die [value()-Methode (xml-Datentyp)](../../t-sql/xml/value-method-xml-data-type.md) verwenden. Es folgt ein Beispiel zum Verwenden der **query()** -Methode:  
  
```sql
declare @x xml  
set @x = N'<a>This example contains an entitized char: <.</a>'  
select @x.query('/a/text()')  
```  
  
 Dies ist das Ergebnis:  
  
```console
This example contains an entitized char: <.  
```  
  
 Es folgt ein Beispiel zum Verwenden der **query(** )-Methode:  
  
```sql
select @x.value('(/a/text())[1]', 'nvarchar(100)')  
```  
  
 Dies ist das Ergebnis:  
  
```console
This example contains an entitized char: <.  
```  
  
## <a name="serializing-a-typed-xml-data-type"></a>Serialisieren eines typisierten xml-Datentyps  
 Eine typisierte **xml** -Datentypinstanz enthält Werte, die entsprechend ihren XML-Schematypen typisiert sind. Diese Werte werden entsprechend ihrem XML-Schematyp in dasselbe Format serialisiert, wie es bei der XQuery-Umwandlung in xs:string entsteht. Weitere Informationen finden Sie unter [Typumwandlungsregeln in XQuery](../../xquery/type-casting-rules-in-xquery.md).  
  
 So wird z. B. der xs:double-Wert 1.34e1 zu 13.4 serialisiert, wie das im folgenden Beispiel gezeigt wird.  
  
```sql
declare @x xml  
set @x =''  
select CAST(@x.query('1.34e1') as nvarchar(50))  
```  
  
 Es wird der Zeichenfolgenwert 13.4 zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Typumwandlungsregeln in XQuery](../../xquery/type-casting-rules-in-xquery.md)   
 [CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
 
