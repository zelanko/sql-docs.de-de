---
title: UPDATE-, DELETE- und INSERT-Anweisungen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284260"
---
# <a name="update-delete-and-insert-statements"></a>UPDATE-, DELETE- und INSERT-Anweisungen
SQL-basierte Anwendungen nehmen Änderungen an Tabellen vor, indem sie die **Anweisungen UPDATE**, **DELETE**und **INSERT** ausführen. Diese Anweisungen sind Teil der Mindest-SQL-Grammatikkonformitätsstufe und müssen von allen Treibern und Datenquellen unterstützt werden.  
  
 Die Syntax dieser Anweisungen lautet:  
  
 **UPDATE** _UPDATE-Tabellenname_  
  
 **SET** SET-Spaltenbezeichner _column-identifier_ **=** -*Ausdruck* &#124; **NULL**  
  
 [**,** _Spaltenbezeichner_ **=** -*Ausdruck* &#124; **NULL**]...  
  
 [**WHERE** _Suchbedingung_]  
  
 **DELETE FROM** _Tabellenname_[**WHERE** _such-condition_]  
  
 **INSERT INTO** _Tabellenname_[**(** _Spaltenbezeichner_ [**,** _Spaltenbezeichner_]... **)**]  
  
 •*Abfragespezifikation* &#124; **VALUES (** _Insert-Wert_ [**,** _Insert-Wert_]... **)**}  
  
 Beachten Sie, dass das *Abfragespezifikationselement* nur in den Grammatiken Core und Extended SQL gültig ist und dass die *Ausdrucks-* und Suchbedingungselemente in den Core- und Extended *SQL-Grammatiken* komplexer werden.  
  
 Wie andere SQL-Anweisungen sind **UPDATE**-, **DELETE-** und **INSERT-Anweisungen** oft effizienter, wenn sie Parameter verwenden. Die folgende Anweisung kann z. B. vorbereitet und wiederholt ausgeführt werden, um mehrere Zeilen in die Tabelle Orders einzufügen:  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Diese Effizienz kann durch Übergeben von Arrays von Parameterwerten erhöht werden. Weitere Informationen zu Anweisungsparametern und Arrays von Parameterwerten finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md).
