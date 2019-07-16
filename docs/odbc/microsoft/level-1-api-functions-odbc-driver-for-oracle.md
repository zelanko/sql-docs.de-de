---
title: Ebene-1-API-Funktionen (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cb1771f88987073b1ef0bcc106f8de28549affe6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085472"
---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>API-Funktionen der ersten Ebene (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Auf dieser Ebene geben kernschnittstellenübereinstimmung-Funktionen sowie zusätzliche Funktionen wie z. B. Transaktionen unterstützen.  
  
|API-Funktion|Hinweise|  
|------------------|-----------|  
|**SQLColumns**|Erstellt ein Resultset für eine Tabelle, die in der Liste der Spalten für die angegebene Tabelle ist oder Tabellen. Wenn Sie Spalten für eine öffentliche Synonym anfordern, Sie müssen das Verbindungsattribut SYNONYMCOLUMNS festgelegt und angegeben haben eine leere Zeichenfolge als das *SzTableOwner* Argument. Beim Zurückgeben von Spalten für Öffentliche Synonyme, setzt der Treiber die TABELLENNAMEN-Spalte auf eine leere Zeichenfolge. Das Resultset enthält eine zusätzliche Spalte mit der ORDNUNGSZAHL POSITION am Ende jeder Zeile. Dieser Wert ist die Ordnungsposition der Spalte in der Tabelle.|  
|**SQLDriverConnect**|Eine Verbindung mit einer vorhandenen Datenquelle. Weitere Informationen finden Sie unter [Verbindungszeichenfolgenformat und Attribute](../../odbc/microsoft/connection-string-format-and-attributes.md).|  
|**SQLGetConnectOption**|Gibt die aktuelle Einstellung der eine Verbindungsoption fest. Diese Funktion wird teilweise unterstützt. Der Treiber unterstützt alle Werte für die *fOption* Argument unterstützt jedoch nicht einige *vParam* Werte für die *fOption* Argument [SQL_TXN_ISOLATION ](../../odbc/microsoft/connect-options.md). Weitere Informationen finden Sie unter [Optionen verbinden](../../odbc/microsoft/connect-options.md).|  
|**SQLGetData**|Ruft den Wert eines einzelnen Felds in den aktuellen Datensatz des angegebenen Resultset.|  
|**SQLGetFunctions**|Gibt "true" für alle unterstützten Funktionen. Implementiert die vom Treiber-Manager.|  
|**SQLGetInfo**|Gibt Informationen zurück, wie z.B. SQLHDBC SQLUSMALLINT, SQLPOINTER, SQLSMALLINT und SQLSMALLINT \*, über den ODBC-Treiber für Oracle und der Datenquelle zugeordnete ein Verbindungshandle *Hdbc*.|  
|**SQLGetStmtOption**|Gibt die aktuelle Einstellung der Option-Anweisung ein. Weitere Informationen finden Sie unter [Anweisungsoptionen](../../odbc/microsoft/statement-options.md).|  
|**SQLGetTypeInfo**|Gibt Informationen zu den Datentypen unterstützt, die von einer Datenquelle zurück. Der Treiber zurückgegeben die Informationen in einer SQL-Resultset.|  
|**SQLParamData**|Zusammen mit **SQLPutData** Parameterdaten während der Ausführung der Anweisung an.|  
|**SQLPutData**|Ermöglicht einer Anwendung zum Senden von Daten für einen Parameter oder eine Spalte für den Treiber während der Ausführung der Anweisung.|  
|**SQLSetConnectOption**|Bietet Zugriff auf Optionen, die Aspekte der Verbindung steuern. Diese Funktion wird teilweise unterstützt: Der Treiber unterstützt alle Werte für die *fOption* Argument unterstützt jedoch nicht einige *vParam* Werte für die *fOption* Argument [SQL_TXN_ISOLATION ](../../odbc/microsoft/connect-options.md). Weitere Informationen finden Sie unter [Optionen verbinden](../../odbc/microsoft/connect-options.md).|  
|**SQLSetStmtOption**|Legt fest, die im Zusammenhang mit der ein Anweisungshandle *Befehls beschäftigt*. Weitere Informationen finden Sie unter [Anweisungsoptionen](../../odbc/microsoft/statement-options.md).|  
|**SQLSpecialColumns**|Ruft ab, die optimale Gruppe von Spalten, die eine Zeile in der Tabelle eindeutig identifiziert.|  
|**SQLStatistics**|Ruft eine Liste der Statistiken zu einer einzelnen Tabelle und die Indizes oder die Tag-Namen, die in der Tabelle zugeordnet. Der Treiber gibt zurück, die Informationen als Resultset.|  
|**SQLTables**|Gibt die Liste der vom Parameter angegebenen Tabellennamen die **SQLTables** Anweisung. Wenn kein Parameter angegeben wird, gibt die Namen der Tabellen in der aktuellen Datenquelle gespeichert. Der Treiber gibt zurück, die Informationen als Resultset.<br /><br /> Enumeration Typs ruft erhalten einen Ergebnis Set-Eintrag für remote-Ansichten oder lokalen parametrisierte Sichten nicht. Allerdings einen Aufruf von **SQLTables** mit einer eindeutigen Tabelle Namensbezeichner findet eine Übereinstimmung für eine Ansicht, falls vorhanden, mit diesem Namen; Dadurch wird die API zu prüfen, Namenskonflikte vor der Erstellung einer neuen Tabelle.<br /><br /> Öffentliche Synonyme werden zurückgegeben, mit dem TABLE_OWNER Wert "".<br /><br /> Ansichten, die im Besitz von SYS oder SYSTEM werden als SYSTEMSICHT identifiziert.|
