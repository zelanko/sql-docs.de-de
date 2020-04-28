---
title: Update-, DELETE-und INSERT-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f12682a5d012d6981afce0085e9c920ed2f2ffbc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284260"
---
# <a name="update-delete-and-insert-statements"></a>UPDATE-, DELETE- und INSERT-Anweisungen
SQL-basierte Anwendungen nehmen Änderungen an den Tabellen vor, indem Sie die Anweisungen **Update**, **Delete**und **Insert** ausführen. Diese Anweisungen sind Teil der minimalen Konformität der SQL-Grammatik und müssen von allen Treibern und Datenquellen unterstützt werden.  
  
 Die Syntax dieser Anweisungen lautet wie folgt:  
  
 **UPDATE** _Tabellennamen_ aktualisieren  
  
 **Festlegen** des _Spalten Bezeichners_ **=** {*Expression* &#124; **null**}  
  
 [**,** _Spalten Bezeichner_ **=** {*Expression* &#124; **null**}]...  
  
 [**Where** _Such Bedingung_]  
  
 **Delete from** _Table-Name_[**Where** _Search-Condition_]  
  
 **INSERT INTO** _Table-Name_[**(** _Spalten-_ ID [**,** _Spalten-_ ID]... **)**]  
  
 {*Query-Specification* &#124; **Werte (** _Insert-Value_ [**,** _Insert-Value_]... **)**}  
  
 Beachten Sie, dass das *Query-Specification-* Element nur in den Core-und erweiterten SQL-Grammatiken gültig ist und dass der *Ausdruck* und die *Such* Bedingungs Elemente in den Kern-und erweiterten SQL-Grammatiken komplexer werden.  
  
 Wie andere SQL-Anweisungen sind **Update**-, **Delete**-und **Insert** -Anweisungen häufig effizienter, wenn Sie Parameter verwenden. Beispielsweise kann die folgende Anweisung vorbereitet und wiederholt ausgeführt werden, um mehrere Zeilen in die Tabelle Orders einzufügen:  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Diese Effizienz kann durch Übergeben von Arrays von Parameterwerten gesteigert werden. Weitere Informationen zu Anweisungs Parametern und Arrays von Parameterwerten finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md).
