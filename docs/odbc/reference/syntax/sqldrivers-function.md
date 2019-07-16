---
title: SQLDrivers-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDrivers
helpviewer_keywords:
- SQLDrivers function [ODBC]
ms.assetid: 6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f54be3d11f4870533513f464c1afdae13e04f367
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104661"
---
# <a name="sqldrivers-function"></a>SQLDrivers-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 2.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLDrivers** enthält Beschreibungen der Treiber und Treiber-Attribut-Schlüsselwörter. Diese Funktion ist nur vom Treiber-Manager implementiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLDrivers(  
     SQLHENV         EnvironmentHandle,  
     SQLUSMALLINT    Direction,  
     SQLCHAR *       DriverDescription,  
     SQLSMALLINT     BufferLength1,  
     SQLSMALLINT *   DescriptionLengthPtr,  
     SQLCHAR *       DriverAttributes,  
     SQLSMALLINT     BufferLength2,  
     SQLSMALLINT *   AttributesLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *EnvironmentHandle*  
 [Eingabe] Umgebungshandles.  
  
 *Richtung*  
 [Eingabe] Bestimmt, ob der Treiber-Manager die nächste treiberbeschreibung in der Liste (SQL_FETCH_NEXT ruft) gibt an, ob die Suche am Anfang der Liste (SQL_FETCH_FIRST) beginnt.  
  
 *DriverDescription*  
 [Ausgabe] Zeiger auf einen Puffer, in die die treiberbeschreibung zurückgegeben werden sollen.  
  
 Wenn *DriverDescription* NULL ist, *DescriptionLengthPtr* gibt immer noch die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) zur zurück in die Puffer verweist *DriverDescription*.  
  
 *BufferLength1*  
 [Eingabe] Länge der **DriverDescription* Puffers in Zeichen.  
  
 *DescriptionLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe der Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen) zur Verfügung, die in zurückgegeben \* *DriverDescription*. Wenn die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als oder gleich ist *BufferLength1*, um die treiberbeschreibung in \* *DriverDescription* auf abgeschnitten  *BufferLength1* abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
 *DriverAttributes*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Liste der Treiber-Attribut-Wert-Paaren zurück (siehe "Kommentare").  
  
 Wenn *DriverAttributes* NULL ist, *AttributesLengthPtr* gibt die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer zurückgegeben verweist *DriverAttributes*.  
  
 *BufferLength2*  
 [Eingabe] Länge der \* *DriverAttributes* Puffers in Zeichen. Wenn die  *\*DriverDescription* Wert ist eine Unicodezeichenfolge (beim Aufrufen von **SQLDriversW**), wird die *Pufferlänge* Argument muss eine gerade Zahl sein.  
  
 *AttributesLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierung Byte) zurückgegeben. verfügbar für die zurückzugebenden in \* *DriverAttributes*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *BufferLength2*, die Liste der Attribut-Wert-Paare im \* *DriverAttributes* auf abgeschnitten  *BufferLength2* abzüglich der Länge des Zeichens Null-Terminierung vorliegt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA zurückgibt, wird SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDrivers** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, zurück ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_ENV und *behandeln* von *EnvironmentHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLDrivers** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|(DM)-Treiber-Manager-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|(DM) des Puffers \* *DriverDescription* nicht groß genug war, um die vollständige treiberbeschreibung zurückzugeben. Aus diesem Grund wurde die Beschreibung abgeschnitten. Die Länge der treiberbeschreibung vollständige wird zurückgegeben, \* *DescriptionLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> (DM) des Puffers \* *DriverAttributes* war nicht groß genug, um die vollständige Liste der Attribut-Wert-Paaren zurück. Aus diesem Grund wurde die Liste abgeschnitten. Die Länge der Liste den ungekürzten von Attribut-Wert-Paaren zurückgegeben **AttributesLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber-Managers (DM) wurde, kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) für Argument angegebene Wert *BufferLength1* war kleiner als 0.<br /><br /> (DM) für Argument angegebene Wert *BufferLength2* war kleiner als 0 oder gleich 1.|  
|HY103|Ungültiger Abrufcode|(DM) der Wert für das Argument angegebene *Richtung* war nicht gleich SQL_FETCH_FIRST oder SQL_FETCH_NEXT.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Kommentare  
 **SQLDrivers** gibt zurück, um die treiberbeschreibung in die \* *DriverDescription* Puffer. Es gibt zusätzliche Informationen über den Treiber in der \* *DriverAttributes* Puffer als eine Liste von Schlüsselwort-Wert-Paaren. Alle Schlüsselwörter aufgeführt für Treiber für alle Treiber, mit Ausnahme von zurückgegeben werden in den Systeminformationen **CreateDSN**, die verwendet, um die Erstellung von Datenquellen aufzufordern, und aus diesem Grund ist optional. Jedes Paar wird mit null Byte beendet, und die vollständige Liste mit null Byte beendet ist (d. h. zwei null-Bytes markieren Sie am Ende der Liste). Beispielsweise gibt möglicherweise einen dateibasierten Treibers mithilfe C++-Syntax die folgende Liste der Attribute zurück ("\0" steht für ein Null-Zeichen):  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 Wenn \* *DriverAttributes* ist nicht groß genug für die gesamte Liste, wird die befehlszeilenergänzungsliste, **SQLDrivers** SQLSTATE 01004 (Daten wurden abgeschnitten) und die Länge der Liste zurückgegeben (mit Ausnahme der letzte Byte von Null-Terminierung vorliegt) wird zurückgegeben, **AttributesLengthPtr*.  
  
 Schlüsselwörter der Treiber-Attribut werden aus den Systeminformationen hinzugefügt, wenn der Treiber installiert ist. Weitere Informationen finden Sie unter [Installieren von ODBC-Komponenten](../../../odbc/reference/install/installing-odbc-components.md).  
  
 Kann eine Anwendung aufrufen **SQLDrivers** mehrere Male auf, alle Treiber Beschreibungen abgerufen. Der Treiber-Manager ruft diese Informationen aus den Systeminformationen ab. Wenn es keine weitere Treiber Beschreibungen gibt **SQLDrivers** SQL_NO_DATA zurückgibt. Wenn **SQLDrivers** mit SQL_FETCH_NEXT aufgerufen wird, unmittelbar nachdem SQL_NO_DATA zurückgegeben wird, um die erste treiberbeschreibung gibt. Informationen zur Verwendung von zurückgegebenen Informationen in einer Anwendungs **SQLDrivers**, finden Sie unter [Auswählen einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Wenn SQL_FETCH_NEXT, um übergeben wird **SQLDrivers** beim ersten Aufruf ist, **SQLDrivers** gibt die Namen der ersten Datenquelle zurück.  
  
 Da **SQLDrivers** implementiert im Treiber-Manager wird für alle Treiber unabhängig davon, einen bestimmten Treiber Einhaltung von Standards unterstützt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ermitteln und Auflisten von Werten, die für die Verbindung mit einer Datenquelle|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Zurückgeben von Datenquellennamen|[SQLDataSources-Funktion](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle mit einer Zeichenfolge oder eines Dialogfelds Verbindungsdialogfeld|[SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
