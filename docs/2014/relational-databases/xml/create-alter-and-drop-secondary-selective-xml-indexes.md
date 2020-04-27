---
title: Erstellen, Ändern und Löschen sekundärer, selektiver XML-Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b96e0bb7f28349e4d0b0ed5225f9b29e58de982f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62637847"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a>Erstellen, Ändern und Löschen sekundärer, selektiver XML-Indizes
  Beschreibt, wie ein neuer sekundärer, selektiver XML-Index erstellt bzw. ein vorhandener sekundärer, selektiver XML-Index geändert oder gelöscht wird.  
  
##  <a name="creating-a-secondary-selective-xml-index"></a><a name="create"></a> Erstellen eines sekundären, selektiven XML-Indexes  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a>Vorgehensweise: Erstellen eines sekundären, selektiven XML-Indexes  
 **Erstellen eines sekundären, selektiven XML-Indexes mit Transact-SQL**  
 Erstellen Sie einen sekundären, selektiven XML-Index, indem Sie die CREATE XML INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [CREATE XML Index &#40;Selective XML Indexes&#41;] (~/t-SQL/Statements/CREATE-XML-Index-Selective-XML-Indexes.  
  
 **Beispiel**  
  
 Im folgenden Beispiel wird ein sekundärer selektiver XML-Index für den Pfad `'pathabc'`erstellt. Der zu indizierende Pfad wird anhand des Namens identifiziert, der ihm bei der Erstellung durch die CREATE SELECTIVE XML INDEX-Anweisung zugewiesen wurde. Weitere Informationen finden Sie unter [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).  
  
```sql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="altering-a-secondary-selective-xml-index"></a><a name="alter"></a> Ändern eines sekundären, selektiven XML-Indexes  
 Die ALTER-Anweisung wird für sekundäre, selektive XML-Indizes nicht unterstützt. Um einen sekundären, selektiven XML-Index zu ändern, löschen Sie den vorhandenen Index und erstellen ihn erneut.  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a>Vorgehensweise: Ändern eines sekundären, selektiven XML-Indexes  
 **Ändern eines sekundären, selektiven XML-Indexes mit Transact-SQL**  
 1.  Löschen Sie den vorhandenen sekundären, selektiven XML-Index, indem Sie die DROP INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [DROP INDEX &#40;selektive XML-Indizes&#41;](../indexes/indexes.md).  
  
2.  Erstellen Sie den Index mit den gewünschten Optionen neu, indem Sie die CREATE XML INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [CREATE XML Index &#40;Selective XML Indexes&#41;] (~/t-SQL/Statements/CREATE-XML-Index-Selective-XML-Indexes.  
  
 **Beispiel**  
  
 Im folgenden Beispiel wird ein sekundärer, selektiver XML-Index geändert, indem er gelöscht und neu erstellt wird.  
  
```sql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="dropping-a-secondary-selective-xml-index"></a><a name="drop"></a> Löschen eines sekundären, selektiven XML-Indexes  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a>Vorgehensweise: Löschen eines sekundären, selektiven XML-Indexes  
 **Löschen eines sekundären, selektiven XML-Indexes mit Transact-SQL**  
 Löschen Sie einen sekundären, selektiven XML-Index, indem Sie die DROP INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [DROP INDEX &#40;selektive XML-Indizes&#41;](../indexes/indexes.md).  
  
 **Beispiel**  
  
 Im folgenden Beispiel wird eine DROP INDEX-Anweisung veranschaulicht.  
  
```sql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Selektive XML-Indizes &#40;SXI&#41;](selective-xml-indexes-sxi.md)  
  
  
