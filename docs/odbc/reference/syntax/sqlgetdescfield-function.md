---
title: SQLGetDescField-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDescField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescField
helpviewer_keywords:
- SQLGetDescField function [ODBC]
ms.assetid: f09ff660-1e4a-4370-be85-90d4da0487d3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cdf2990056c297d217248543812e347b61d3486d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103812"
---
# <a name="sqlgetdescfield-function"></a>SQLGetDescField-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standardkompatibilität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDescField** gibt die aktuelle Einstellung oder der Wert, der ein einzelnes Feld einem anwendungsparameterdeskriptor-Datensatz zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetDescField(  
     SQLHDESC        DescriptorHandle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     FieldIdentifier,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *DescriptorHandle*  
 [Eingabe] Deskriptorhandles.  
  
 *RecNumber*  
 [Eingabe] Gibt an, die von dem die Anwendung Informationen sucht anwendungsparameterdeskriptor-Datensatz. Deskriptordatensätze sind von 0 (null) mit der Datensatznummer lesezeichendatensatzes wird 0 nummeriert. Wenn die *FieldIdentifier* Argument gibt an, ein Headerfeld *RecNumber* wird ignoriert. Wenn *RecNumber* ist kleiner als oder gleich SQL_DESC_COUNT die Zeile enthält jedoch keine Daten für eine Spalte oder Parameter, einen Aufruf von **SQLGetDescField** gibt die Standardwerte der Felder zurück. (Weitere Informationen finden Sie unter "Initialisierung der Deskriptorfelder" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *FieldIdentifier*  
 [Eingabe] Gibt das Feld des Deskriptors, deren Wert zurückgegeben werden. Weitere Informationen finden Sie unter der "*FieldIdentifier* Argument" im Abschnitt [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 *ValuePtr*  
 [Ausgabe] Zeiger auf einen Puffer in das die Deskriptorinformationen zurückgegeben. Der Datentyp hängt vom Wert der *FieldIdentifier*.  
  
 Wenn *ValuePtr* Ganzzahltyp ist, sollten Anwendungen einen Puffer mit SQLULEN verwenden und initialisiert den Wert auf 0 vor dem Aufrufen dieser Funktion als einige Treiber kann nur die unteren 32-Bit- oder 16-Bit eines Puffers zu schreiben und lassen Bits höherer Ordnung unverändert.  
  
 Wenn *ValuePtr* NULL ist, *StringLengthPtr* gibt die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *ValuePtr*.  
  
 *BufferLength*  
 [Eingabe] Wenn *FieldIdentifier* ist ein ODBC-definierten-Feld und *ValuePtr* zeigt auf eine Zeichenfolge oder ein binärer Puffer, in dieses Argument muss die Länge des \* *ValuePtr*. Wenn *FieldIdentifier* ist ein ODBC-definierten-Feld und \* *ValuePtr* ist eine ganze Zahl, *Pufferlänge* wird ignoriert. Wenn der Wert in  *\*ValuePtr* wird von einem Unicode-Datentyp (beim Aufrufen von **SQLGetDescFieldW**), wird die *Pufferlänge* Argument muss eine gerade Zahl sein.  
  
 Wenn *FieldIdentifier* ist ein Feld treiberdefinierten, die Anwendung zeigt die Art des Felds um den Treiber-Manager an, indem die *Pufferlänge* Argument. *BufferLength* können die folgenden Werte aufweisen:  
  
-   Wenn  *\*ValuePtr* ist ein Zeiger auf eine Zeichenfolge, *Pufferlänge* ist die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn  *\*ValuePtr* ist ein Zeiger auf ein binärer Puffer, aus, und klicken Sie dann die Anwendung das Ergebnis der SQL_LEN_BINARY_ATTR platziert (*Länge*)-Makro in *Pufferlänge*. Dadurch wird einen negativen Wert im platziert *Pufferlänge*.  
  
-   Wenn  *\*ValuePtr* ist ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder Binärzeichenfolge, *Pufferlänge* Wert SQL_IS_POINTER haben sollte.  
  
-   Wenn  *\*ValuePtr* ist einen Datentyp fester Länge enthält *Pufferlänge* ist entweder SQL_IS_INTEGER SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_IS_USMALLINT, nach Bedarf.  
  
 *StringLengthPtr*  
 [Ausgabe] Zeiger auf den Puffer für die Rückgabe der Gesamtanzahl der Bytes, die (mit Ausnahme von der Anzahl der Bytes, die für die Null-Terminierungszeichen erforderlich) zur Verfügung, die in zurückgegeben **ValuePtr*.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA zurückgibt oder SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA zurückgegeben wird, wenn *RecNumber* ist größer als die aktuelle Anzahl der deskriptordatensätze.  
  
 SQL_NO_DATA zurückgegeben wird, wenn *DescriptorHandle* ist ein IRD-Handle und die Anweisung befindet sich im Zustand vorbereitete oder ausgeführte. es wurde jedoch keine geöffneten Cursor zugeordnet.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetDescField** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und eine *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLGetDescField** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Puffer \* *ValuePtr* war nicht groß genug, um die gesamte Deskriptorfeld zurückgeben, damit das Feld abgeschnitten wurde. Die Länge des Felds den ungekürzten Deskriptor wird zurückgegeben, **StringLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|(DM) die *RecNumber* Argument war gleich 0, das Anweisungsattribut SQL_ATTR_USE_BOOKMARK SQL_UB_OFF, und die *DescriptorHandle* Argument war ein IRD-Handle. (Dieser Fehler kann für eine explizit zugewiesene Deskriptor zurückgegeben werden, nur dann, wenn der Deskriptor ein Anweisungshandle zugeordnet ist.)<br /><br /> Die *FieldIdentifier* Argument wurde ein Datensatzfeld, der *RecNumber* Argument wurde 0 (null) und die *DescriptorHandle* Argument war ein IPD-Handle.<br /><br /> Die *RecNumber* Argument war kleiner als 0.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zum Belegen des Speichers zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY007|Zugeordnete Anweisung ist nicht vorbereitet.|*DescriptorHandle* zugeordnet wurde eine *StatementHandle* als ein IRD aus, und die zugeordnete Anweisung Handle hatte nicht vorbereitet oder ausgeführt.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) *DescriptorHandle* zugeordnet wurde eine *StatementHandle* für den eine asynchron ausgeführte Funktion (diese keiner) aufgerufen wurde, und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) *DescriptorHandle* zugeordnet wurde eine *StatementHandle* für die **SQLExecute**, **SQLExecDirect**,  **SQLBulkOperations**, oder **SQLSetPos** war aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *DescriptorHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLGetDescField** Funktion aufgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY021|Inkonsistente deskriptorinformation|Die Felder SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE bilden keine gültiger ODBC-SQL-Typ, eine gültige treiberspezifischen SQL-Typ (für Descriptor, IPD) oder einen gültigen Typ für den ODBC-C (für APDs oder ARDs).|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM)  *\*ValuePtr* wurde eine Zeichenfolge, und *Pufferlänge* ist kleiner als 0 (null).|  
