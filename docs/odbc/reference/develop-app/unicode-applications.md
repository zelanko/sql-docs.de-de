---
title: Unicode-Anwendungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94bd5211c878904453624adb2acd0fe435ebc812
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298946"
---
# <a name="unicode-applications"></a>Unicode-Anwendungen
Sie können eine Anwendung als Unicode-Anwendung auf zwei Arten neu kompilieren:  
  
-   Fügen Sie die **Unicode-#define** in der Sqlucode.h-Headerdatei in die Anwendung ein.  
  
-   Kompilieren Sie die Anwendung mit der Unicode-Option des Compilers. (Diese Option unterscheidet sich für verschiedene Compiler.)  
  
 Um eine ANSI-Anwendung in eine Unicode-Anwendung zu konvertieren, schreiben Sie die Anwendung, um Unicode-Daten zu speichern und zu übergeben. Darüber hinaus müssen Aufrufe von Funktionen, die SQLPOINTER-Argumente unterstützen, konvertiert werden, um die Anzahl der Bytes zu verwenden.  
  
 Nachdem eine Anwendung als Unicode-Anwendung kompiliert wurde, erkennt der Treiber-Manager, wenn die Anwendung eine ODBC-API-Funktion aufruft (ohne Suffix), die Anwendung als Unicode-Anwendung und konvertiert den Funktionsaufruf in eine Unicode-Funktion (mit dem *Suffix W),* wenn der zugrunde liegende Treiber Unicode unterstützt. Wenn eine ANSI-Anwendung einen Funktionsaufruf ohne Suffix ausführt, konvertiert der Treiber-Manager sie in ANSI, wenn der zugrunde liegende Treiber ANSI unterstützt. Wenn sowohl die Anwendung als auch der Treiber dieselbe Zeichencodierung unterstützen, leitet der Treiber-Manager die Aufrufe an den Treiber weiter (mit bestimmten Ausnahmen für ANSI-Anwendungen).  
  
 Eine Anwendung kann sowohl Unicode-Funktionen (mit dem *Suffix W)* als auch ANSI-Funktionen (mit oder ohne *A-Suffix)* aufrufen. Unicode- und ANSI-Funktionsaufrufe können gemischt werden. Wenn die Cursorbibliothek verwendet werden soll, können Unicode- und ANSI-Funktionsaufrufe jedoch nicht gemischt werden. Die Cursorbibliothek ist entweder Unicode oder ANSI, keine Mischung.  
  
 Eine Anwendung kann so geschrieben werden, dass sie entweder als Unicode-Anwendung oder als ANSI-Anwendung kompiliert werden kann. In diesem Fall können Zeichendatentypen als SQL_C_TCHAR deklariert werden. Dies ist ein Makro, das SQL_C_WCHAR einfügt, wenn die Anwendung als Unicode-Anwendung kompiliert wird, oder SQL_C_CHAR wenn sie als ANSI-Anwendung kompiliert wird. Der Anwendungsprogrammierer muss auf Funktionen achten, die SQLPOINTER als Argument verwenden, da sich die Größe des Length-Arguments ändert (für Zeichenfolgendatentypen), je nachdem, ob die Anwendung ANSI oder Unicode ist.  
  
 Eine Funktion kann auf eine von drei Arten aufgerufen werden: als *W* Unicode-only-Funktionsaufruf (mit dem W-Suffix), als ANSI-only-Funktionsaufruf (mit dem *Suffix A)* oder als ODBC-Funktionsaufruf ohne Suffix. Die Argumente für die drei Formen einer Funktion sind identisch. Nur Funktionen mit \* SQLCHAR-Argumenten oder SQLPOINTER-Argumenten, die auf Zeichenfolgen verweisen, erfordern Unicode- und ANSI-Formulare. Für Funktionen, die Argumente haben, die als Zeichentyp deklariert werden können, z. B. **SQLBindCol** oder **SQLGetData** (die nicht über Unicode- und ANSI-Formulare verfügen), kann das Argument als Unicode-Typ, ANSI-Typ oder im Fall eines C-Typarguments als SQL_C_TCHAR-Makro deklariert werden. Weitere Informationen finden Sie unter [Unicode-Daten](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Eine Anwendung kann als Unicode-Anwendung geschrieben werden, auch wenn keine Unicode-Treiber verfügbar sind, mit denen sie arbeiten kann. Der Treiber-Manager wird Unicode-Funktionen und Datentypen ANSI zuordnen. Es gibt einige Einschränkungen für den Unicode für ANSI-Zuordnungen, die ausgeführt werden können. Das Vorhandensein eines Unicode-Treibers für die Unicode-Anwendung, mit dem gearbeitet werden kann, führt zu einer besseren Leistung und beseitigt die Einschränkungen, die dem Unicode für ANSI-Zuordnungen innewohnen.
