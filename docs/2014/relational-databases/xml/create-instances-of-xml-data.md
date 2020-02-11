---
title: Erstellen Sie Instanzen der XML-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- type casting string instances [XML in SQL Server]
- XML [SQL Server], typed
- xml data type [SQL Server], generating instances
- casting string instances [XML in SQL Server]
- typed XML
- generating XML instances [SQL Server]
- XML [SQL Server], generating instances
- white space [XML in SQL Server]
ms.assetid: dbd6c06f-db6e-44a7-855a-6a55bf374907
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae842748d2d510c5c00f329f5e28cd49a0c86ef3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62637608"
---
# <a name="create-instances-of-xml-data"></a>Erstellen von Instanzen der XML-Daten
  In diesem Thema wird beschrieben, wie XML-Instanzen generiert werden.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gibt es folgende Möglichkeiten, XML-Instanzen zu generieren:  
  
-   Typumwandlung von Zeichenfolgeninstanzen  
  
-   Verwenden der SELECT-Anweisung mit der FOR XML-Klausel  
  
-   Verwenden von Konstantenzuweisungen  
  
-   Verwenden von Massenladen  
  
## <a name="type-casting-string-and-binary-instances"></a>Typumwandlung von Zeichenfolgen und Binärinstanzen  
 Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle Zeichen folgen-Datentypen, z. b. [**n**] [**var**]**char**, **[n] Text**, **varbinary**und **Image**, im- `xml` Datentyp analysieren, indem Sie die Zeichenfolge `xml` umwandeln (cast) oder konvertieren (Convert). Nicht typisiertes XML wird überprüft, um die Wohlgeformtheit zu bestätigen. Wenn dem Typ ein Schema zugeordnet ist, `xml` wird auch die Validierung ausgeführt. Weitere Informationen finden Sie unter [Vergleichen von typisiertem XML mit nicht typisiertem XML](compare-typed-xml-to-untyped-xml.md).  
  
 XML-Dokumente können unterschiedlich codiert werden (z. B.: UTF-8, UTF-16, Windows-1252). Im Folgenden werden die Regeln erläutert, nach denen Zeichenfolgen- und Binärtypen mit der Codierung des XML-Dokuments interagieren und die das Verhalten des Parsers steuern.  
  
 Da **nvarchar** eine Doppelbyte-Unicode-Codierung wie UTF-16 oder UCS-2 annimmt, behandelt der XML-Parser den Zeichenfolgenwert als Doppelbyte-Unicode-codiertes XML-Dokument oder -Fragment. Dies bedeutet, dass auch das XML-Dokument in Doppelbyte-Unicode codiert sein muss, um mit dem Quelldatentyp kompatibel zu sein. Ein UTF-16-codiertes XML-Dokument kann eine UTF-16-Bytereihenfolgemarke (BOM, Byte Order Mark) besitzen, benötigt diese aber nicht, da der Kontext des Quelltyps deutlich macht, dass es sich nur um ein Doppelbyte-Unicode-Dokument handeln kann.  
  
 Der Inhalt einer **varchar** -Zeichenfolge wird vom XML-Parser als Einzelbyte-XML-Dokument/-Fragment behandelt. Da der Quellzeichenfolge **varchar** eine Codepage zugeordnet ist, verwendet der Parser diese Codepage für die Codierung, wenn im XML-Code keine explizite Codierung angegeben ist. Wenn eine XML-Instanz eine BOM- oder eine Codierungsdeklaration besitzt, muss diese zur Codepage passen. Andernfalls gibt der Parser einen Fehler aus.  
  
 Der Inhalt von **varbinary** wird als Codepointdatenstrom behandelt, der direkt an den XML-Parser übergeben wird. Daher muss das XML-Dokument oder -Fragment die BOM- oder eine andere Codierungsangabe inline enthalten. Der Parser bestimmt die Codierung ausschließlich anhand des Datenstroms. Dies bedeutet, dass UTF-16-codiertes XML die UTF-16-BOM enthalten muss, und dass eine Instanz ohne BOM und ohne Deklaration als UTF-8 interpretiert wird.  
  
 Wenn die Codierung des XML-Dokuments im Vorfeld nicht bekannt ist und die Daten vor der Konvertierung in XML als Zeichenfolgen- oder als Binärdaten übergeben werden, sollten die Daten als **varbinary**behandelt werden. Wenn z.B. Daten aus einer XML-Datei mit OpenRowset() gelesen werden, sollten die zu lesenden Daten als **varbinary(max)** -Wert festgelegt sein:  
  
