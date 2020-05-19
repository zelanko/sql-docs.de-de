---
title: Erstellen von Variablen und Spalten des XML-Datentyps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- xml data type [SQL Server], columns
ms.assetid: 8994ab6e-5519-4ba2-97a1-fac8af6f72db
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a62d8fbafc353e2d71223506b7fb4516d184b494
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717093"
---
# <a name="create-xml-data-type-variables-and-columns"></a>Erstellen von Variablen und Spalten des XML-Datentyps
  Der `xml` -Datentyp ist ein integrierter Datentyp in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und ähnelt in gewisser Weise anderen integrierten Typen wie `int` und `varchar` . Wie andere integrierte Typen können Sie den- `xml` Datentyp als Spaltentyp verwenden, wenn Sie eine Tabelle als Variablentyp, als Parametertyp, als Funktions Rückgabetyp oder in [Cast und Convert](/sql/t-sql/functions/cast-and-convert-transact-sql)erstellen.  
  
## <a name="creating-columns-and-variables"></a>Erstellen von Variablen und Spalten  
 Verwenden Sie zur Erstellung einer Spalte des `xml` -Typs als Teil einer Tabelle eine `CREATE TABLE` -Anweisung, wie im folgenden Beispiel gezeigt:  
  
```  
CREATE TABLE T1(Col1 int primary key, Col2 xml)   
```  
  
 Sie können eine `DECLARE statement` verwenden, um eine Variable des `xml` -Typs zu erstellen, wie das folgende Beispiel zeigt.  
  
```  
DECLARE @x xml   
```  
  
 Erstellen Sie eine typisierte `xml` -Variable, indem Sie eine XML-Schemaauflistung angeben, wie im folgenden Beispiel gezeigt.  
  
```  
DECLARE @x xml (Sales.StoreSurveySchemaCollection)  
```  
  
 Verwenden Sie zum Übergeben eines Parameters des `xml` -Typs an eine gespeicherte Prozedur eine `CREATE PROCEDURE` -Anweisung, wie im folgenden Beispiel gezeigt.  
  
```  
CREATE PROCEDURE SampleProc(@XmlDoc xml) AS ...   
```  
  
 Zum Abfragen von den in Spalten, Variablen oder Parametern gespeicherten XML-Instanzen können Sie XQuery verwenden. Sie können auch die XML-Datenbearbeitungssprache (XML DML, Data Manipulation Language) verwenden, um Updates an den XML-Instanzen vorzunehmen. Da der XQuery-Standard zum Zeitpunkt der Entwicklung keine Definition der XQuery-DML enthielt, führt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Erweiterungen der [XML Data Modification Language (XML DML)](/sql/t-sql/xml/xml-data-modification-language-xml-dml) für XQuery ein. Diese Erweiterungen ermöglichen Einfügungs-, Update- und Löschvorgänge.  
  
## <a name="assigning-defaults"></a>Zuweisen von Standardeinstellungen  
 Sie können einer Spalte vom Typ `xml` in einer Tabelle eine standardmäßige XML-Instanz zuweisen. Sie können das Standard-XML auf zweierlei Weise bereitstellen: durch Verwenden einer XML-Konstante oder durch Verwenden einer expliziten Umwandlung in den `xml`-Typ.  
  
 Um das Standard-XML als XML-Konstante bereitzustellen, verwenden Sie die im folgenden Beispiel gezeigte Syntax. Beachten Sie, dass die Zeichenfolge implizit in den `xml`-Typ umgewandelt wird (durch CAST).  
  
```  
CREATE TABLE T (XmlColumn xml default N'<element1/><element2/>')  
```  
  
 Um das Standard-XML als explizites `CAST` in `xml`bereitzustellen, verwenden Sie die im folgenden Beispiel gezeigte Syntax.  
  
