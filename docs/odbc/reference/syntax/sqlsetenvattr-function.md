---
title: SQLSetEnvAttr-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetEnvAttr
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetEnvAttr
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC]
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 640b1e6947d67b92e2b7f8e623597e1d99d4a877
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299540"
---
# <a name="sqlsetenvattr-function"></a>SQLSetEnvAttr-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetEnvAttr** legt Attribute fest, die Aspekte von Umgebungen steuern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *EnvironmentHandle*  
 [Eingabe] Umgebungshandle.  
  
 *Attribut*  
 [Eingabe] Zu setzendes Attribut, aufgeführt in "Kommentare".  
  
 *ValuePtr*  
 [Eingabe] Zeiger auf den Wert, der *Attribute*zugeordnet werden soll. Abhängig vom Wert von *Attribut*ist *ValuePtr* ein 32-Bit-Ganzzahlwert oder ein Punkt auf eine null-terminierte Zeichenfolge.  
  
 *StringLength*  
 [Eingabe] Wenn *ValuePtr* auf eine Zeichenfolge oder einen Binärpuffer verweist, sollte dieses Argument die Länge von **ValuePtr*haben. Bei Zeichenfolgendaten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *ValuePtr* eine ganze Zahl ist, wird *StringLength* ignoriert.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetEnvAttr** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_ENV und einem *Handle* von *EnvironmentHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLSetEnvAttr** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben. Wenn ein Treiber kein Umgebungsattribut unterstützt, kann der Fehler nur während der Verbindungszeit zurückgegeben werden.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber unterstützte den in *ValuePtr* angegebenen Wert nicht und ersetzte einen ähnlichen Wert. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das Attributargument identifizierte ein Umgebungsattribut, das einen Zeichenfolgenwert erforderte, und das *ValuePtr-Argument* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) *EnvironmentHandle*wurde ein Verbindungshandle zugewiesen.<br /><br /> (DM) **SQL_ATTR_ODBC_VERSION** wurde nicht mit **SQLSetEnvAttr** festgelegt, und *Attribut* ist nicht gleich **SQL_ATTR_ODBC_VERSION**. Sie müssen **SQL_ATTR_ODBC_VERSION** nicht explizit festlegen, wenn Sie **SQLAllocHandleStd**verwenden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY024|Ungültiger Attributwert|Angesichts des angegebenen *Attributwerts* wurde in *ValuePtr*ein ungültiger Wert angegeben.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|Das *StringLength-Argument* war kleiner als 0, wurde jedoch nicht SQL_NTS.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) Der für das Argument *Attribut* angegebene Wert war für die vom Treiber unterstützte ODBC-Version ungültig.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der für das Argument *Attribut* angegebene Wert war ein gültiges ODBC-Umgebungsattribut für die vom Treiber unterstützte ODBC-Version, wurde jedoch vom Treiber nicht unterstützt.<br /><br /> (DM) Das *Attributargument* wurde SQL_ATTR_OUTPUT_NTS, und *ValuePtr* wurde SQL_FALSE.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **SQLSetEnvAttr** nur aufrufen, wenn der Umgebung kein Verbindungshandle zugewiesen ist. Alle Umgebungsattribute, die von der Anwendung für die Umgebung erfolgreich festgelegt wurden, bleiben bestehen, bis **SQLFreeHandle** in der Umgebung aufgerufen wird. In ODBC *3.x*können mehrere Umgebungshandles gleichzeitig zugewiesen werden.  
  
 Das Format der über *ValuePtr* festgelegten Informationen hängt vom angegebenen *Attribut*ab. **SQLSetEnvAttr** akzeptiert Attributinformationen in einem von zwei verschiedenen Formaten: einer null-terminierten Zeichenfolge oder einem 32-Bit-Ganzzahlwert. Das Format der einzelnen Attribute wird in der Beschreibung des Attributs angegeben.  
  
 Es sind keine treiberspezifischen Umgebungsattribute vorhanden.  
  
 Verbindungsattribute können nicht durch einen Aufruf von **SQLSetEnvAttr**festgelegt werden. Wenn Sie dies versuchen, wird SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurückgegeben.  
  
