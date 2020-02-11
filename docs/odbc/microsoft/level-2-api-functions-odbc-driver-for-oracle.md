---
title: API-Funktionen der Ebene 2 (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7600734fef44071b1f5e35c136a6b9facdb8b390
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949037"
---
# <a name="level-2-api-functions-odbc-driver-for-oracle"></a>API-Funktionen der zweiten Ebene (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Funktionen auf dieser Ebene bieten eine Schnittstellen Konformität der Ebene 1 sowie zusätzliche Funktionen, wie z. b. die Unterstützung von Lesezeichen, dynamischen Parametern und die asynchrone Ausführung von ODBC-Funktionen.  
  
|API-Funktion|Notizen|  
|------------------|-----------|  
|**SQLBindParameter**|Ordnet einen Puffer mit einer Parameter Markierung in einer SQL-Anweisung zu.|  
|**SQLBrowseConnect**|Gibt aufeinander folgende Ebenen von Attributen und Attributwerten zurück.|  
|**SQLDataSources**|Listet Datenquellen Namen auf. Wird vom Treiber-Manager implementiert.|  
|**SQLDescribeParam**|Gibt die Beschreibung einer Parameter Markierung zurück, die einer vorbereiteten SQL-Anweisung zugeordnet ist.<br /><br /> Gibt basierend auf der Verarbeitung der Anweisung eine optimale Schätzung des-Parameters zurück. Wenn der Parametertyp nicht bestimmt werden kann, wird SQL_VARCHAR mit der Länge 2000 zurückgegeben.|  
|**SQLDrivers**|Wird vom Treiber-Manager implementiert.|  
|**SQLExtendedFetch**|Ähnlich wie **SQLFetch** , gibt jedoch mehrere Zeilen zurück, wobei ein Array für jede Spalte verwendet wird. Das Resultset ist vorwärts ScrollBar und kann rückwärts scrollfähig gemacht werden, wenn der Cursor als statisch und nicht vorwärts definiert ist. Für Vorwärts Cursor mit Standard Spalten Bindung werden Spaltendaten aus Datasets, die größer als das Verbindungs Attribut bufferSize sind, direkt in Datenpuffer abgerufen. Unterstützt keine Lesezeichen mit variabler Länge und unterstützt nicht das Abrufen eines Rowsets in einem Offset (mit Ausnahme von 0) aus einem Lesezeichen.|  
|**SQLForeignKeys**|Gibt eine Liste von Fremdschlüsseln in einer einzelnen Tabelle oder eine Liste von Fremdschlüsseln in anderen Tabellen zurück, die auf eine einzelne Tabelle verweisen.|  
|**SQLMoreResults**|Bestimmt, ob weitere Ergebnisse für ein Anweisungs Handle, hstmt, mit SELECT-, Update-, INSERT-oder DELETE-Anweisungen ausstehen. wenn dies der Fall ist, wird die Verarbeitung für diese Ergebnisse initialisiert.<br /><br /> Oracle unterstützt mehrere Resultsets nur aus gespeicherten Prozeduren, wenn {Resultset...}-Escapesequenzen verwendet werden.|  
|**SQLNativeSql**|Weitere Informationen zur Verwendung finden Sie unter [zurückgeben von Array Parametern aus gespeicherten Prozeduren](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLNumParams**|Gibt die Anzahl der Parameter in einer SQL-Anweisung zurück. Die Anzahl der Parameter sollte gleich der Anzahl von Fragezeichen in der SQL-Anweisung sein, die an **SQLPrepare**weitergegeben wurde.|  
|**SQLPrimaryKeys**|Gibt die Spaltennamen zurück, die den Primärschlüssel für eine Tabelle bilden.|  
|**SQLProcedureColumns**|Gibt eine Liste von Eingabe-und Ausgabeparametern, den Rückgabewert, die Spalten im Resultset einer einzelnen Prozedur und zwei zusätzliche Spalten, Überladung und ORDINAL_POSITION zurück. Überladung ist die Überladungs Spalte aus der ALL_ARGUMENTS Tabelle der Oracle-Daten Wörterbuch Sicht. ORDINAL_POSITION ist die Sequenz Spalte aus der ALL_ARGUMENTS Tabelle der Oracle-Daten Wörterbuch Sicht. Für Paket Prozeduren ist die Spalte "Prozedur Name" im Format *packagename. Prozedurname. Prozedurname.* Gibt keine Prozedur Spalten eines erstellten Synonyms zurück, das auf eine Prozedur oder eine Funktion verweist.|  
|**'SQLProcedures'**|Gibt eine Liste der Prozeduren in der Datenquelle zurück. Für Paket Prozeduren ist die Spalte "Prozedur Name" im Format *packagename. Prozedurname. Prozedurname.*<br /><br /> Da Oracle keine Möglichkeit bietet, packende Prozeduren von verpackten Funktionen zu unterscheiden, gibt der Treiber SQL_PT_UNKNOWN für die PROCEDURE_TYPE Spalte zurück.|  
|**SQLSetPos**|Legt die Cursorposition in einem Rowset fest. Sie können **SQLSetPos** mit **SQLGetData** verwenden, um Zeilen aus ungebundenen Spalten abzurufen, nachdem der Cursor für eine bestimmte Zeile im Rowset positioniert wurde. Zeilen, die mithilfe von *fOption* SQL_ADD dem Resultset hinzugefügt werden, werden nach der letzten Zeile im Resultset hinzugefügt.|  
|**SQLSetScrollOptions**|Legt Optionen zum Steuern des Verhaltens von Cursorn fest, die einem Anweisungs Handle (hstmt) zugeordnet sind. Weitere Informationen finden Sie unter [Cursor Type und](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)Parallelitäts Kombinationen.|
