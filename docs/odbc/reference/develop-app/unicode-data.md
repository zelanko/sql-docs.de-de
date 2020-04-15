---
title: Unicode-Daten | Microsoft Docs
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
ms.openlocfilehash: 73ea9035b05f04fec1527ca2aa98531a807db8cf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307397"
---
# <a name="unicode-data"></a>Unicode-Daten
SQL Unicode-Datentypen werden bereitgestellt, um Daten zu beschreiben, die sich nativ in Unicode auf dem DBMS befinden. Ein C-Unicode-Datentyp wird bereitgestellt, damit eine Anwendung Daten an einen Unicode-Puffer binden kann. Der Treiber-Manager kann Daten von einem Unicode C-Typ (SQL_C_WCHAR) konvertieren, damit er mit einem ANSI-Treiber funktioniert.  
  
 Ein ODBC 3.0 oder 2. *x-Anwendung* wird immer an die ANSI-Datentypen gebunden. Für eine optimale Leistung sollte eine ODBC 3.5 (oder höher) Anwendung an den ANSI-Daten-C-Typ binden, wenn der SQL-Spaltentyp ANSI ist, und an den Unicode C-Datentyp binden, wenn der SQL-Spaltentyp Unicode ist.  
  
 Die SQL Unicode-Typindikatoren sind SQL_WCHAR, SQL_WVARCHAR und SQL_WLONGVARCHAR. SQL_WCHAR Daten haben eine feste Zeichenfolgenlänge, während SQL_WVARCHAR eine variable Länge mit einem deklarierten Maximum hat und SQL_WLONGVARCHAR eine variable Länge mit einem Maximum hat, das von der Datenquelle abhängt.  
  
 Der C Unicode Typ Indikator ist SQL_C_WCHAR. Dies ist die Standardeinstellung für jeden SQL Unicode-Typindikator. Alle SQL-Typen können in SQL_C_WCHAR konvertiert werden, und SQL_C_WCHAR können in alle SQL-Typen konvertiert werden. Eine Anwendung kann Daten auf drei Arten abrufen:  
  
-   Rufen Sie die Daten als SQL_C_CHAR ab.  
  
-   Rufen Sie die Daten als SQL_C_WCHAR ab.  
  
-   Deklarieren Sie die Daten als SQL_C_TCHAR. Dies ist ein Makro, das SQL_C_WCHAR einfügt, wenn die Anwendung als Unicode-Anwendung kompiliert wird, oder SQL_C_CHAR wenn sie als ANSI-Anwendung kompiliert wird.  
  
 SQL_C_TCHAR wird in einer Funktion wie folgt deklariert:  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 Wenn die Anwendung als Unicode-Anwendung kompiliert wird, wird das *ValueType-Argument* von SQL_C_TCHAR in SQL_C_WCHAR geändert. Wenn die Anwendung als ANSI-Anwendung kompiliert wird, wird das *ValueType-Argument* in SQL_C_CHAR geändert.  
  
 Unicode-Treiber müssen weiterhin ANSI-Datentypen unterstützen, einschließlich SQL_CHAR. Wenn eine Anwendung, die mit einem Unicode-Treiber arbeitet, an SQL_CHAR gebunden ist, wird der Treiber-Manager die SQL_CHAR Daten nicht SQL_WCHAR zuordnen. Der Unicode-Treiber muss die SQL_CHAR Daten akzeptieren.  
  
 Der Treiber-Manager speichert Treiber- und DSN-Namen in Unicode und ordnet sie bei Bedarf ANSI zu. Wenn ein Unicode-Zeichen nicht einem ANSI-Zeichen zugeordnet werden kann (wie es auftreten kann, wenn Zeichen von einer Codepage, die nicht die systemeigene Codepage des Computers ist, in Treiber- und DSN-Namen verwendet werden), werden die Zeichen, die nicht konvertiert werden konnten, durch ein vom System bereitgestelltes Standardzeichen dargestellt.
