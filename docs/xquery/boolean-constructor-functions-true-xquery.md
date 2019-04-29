---
title: "\"true\"-Funktion (XQuery) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:true function
- true function
ms.assetid: 318e370d-0444-4812-afe4-307df7ef9f3b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 611d23ad84df3087a259cbaf60870129b841715b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63047614"
---
# <a name="boolean-constructor-functions---true-xquery"></a>Boolesche Konstruktorfunktionen – true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den xs:boolean-Wert True zurück. Dieser entspricht `xs:boolean("1")`.  
  
## <a name="syntax"></a>Syntax  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. Verwenden der XQuery Boolean-Funktion true()  
 Das folgende Beispiel fragt eine nicht typisierte **Xml** Variable. Der Ausdruck in der **Value()-Methode** Methode gibt den booleschen Wert **TRUE()"** ist"aaa"den Wert des Attributs. Die **Value()-Methode** Methode der **Xml** -Datentyp konvertiert den booleschen Wert in einen Bitwert und gibt sie zurück.  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 Im folgenden Beispiel wird die Abfrage angegeben für eine typisierte **Xml** Spalte. Die `if` -Ausdruck überprüft den typisierten booleschen Wert, der die <`ROOT`>-Element und gibt Sie den konstruierten XML-Code entsprechend zurück. Das Beispiel führt die folgenden Aktionen aus:  
  
-   Erstellt eine XML-schemaauflistung, die definiert die <`ROOT`>-Element des Typs xs: Boolean.  
  
-   Erstellt eine Tabelle mit typisierter **Xml** Spalte, indem Sie die XML-schemaauflistung.  
  
-   Speichert eine XML-Instanz in der Spalte und fragt sie ab.  
  
```  
-- Drop table if exist  
--DROP TABLE T  
--go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="ROOT" type="boolean" nillable="true"/>  
</schema>'  
go  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<ROOT xmlns="QNameXSD">true</ROOT>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare namespace a="QNameXSD";   
   if (/a:ROOT[1] eq true()) then  
       <result>Found boolean true</result>  
   else  
       <result>Found boolean false</result>')  
  
FROM T  
-- result = <result>Found boolean true</result>  
-- Clean up  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Boolesche Konstruktorfunktionen &#40;XQuery&#41;](https://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  
