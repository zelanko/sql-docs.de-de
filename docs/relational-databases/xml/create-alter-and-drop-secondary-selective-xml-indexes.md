---
title: Erstellen, Ändern und Löschen sekundärer selektiver XML-Indizes | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
ms.openlocfilehash: f86ff1eb81984414afaee99bd8fc76525825c219
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664624"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a>Erstellen, Ändern und Löschen sekundärer, selektiver XML-Indizes
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Beschreibt, wie ein neuer sekundärer, selektiver XML-Index erstellt bzw. ein vorhandener sekundärer, selektiver XML-Index geändert oder gelöscht wird.  
  
##  <a name="creating-a-secondary-selective-xml-index"></a><a name="create"></a> Erstellen eines sekundären, selektiven XML-Indexes  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a>Vorgehensweise: Erstellen eines sekundären, selektiven XML-Indexes  
 **Erstellen eines sekundären, selektiven XML-Indexes mit Transact-SQL**  
 Erstellen Sie einen sekundären, selektiven XML-Index, indem Sie die CREATE XML INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [CREATE XML INDEX &#40;selektive XML-Indizes&#41;](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
 **Beispiel**  
  
 Im folgenden Beispiel wird ein sekundärer selektiver XML-Index für den Pfad `'pathabc'`erstellt. Der zu indizierende Pfad wird anhand des Namens identifiziert, der ihm bei der Erstellung durch die CREATE SELECTIVE XML INDEX-Anweisung zugewiesen wurde. Weitere Informationen finden Sie unter [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
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
 1.  Löschen Sie den vorhandenen sekundären, selektiven XML-Index, indem Sie die DROP INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [DROP INDEX &#40;selektive XML-Indizes&#41;](../../t-sql/statements/drop-index-selective-xml-indexes.md).  
  
2.  Erstellen Sie den Index mit den gewünschten Optionen neu, indem Sie die CREATE XML INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [CREATE XML INDEX &#40;selektive XML-Indizes&#41;](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
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
 Löschen Sie einen sekundären, selektiven XML-Index, indem Sie die DROP INDEX-Anweisung aufrufen. Weitere Informationen finden Sie unter [DROP INDEX &#40;selektive XML-Indizes&#41;](../../t-sql/statements/drop-index-selective-xml-indexes.md).  
  
 **Beispiel**  
  
 Im folgenden Beispiel wird eine DROP INDEX-Anweisung veranschaulicht.  
  
```sql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Selektive XML-Indizes &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  