```  
select CAST(x as XML)   
from OpenRowset(BULK 'filename.xml', SINGLE_BLOB) R(x)  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt XML intern in einer effizienten Binärdarstellung dar, die UTF-16-Codierung verwendet. Vom Benutzer bereitgestellte Codierung wird nicht beibehalten, während des Analysevorgangs jedoch berücksichtigt.  
  
### <a name="type-casting-clr-user-defined-types"></a>Typumwandlung benutzerdefinierter CLR-Typen  
 Wenn ein benutzerdefinierter CLR-Typ eine XML-Serialisierung besitzt, können Instanzen dieses Typs explizit in einen XML-Datentyp umgewandelt werden. Weitere Einzelheiten zur XML-Serialisierung von benutzerdefinierten CLR-Typen finden Sie unter [XML-Serialisierung auf Grundlage von CLR-Datenbankobjekten](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md).  
  
### <a name="white-space-handling-in-typed-xml"></a>Leerzeichenbehandlung in typisiertem XML  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]werden Leerzeichen in Elementinhalten als unbedeutend betrachtet, wenn diese in einer Sequenz von Nur-Leerzeichen-Zeichendaten auftreten, die durch ein Markup wie z. B. Begin- oder End-Tags getrennt und nicht in Entitäten geändert werden. (CDATA-Abschnitte werden ignoriert). Diese Behandlung von Leerzeichen unterscheidet sich von der Beschreibung von Leerzeichen in der XML 1.0-Spezifikation, die vom W3C (World Wide Web Consortium) veröffentlicht wird. Die Ursache ist darin zu suchen, dass der XML-Parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur eine beschränkte Anzahl der in XML 1.0 definierten DTD-Teilmengen erkennt. Weitere Informationen zu den beschränkten DTD-Teilmengen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt werden, finden Sie unter [CAST und CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
 Standardmäßig verwirft der XML-Parser insignifikante Leerzeichen, wenn Zeichenfolgendaten in XML konvertiert werden, wenn eine der folgenden Bedingungen zutrifft:  
  
-   
  `The xml:space` -Attribut ist nicht für ein Element oder seine Vorgängerelemente definiert.  
  
-   Das `xml:space` -Attribut für ein Element oder eines seiner Vorgängerelemente weist den Standardwert auf.  
  
 Beispiel:  
  
```  
declare @x xml  
set @x = '<root>      <child/>     </root>'  
select @x   
```  
  
 Dies ist das Ergebnis:  
  
```  
<root><child/></root>  
```  
  
 Sie können dieses Verhalten jedoch ändern. Um Leerzeichen für eine xml DT-Instanz beizubehalten, verwenden Sie den CONVERT-Operator und seinen optionalen *style* -Parameter, um einen Wert von 1 festzulegen. Beispiel:  
  
```  
SELECT CONVERT(xml, N'<root>      <child/>     </root>', 1)  
```  
  
 Wenn der *style* -Parameter nicht verwendet oder sein Wert auf 0 festgelegt wird, werden insignifikante Leerzeichen für die Konvertierung der xml DT-Instanz nicht beibehalten. Weitere Informationen zum Verwenden des CONVERT-Operators und seines *style*-Parameters beim Konvertieren von Zeichenfolgendaten in XML DT-Instanzen finden Sie unter [CAST und CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
### <a name="example-cast-a-string-value-to-typed-xml-and-assign-it-to-a-column"></a>Beispiel: Umwandeln eines Zeichenfolgenwertes in typisiertes XML und Zuweisen des Wertes zu einer Spalte  
 Im folgenden Beispiel wird eine Zeichen folgen Variable, die ein XML-Fragment `xml` enthält, in den-Datentyp umgewandelt `xml` und dann in der Type-Spalte gespeichert:  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
go  
DECLARE  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
```  
  
 Der folgende INSERT-Vorgang konvertiert implizit eine Zeichenfolge in `xml` den-Typ:  
  
```  
INSERT INTO T VALUES (3, @s)   
```  
  
 Sie können die Zeichenfolge explizit in den `xml` Typ umwandeln:  
  
```  
INSERT INTO T VALUES (3, cast (@s as xml))  
```  
  
 Sie können auch convert() wie im folgenden Beispiel gezeigt verwenden:  
  
```  
INSERT INTO T VALUES (3, convert (xml, @s))   
```  
  
### <a name="example-convert-a-string-to-typed-xml-and-assign-it-to-a-variable"></a>Beispiel: Konvertieren einer Zeichenfolge in typisiertes XML und Zuweisen der Zeichenfolge zu einer Spalte  
 Im folgenden Beispiel wird eine Zeichenfolge in den- `xml` Typ konvertiert und einer Variablen des- `xml` Datentyps zugewiesen:  
  
```  
declare @x xml  
declare  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
set @x =convert (xml, @s)  
select @x  
```  
  
