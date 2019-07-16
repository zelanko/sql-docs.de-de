---
title: Unicode-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], data
- data types [ODBC], Unicode
- C data types [ODBC], Unicode
- SQL data types [ODBC], Unicode
ms.assetid: abc28718-e6d9-49fb-97ff-402d50c3c375
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 899924b5c0847d5f42e383a9e04c33298bb368b9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68087749"
---
# <a name="unicode-data"></a>Unicode-Daten
SQL-Unicode-Datentypen werden bereitgestellt, um Daten zu beschreiben, die im Unicode-Format nativ auf DBMS befindet. Ein C-Unicode-Datentyp wird bereitgestellt, um eine Anwendung so binden Sie Daten in einen Unicode-Puffer zu ermöglichen. Der Treiber-Manager können Daten aus einem Unicode-C-Typ (SQL_C_WCHAR), um es zu machen konvertieren-Funktion mit einem ANSI-Treiber.  
  
 Eine ODBC 3.0 oder 2. *x* Anwendung immer eine Bindung mit der ANSI-Datentypen. Für eine optimale Leistung sollten eine ODBC 3.5 (oder höhere)-Anwendung in die ANSI-C-Datentyp binden, wenn der SQL-Spaltentyp ANSI ist und in den Unicode-C-Datentyp binden sollten, wenn der SQL-Spaltentyp aus Unicode besteht.  
  
 Die SQL-Unicode-Typ-Indikatoren sind SQL_WCHAR, SQL_WVARCHAR und SQL_WLONGVARCHAR. SQL_WCHAR-Daten verfügt über eine Zeichenfolge fester Länge, während SQL_WVARCHAR einen Variablen Länge mit einer maximalen deklarierten hat und SQL_WLONGVARCHAR Variablen Länge mit einer maximalen, von denen die Datenquelle abhängig.  
  
 Der Typindikator C Unicode ist SQL_C_WCHAR an. Dies ist die Standardeinstellung für die einzelnen Indikatoren der SQL-Unicode-Typ. Alle von der SQL-Datentypen konvertiert werden können SQL_C_WCHAR, und für alle von der SQL-Datentypen SQL_C_WCHAR konvertiert werden kann. Eine Anwendung kann Daten in eine von drei Arten abrufen:  
  
-   Ruft die Daten als SQL_C_CHAR.  
  
-   Ruft die Daten als SQL_C_WCHAR an.  
  
-   Deklarieren Sie die Daten als SQL_C_TCHAR an. Dies ist ein Makro, mit dem SQL_C_WCHAR eingefügt, wenn die Anwendung, als Unicode-Anwendung kompiliert wird oder SQL_C_CHAR eingefügt, wenn es als ANSI-Anwendung kompiliert wird.  
  
 SQL_C_TCHAR wird in einer Funktion wie folgt deklariert:  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 Bei der Kompilierung der Anwendung eine Unicode-Anwendung, die *ValueType* Argument aus SQL_C_TCHAR in SQL_C_WCHAR geändert. Bei der Kompilierung der Anwendung als ANSI-Anwendung, die *ValueType* Argument in SQL_C_CHAR geändert.  
  
 Unicode-Treiber müssen immer noch mit ANSI-Datentypen, einschließlich SQL_CHAR unterstützen. Wenn eine Anwendung, die Arbeit mit einem Unicode-Treiber SQL_CHAR gebunden, wird der Treiber-Manager die SQL_CHAR-Daten nicht SQL_WCHAR zuordnen. Der Unicode-Treiber muss die SQL_CHAR-Daten akzeptieren.  
  
 Der Treiber-Manager speichert im Unicode-Treiber und die DSN-Namen und ordnet sie ANSI nach Bedarf. Wenn ein Unicode-Zeichen in ein ANSI-Zeichen (wie auftreten können, wenn Zeichen aus einer Codepage, die nicht die systemeigenen Code auf dem Computer ist in der DSN-Namen und Treiber verwendet werden) zugeordnet werden kann, werden die Zeichen, die nicht konvertiert werden können durch eine Standard-Sup Zeichen dargestellt. vom System plied.
