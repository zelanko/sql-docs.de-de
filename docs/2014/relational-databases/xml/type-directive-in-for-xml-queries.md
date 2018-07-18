---
title: TYPE-Direktive in FOR XML-Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2868591cbb80cfb39eaaa81d6cbe75d2bda08c6d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294220"
---
# <a name="type-directive-in-for-xml-queries"></a>TYPE-Direktive in FOR XML-Abfragen
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Unterstützung für die [Xml &#40;Transact-SQL&#41; ](/sql/t-sql/xml/xml-transact-sql) können Sie optional anzufordern, die das Ergebnis einer FOR XML-Abfrage, als zurückgegeben werden `xml` Datentyp durch Angeben der TYPE-Direktive. Dies ermöglicht Ihnen, das Ergebnis einer FOR XML-Abfrage auf dem Server zu verarbeiten. Sie können beispielsweise eine XQuery dafür angeben, weisen Sie das Ergebnis einer `xml` Variablen vom Typ, oder schreiben [geschachtelte FOR XML-Abfragen](use-nested-for-xml-queries.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gibt Daten an den Client als Ergebnis verschiedener Server-serverkonstrukte wie FOR XML-Abfragen, die die TYPE-Direktive verwenden, oder bei denen die `xml` -Datentyp wird verwendet, um die XML-instanzdatenwerte aus SQL-Tabellenspalten und Ausgabe zurückzugeben Parameter. Im Code der Clientanwendung erfordert der ADO.NET-Anbieter, dass die Informationen vom XML-Datentyp im Binärcode vom Server gesendet werden. Wenn Sie jedoch FOR XML ohne die TYPE-Direktive verwenden, werden die XML-Daten als Zeichenfolgentyp zurückgesendet. Der Clientanbieter ist in jedem Fall fähig, beide XML-Formate zu verarbeiten. Beachten Sie, dass FOR XML der obersten Ebene ohne die TYPE-Direktive nicht mit Cursorn verwendet werden kann.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele veranschaulichen die Verwendung der TYPE-Direktive für FOR XML-Abfragen.  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a>Abrufen von FOR XML-Abfrageergebnissen als XML-Typ  
 Die folgende Abfrage ruft Informationen zu Kundenkontakten aus der `Contacts` -Tabelle auf. In `TYPE` ist die `FOR XML`-Direktive angegeben, daher wird das Ergebnis als `xml`-Typ zurückgegeben.  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 Dies ist das Teilergebnis:  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a>Zuweisen von FOR XML-Abfrageergebnissen zu einer Variablen vom Typ XML  
 Im folgenden Beispiel einer FOR XML-Ergebnis zugewiesen wird ein `xml` Variablen vom Typ `@x`. Die Abfrage ruft Kontaktinformationen, z. B. die `BusinessEntityID`, `FirstName`, `LastName`, sowie zusätzliche Telefonnummern aus den `AdditionalContactInfo` Spalte `xml``TYPE`. Die XML-Daten werden als `xml`-Typ zurückgegeben, da in der `FOR XML`-Klausel die `TYPE`-Direktive angegeben ist, und anschließend einer Variablen zugewiesen.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a>Abfragen von Ergebnissen einer FOR XML-Abfrage  
 FOR XML-Abfragen geben XML-Daten zurück. Sie können daher anwenden `xml` Datentypmethoden, z. B. `query()` und `value()`, auf das von FOR XML-Abfragen zurückgegebene XML-Ergebnis.  
  
 In der folgenden Abfrage wird der `query()` Methode der `xml` -Datentyp wird verwendet, um das Ergebnis der `FOR XML` Abfrage. Weitere Informationen finden Sie unter [query&#40;&#41;-Methode &#40;xml-Datentyp&#41;](/sql/t-sql/xml/query-method-xml-data-type).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 Die innere `SELECT … FOR XML` Abfrage gibt ein `xml` geben das Ergebnis der äußeren `SELECT` gilt die `query()` Methode, um die `xml` Typ. Beachten Sie, dass die `TYPE` -Direktive angegeben ist.  
  
 Dies ist das Ergebnis:  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 In der folgenden Abfrage wird die `value()`-Methode vom Datentyp `xml` verwendet, um einen Wert aus dem XML-Ergebnis einer `SELECT…FOR XML`-Abfrage abzurufen. Weitere Informationen finden Sie unter [value&#40;&#41;-Methode &#40;xml-Datentyp&#41;](/sql/t-sql/xml/value-method-xml-data-type).  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 Der XQuery-Pfadausdruck in der `value()` -Methode ruft die erste Telefonnummer des Kundenkontakts mit der `BusinessEntityID` `1`ab.  
  
> [!NOTE]  
>  Wenn die TYPE-Direktive nicht angegeben ist, wird das FOR XML-Abfrageergebnis als Typ zurückgegeben `nvarchar(max)`.  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a>Verwenden von FOR XML-Abfrageergebnissen in INSERT-, UPDATE- und DELETE-Anweisungen (Transact-SQL-DML)  
 Das folgende Beispiel stellt dar, wie FOR XML-Abfragen in DML-Anweisungen (DML, Data Manipulation Language) verwendet werden können. Im Beispiel die `FOR XML` gibt eine Instanz des `xml` Typ. Die `INSERT` -Anweisung fügt diese XML-Daten in eine Tabelle ein.  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [FOR XML &#40;SQL Server&#41;](../xml/for-xml-sql-server.md)  
  
  