|HY091|Ungültiger Deskriptorfeldbezeichner|*FieldIdentifier* kein ODBC-definierten-Feld und nicht wurde ein implementierungsdefinierte Wert.<br /><br /> *FieldIdentifier* wurde nicht definiert, für die *DescriptorHandle*.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum Zustand "angehalten" [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *DescriptorHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Kann eine Anwendung aufrufen **SQLGetDescField** um den Wert eines einzelnen Felds eines Datensatzes Deskriptor zurückzugeben. Ein Aufruf von **SQLGetDescField** die Einstellung eines Felds in einen Deskriptortyp, wie z.B. Headerfelder Datensatzfelder und Lesezeichen Felder zurückgeben kann. Eine Anwendung kann die Einstellungen aus mehreren Feldern in die gleichen oder ein anderen-Deskriptoren in willkürlicher Reihenfolge abrufen, indem Sie wiederholte Aufrufe an **SQLGetDescField**. **SQLGetDescField** kann auch zum Zurückgeben von deskriptorfelder treiberdefinierten aufgerufen werden.  
  
 Zur Verbesserung der Leistung, eine Anwendung nicht aufrufen sollten **SQLGetDescField** für eine IRD vor der Ausführung einer Anweisung.  
  
 Die Einstellungen aus mehreren Feldern, die den Namen, Datentyp und Speicherung von Daten für Spalte oder Parameter zu beschreiben, können auch in einem einzigen Aufruf abgerufen werden **SQLGetDescRec**. **SQLGetStmtAttr** aufgerufen werden, um die Einstellung von einem einzelnen Feld im Deskriptor-Header zurückgegeben, der auch ein Anweisungsattribut ist. **SQLColAttribute**, **SQLDescribeCol**, und **SQLDescribeParam** Datensatz oder ein Lesezeichen Felder zurück.  
  
 Wenn eine Anwendung ruft **SQLGetDescField** zum Abrufen des Werts eines Felds, das für einen bestimmten Deskriptortyp undefiniert ist die Funktion gibt SQL_SUCCESS zurück, aber der Wert zurückgegeben, für das Feld ist nicht definiert. Zum Beispiel der Aufruf **SQLGetDescField** für das Feld SQL_DESC_NAME oder SQL_DESC_NULLABLE eines APD oder ARD SQL_SUCCESS jedoch einen nicht definierten Wert für das Feld zurück.  
  
 Wenn eine Anwendung ruft **SQLGetDescField** zum Abrufen des Werts eines Felds aus, für einen bestimmten Deskriptortyp definiert ist, aber hat keinen Standardwert und wurde noch nicht festgelegt, die Funktion gibt SQL_SUCCESS zurück, aber der Wert zurückgegeben. für das Feld nicht definiert ist. Weitere Informationen für die Initialisierung der deskriptorfelder und Beschreibungen der Felder finden Sie unter "Initialisierung der Deskriptorfelder" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Weitere Informationen zu den sicherheitsbeschreibungen, finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen von deskriptorfelder für mehrere|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen einer einzelnen Deskriptorfeld|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen von mehreren deskriptorfeldern|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
