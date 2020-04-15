---
title: Identifier-Argumente | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6831eab30daebe37baecebe3ed7053537d7de8f8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300160"
---
# <a name="identifier-arguments"></a>Bezeichnerargumente
Wenn eine Zeichenfolge in einem Bezeichnerargument zitiert wird, entfernt der Treiber führende und nachfolgende Leerzeichen und behandelt buchstäblich die Zeichenfolge innerhalb der Anführungszeichen. Wenn die Zeichenfolge nicht zitiert wird, entfernt der Treiber nachfolgende Leerzeichen und faltet die Zeichenfolge in Großbuchstaben. Wenn Sie ein Bezeichnerargument auf einen Nullzeiger festlegen, werden SQL_ERROR und SQLSTATE HY009 (Ungültige Verwendung von NULL-Zeiger) zurückgegeben, es sei denn, das Argument ist ein Katalogname, und Kataloge werden nicht unterstützt.  
  
 Diese Argumente werden als Bezeichnerargumente behandelt, wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist. In diesem Fall werden der Unterstrich (_) und das Prozentzeichen (%) werden als das tatsächliche Zeichen und nicht als Suchmusterzeichen behandelt. Diese Argumente werden je nach Argument entweder als gewöhnliches Argument oder als Musterargument behandelt, wenn dieses Attribut auf SQL_FALSE festgelegt ist.  
  
 Obwohl Bezeichner, die Sonderzeichen enthalten, in SQL-Anweisungen zitiert werden müssen, dürfen sie nicht zitiert werden, wenn sie als Katalogfunktionsargumente übergeben werden, da An katalogfunktionen übergebene Anführungszeichen wörtlich interpretiert werden. Angenommen, das Bezeichneranführungszeichen (das treiberspezifisch ist und über **SQLGetInfo**zurückgegeben wird) ist ein doppeltes Anführungszeichen ("). Der erste Aufruf von **SQLTables** gibt ein Resultset zurück, das Informationen über die Tabelle "Kreditorenkonten" enthält, während der zweite Aufruf Informationen über die Tabelle "Accounts Payable" zurückgibt, was wahrscheinlich nicht beabsichtigt ist.  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 Zitierte Bezeichner werden verwendet, um einen echten Spaltennamen von einer Pseudospalte mit demselben Namen zu unterscheiden, z. B. ROWID in Oracle. Wenn "ROWID" in einem Argument einer Katalogfunktion übergeben wird, funktioniert die Funktion mit der ROWID-Pseudospalte, falls vorhanden. Wenn die Pseudospalte nicht vorhanden ist, funktioniert die Funktion mit der Spalte "ROWID". Wenn ROWID in einem Argument einer Katalogfunktion übergeben wird, funktioniert die Funktion mit der ROWID-Spalte.  
  
 Weitere Informationen zu angesetzten Bezeichnern finden Sie unter [Quoted Identifiers](../../../odbc/reference/develop-app/quoted-identifiers.md).
