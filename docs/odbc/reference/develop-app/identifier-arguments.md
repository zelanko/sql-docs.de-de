---
title: Bezeichnerargumente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- identifier arguments [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], identifier
ms.assetid: b9de003f-cb49-4dec-b528-14a5b8ff12bd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 156dfaf5c6a6a4ec06a0c96b5f726383cba32ba6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62447549"
---
# <a name="identifier-arguments"></a>Bezeichnerargumente
Wenn eine Zeichenfolge in einem Argument Bezeichner in Anführungszeichen steht, wird der Treiber entfernt führende und nachfolgende Leerzeichen und behandelt buchstäblich die Zeichenfolge in Anführungszeichen. Wenn die Zeichenfolge nicht in Anführungszeichen eingeschlossen ist, entfernt der Treiber nachfolgende Leerzeichen und Aufteilungen die Zeichenfolge in Großbuchstaben. Wird ein ID-Argument auf einen null-Zeiger gibt SQL_ERROR zurück, und SQLSTATE HY009 (Ungültige Verwendung von null-Zeiger), es sei denn, das Argument ein Katalogname ist und Kataloge werden nicht unterstützt.  
  
 Diese Argumente werden als bezeichnerargumente behandelt, wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE festgelegt ist. In diesem Fall für die Anmeldung der Unterstrich (_) und den Prozentsatz (%) Welches Zeichen tatsächlich, nicht als Suche Muster Zeichen werden als behandelt. Diese Argumente werden als ein normales Argument oder ein Muster-Argument, abhängig von das Argument behandelt, wenn dieses Attribut auf SQL_FALSE festgelegt ist.  
  
 Obwohl Bezeichner mit Sonderzeichen in SQL-Anweisungen in Anführungszeichen gesetzt werden müssen, müssen sie nicht in Anführungszeichen gesetzt werden beim Übergeben als Argumente für Katalog-Funktion, da die Katalogfunktionen, die an Anführungszeichen als solche interpretiert werden. Nehmen wir beispielsweise an den Bezeichner Anführungszeichens (d. h. treiberspezifische und über zurückgegebenen **SQLGetInfo**) ist ein doppeltes Anführungszeichen ("). Der erste Aufruf **SQLTables** gibt ein Resultset mit Informationen zu der Tabelle "Accounts Payable", während der zweite Aufruf Informationen zu der Tabelle "Accounts Payable" zurückgibt, handelt es sich wahrscheinlich nicht beabsichtigt war.  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 Bezeichner in Anführungszeichen werden verwendet, um einen Namen für die "true" Spalte aus einer Pseudo-Spalte mit dem gleichen Namen, z. B. ROWID in Oracle zu unterscheiden. Wenn "ROWID" in einem Argument einer Katalog-Funktion übergeben wird, funktioniert die Funktion mit der ROWID-Pseudo-Spalte, wenn es vorhanden ist. Wenn es sich bei die Pseudo-Spalte nicht vorhanden ist, wird die Funktion mit der Spalte "ROWID" funktionieren. Wenn ROWID in einem Argument einer Katalog-Funktion übergeben wird, funktioniert die Funktion, mit der ROWID-Spalte.  
  
 Weitere Informationen zu Bezeichnern finden Sie unter [Bezeichner in Anführungszeichen](../../../odbc/reference/develop-app/quoted-identifiers.md).
