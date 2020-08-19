---
description: API-Funktionen der ersten Ebene (ODBC-Treiber für Oracle)
title: API-Funktionen der Ebene 1 (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
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
ms.openlocfilehash: 0c82ab0f481fbc60d0308895640371e84886e77e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483543"
---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>API-Funktionen der ersten Ebene (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Die Funktionen auf dieser Ebene bieten eine Kern Schnittstellen Konformität sowie zusätzliche Funktionen wie z. b. Transaktionsunterstützung.  
  
|API-Funktion|Notizen|  
|------------------|-----------|  
|**SQLColumns**|Erstellt ein Resultset für eine Tabelle, bei der es sich um die Spaltenliste für die angegebene Tabelle oder Tabellen handelt. Wenn Sie Spalten für ein öffentliches Synonym anfordern, müssen Sie das synonymcolumns-Verbindungs Attribut festgelegt und eine leere Zeichenfolge als *sztableowner* -Argument angegeben haben. Beim Zurückgeben von Spalten für öffentliche Synonyme legt der Treiber die Tabellennamen Spalte auf eine leere Zeichenfolge fest. Das Resultset enthält eine zusätzliche Spalte, Ordinalposition, am Ende jeder Zeile. Dieser Wert ist die Ordinalposition der Spalte in der Tabelle.|  
|**SQLDriverConnect**|Stellt eine Verbindung mit einer vorhandenen Datenquelle her. Weitere Informationen finden Sie unter [Format und Attribute der Verbindungs Zeichenfolge](../../odbc/microsoft/connection-string-format-and-attributes.md).|  
|**SQLGetConnectOption**|Gibt die aktuelle Einstellung einer Verbindungs Option zurück. Diese Funktion wird teilweise unterstützt. Der Treiber unterstützt alle Werte für das *fOption* -Argument, unterstützt jedoch einige *vParam* -Werte für das *fOption* -Argument [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md)nicht. Weitere Informationen finden Sie unter [Connect Options](../../odbc/microsoft/connect-options.md).|  
|**SQLGetData**|Ruft den Wert eines einzelnen Felds im aktuellen Datensatz des angegebenen Resultsets ab.|  
|**SQLGetFunctions**|Gibt true für alle unterstützten Funktionen zurück. Wird vom Treiber-Manager implementiert.|  
|**SQLGetInfo**|Gibt Informationen \* über den ODBC-Treiber für Oracle und die Datenquelle, die einem Verbindungs Handle ( *hdbc*) zugeordnet ist, mit SQLHDBC, sqlusmallint, SQLPOINTER, SQLSMALLINT und SQLSMALLINT zurück.|  
|**SQLGetStmtOption**|Gibt die aktuelle Einstellung einer Anweisungs Option zurück. Weitere Informationen finden Sie unter [Anweisungs Optionen](../../odbc/microsoft/statement-options.md).|  
|**SQLGetTypeInfo**|Gibt Informationen zu den Datentypen zurück, die von einer Datenquelle unterstützt werden. Der Treiber gibt die Informationen in einem SQL-Resultset zurück.|  
|**SQLParamData**|Wird in Verbindung mit **SQLPutData** verwendet, um Parameterdaten zur Anweisungs Ausführungszeit anzugeben.|  
|**SQLPutData**|Ermöglicht es einer Anwendung, Daten für einen Parameter oder eine Spalte zur Anweisungs Ausführungszeit an den Treiber zu senden.|  
|**SQLSetConnectOption**|Bietet Zugriff auf Optionen, die die Aspekte der Verbindung steuern. Diese Funktion wird teilweise unterstützt: der Treiber unterstützt alle Werte für das *fOption* -Argument, unterstützt jedoch einige *vParam* -Werte für das *fOption* -Argument [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md)nicht. Weitere Informationen finden Sie unter [Connect Options](../../odbc/microsoft/connect-options.md).|  
|**SQLSetStmtOption**|Legt Optionen fest, die sich auf ein Anweisungs Handle ( *hstmt*) beziehen. Weitere Informationen finden Sie unter [Anweisungs Optionen](../../odbc/microsoft/statement-options.md).|  
|**'SQLSpecialColumns'**|Ruft den optimalen Satz von Spalten ab, der eine Zeile in der Tabelle eindeutig identifiziert.|  
|**'SQLStatistics'**|Ruft eine Liste von Statistiken zu einer einzelnen Tabelle und den Indizes bzw. Tagnamen ab, die der Tabelle zugeordnet sind. Der Treiber gibt die Informationen als Resultset zurück.|  
|**SQLTables**|Gibt die Liste der Tabellennamen zurück, die durch den-Parameter in der **SQLTables** -Anweisung angegeben werden. Wenn kein Parameter angegeben wird, gibt die in der aktuellen Datenquelle gespeicherten Tabellennamen zurück. Der Treiber gibt die Informationen als Resultset zurück.<br /><br /> Enumerationstyp Aufrufe empfangen keinen resultseteintrag für Remote Sichten oder lokale parametrisierte Sichten. Ein **SQLTables** -Befehl mit einem eindeutigen tabellenbezeichnerspezifizierer findet eine Entsprechung für eine solche Sicht, falls vorhanden, jedoch mit diesem Namen. Dadurch kann die API vor der Erstellung einer neuen Tabelle Nachnamens Konflikten suchen.<br /><br /> Öffentliche Synonyme werden mit dem TABLE_OWNER Wert "" zurückgegeben.<br /><br /> Sichten, die sich im Besitz von sys oder System befinden, werden als System Ansicht identifiziert.|
