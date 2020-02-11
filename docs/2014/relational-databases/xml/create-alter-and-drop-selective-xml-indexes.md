---
title: Erstellen, Ändern und Löschen selektiver XML-Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a95fa1c010197d0107c757198d9db7eaf8d3c42e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62637598"
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a>Erstellen, Ändern und Löschen selektiver XML-Indizes
  Beschreibt, wie ein neuer selektiver XML-Index erstellt bzw. ein vorhandener selektiver XML-Index geändert oder gelöscht wird.  
  
 Weitere Informationen über selektive XML-Indizes finden Sie unter [Selektive XML-Indizes &#40;SXI&#41;](selective-xml-indexes-sxi.md).  
  
##  <a name="create"></a> Erstellen eine selektiven XML-Indexes  
  
### <a name="how-to-create-a-selective-xml-index"></a>Vorgehensweise: Erstellen eines selektiven XML-Indexes  
 **Erstellen eines selektiven XML-Indexes mit Transact-SQL**  
 Erstellen Sie einen selektiven XML-Index, indem Sie die CREATE SELECTIVE XML INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).  
  
 **Beispiel**  
  
 Im folgenden Beispiel wird die Syntax zum Erstellen eines selektiven XML-Indexes veranschaulicht. Zudem werden mehrere Variationen der Syntax, die die zu indizierenden Pfade beschreibt, mit optionalen Optimierungshinweisen angegeben.  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
  
##  <a name="alter"></a> Ändern eines selektiven XML-Indexes  
  
### <a name="how-to-alter-a-selective-xml-index"></a>Vorgehensweise: Ändern eines selektiven XML-Indexes  
 **Ändern eines selektiven XML-Indexes mit Transact-SQL**  
 Ändern Sie einen vorhandenen selektiven XML-Index, indem Sie die ALTER INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [ALTER INDEX &#40;selektive XML-Indizes&#41;](../indexes/indexes.md).  
  
 **Beispiel**  
  
 Im folgenden Beispiel wird eine ALTER INDEX-Anweisung veranschaulicht. Mit dieser Anweisung wird der Pfad `'/a/b/m'` dem XQuery-Teil des Indexes hinzugefügt und der Pfad `'/a/b/e'` vom SQL-Teil des Indexes, der im Beispiel im Thema [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql) erstellt wurde, gelöscht. Der zu löschende Pfad ist anhand des Namens zu erkennen, der ihm bei der Erstellung zugewiesen wurde.  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
  
##  <a name="drop"></a> Löschen eines selektiven XML-Indexes  
  
### <a name="how-to-drop-a-selective-xml-index"></a>Vorgehensweise: Löschen eines selektiven XML-Indexes  
 **Löschen eines selektiven XML-Indexes mit Transact-SQL**  
 Löschen Sie einen selektiven XML-Index, indem Sie die DROP INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [DROP INDEX &#40;selektive XML-Indizes&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes).  
  
 **Beispiel**  
  
 Im folgenden Beispiel wird eine DROP INDEX-Anweisung veranschaulicht.  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
 
  
  