|*Attribut*|*ValuePtr-Inhalt*|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)|Ein 32-Bit-SQLUINTEGER-Wert, der das Verbindungspooling auf Umgebungsebene aktiviert oder deaktiviert. Folgende Werte werden verwendet:<br /><br /> SQL_CP_OFF = Verbindungspooling ist deaktiviert. Dies ist die Standardoption.<br /><br /> SQL_CP_ONE_PER_DRIVER = Für jeden Treiber wird ein einzelner Verbindungspool unterstützt. Jede Verbindung in einem Pool ist einem Treiber zugeordnet.<br /><br /> SQL_CP_ONE_PER_HENV = Für jede Umgebung wird ein einzelner Verbindungspool unterstützt. Jede Verbindung in einem Pool ist einer Umgebung zugeordnet.<br /><br /> SQL_CP_DRIVER_AWARE = Verwenden Sie die Verbindungspool-Awareness-Funktion des Treibers, sofern diese verfügbar ist. Wenn der Treiber die Verbindungspoolkenntnis nicht unterstützt, wird SQL_CP_DRIVER_AWARE ignoriert und SQL_CP_ONE_PER_HENV verwendet. Weitere Informationen finden Sie unter [Treiber-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md). In einer Umgebung, in der einige Treiber unterstützen und einige Treiber die Bekanntheit des Verbindungspools nicht unterstützen, können SQL_CP_DRIVER_AWARE die Anzeigefunktion für verbindungspool für die unterstützenden Treiber aktivieren, aber es entspricht der Einstellung, SQL_CP_ONE_PER_HENV auf treibern festzulegen, die die Funktion zur Sensibilisierung des Verbindungspools nicht unterstützen.<br /><br /> Das Verbindungspooling wird durch Aufrufen von **SQLSetEnvAttr** aktiviert, um das SQL_ATTR_CONNECTION_POOLING-Attribut auf SQL_CP_ONE_PER_DRIVER oder SQL_CP_ONE_PER_HENV festzulegen. Dieser Aufruf muss erfolgen, bevor die Anwendung die freigegebene Umgebung zuweist, für die das Verbindungspooling aktiviert werden soll. Das Umgebungshandle im Aufruf von **SQLSetEnvAttr** ist auf null festgelegt, was SQL_ATTR_CONNECTION_POOLING ein Attribut auf Prozessebene macht. Nachdem die Verbindungspooling aktiviert ist, weist die Anwendung eine implizite gemeinsame Umgebung zu, indem **SIE SQLAllocHandle** mit dem *InputHandle-Argument* auf SQL_HANDLE_ENV.<br /><br /> Nachdem das Verbindungspooling aktiviert wurde und eine freigegebene Umgebung für eine Anwendung ausgewählt wurde, können SQL_ATTR_CONNECTION_POOLING für diese Umgebung nicht zurückgesetzt werden, da **SQLSetEnvAttr** beim Festlegen dieses Attributs mit einem NULL-Umgebungshandle aufgerufen wird. Wenn dieses Attribut festgelegt ist, während das Verbindungspooling in einer freigegebenen Umgebung bereits aktiviert ist, wirkt sich das Attribut nur auf freigegebene Umgebungen aus, die anschließend zugewiesen werden.<br /><br /> Es ist auch möglich, das Verbindungspooling in einer Umgebung zu aktivieren. Beachten Sie Folgendes zum Pooling von Umgebungsverbindungen:<br /><br /> - Das Aktivieren des Verbindungspoolings für ein NULL-Handle ist ein Attribut auf Prozessebene. Anschließend werden zugewiesene Umgebungen eine freigegebene Umgebung sein und die Verbindungspooleinstellung auf Prozessebene erben.<br />- Nachdem eine Umgebung zugewiesen wurde, kann eine Anwendung ihre Verbindungspooleinstellung weiterhin ändern.<br />- Wenn das Pooling der Umgebungsverbindung aktiviert ist und der Treiber der Verbindung Treiberpooling verwendet, wird das Umgebungspooling bevorzugt.<br /><br /> SQL_ATTR_CONNECTION_POOLING wird im Treiber-Manager implementiert. Ein Treiber muss SQL_ATTR_CONNECTION_POOLING nicht implementieren. ODBC 2.0- und 3.0-Anwendungen können dieses Umgebungsattribut festlegen.<br /><br /> Weitere Informationen finden Sie unter [ODBC-Verbindungspooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_CP_MATCH (ODBC 3.0)|Ein 32-Bit-SQLUINTEGER-Wert, der bestimmt, wie eine Verbindung aus einem Verbindungspool ausgewählt wird. Wenn **SQLConnect** oder **SQLDriverConnect** aufgerufen wird, bestimmt der Treiber-Manager, welche Verbindung aus dem Pool wiederverwendet wird. Der Treiber-Manager versucht, die Verbindungsoptionen im Aufruf und die von der Anwendung festgelegten Verbindungsattribute mit den Schlüsselwörtern und Verbindungsattributen der Verbindungen im Pool abzugleichen. Der Wert dieses Attributs bestimmt die Genauigkeit der übereinstimmenden Kriterien.<br /><br /> Die folgenden Werte werden verwendet, um den Wert dieses Attributs festzulegen:<br /><br /> SQL_CP_STRICT_MATCH = Nur Verbindungen, die genau mit den Verbindungsoptionen im Aufruf übereinstimmen, und die von der Anwendung festgelegten Verbindungsattribute werden wiederverwendet. Dies ist die Standardoption.<br /><br /> SQL_CP_RELAXED_MATCH = Verbindungen mit übereinstimmenden Verbindungszeichenfolgenschlüsselwörtern können verwendet werden. Schlüsselwörter müssen übereinstimmen, aber nicht alle Verbindungsattribute müssen übereinstimmen.<br /><br /> Weitere Informationen dazu, wie der Treiber-Manager die Übereinstimmung beim Herstellen einer Verbindung mit einer gepoolten Verbindung ausführt, finden Sie unter [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md). Weitere Informationen zum Verbindungspooling finden Sie unter [ODBC Connection Pooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_ODBC_VERSION (ODBC 3.0)|Eine 32-Bit-Ganzzahl, die bestimmt, ob bestimmte Funktionen ODBC *2.x-Verhalten* oder ODBC *3.x-Verhalten* aufweisen. Die folgenden Werte werden verwendet, um den Wert dieses Attributs festzulegen:<br /><br /> SQL_OV_ODBC3_80 = Der Treiber-Manager und der Treiber weisen das folgende ODBC 3.8-Verhalten auf:<br /><br /> - Der Treiber gibt odBC *3.x-Codes* für Datum, Uhrzeit und Zeitstempel zurück und erwartet.<br />- Der Treiber gibt ODBC *3.x* SQLSTATE-Codes zurück, wenn **SQLError**, **SQLGetDiagField**oder **SQLGetDiagRec** aufgerufen wird.<br />- Das *Argument CatalogName* in einem Aufruf von **SQLTables** akzeptiert ein Suchmuster.<br />- Der Treiber-Manager unterstützt die Erweiterbarkeit des C-Datentyps. Weitere Informationen zur Erweiterbarkeit des C-Datentyps finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).<br /><br /> Weitere Informationen finden Sie [unter Neuerungen in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).<br /><br /> SQL_OV_ODBC3 = Der Treiber-Manager und der Treiber weisen das folgende ODBC *3.x-Verhalten* auf:<br /><br /> - Der Treiber gibt odBC *3.x-Codes* für Datum, Uhrzeit und Zeitstempel zurück und erwartet.<br />- Der Treiber gibt ODBC *3.x* SQLSTATE-Codes zurück, wenn **SQLError**, **SQLGetDiagField**oder **SQLGetDiagRec** aufgerufen wird.<br />- Das *Argument CatalogName* in einem Aufruf von **SQLTables** akzeptiert ein Suchmuster.<br />- Der Treiber-Manager unterstützt keine Erweiterbarkeit des C-Datentyps.<br /><br /> SQL_OV_ODBC2 = Der Treiber-Manager und der Treiber weisen das folgende ODBC *2.x-Verhalten* auf. Dies ist besonders nützlich für eine ODBC *2.x-Anwendung,* die mit einem ODBC *3.x-Treiber* arbeitet.<br /><br /> - Der Treiber gibt zurück und erwartet ODBC *2.x-Codes* für Datum, Uhrzeit und Zeitstempel.<br />- Der Treiber gibt ODBC *2.x* SQLSTATE-Codes zurück, wenn **SQLError**, **SQLGetDiagField**oder **SQLGetDiagRec** aufgerufen wird.<br />- Das *Argument CatalogName* in einem Aufruf von **SQLTables** akzeptiert kein Suchmuster.<br />- Der Treiber-Manager unterstützt keine Erweiterbarkeit des C-Datentyps.<br /><br /> Eine Anwendung muss dieses Umgebungsattribut festlegen, bevor sie eine Funktion aufruft, die über ein SQLHENV-Argument verfügt, oder der Aufruf gibt SQLSTATE HY010 (Funktionssequenzfehler) zurück. Es ist treiberspezifisch, ob zusätzliches Verhalten für diese Umgebungsflags vorhanden ist.<br /><br /> - Weitere Informationen finden Sie unter [Deklarieren der ODBC-Version](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) und [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md)der Anwendung .|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3.0)|Eine 32-Bit-Ganzzahl, die bestimmt, wie der Treiber Zeichenfolgendaten zurückgibt. Wenn SQL_TRUE, gibt der Treiber Zeichenfolgendaten null-terminated zurück. Wenn SQL_FALSE, gibt der Treiber keine Zeichenfolgendaten null-beendet zurück.<br /><br /> Dieses Attribut ist standardmäßig SQL_TRUE. Ein Aufruf von **SQLSetEnvAttr,** um es auf SQL_TRUE gibt SQL_SUCCESS zurück. Ein Aufruf von **SQLSetEnvAttr** zum Festlegen auf SQL_FALSE gibt SQL_ERROR und SQLSTATE HYC00 zurück (Optionale Funktion nicht implementiert).|  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuweisen eines Griffs|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Zurückgeben der Einstellung eines Umgebungsattributs|[SQLGetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Neuerungen in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
