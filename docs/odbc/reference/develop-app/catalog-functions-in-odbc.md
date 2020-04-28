---
title: Katalog Funktionen in ODBC | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6731018b99f2f3043e48ee7c174a08cb9ef71fc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306231"
---
# <a name="catalog-functions-in-odbc"></a>Katalogfunktionen in ODBC
ODBC enthält die folgenden Katalog Funktionen:  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|**SQLTables**|Gibt eine Liste von Katalogen, Schemas, Tabellen oder Tabellentypen in der Datenquelle zurück.|  
|**SQLColumns**|Gibt eine Liste von Spalten in einer oder mehreren Tabellen zurück.|  
|**'SQLStatistics'**|Gibt eine Liste von Statistiken zu einer einzelnen Tabelle zurück. Gibt außerdem eine Liste von Indizes zurück, die dieser Tabelle zugeordnet sind.|  
|**'SQLSpecialColumns'**|Gibt eine Liste von Spalten zurück, die eine Zeile in einer einzelnen Tabelle eindeutig identifiziert. Gibt auch eine Liste der Spalten in dieser Tabelle zurück, die automatisch aktualisiert werden.|  
|**SQLPrimaryKeys**|Gibt eine Liste von Spalten zurück, die den Primärschlüssel einer einzelnen Tabelle bilden.|  
|**SQLForeignKeys**|Gibt eine Liste von Fremdschlüsseln in einer einzelnen Tabelle oder eine Liste von Fremdschlüsseln in anderen Tabellen zurück, die auf eine einzelne Tabelle verweisen.|  
|**SQLTablePrivileges**|Gibt eine Liste der Berechtigungen zurück, die einer oder mehreren Tabellen zugeordnet sind.|  
|**SQLColumnPrivileges**|Gibt eine Liste von Berechtigungen zurück, die einer oder mehreren Spalten in einer einzelnen Tabelle zugeordnet sind.|  
|**'SQLProcedures'**|Gibt eine Liste der Prozeduren in der Datenquelle zurück.|  
|**SQLProcedureColumns**|Gibt eine Liste von Eingabe-und Ausgabeparametern, den Rückgabewert und die Spalten im Resultset einer einzelnen Prozedur zurück.|  
|**SQLGetTypeInfo**|Gibt eine Liste der SQL-Datentypen zurück, die von der Datenquelle unterstützt werden. Diese Datentypen werden im Allgemeinen in **CREATE TABLE** -und **ALTER TABLE** -Anweisungen verwendet.|  
  
 Da **SQLTables**, **SQLColumns**, **SQLStatistics**und **SQLSpecialColumns** der Open Group-CLI entsprechen und **SQLGetTypeInfo** der ISO 92-CLI entspricht, werden Sie von den meisten Treibern implementiert. Die verbleibenden Katalog Funktionen befinden sich im ODBC-Konformitäts Grad.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Schemaansichten](../../../odbc/reference/develop-app/schema-views.md)
