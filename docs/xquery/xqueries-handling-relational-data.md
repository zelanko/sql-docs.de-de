---
title: XQuery-Abfragen verarbeiten von relationalen Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- relational data [XQuery]
- XQuery, relational data
ms.assetid: 9812b71a-52ec-48a0-92f3-016a93660229
author: rothja
ms.author: jroth
ms.openlocfilehash: ed4583b30ed1e4538a36079f9f7794704b819cda
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946167"
---
# <a name="xqueries-handling-relational-data"></a>Behandlung relationaler Daten mit XQuery-Abfragen
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Sie geben die XQuery-Abfrage für eine **Xml** -Typspalte oder-Variable mithilfe einer der der [XML-Datentypmethoden](../t-sql/xml/xml-data-type-methods.md). Dazu gehören **query()** , **Value()-Methode**, **exist()** , oder **modify()** . Die XQuery wird für die XML-Instanz ausgeführt, die in der XML generierenden Abfrage angegeben ist.  
  
 XML, das durch Ausführen einer XQuery-Abfrage erzeugt wird, kann Werte enthalten, die aus anderen Transact-SQL-Variablen oder aus Rowsetspalten abgerufen werden. Um relationale Nicht-XML-Daten an das XML-Ergebnis zu binden, bietet SQL Server die folgenden Pseudofunktionen als XQuery-Erweiterungen:  
  
-   **SQL:Column()** Funktion  
  
-   **sql:variable()** function  
  
 Sie können diese XQuery-Erweiterungen verwenden, beim Angeben einer XQuery-Abfrage in der **query()** -Methode der der **Xml** -Datentyp. Daher die **query()** erzeugt die Methode kann XML, das Daten von XML- und nicht-kombiniert-**Xml** -Datentypen.  
  
 Sie können diese Funktionen auch verwenden, bei der Verwendung der **Xml** -Datentypmethoden **modify()** , **Value()-Methode**, **query()** , und  **EXIST()** zum Verfügbarmachen eines relationalen Werts in XML.  
  
 Weitere Informationen finden Sie unter [SQL:Column()-Funktion (XQuery)](../xquery/xquery-extension-functions-sql-column.md) und [SQL:Variable()-Funktion (XQuery)](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Daten &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery-Sprachreferenz &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [XML-Konstruktion &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)  
  
  
