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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94bd5211c878904453624adb2acd0fe435ebc812
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298946"
---
# <a name="unicode-applications"></a>Unicode-Anwendungen
Eine Anwendung kann auf zwei Arten als Unicode-Anwendung neu kompiliert werden:  
  
-   Fügen Sie die in der Header Datei sqlucode. h enthaltene Unicode- **#define** in die Anwendung ein.  
  
-   Kompilieren Sie die Anwendung mit der Unicode-Option des Compilers. (Diese Option unterscheidet sich für verschiedene Compiler.)  
  
 Um eine ANSI-Anwendung in eine Unicode-Anwendung zu konvertieren, schreiben Sie die Anwendung, um Unicode-Daten zu speichern und zu übergeben. Außerdem müssen Aufrufe von Funktionen, die SQLPOINTER-Argumente unterstützen, konvertiert werden, um die Anzahl von Bytes zu verwenden.  
  
 Wenn eine Anwendung als Unicode-Anwendung kompiliert wird und die Anwendung eine ODBC-API-Funktion (ohne Suffix) aufruft, erkennt der Treiber-Manager die Anwendung als Unicode-Anwendung und konvertiert den Funktionsaufruf in eine Unicode-Funktion (mit dem *W* -Suffix), wenn der zugrunde liegende Treiber Unicode unterstützt. Wenn eine ANSI-Anwendung einen Funktions Aufrufvorgang ohne Suffix ausführt, konvertiert der Treiber-Manager Sie in ANSI, wenn der zugrunde liegende Treiber ANSI unterstützt. Wenn die gleiche Zeichencodierung sowohl von der Anwendung als auch vom Treiber unterstützt wird, übergibt der Treiber-Manager die Aufrufe an den Treiber (mit bestimmten Ausnahmen für ANSI-Anwendungen).  
  
 Eine Anwendung kann beide Unicode-Funktionen (mit dem *W* -Suffix) und ANSI-Funktionen (mit oder *ohne Suffix)* aufzurufen. Unicode-und ANSI-Funktionsaufrufe können gemischt werden. Wenn die Cursor Bibliothek verwendet werden soll, können Unicode-und ANSI-Funktionsaufrufe jedoch nicht gemischt werden. Die Cursor Bibliothek ist entweder Unicode oder ANSI, keine Mischung.  
  
 Eine Anwendung kann so geschrieben werden, dass Sie entweder als Unicode-Anwendung oder als ANSI-Anwendung kompiliert werden kann. In diesem Fall können Zeichen Datentypen als SQL_C_TCHAR deklariert werden. Dies ist ein Makro, das SQL_C_WCHAR einfügt, wenn die Anwendung als Unicode-Anwendung kompiliert wird, oder SQL_C_CHAR, wenn Sie als ANSI-Anwendung kompiliert wird, einfügt. Der Programmierer der Anwendung muss bei Funktionen, die SQLPOINTER als Argument annehmen, vorsichtig sein, da sich die Größe des Längen Arguments (für Zeichen folgen-Datentypen) in Abhängigkeit davon ändert, ob die Anwendung ANSI oder Unicode ist.  
  
 Eine Funktion kann mit einer von drei Methoden aufgerufen werden: als ein nur-Unicode-Funktionsaufruf (mit dem Suffix " *W* "), als ein nur-ANSI-Funktionsaufruf (mit *einem* Suffix) oder als ODBC-Funktionsaufruf ohne Suffix. Die Argumente für die drei Formen einer Funktion sind identisch. Nur die Funktionen mit SQLCHAR \* -Argumenten oder SQLPOINTER-Argumenten, die auf Zeichen folgen verweisen, erfordern Unicode-und ANSI-Formulare. Für Funktionen, die über Argumente verfügen, die als Zeichentyp deklariert werden können, z. b. **SQLBindCol** oder **SQLGetData** (die nicht über Unicode-und ANSI-Formulare verfügen), kann das Argument als Unicode-Typ, ANSI-Typ oder im Fall eines C-Typarguments als SQL_C_TCHAR Makro deklariert werden. Weitere Informationen finden Sie unter [Unicode-Daten](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Eine Anwendung kann auch dann als Unicode-Anwendung geschrieben werden, wenn keine Unicode-Treiber verfügbar sind, damit Sie verwendet werden kann. Der Treiber-Manager ordnet Unicode-Funktionen und-Datentypen ANSI zu. Es gibt einige Einschränkungen für die Unicode-zu-ANSI-Zuordnungen, die ausgeführt werden können. Das vorhanden sein eines Unicode-Treibers für die Unicode-Anwendung, mit dem gearbeitet wird, führt zu einer besseren Leistung und entfernt die Einschränkungen, die in den Unicode-Zuordnungen enthalten sind.
