---
title: LEVEL 2-API-Funktionen (ODBC-Treiber für Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC level 2 API functions [ODBC]
- functions [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], functions
- ODBC API functions [ODBC]
- API functions [ODBC]
- level 2 API functions [ODBC]
ms.assetid: d9f49520-72d7-4234-8635-260d0ce4199c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1e181c5863d6b906eaf9a3ba499728c595f0449
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284180"
---
# <a name="level-2-api-functions-odbc-driver-for-oracle"></a>API-Funktionen der zweiten Ebene (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Funktionen auf dieser Ebene bieten Level 1-Schnittstellenkonformität sowie zusätzliche Funktionen wie Unterstützung für Lesezeichen, dynamische Parameter und asynchrone Ausführung von ODBC-Funktionen.  
  
|API-Funktion|Notizen|  
|------------------|-----------|  
|**SQLBindParameter**|Ordnet einen Puffer einer Parametermarkierung in einer SQL-Anweisung zu.|  
|**SQLBrowseConnect**|Gibt aufeinanderfolgende Ebenen von Attributen und Attributwerten zurück.|  
|**SQLDataSources**|Listet Datenquellennamen auf. Vom Treiber-Manager implementiert.|  
|**SQLDescribeParam**|Gibt die Beschreibung einer Parametermarkierung zurück, die einer vorbereiteten SQL-Anweisung zugeordnet ist.<br /><br /> Gibt eine beste Vermutung über den Parameter zurück, basierend auf dem Analysieren der Anweisung. Wenn der Parametertyp nicht bestimmt werden kann, gibt SQL_VARCHAR mit der Länge 2000 zurück.|  
|**SQLDrivers**|Vom Treiber-Manager implementiert.|  
|**SQLExtendedFetch**|Ähnlich wie **SQLFetch** gibt er jedoch mehrere Zeilen zurück, die ein Array für jede Spalte verwenden. Das Resultset ist vorwärts scrollbar und kann rückwärts scrollbar gemacht werden, wenn der Cursor als statisch und nicht vorwärts definiert ist. Bei Vorwärtscursorn mit Standardspaltenbindung werden Spaltendaten aus Datensätzen, die größer als das BUFFERSIZE-Verbindungsattribut sind, direkt in Datenpuffer abgerufen. Unterstützt keine Lesezeichen variabler Länge und unterstützt nicht das Abrufen eines Rowsets mit einem Offset (außer 0) aus einer Textmarke.|  
|**SQLForeignKeys**|Gibt eine Liste von Fremdschlüsseln in einer einzelnen Tabelle oder eine Liste von Fremdschlüsseln in anderen Tabellen zurück, die auf eine einzelne Tabelle verweisen.|  
|**SQLMoreResults**|Bestimmt, ob weitere Ergebnisse für ein Anweisungshandle, hstmt, das SELECT-, UPDATE-, INSERT- oder DELETE-Anweisungen enthält, ausstehen und wenn ja, initialisiert die Verarbeitung für diese Ergebnisse.<br /><br /> Oracle unterstützt mehrere Resultsets nur aus gespeicherten Prozeduren, wenn Escapesequenzen von "resultset..." verwendet werden.|  
|**SQLNativeSql**|Informationen zur Verwendung finden Sie unter [Zurückgeben von Arrayparametern aus gespeicherten Prozeduren](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLNumParams**|Gibt die Anzahl der Parameter in einer SQL-Anweisung zurück. Die Anzahl der Parameter sollte der Anzahl der Fragezeichen in der SQL-Anweisung entsprechen, die an **SQLPrepare**übergeben wird.|  
|**SQLPrimaryKeys**|Gibt die Spaltennamen zurück, aus denen der Primärschlüssel für eine Tabelle besteht.|  
|**SQLProcedureColumns**|Gibt eine Liste der Eingabe- und Ausgabeparameter, den Rückgabewert, die Spalten im Resultset einer einzelnen Prozedur und zwei zusätzliche Spalten, OVERLOAD und ORDINAL_POSITION. OVERLOAD ist die SPALTE OVERLOAD aus der ALL_ARGUMENTS Tabelle der Oracle Data Dictionary View. ORDINAL_POSITION ist die Spalte SEQUENCE aus der Tabelle ALL_ARGUMENTS der Oracle Data Dictionary View. Bei verpackten Prozeduren ist die Spalte PROCEDURE NAME im Format *packagename.procedurename.* Gibt nicht die Prozedurspalten eines erstellten Synonyms zurück, das auf eine Prozedur oder Funktion verweist.|  
|**'SQLProcedures'**|Gibt eine Liste der Prozeduren in der Datenquelle zurück. Bei verpackten Prozeduren ist die Spalte PROCEDURE NAME im Format *packagename.procedurename.*<br /><br /> Da Oracle keine Möglichkeit bietet, verpackte Prozeduren von gepackten Funktionen zu unterscheiden, gibt der Treiber SQL_PT_UNKNOWN für die Spalte PROCEDURE_TYPE zurück.|  
|**SQLSetPos**|Legt die Cursorposition in einem Rowset fest. Sie können **SQLSetPos** mit **SQLGetData** verwenden, um Zeilen aus ungebundenen Spalten abzurufen, nachdem Sie den Cursor in eine bestimmte Zeile im Rowset positioniert haben. Zeilen, die dem Resultset mit *fOption* SQL_ADD hinzugefügt wurden, werden nach der letzten Zeile im Resultset hinzugefügt.|  
|**SQLSetScrollOptionen**|Legt Optionen fest, die das Verhalten von Cursorn steuern, die einem Anweisungshandle, hstmt, zugeordnet sind. Weitere Informationen finden Sie unter [Cursortyp und Parallelitätskombinationen](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|
