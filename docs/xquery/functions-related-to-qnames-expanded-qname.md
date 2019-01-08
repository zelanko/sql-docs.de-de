---
title: Expanded-QName (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- expanded-QName function
- fn:expanded-QName function
ms.assetid: b8377042-95cc-467b-9ada-fe43cebf4bc3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6715c89ff3086f5031e2554929aced39d6f135db
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52501906"
---
# <a name="functions-related-to-qnames---expanded-qname"></a>Funktionen, die sich auf QNames beziehen – expanded-QName
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt einen Wert vom Typ xs: QName mit dem angegebenen Namespace-URI in der *$paramURI* und dem lokalen Namen, die im angegebenen die *$paramLocal*. Wenn *$paramURI* die leere Zeichenfolge oder leere Sequenz ist, ist es kein Namespace darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
fn:expanded-QName($paramURI as xs:string?, $paramLocal as xs:string?) as xs:QName?  
```  
  
## <a name="arguments"></a>Argumente  
 *$paramURI*  
 Der Namespace-URI (Universal Resource Identifier) für QName.  
  
 *$paramLocal*  
 Der lokale Teil des Namens von QName.  
  
## <a name="remarks"></a>Hinweise  
 Die folgenden Informationen gelten für die **expanded-QName()** Funktion:  
  
-   Wenn die *$paramLocal* angegebene Wert nicht in der lexikalisch richtigen Form für xs: NCName-Typ, die leere Sequenz zurückgegeben, und stellt einen dynamischen Fehler.  
  
-   Das Konvertieren des Typs xs:QName in andere Typen wird in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht unterstützt. Aus diesem Grund die **expanded-QName()** Funktion kann nicht in XML-Konstruktion verwendet werden. Wenn Sie beispielsweise einen Knoten wie `<e> expanded-QName(...) </e>` konstruieren, darf der Wert nicht typisiert sein. Um dies zu erreichen, müssten Sie den von `expanded-QName()` zurückgegebenen Wert vom Typ xs:QName in xdt:untypedAtomic konvertieren. Dies wird jedoch nicht unterstützt. Eine Lösungsmöglichkeit wird nachfolgend in diesem Thema bereitgestellt.  
  
-   Sie können vorhandene Werte vom Typ QName ändern oder vergleichen. Z. B. `/root[1]/e[1] eq expanded-QName("https://nsURI" "myNS")` vergleicht den Wert des Elements <`e`>, mit der vom QName der **expanded-QName()** Funktion.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** -Typspalten in der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] Datenbank.  
  
### <a name="a-replacing-a-qname-type-node-value"></a>A. Ersetzen eines Knotenwerts vom Typ QName  
 In diesem Beispiel wird veranschaulicht, wie Sie den Wert eines Elementknotens vom Typ QName ändern können. Das Beispiel führt die folgenden Aktionen aus:  
  
-   Erstellen einer XML-Schemaauflistung, die ein Element vom Typ QName definiert.  
  
-   Erstellt eine Tabelle mit einer **Xml** Type-Spalte, indem Sie die XML-schemaauflistung.  
  
-   Speichern einer XML-Instanz in der Tabelle.  
  
-   Verwendet die **modify()** -Methode der Xml-Datentyps zum Ändern des Werts des Elements vom Typ QName in der Instanz. Die **expanded-QName()** Funktion wird verwendet, um den neuen Wert der QName-Typ zu generieren.  
  
```  
-- If XML schema collection (if exists)  
-- drop xml schema collection SC  
-- go  
-- Create XML schema collection  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="https://www.w3.org/2001/XMLSchema"  
    xmlns:xs="https://www.w3.org/2001/XMLSchema"   
    targetNamespace="QNameXSD"   
      xmlns:xqo="QNameXSD" elementFormDefault="qualified">  
      <element name="Root" type="xqo:rootType" />  
      <complexType name="rootType">  
            <sequence minOccurs="1" maxOccurs="1">  
                        <element name="ElemQN" type="xs:QName" />  
            </sequence>  
      </complexType>  
</schema>'  
go  
-- Create table.  
CREATE TABLE T( XmlCol xml(SC) )  
-- Insert sample XML instnace  
INSERT INTO T VALUES ('  
<Root xmlns="QNameXSD" xmlns:ns="https://myURI">  
      <ElemQN>ns:someName</ElemQN>  
</Root>')  
go  
-- Verify the insertion  
SELECT * from T  
go  
-- Result  
<Root xmlns="QNameXSD" xmlns:ns="https://myURI">  
  <ElemQN>ns:someName</ElemQN>  
</Root>   
```  
  
 In der folgenden Abfrage wird die <`ElemQN`> Wert des Elements wird mithilfe von ersetzt die **modify()** -Methode der Xml-Datentyps und des Replace Value of XML DML angezeigt.  
  
```  
-- the value.  
UPDATE T   
SET XmlCol.modify('  
  declare default element namespace "QNameXSD";   
  replace value of /Root[1]/ElemQN   
  with expanded-QName("https://myURI", "myLocalName") ')  
go  
-- Verify the result  
SELECT * from T  
go  
```  
  
 Dies ist das Ergebnis. Beachten Sie, dass das <`ElemQN`>-Element vom Typ QName jetzt über einen neuen Wert verfügt:  
  
```  
<Root xmlns="QNameXSD" xmlns:ns="urn">  
  <ElemQN xmlns:p1="https://myURI">p1:myLocalName</ElemQN>  
</Root>  
```  
  
 Die folgenden Anweisungen entfernen die in diesem Beispiel verwendeten Objekte.  
  
```  
-- Cleanup  
DROP TABLE T  
go  
drop xml schema collection SC  
go  
```  
  
### <a name="b-dealing-with-the-limitations-when-using-the-expanded-qname-function"></a>B. Umgehend mit den Einschränkungen bei Verwendung der erweiterten QName()-Funktion  
 Die **expanded-QName** Funktion kann nicht in XML-Konstruktion verwendet werden. Dies wird anhand des folgenden Beispiels veranschaulicht. Im Beispiel wird zuerst ein Knoten eingefügt, um diese Einschränkung zu umgehen, und dann wird der Knoten geändert.  
  
```  
-- if exists drop the table T  
--drop table T  
-- go  
-- Create XML schema collection  
-- DROP XML SCHEMA COLLECTION SC  
-- go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="https://www.w3.org/2001/XMLSchema">  
      <element name="root" type="QName" nillable="true"/>  
</schema>'  
go  
 -- Create table T with a typed xml column (using the XML schema collection)  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- Insert an XML instance.  
insert into T values ('<root xmlns:a="https://someURI">a:b</root>')  
 go  
-- Verify  
SELECT *   
FROM T  
```  
  
 Im folgenden Versuch wird ein weiteres <`root`>-Element hinzugefügt. Dadurch wird jedoch ein Fehler erzeugt, da die erweiterte QName()-Funktion in der XML-Konstruktion nicht unterstützt wird.  
  
```  
update T SET xmlCol.modify('  
insert <root>{expanded-QName("https://ns","someLocalName")}</root> as last into / ')  
go  
```  
  
 Dies kann vermieden werden, indem zunächst eine Instanz mit einem Wert für das <`root`>-Element eingefügt und anschließend bearbeitet wird. In diesem Beispiel wird zunächst ein Nullwert verwendet, wenn das <`root`>-Element eingefügt wird. Die XML-Schemaauflistung in diesem Beispiel lässt einen Nullwert für das <`root`>-Element zu.  
  
```  
update T SET xmlCol.modify('  
insert <root xsi:nil="true"/> as last into / ')  
go  
-- now replace the nil value with another QName.  
update T SET xmlCol.modify('  
replace value of /root[last()] with expanded-QName("https://ns","someLocalName") ')  
go  
 -- verify   
SELECT * FROM T  
go  
-- result  
<root>b</root>  
```  
  
 `<root xmlns:a="https://someURI">a:b</root>`  
  
 `<root xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:p1="https://ns">p1:someLocalName</root>`  
  
 Sie können den Wert für QName vergleichen, wie in der folgenden Abfrage gezeigt: Die Abfrage gibt nur die <`root`> andere Elemente, deren Werte den QName entsprechen-Typs von zurückgegebene Wert die **expanded-QName()** Funktion.  
  
```  
SELECT xmlCol.query('  
    for $i in /root  
    return  
       if ($i eq expanded-QName("https://ns","someLocalName") ) then  
          $i  
       else  
          ()')  
FROM T  
```  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Es gibt eine Einschränkung: Die **expanded-QName()** -Funktion die leere Sequenz als zweites Argument akzeptiert und gibt zurück, statt einen Laufzeitfehler auszulösen, wenn das zweite Argument fehlerhaft ist leer.  
  
## <a name="see-also"></a>Siehe auch  
 [Functions Related to QNames sich &#40;XQuery&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
