---
title: Katalogfunktionen in ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], listed
- functions [ODBC], catalog functions
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8cd46fbc8f633ef31f00fa60ced885f9455f185
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062733"
---
# <a name="catalog-functions-in-odbc"></a>Katalogfunktionen in ODBC
ODBC enthält die folgenden Katalogfunktionen:  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|**SQLTables**|Gibt eine Liste der Kataloge, Schemas, Tabellen und Tabellentypen in der Datenquelle zurück.|  
|**SQLColumns**|Gibt eine Liste der Spalten in einer oder mehreren Tabellen zurück.|  
|**SQLStatistics**|Gibt eine Liste der Statistiken zu einer einzelnen Tabelle. Gibt auch eine Liste von Indizes dieser Tabelle zugeordnet.|  
|**SQLSpecialColumns**|Gibt eine Liste der Spalten, die eine Zeile in einer einzelnen Tabelle eindeutig identifiziert. Gibt auch eine Liste der Spalten, in dieser Tabelle, die automatisch aktualisiert werden.|  
|**SQLPrimaryKeys**|Gibt eine Liste der Spalten, die den Primärschlüssel einer Tabelle zu erstellen.|  
|**SQLForeignKeys**|Gibt eine Liste von Fremdschlüsseln in einer einzelnen Tabelle oder eine Liste von Fremdschlüsseln in anderen Tabellen, die auf einer einzelnen Tabelle verweisen zurück.|  
|**SQLTablePrivileges**|Gibt eine Liste der Berechtigungen, die einer oder mehreren Tabellen zugeordnet.|  
|**SQLColumnPrivileges**|Gibt eine Liste der Berechtigungen, die eine oder mehrere Spalten in einer einzelnen Tabelle zugeordnet sind.|  
|**SQLProcedures**|Gibt eine Liste der Verfahren in der Datenquelle zurück.|  
|**SQLProcedureColumns**|Gibt eine Liste von Eingabe-und Ausgabeparameter, der Rückgabewert und die Spalten im Resultset einer einzigen Prozedur zurück.|  
|**SQLGetTypeInfo**|Gibt eine Liste der SQL-Datentypen, die von der Datenquelle unterstützt. Diese Datentypen werden in der Regel in verwendet **CREATE TABLE** und **ALTER TABLE** Anweisungen.|  
  
 Da **SQLTables**, **SQLColumns**, **SQLStatistics**, und **SQLSpecialColumns** entsprechen die Open Group-CLI und **SQLGetTypeInfo** entspricht dem ISO-92-Befehlszeilenschnittstelle, die sie von den meisten-Treibern implementiert werden. Die übrigen Katalogfunktionen sind in der ODBC-Konformitätsgrad.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Daten, die von Katalogfunktionen zurückgegeben werden](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Schemaansichten](../../../odbc/reference/develop-app/schema-views.md)
