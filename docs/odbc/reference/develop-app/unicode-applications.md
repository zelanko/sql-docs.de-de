---
title: Unicode-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], compiling as Unicode application
- Unicode [ODBC], functions
- compiling Unicode applications [ODBC]
- functions [ODBC], Unicode functions
ms.assetid: 7986c623-2792-4e77-bfee-c86cbf84f08d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fc9cb98837d206d5279d1f14d4a57ce56782759
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633380"
---
# <a name="unicode-applications"></a>Unicode-Anwendungen
Sie können eine Anwendung als Unicode-Anwendung in eine von zwei Arten kompilieren:  
  
-   Die Unicode enthalten **#define** in die Headerdatei Sqlucode.h in der Anwendung enthalten sind.  
  
-   Kompilieren Sie die Anwendung mit Unicode-Compileroption. (Diese Option wird für andere Compiler unterschiedlich sein.)  
  
 Schreiben Sie die Anwendung zum Speichern und übergeben von Unicode-Daten, um eine ANSI-Anwendung in eine Unicode-Anwendung zu konvertieren. Darüber hinaus müssen Aufrufe von Funktionen, die SQLPOINTER Argumente zu unterstützen konvertiert werden, um die Anzahl von Bytes verwenden.  
  
 Nach eine Anwendung als Unicode-Anwendung kompiliert wird, wenn die Anwendung eine ODBC-API-Funktion (ohne Suffix) aufruft, erkennt die Anwendung als Unicode-Anwendung und den Funktionsaufruf an eine Unicode-Funktion (mit der konvertiertderTreiber-Manager *W* Suffix) Wenn der zugrunde liegenden Treiber Unicode unterstützt. Wenn eine ANSI-Anwendung auf einen Funktionsaufruf ohne Suffix ist, konvertiert der Treiber-Manager es in ANSI, wenn der zugrunde liegenden Treiber ANSI unterstützt. Wenn die Anwendung und der Treiber die gleiche zeichencodierung unterstützt, übergibt der Treiber-Manager die Aufrufe über den Treiber (mit Ausnahmen für ANSI-Anwendungen).  
  
 Eine Anwendung kann beide Unicode-Funktionen aufrufen (mit der *W* Suffix) und ANSI-Funktionen (mit oder ohne die *ein* Suffix). Unicode und ANSI-Funktionsaufrufe können kombiniert werden. Wenn die Cursorbibliothek verwendet werden, können nicht jedoch Unicode und ANSI-Funktionsaufrufe kombiniert werden. Die Cursorbibliothek ist entweder Unicode oder ANSI, keine Mischung.  
  
 Eine Anwendung kann geschrieben werden, sodass er als ein Unicode-Anwendung oder eine ANSI-Anwendung kompiliert werden kann. In diesem Fall können Zeichen-Datentypen als SQL_C_TCHAR deklariert werden. Dies ist ein Makro, mit dem SQL_C_WCHAR eingefügt, wenn die Anwendung, als Unicode-Anwendung kompiliert wird oder SQL_C_CHAR eingefügt, wenn es als ANSI-Anwendung kompiliert wird. Der Programmierer muss darauf achten von Funktionen, die SQLPOINTER als deren Argument akzeptieren, da die Größe der Length-Argument (für Zeichenfolgen-Datentypen) ändern je nachdem, ob die Anwendung ANSI- oder Unicode.  
  
 Eine Funktion kann in drei verschiedene Arten aufgerufen werden: als nur-Unicode-Funktionsaufruf (mit der *W* Suffix), ein nur-ANSI-Funktionsaufruf (mit der *ein* Suffix), oder der ODBC-Funktionsaufruf ohne Suffix. Die Argumente für die drei Formen von einer Funktion sind identisch. Nur die Funktionen mit SQLCHAR \* Argumente oder SQLPOINTER-Argumente, die auf Zeichenfolgen verweisen erfordern Unicode und ANSI-Formulare. Für Funktionen, die Argumente, die als einen Zeichentyp handelt, z. B. deklariert werden können, haben **SQLBindCol** oder **SQLGetData** (die nicht mit Unicode und ANSI-Formulare), das Argument kann als der Unicode-Datentyp deklariert werden ANSI geben, oder geben Sie im Falle eines C-Argument, das SQL_C_TCHAR-Makro. Weitere Informationen finden Sie unter [Unicode-Daten](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Eine Anwendung kann als Unicode-Anwendung geschrieben werden, auch wenn keine Unicode-Treiber für die Arbeit mit verfügbar sind. Der Treiber-Manager werden Unicode-Funktionen und Datentypen in ANSI zugeordnet werden. Es gibt einige Einschränkungen für das Konvertieren von Unicode in ANSI-Zuordnungen, die ausgeführt werden können. Das Vorhandensein eines Unicode-Treibers für die Unicode-Anwendung zur Zusammenarbeit mit führt zu besserer Leistung und die Einschränkungen, die sich das Konvertieren von Unicode in ANSI-Zuordnungen entfernen.
