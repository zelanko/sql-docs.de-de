---
description: Unicode-Daten
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f217e6b629936cc835d134c89d972bb1408b9d0b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339116"
---
# <a name="unicode-data"></a>Unicode-Daten
SQL-Unicode-Datentypen werden bereitgestellt, um Daten zu beschreiben, die nativ auf dem DBMS in Unicode gespeichert werden. Ein C-Unicode-Datentyp wird bereitgestellt, damit eine Anwendung Daten an einen Unicode-Puffer binden kann. Der Treiber-Manager kann Daten von einem Unicode-C-Typ (SQL_C_WCHAR) konvertieren, damit er mit einem ANSI-Treiber funktioniert.  
  
 Ein ODBC-3,0 oder 2. die *x* -Anwendung wird immer an die ANSI-Datentypen gebunden. Um eine optimale Leistung zu erzielen, sollte eine ODBC 3,5 (oder höher)-Anwendung an den ANSI-Daten c-Typ gebunden werden, wenn der SQL-Spaltentyp ANSI ist, und eine Bindung an den Unicode-c-Datentyp herstellen, wenn der SQL-Spaltentyp  
  
 Die SQL-Unicode-Typindikatoren sind SQL_WCHAR, SQL_WVARCHAR und SQL_WLONGVARCHAR. SQL_WCHAR Daten verfügen über eine festgelegte Zeichen folgen Länge, während SQL_WVARCHAR eine Variable Länge mit einem deklarierten Maximum aufweist und SQL_WLONGVARCHAR eine Variable Länge mit einem maximalen hat, die von der Datenquelle abhängt.  
  
 Der C-Unicode-Typindikator ist SQL_C_WCHAR. Dies ist die Standardeinstellung für jeden der SQL-Unicode-Typindikatoren. Alle SQL-Typen können in SQL_C_WCHAR konvertiert werden, und SQL_C_WCHAR können in alle SQL-Typen konvertiert werden. Eine Anwendung kann Daten auf eine von drei Arten abrufen:  
  
-   Rufen Sie die Daten als SQL_C_CHAR ab.  
  
-   Rufen Sie die Daten als SQL_C_WCHAR ab.  
  
-   Deklarieren Sie die Daten als SQL_C_TCHAR. Dies ist ein Makro, das SQL_C_WCHAR einfügt, wenn die Anwendung als Unicode-Anwendung kompiliert wird, oder SQL_C_CHAR, wenn Sie als ANSI-Anwendung kompiliert wird, einfügt.  
  
 SQL_C_TCHAR wird in einer Funktion wie folgt deklariert:  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 Wenn die Anwendung als Unicode-Anwendung kompiliert wird, wird das *ValueType* -Argument von SQL_C_TCHAR in SQL_C_WCHAR geändert. Wenn die Anwendung als ANSI-Anwendung kompiliert wird, wird das *ValueType* -Argument in SQL_C_CHAR geändert.  
  
 Unicode-Treiber müssen weiterhin ANSI-Datentypen unterstützen, einschließlich SQL_CHAR. Wenn eine Anwendung, die mit einem Unicode-Treiber arbeitet, an SQL_CHAR gebunden wird, ordnet der Treiber-Manager die SQL_CHAR Daten nicht SQL_WCHAR zu. Der Unicode-Treiber muss die SQL_CHAR Daten akzeptieren.  
  
 Der Treiber-Manager speichert Treiber-und DSN-Namen in Unicode und ordnet diese nach Bedarf ANSI zu. Wenn ein Unicode-Zeichen nicht einem ANSI-Zeichen zugeordnet werden kann (wie es vorkommen kann, wenn Zeichen aus einer Codepage, bei der es sich nicht um die systemeigene Codepage des Computers handelt, in Treiber-und DSN-Namen verwendet werden), werden die Zeichen, die nicht konvertiert werden konnten, durch ein vom System bereitgestelltes Standard Zeichen dargestellt.