```  
CREATE TABLE T (XmlColumn xml   
                  default CAST(N'<element1/><element2/>' AS xml))  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt auch NULL- und NOT NULL-Einschränkungen für Spalten vom Typ `xml`. Beispiel:  
  
```  
CREATE TABLE T (XmlColumn xml NOT NULL)  
```  
  
## <a name="specifying-constraints"></a>Angeben von Einschränkungen  
 Beim Erstellen von Spalten vom Typ `xml` können Sie auf Spalten- oder Tabellenebene Einschränkungen definieren. Verwenden Sie Einschränkungen in den folgenden Situationen:  
  
-   Ihre Geschäftsrichtlinien können nicht in XML-Schemas ausgedrückt werden. Beispielsweise muss sich die Lieferadresse eines Blumenladens in einem Umkreis von 50 Kilometern zum Ladenstandort befinden. Dies kann in Form einer Einschränkung für die XML-Spalte formuliert werden. Die Einschränkung kann `xml`-Datentypmethoden einbeziehen.  
  
-   Ihre Einschränkung bezieht andere XML- oder Nicht-XML-Spalten in der Tabelle ein. Beispielsweise, wenn die Übereinstimmung der ID eines in einer XML-Instanz gefundenen Kunden (`/Customer/@CustId`) mit dem Wert in einer relationalen CustomerID-Spalte erzwungen werden soll.  
  
 Sie können Einschränkungen für typisierte oder nicht typisierte Spalten des `xml`-Datentyps eingegeben. Die [XML-Datentypmethoden](/sql/t-sql/xml/xml-data-type-methods) können jedoch beim Angeben von Einschränkungen nicht verwendet werden. Beachten Sie zudem, dass der `xml`-Datentyp die folgenden Spalten- und Tabelleneinschränkungen nicht unterstützt:  
  
-   PRIMARY KEY/ FOREIGN KEY  
  
-   UNIQUE  
  
-   COLLATE  
  
     XML stellt eine eigene Codierung bereit. Sortierungen gelten nur für Zeichenfolgentypen. Der `xml`-Datentyp stellt keinen Zeichenfolgentyp dar. Er besitzt jedoch die Zeichenfolgendarstellung und ermöglicht das Umwandeln in und aus Zeichenfolgen-Datentypen.  
  
-   RULE  
  
 Eine Alternative zur Verwendung von Einschränkungen ist die Erstellung eines Wrappers, einer benutzerdefinierten Funktion, um die Methode des `xml`-Datentyps einzubinden und die benutzerdefinierte Funktion in der CHECK-Einschränkung anzugeben, wie im folgenden Beispiel zu sehen ist.  
  
 Im folgenden Beispiel gibt die Einschränkung für `Col2` an, dass jede der in dieser Spalte gespeicherten XML-Instanzen ein `<ProductDescription>` -Element aufweisen muss, das ein `ProductID` -Attribut enthält. Diese Einschränkung wird durch folgende benutzerdefinierte Funktion erzwungen:  
  
```  
CREATE FUNCTION my_udf(@var xml) returns bit  
AS BEGIN   
RETURN @var.exist('/ProductDescription/@ProductID')  
END  
GO  
```  
  
 Beachten Sie, dass die `exist()` -Methode des `xml` -Datentyps `1` zurückgibt, wenn das `<ProductDescription>` -Element der Instanz das `ProductID` -Attribut enthält. Andernfalls wird `0`zurückgegeben.  
  
 Jetzt können Sie eine Tabelle mit einer Einschränkung auf Spaltenebene erstellen, wie im Folgenden gezeigt:  
  
```  
CREATE TABLE T (  
    Col1 int primary key,   
    Col2 xml check(dbo.my_udf(Col2)=1))  
GO  
```  
  
 Die folgende Einfügung wird erfolgreich ausgeführt:  
  
```  
INSERT INTO T values(1,'<ProductDescription ProductID="1" />')  
```  
  
 Aufgrund der Einschränkung erzeugt die folgende Einfügung einen Fehler:  
  
```  
INSERT INTO T values(1,'<Product />')  
```  
  
## <a name="same-or-different-table"></a>Gleiche oder unterschiedliche Tabelle  
 Eine- `xml` Datentyp Spalte kann in einer Tabelle erstellt werden, die andere relationale Spalten enthält, oder in einer separaten Tabelle mit einer Fremdschlüssel Beziehung zu einer Haupttabelle.  
  
 Erstellen Sie eine- `xml` Datentyp Spalte in derselben Tabelle, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Ihre Anwendung führt einen Datenabruf für die XML-Spalte durch und benötigt keinen XML-Index für die XML-Spalte.  
  
-   Sie möchten einen XML-Index für die `xml`-Datentypspalte erstellen, und der Primärschlüssel der Haupttabelle ist derselbe wie ihr Gruppierungsschlüssel. Weitere Informationen finden Sie unter [XML-Indizes &#40;SQL Server&#41;](xml-indexes-sql-server.md).  
  
 Erstellen Sie die `xml`-Datentypspalte in einer getrennten Tabelle, wenn die folgenden Bedingungen zutreffen:  
  
-   Sie möchten einen XML-Index für die `xml`-Datentypspalte erstellen, der Primärschlüssel der Haupttabelle unterscheidet sich jedoch von ihrem Gruppierungsschlüssel, oder die Haupttabelle besitzt keinen Primärschlüssel, oder die Haupttabelle ist ein Heap (kein Gruppierungsschlüssel). Das kann der Fall sein, wenn die Haupttabelle bereits vorhanden ist.  
  
-   Sie wollen vermeiden, dass Tabellenscans verlangsamt werden, weil die XML-Spalte in der Tabelle vorhanden ist. Dies beansprucht Speicherplatz, unabhängig davon, ob die Speicherung innerhalb oder außerhalb der Zeile erfolgt.  
  
  