## <a name="using-the-select-statement-with-a-for-xml-clause"></a>Verwenden der SELECT-Anweisung mit einer FOR XML-Klausel  
 Sie können die FOR XML-Klausel in einer SELECT-Anweisung verwenden, um Ergebnisse als XML zurückzugeben. Beispiel:  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = (SELECT Column1, Column2  
               FROM   Table1, Table2  
               WHERE   Some condition  
               FOR XML AUTO)  
 ...  
```  
  
 Die SELECT-Anweisung gibt ein XML-Textfragment zurück, das dann während der Zuweisung zur `xml` Variablen des-Datentyps analysiert wird.  
  
 Sie können auch die [Type-Direktive](type-directive-in-for-xml-queries.md) in der for XML-Klausel verwenden, die direkt ein for XML `xml` -Abfrageergebnis als Typ zurückgibt:  
  
```  
Declare @xmlDoc xml  
SET @xmlDoc = (SELECT ProductModelID, Name  
               FROM   Production.ProductModel  
               WHERE  ProductModelID=19  
               FOR XML AUTO, TYPE)  
SELECT @xmlDoc  
```  
  
 Dies ist das Ergebnis:  
  
```  
<Production.ProductModel ProductModelID="19" Name="Mountain-100" />...  
```  
  
 Im folgenden Beispiel wird das typisierte `xml` Ergebnis einer for XML-Abfrage in eine `xml` Spalte vom Typ eingefügt:  
  
```  
CREATE TABLE T1 (c1 int, c2 xml)  
go  
INSERT T1(c1, c2)  
SELECT 1, (SELECT ProductModelID, Name  
           FROM Production.ProductModel  
           WHERE ProductModelID=19  
           FOR XML AUTO, TYPE)  
SELECT * FROM T1  
go  
```  
  
 Weitere Informationen zu FOR XML finden Sie unter [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md).  
  
> [!NOTE]  
>  Von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden `xml`-Datentypinstanzen an den Client zurückgegeben, die das Ergebnis unterschiedlicher Serverkonstrukte sind (z. B. FOR XML-Abfragen, für die die TYPE-Direktive verwendet wird, oder bei denen der `xml`-Datentyp verwendet wird, um XML aus SQL-Spalten, -Variablen und -Ausgabeparametern zurückzugeben). Im Clientanwendungscode wird vom ADO.NET-Anbieter angefordert, dass diese `xml`-Datentypinformationen als Binärcode vom Server gesendet werden. Wenn Sie FOR XML jedoch ohne die TYPE-Direktive verwenden, werden die XML-Daten als Zeichenfolgentyp zurückgegeben. Der Clientanbieter ist in jedem Fall fähig, beide XML-Formate zu verarbeiten.  
  
## <a name="using-constant-assignments"></a>Verwenden von Konstantenzuweisungen  
 Eine Zeichen folgen Konstante kann verwendet werden, wenn eine Instanz `xml` des-Datentyps erwartet wird. Dies entspricht einer impliziten CAST-Anweisung für die Zeichenfolge in XML. Beispiel:  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
-- Or  
SET @xmlDoc = N'<?xml version="1.0" encoding="ucs-2"?><doc/>'  
```  
  
 Im vorherigen Beispiel wird die Zeichenfolge implizit in `xml` den-Datentyp konvertiert und einer `xml` Variablen vom Typ zugewiesen.  
  
 Im folgenden Beispiel wird eine Konstante Zeichenfolge in `xml` eine Spalte vom Typ eingefügt:  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
INSERT INTO T VALUES (3, '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>')   
```  
  
> [!NOTE]  
>  Für typisiertes XML wird das XML für das angegebene Schema überprüft. Weitere Informationen finden Sie unter [Vergleichen von typisiertem XML mit nicht typisiertem XML](compare-typed-xml-to-untyped-xml.md).  
  
## <a name="using-bulk-load"></a>Verwenden von Massenkopieren  
 Die verbesserten [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) -Funktionen ermöglichen das Massenkopieren von XML-Dokumenten in der Datenbank. Sie können XML-Instanzen aus Dateien in die `xml` Typspalten in der Datenbank Massen laden. Funktionierende Beispiele finden Sie unter [Beispiele für den Massenimport und -export von XML-Dokumenten &#40;SQL Server&#41;](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md). Weitere Informationen über das Laden von XML-Dokumenten finden Sie unter [Laden von XML-Daten](load-xml-data.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Abrufen und Abfragen von XML-Daten](retrieve-and-query-xml-data.md)|Beschreibt die Teile von XML-Instanzen, die nicht beibehalten werden, wenn sie in Datenbanken gespeichert werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichen von typisiertem XML mit nicht typisiertem XML](compare-typed-xml-to-untyped-xml.md)   
 [XML-Datentypmethoden](/sql/t-sql/xml/xml-data-type-methods)   
 [XML DML &#40;Data Modification Language&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml)   
 [XML-Daten &#40;SQL Server&#41;](xml-data-sql-server.md)  
  
  
