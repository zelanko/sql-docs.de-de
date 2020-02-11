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
ms.openlocfilehash: 93cf744cf105762fb90a92049d6698e67a19d58c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138995"
---
# <a name="identifier-arguments"></a>Bezeichnerargumente
Wenn eine Zeichenfolge in einem bezeichnerargument in Anführungszeichen gesetzt wird, entfernt der Treiber führende und nachfolgende Leerzeichen und behandelt die Zeichenfolge innerhalb der Anführungszeichen. Wenn die Zeichenfolge nicht in Anführungszeichen eingeschlossen wird, entfernt der Treiber nachfolgende Leerzeichen und fasst die Zeichenfolge in Großbuchstaben um. Wenn ein bezeichnerargument auf einen NULL-Zeiger festgelegt wird, wird SQL_ERROR und SQLSTATE HY009 (Ungültige Verwendung des NULL-Zeigers) zurückgegeben, es sei denn, das Argument ist ein Katalog Name, und Kataloge  
  
 Diese Argumente werden als bezeichnerargumente behandelt, wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist. In diesem Fall ist der Unterstrich (_) und das Prozentzeichen (%). wird als das eigentliche Zeichen und nicht als Suchmuster behandelt. Diese Argumente werden entweder als normales Argument oder Muster Argument behandelt, je nach Argument, wenn dieses Attribut auf SQL_FALSE festgelegt ist.  
  
 Obwohl Bezeichner, die Sonderzeichen enthalten, in SQL-Anweisungen angegeben werden müssen, dürfen Sie nicht in Anführungszeichen eingeschlossen werden, wenn Sie als Katalog Funktionsargumente übermittelt werden, da an Katalog Funktionen übergebenen Anführungszeichen buchstäblich interpretiert werden Nehmen wir beispielsweise an, dass das bezeichneranführungs Zeichen (das Treiber spezifisch und durch **SQLGetInfo**zurückgegeben wird) ein doppeltes Anführungszeichen (") ist. Der erste **SQLTables** -Befehl gibt ein Resultset zurück, das Informationen über die Tabelle mit den zu zahlenden Konten enthält, während der zweite-Rückruf Informationen über die Tabelle "Konten bezahlt" zurückgibt, die wahrscheinlich nicht beabsichtigt war.  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 Bezeichner in Anführungszeichen werden verwendet, um einen echten Spaltennamen von einer Pseudo Spalte mit demselben Namen, wie z. b. ROWID in Oracle, zu unterscheiden. Wenn "ROWID" in einem Argument einer Katalog Funktion übermittelt wird, funktioniert die Funktion mit der ROWID-Pseudo Spalte, sofern vorhanden. Wenn die Pseudo Spalte nicht vorhanden ist, kann die Funktion mit der Spalte "ROWID" verwendet werden. Wenn ROWID in einem Argument einer Katalog Funktion übermittelt wird, funktioniert die Funktion mit der ROWID-Spalte.  
  
 Weitere Informationen zu [Bezeichnern in Anführungszeichen finden Sie](../../../odbc/reference/develop-app/quoted-identifiers.md)unter Bezeichner in Anführungszeichen.
