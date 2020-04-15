---
title: API-Funktionen der Stufe 1 (ODBC-Treiber für Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], ODBC driver for Oracle
- ODBC level 1 API functions [ODBC]
- ODBC driver for Oracle [ODBC], functions
- level 1 API functions [ODBC]
- API functions [ODBC]
ms.assetid: 98cced6f-41b8-43c1-a3cd-f4ea1615c0af
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37305ee75ebeb0686bafe039f1102cb3c6e18674
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299950"
---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>API-Funktionen der ersten Ebene (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Funktionen auf dieser Ebene bieten Core-Schnittstellenkonformität sowie zusätzliche Funktionen wie Transaktionsunterstützung.  
  
|API-Funktion|Notizen|  
|------------------|-----------|  
|**SQLColumns**|Erstellt ein Resultset für eine Tabelle, d. h. die Spaltenliste für die angegebene Tabelle oder Tabellen. Wenn Sie Spalten für ein PUBLIC-Synonym anfordern, müssen Sie das VERBINDUNGSattribut SYNONYMCOLUMNS festgelegt und eine leere Zeichenfolge als *szTableOwner-Argument* angegeben haben. Beim Zurückgeben von Spalten für PUBLIC-Synonyme legt der Treiber die Spalte TABLE NAME auf eine leere Zeichenfolge fest. Das Resultset enthält eine zusätzliche Spalte, ORDINAL POSITION, am Ende jeder Zeile. Dieser Wert ist die Ordinalposition der Spalte in der Tabelle.|  
|**SQLDriverConnect**|Stellt eine Verbindung mit einer vorhandenen Datenquelle her. Weitere Informationen finden Sie unter [Verbindungszeichenfolgenformat und Attribute](../../odbc/microsoft/connection-string-format-and-attributes.md).|  
|**SQLGetConnectOption**|Gibt die aktuelle Einstellung einer Verbindungsoption zurück. Diese Funktion wird teilweise unterstützt. Der Treiber unterstützt alle Werte für das *fOption-Argument,* unterstützt jedoch keine *vParam-Werte* für das *fOption-Argument* [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). Weitere Informationen finden Sie unter [Verbindungsoptionen](../../odbc/microsoft/connect-options.md).|  
|**SQLGetData**|Ruft den Wert eines einzelnen Felds im aktuellen Datensatz des angegebenen Resultsets ab.|  
|**SQLGetFunctions**|Gibt TRUE für alle unterstützten Funktionen zurück. Vom Treiber-Manager implementiert.|  
|**SQLGetInfo**|Gibt Informationen zurück, einschließlich SQLHDBC, SQLUSMALLINT, SQLPOINTER, SQLSMALLINT und SQLSMALLINT \*, über den ODBC-Treiber für Oracle und die Datenquelle, die einem Verbindungshandle zugeordnet ist, *hdbc*.|  
|**SQLGetStmtOption**|Gibt die aktuelle Einstellung einer Anweisungsoption zurück. Weitere Informationen finden Sie unter [Anweisungsoptionen](../../odbc/microsoft/statement-options.md).|  
|**SQLGetTypeInfo**|Gibt Informationen zu den Datentypen zurück, die von einer Datenquelle unterstützt werden. Der Treiber gibt die Informationen in einem SQL-Ergebnissatz zurück.|  
|**SQLParamData**|Wird in Verbindung mit **SQLPutData** verwendet, um Parameterdaten zur Ausführungszeit der Anweisung anzugeben.|  
|**SQLPutData**|Ermöglicht einer Anwendung, Daten für einen Parameter oder eine Spalte zum Zeitpunkt der Ausführung sende.|  
|**SQLSetConnectOption**|Bietet Zugriff auf Optionen, die Aspekte der Verbindung steuern. Diese Funktion wird teilweise unterstützt: Der Treiber unterstützt alle Werte für das *fOption-Argument,* unterstützt jedoch keine *vParam-Werte* für das *fOption-Argument* [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). Weitere Informationen finden Sie unter [Verbindungsoptionen](../../odbc/microsoft/connect-options.md).|  
|**SQLSetStmtOption**|Legt Optionen fest, die sich auf ein Anweisungshandle beziehen, *hstmt*. Weitere Informationen finden Sie unter [Anweisungsoptionen](../../odbc/microsoft/statement-options.md).|  
|**'SQLSpecialColumns'**|Ruft den optimalen Satz von Spalten ab, der eine Zeile in der Tabelle eindeutig identifiziert.|  
|**'SQLStatistics'**|Ruft eine Liste von Statistiken zu einer einzelnen Tabelle und den der Tabelle zugeordneten Indizes oder Tagnamen ab. Der Treiber gibt die Informationen als Ergebnissatz zurück.|  
|**SQLTables**|Gibt die Liste der Tabellennamen zurück, die durch den Parameter in der **SQLTables-Anweisung** angegeben sind. Wenn kein Parameter angegeben ist, werden die in der aktuellen Datenquelle gespeicherten Tabellennamen zurückgegeben. Der Treiber gibt die Informationen als Ergebnissatz zurück.<br /><br /> Enumerationstypaufrufe erhalten keinen Ergebnissatzeintrag für Remoteansichten oder lokale parametrisierte Ansichten. Ein Aufruf von **SQLTables** mit einem eindeutigen Tabellennamensbezeichner findet jedoch eine Übereinstimmung für eine solche Ansicht, falls vorhanden, mit diesem Namen. Dadurch kann die API vor dem Erstellen einer neuen Tabelle nach Namenskonflikten suchen.<br /><br /> PUBLIC Synonyme werden mit einem TABLE_OWNER Wert von "" zurückgegeben.<br /><br /> VIEWS von SYS oder SYSTEM werden als SYSTEM VIEW identifiziert.|
