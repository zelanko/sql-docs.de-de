---
title: UPDATE, DELETE und INSERT-Anweisungen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00732de7eca32dc8b2984fdda14163c77c66ad43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62632478"
---
# <a name="update-delete-and-insert-statements"></a>UPDATE-, DELETE- und INSERT-Anweisungen
SQL-basierten Anwendungen und nehmen Sie Änderungen an Tabellen durch Ausführen der **UPDATE**, **löschen**, und **einfügen** Anweisungen. Diese Anweisungen sind Teil der Konformitätsgrad des mindestens SQL-Grammatik und von allen Treibern und Datenquellen unterstützt werden müssen.  
  
 Die Syntax dieser Anweisungen lautet:  
  
 **UPDATE** _Tabellenname_  
  
 **SET** _column-identifier_ **=** {*expression* &#124; **NULL**}  
  
 [**,** _Spaltenbezeichner_ **=** {*Ausdruck* &#124; **NULL**}]...  
  
 [**, In denen** _Suchbedingung_]  
  
 **DELETE FROM** _Tabellenname_[**, in denen** _Suchbedingung_]  
  
 **INSERT INTO** _Tabellenname_[**(** _Spaltenbezeichner_ [**,** _Spaltenbezeichner-_]... **)**]  
  
 {*-Abfragespezifikation* &#124; **Werte (** _Wert einfügen_ [**,** _Wert einfügen_]... **)**}  
  
 Beachten Sie, dass die *-Abfragespezifikation* Element ist nur in der Core und erweiterte SQL-Grammatik, und dass die *Ausdruck* und *Suchbedingung* Elemente steigern. komplexe, in der Core und erweiterte SQL-Grammatik.  
  
 Andere SQL-Anweisungen, wie **UPDATE**, **löschen**, und **einfügen** Anweisungen sind häufig effizienter, wenn sie Parameter verwenden. Beispielsweise kann die folgende Anweisung vorbereitet und wiederholt ausgeführt, um mehrere Zeilen in der Tabelle Orders einzufügen:  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Diese Effizienz kann durch Übergeben von Arrays für Parameterwerte erhöht werden. Weitere Informationen über Parameter und Arrays von Parameterwerten finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md).
