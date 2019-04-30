---
title: SQLDataSources-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSources
helpviewer_keywords:
- SQLDataSources function [ODBC]
ms.assetid: 3f63b1b4-e70e-44cd-96c6-6878d50d0117
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7b04dc2554b820fc6ac8344457754aae984d4b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63258852"
---
# <a name="sqldatasources-function"></a>SQLDataSources-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLDataSources** gibt Informationen zu einer Datenquelle zurück. Diese Funktion ist nur vom Treiber-Manager implementiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLDataSources(  
     SQLHENV          EnvironmentHandle,  
     SQLUSMALLINT     Direction,  
     SQLCHAR *        ServerName,  
     SQLSMALLINT      BufferLength1,  
     SQLSMALLINT *    NameLength1Ptr,  
     SQLCHAR *        Description,  
     SQLSMALLINT      BufferLength2,  
     SQLSMALLINT *    NameLength2Ptr);  
```  
  
## <a name="arguments"></a>Argumente  
 *EnvironmentHandle*  
 [Eingabe] Umgebungshandles.  
  
 *Richtung*  
 [Eingabe] Bestimmt, welche Datenquelle des Treiber-Managers über Informationen zurückgibt. Mögliche Werte sind:  
  
 SQL_FETCH_NEXT (auf der nächsten Datenquellenname in der Liste abrufen), SQL_FETCH_FIRST (abzurufenden vom Anfang der Liste), SQL_FETCH_FIRST_USER (zum Abrufen der ersten Benutzer-DSN) oder SQL_FETCH_FIRST_SYSTEM (abzurufenden vom ersten System-DSN).  
  
 Wenn *Richtung* nastaven NA hodnotu SQL_FETCH_FIRST, nachfolgende Aufrufe von **SQLDataSources** mit *Richtung* auf SQL_FETCH_NEXT zurückgeben, sowohl Benutzer-als auch System-DSNs. Wenn *Richtung* nastaven NA hodnotu SQL_FETCH_FIRST_USER, alle nachfolgenden Aufrufe **SQLDataSources** mit *Richtung* auf SQL_FETCH_NEXT zurückgeben, nur die Benutzer-DSNs. Wenn *Richtung* nastaven NA hodnotu SQL_FETCH_FIRST_SYSTEM, alle nachfolgenden Aufrufe **SQLDataSources** mit *Richtung* auf SQL_FETCH_NEXT zurückgeben, nur System-DSNs.  
  
 *ServerName*  
 [Ausgabe] Zeiger auf einen Puffer, in den Namen der Datenquelle zurückgegeben werden sollen.  
  
 Wenn *ServerName* NULL ist, *NameLength1Ptr* gibt die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *ServerName*.  
  
 *BufferLength1*  
 [Eingabe] Länge der **ServerName* Puffer, in Zeichen; Dies muss nicht länger als SQL_MAX_DSN_LENGTH sowie das Null-Abschlusszeichen sein.  
  
 *NameLength1Ptr*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe der Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen) zur Verfügung, die in zurückgegeben \* *ServerName*. Wenn die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als oder gleich ist *BufferLength1*, der Name der Datenquelle in \* *ServerName* auf abgeschnitten *BufferLength1* abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
 *Beschreibung*  
 [Ausgabe] Zeiger auf einen Puffer, in die die Beschreibung des Treibers verknüpft ist, mit der Datenquelle zurückgegeben werden sollen. Z. B. Access oder SQL Server.  
  
 Wenn *Beschreibung* NULL ist, *NameLength2Ptr* gibt die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *Beschreibung*.  
  
 *BufferLength2*  
 [Eingabe] Länge in Zeichen von der **Beschreibung* Puffer.  
  
 *NameLength2Ptr*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe der Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen) zur Verfügung, die in zurückgegeben \* *Beschreibung*. Wenn die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als oder gleich ist *BufferLength2*, um die treiberbeschreibung in \* *Beschreibung* auf abgeschnitten *BufferLength2*  abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDataSources** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit eine *HandleType*SQL_HANDLE_ENV auf, und ein *behandeln* von *EnvironmentHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLDataSources** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|(DM)-Treiber-Manager-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|(DM) des Puffers \* *ServerName* nicht groß genug war, der vollständige Name der Datenquelle zurückgegeben. Aus diesem Grund wurde der Name verkürzt angezeigt. Die Länge der Namen der gesamten Datenquelle wird im zurückgegeben \* *NameLength1Ptr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> (DM) des Puffers \* *Beschreibung* nicht groß genug war, um die vollständige treiberbeschreibung zurückzugeben. Aus diesem Grund wurde die Beschreibung abgeschnitten. Die Länge der die ungekürzte datenquellenbeschreibung wird zurückgegeben, **NameLength2Ptr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler.|(DM) ist ein Fehler aufgetreten für die gab es keine spezifischen SQLSTATE und für die keine implementierungsabhängige SQLSTATE definiert wurde. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber-Managers (DM) wurde, kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) für Argument angegebene Wert *BufferLength1* war kleiner als 0.<br /><br /> (DM) für Argument angegebene Wert *BufferLength2* war kleiner als 0.|  
|HY103|Ungültiger Abrufcode|(DM) der Wert für das Argument angegebene *Richtung* war nicht gleich SQL_FETCH_FIRST SQL_FETCH_FIRST_USER, SQL_FETCH_FIRST_SYSTEM oder SQL_FETCH_NEXT.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Kommentare  
 Da **SQLDataSources** implementiert im Treiber-Manager wird für alle Treiber unabhängig davon, einen bestimmten Treiber Einhaltung von Standards unterstützt.  
  
 Kann eine Anwendung aufrufen **SQLDataSources** mehrere Male auf, um alle Datenquellennamen abzurufen. Der Treiber-Manager ruft diese Informationen aus den Systeminformationen ab. Der Treiber-Manager gibt SQL_NO_DATA zurück, wenn es keine weitere Datenquellennamen sind. Wenn **SQLDataSources** mit SQL_FETCH_NEXT aufgerufen wird, unmittelbar nachdem SQL_NO_DATA zurückgegeben wird, wird der Name der ersten Datenquelle zurückgegeben. Informationen zur Verwendung von zurückgegebenen Informationen in einer Anwendungs **SQLDataSources**, finden Sie unter [Auswählen einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Wenn SQL_FETCH_NEXT, um übergeben wird **SQLDataSources** beim ersten Aufruf ist, wird der Name der ersten Datenquelle zurückgegeben.  
  
 Der Treiber ermittelt, wie die Datenquellennamen mit tatsächlichen Datenquellen zugeordnet werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ermitteln und Auflisten von Werten, die für die Verbindung mit einer Datenquelle|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle mit einer Zeichenfolge oder eines Dialogfelds Verbindungsdialogfeld|[SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Zurückgeben von Beschreibungen der Treiber und Attribute|[SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
