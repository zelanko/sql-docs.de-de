---
title: local-name-from-QName (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name-from-QName function
- local-name-from-QName function
ms.assetid: fafed718-8c3c-403f-93ee-ec51fc157a6e
author: rothja
ms.author: jroth
ms.openlocfilehash: 765d412b9f3f0395a9bca6fd52c74135ddde3ff4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68004560"
---
# <a name="functions-related-to-qnames---local-name-from-qname"></a>Funktionen, die sich auf QNames beziehen – local-name-from-QName
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt einen xs: NCName zurück, der den lokalen Teil von QName darstellt, der durch *$arg*angegeben wird. Das Ergebnis ist eine leere Sequenz, wenn *$arg* die leere Sequenz ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
fn:local-name-from-QName($arg as xs:QName?) as xs:NCName?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Der QName, aus dem der lokale Name extrahiert werden soll.  
  
## <a name="examples"></a>Beispiele  
 Dieses Thema stellt XQuery-Beispiele für XML-Instanzen bereit, die **xml** in verschiedenen Spalten vom Typ [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] XML in der-Datenbank gespeichert sind.  
  
 Im folgenden Beispiel wird die **local-name-from-QName ()-** Funktion verwendet, um die lokalen Namen und Namespace-URI-Teile aus einem QName-Typwert abzurufen. Das Beispiel führt die folgenden Aktionen aus:  
  
-   Erstellen einer XML-Schemaauflistung.  
  
-   Erstellen einer Tabelle mit einer Spalte des Typs xml. Der xml-Typ wird mithilfe der XML-Schemaauflistung typisiert.  
  
-   Speichern einer XML-Beispielinstanz in der Tabelle. Mithilfe der **Query ()** -Methode des XML-Datentyps wird der Abfrage Ausdruck ausgeführt, um den lokalen Namensteil des QName-typwerts aus der-Instanz abzurufen.  
  
```sql
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="root" type="QName" nillable="true"/>  
</schema>'  
go  
  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<root xmlns="QNameXSD" xmlns:a="https://someURI">a:someLocalName</root>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare default element namespace "QNameXSD"; local-name-from-QName(/root[1])')  
FROM T  
-- Result = someLocalName  
-- You can retrieve namespace URI part from the QName using the namespace-uri-from-QName() function  
SELECT xmlCol.query('declare default element namespace "QNameXSD"; namespace-uri-from-QName(/root[1])')  
FROM T  
-- Result = https://someURI  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen im Zusammenhang mit QNames &#40;XQuery-&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
