---
title: Ebene-2-API-Funktionen (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: be472a4a99324927128514fa9f8cbf19d44d49cc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825900"
---
# <a name="level-2-api-functions-odbc-driver-for-oracle"></a>API-Funktionen der zweiten Ebene (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Funktionen, die auf dieser Ebene bieten schnittstellenübereinstimmung der Stufe 1 sowie zusätzliche Funktionen wie Unterstützung für asynchrone Ausführung der ODBC-Funktionen, Lesezeichen und dynamische Parameter auf.  
  
|API-Funktion|Hinweise|  
|------------------|-----------|  
|**SQLBindParameter**|Ordnet einen Puffer mit einer parametermarkierung in einer SQL­Anweisung.|  
|**SQLBrowseConnect**|Gibt die Attribute und Attributwerte aufeinander folgenden Steuerungsebenen zurück.|  
|**SQLDataSources**|Listet die Datenquellennamen. Implementiert die vom Treiber-Manager.|  
|**SQLDescribeParam**|Gibt die Beschreibung einer parametermarkierung zugeordneten vorbereitete SQL-Anweisung zurück.<br /><br /> Gibt zurück, von welchen der Parameter ist, basierend auf der Analyse der Anweisung, eine bestmögliche Schätzung. Wenn der Parametertyp kann nicht bestimmt werden, gibt SQL_VARCHAR Länge: 2000 zurück.|  
|**SQLDrivers**|Implementiert die vom Treiber-Manager.|  
|**SQLExtendedFetch**|Ähnlich wie **SQLFetch** jedoch mehrere Zeilen, die über ein Array für jede Spalte zurückgegeben. Das Resultset ist vorwärts bildlauffähige und rückwärts-scrollfähig des Cursors definiert ist, werden statische, nicht nur vorwärts gerichteten vorgenommen werden kann. Für Vorwärtscursor mit standardbindung für die Spalte Daten aus Datasets, die größer als das Verbindungsattribut BUFFERSIZE Spalte direkt in den Datenpuffer abgerufen. Lesezeichen mit variabler Länge, die nicht unterstützt, und unterstützt nicht das Abrufen eines Rowsets mit einem Offset (ungleich 0) in einem Lesezeichen.|  
|**SQLForeignKeys**|Gibt eine Liste von Fremdschlüsseln in einer einzelnen Tabelle oder eine Liste von Fremdschlüsseln in anderen Tabellen, die auf einer einzelnen Tabelle verweisen zurück.|  
|**SQLMoreResults**|Bestimmt, ob weitere Ergebnisse ausstehen, die für ein Anweisungshandle Befehls beschäftigt, SELECT, UPDATE, INSERT oder DELETE-Anweisungen enthält, und wenn dies der Fall ist, initialisiert die Verarbeitung für diese Ergebnisse.<br /><br /> Oracle unterstützt mehrerer Resultsets aus gespeicherten Prozeduren werden nur die Verwendung von {Resultset...} Escape-Sequenzen.|  
|**SQLNativeSql**|Weitere Informationen zur Verwendung finden Sie unter [Zurückgeben von Arrayparametern aus gespeicherten Prozeduren](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLNumParams**|Gibt die Anzahl von Parametern in einer SQL-Anweisung zurück. Die Anzahl der Parameter sollte die Anzahl der Fragezeichen in der SQL-Anweisung, die an gleich **SQLPrepare**.|  
|**SQLPrimaryKeys**|Gibt den Namen der Spalten, die den Primärschlüssel für eine Tabelle bilden.|  
|**SQLProcedureColumns**|Gibt eine Liste von Eingabe- und Ausgabeparameter, der zurückgegebene Wert, der Spalten im Resultset einer einzigen Prozedur sowie zwei zusätzliche Spalten, die ÜBERLADUNG und ORDINAL_POSITION zurück. ÜBERLADUNG ist die ÜBERLADUNG-Spalte aus der Tabelle ALL_ARGUMENTS der Oracle-Wörterbuch an. ORDINAL_POSITION ist der SEQUENCE-Spalte aus der Tabelle ALL_ARGUMENTS der Oracle-Wörterbuch an. Für verpackten Prozeduren ist die NAME der Prozedur-Spalte *packagename.procedurename* Format. Die prozedurspalten auf, der ein Synonym erstellt, die auf eine Prozedur oder Funktion verweist, wird nicht zurückgegeben werden.|  
|**SQLProcedures**|Gibt eine Liste der Verfahren in der Datenquelle zurück. Für verpackten Prozeduren ist die NAME der Prozedur-Spalte *packagename.procedurename* Format.<br /><br /> Da Oracle nicht über eine Möglichkeit zur Unterscheidung der verpackten Prozeduren von kompilierten Funktionen bietet, gibt der Treiber die SQL_PT_UNKNOWN zurück, für die Spalte PROCEDURE_TYPE aus.|  
|**SQLSetPos**|Die Cursorposition in einem Rowset festgelegt. Sie können **SQLSetPos** mit **SQLGetData** um Zeilen von ungebundenen Spalten abzurufen, nach dem Positionieren des Cursors an einer bestimmten Zeile im Rowset. Das Resultset mit hinzugefügten Zeilen *fOption* SQL_ADD werden hinzugefügt, nachdem die letzte Zeile im Resultset.|  
|**SQLSetScrollOptions**|Legt Optionen, die zum Steuern des Verhaltens von Cursorn, die ein Anweisungshandle Befehls beschäftigt zugeordnet. Weitere Informationen finden Sie unter [Cursortyp und Parallelitätskombinationen](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|
