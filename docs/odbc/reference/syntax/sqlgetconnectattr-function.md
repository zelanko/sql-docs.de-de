---
title: SQLGetConnectAttr-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectAttr
helpviewer_keywords:
- SQLGetConnectAttr function [ODBC]
ms.assetid: 2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a24ccf58a1cd0f6d0f4fb2fd32dbee79feb896b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204439"
---
# <a name="sqlgetconnectattr-function"></a>SQLGetConnectAttr-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standardkompatibilität: ISO-92  
  
 **Zusammenfassung**  
 **SQLGetConnectAttr** gibt die aktuelle Einstellung der ein Verbindungsattribut.  
  
> [!NOTE]
>  Weitere Informationen dazu, was der Treiber-Manager diese Funktion auf, wenn eine ODBC 3. zuordnet *.x* Anwendung arbeitet mit einer ODBC 2.*.x* -Treiber verwenden, finden Sie unter [Zuordnen von Ersatzfunktionen für rückwärts Kompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLGetConnectAttr(  
     SQLHDBC        ConnectionHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *Attribut*  
 [Eingabe] Attribut, das abgerufen werden.  
  
 *ValuePtr*  
 [Ausgabe] Ein Zeiger auf Speicher, in dem den aktuellen Wert des Attributs gemäß zurückgegeben *Attribut*. Integer-Typ einige Treiber können nur die untere 32-Bit-schreiben oder 16-Bit, der einen Puffer und eine verlassen Bits höherer Ordnung unverändert. Anwendungen sollten daher verwendet einen Puffer mit SQLULEN erstellt wurde, und initialisieren den Wert auf 0 vor dem Aufrufen dieser Funktion.  
  
 Wenn *ValuePtr* NULL ist, *StringLengthPtr* gibt die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *ValuePtr*.  
  
 *BufferLength*  
 [Eingabe] Wenn *Attribut* ist ein ODBC-definierten Attribut und *ValuePtr* zeigt auf eine Zeichenfolge oder ein binärer Puffer, in dieses Argument muss die Länge des \* *ValuePtr*. Wenn *Attribut* ist ein ODBC-definierten Attribut und \* *ValuePtr* ist eine ganze Zahl, *Pufferlänge* wird ignoriert. Wenn der Wert in  *\*ValuePtr* ist eine Unicodezeichenfolge (beim Aufrufen von **SQLGetConnectAttrW**), wird die *Pufferlänge* Argument muss eine gerade Zahl sein.  
  
 Wenn *Attribut* ein treiberdefinierten-Attribut, wird die Anwendung zeigt die Art des Attributs auf den Treiber-Manager an, indem die *Pufferlänge* Argument. *BufferLength* können die folgenden Werte aufweisen:  
  
-   Wenn  *\*ValuePtr* ist ein Zeiger auf eine Zeichenfolge, *Pufferlänge* ist die Länge der Zeichenfolge.  
  
-   Wenn  *\*ValuePtr* ist ein Zeiger auf ein binärer Puffer, der Anwendung stellen das Ergebnis der SQL_LEN_BINARY_ATTR (*Länge*)-Makro in *Pufferlänge*. Dadurch wird einen negativen Wert im platziert *Pufferlänge*.  
  
-   Wenn  *\*ValuePtr* ist ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder Binärzeichenfolge, *Pufferlänge* Wert SQL_IS_POINTER haben sollte.  
  
-   Wenn  *\*ValuePtr* enthält einen Datentyp mit fester Länge *Pufferlänge* ist SQL_IS_INTEGER oder SQL_IS_UINTEGER, nach Bedarf.  
  
 *StringLengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen) zurückgegeben. verfügbar für die zurückzugebenden in \* *ValuePtr*. Wenn \* *ValuePtr* ist ein null-Zeiger wird keine Länge zurückgegeben. Wenn Sie den Wert des Attributs ist eine Zeichenfolge und die Anzahl der Bytes, die für die Rückgabe verfügbar ist größer als *Pufferlänge* abzüglich der Länge des Zeichens Null-Terminierung vorliegt, die Daten in  *\*ValuePtr*auf abgeschnitten *Pufferlänge* abzüglich der Länge des Zeichens Null-Terminierung vorliegt und Null-terminiert ist vom Treiber.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA zurückgibt, wird SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetConnectAttr** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert aus der Struktur diagnostische Daten abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* SQL_HANDLE_DBC auf, und ein *behandeln* von *ConnectionHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLGetConnectAttr** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben . Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Die Daten im zurückgegebenen \* *ValuePtr* wurde abgeschnitten, um werden *Pufferlänge* abzüglich der Länge des ein Null-Terminierungszeichen. Die Länge des Werts den ungekürzten Zeichenfolge wird zurückgegeben, **StringLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) eine *Attribut* -Wert, der eine geöffnete Verbindung erforderlich sind, wurde angegeben.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die Fehlermeldung, die aus der Struktur von Diagnosedaten durch das Argument zurückgegeben *MessageText* in **SQLGetDiagField** beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) **SQLBrowseConnect** wurde aufgerufen, die *ConnectionHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion aufgerufen wurde, bevor **SQLBrowseConnect** SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgegeben.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *ConnectionHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM)  *\*ValuePtr* ist eine Zeichenfolge, und die Pufferlänge ist kleiner als 0 (null), aber nicht gleich SQL_NTS.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der angegebene Wert für das Argument *Attribut* war nicht gültig für die Version von ODBC, die vom Treiber unterstützt werden.|  
|HY114|Auf Serverebene asynchrone Ausführung der unterstützt Treiber nicht.|(DM) versucht eine Anwendung, die asynchrone Ausführung mit SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE für einen Treiber zu aktivieren, die asynchrone Verbindungsvorgänge nicht unterstützt.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Der angegebene Wert für das Argument *Attribut* wurde ein gültiger ODBC-Verbindungsattribut, für die ODBC-Version vom Treiber unterstützt werden, jedoch wurde vom Treiber nicht unterstützt.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber, der die entspricht der *ConnectionHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Allgemeine Informationen zu Verbindungsattributen finden Sie unter [Verbindungsattribute](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Eine Liste der Attribute, die festgelegt werden können, finden Sie unter [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md). Beachten Sie, dass bei *Attribut* gibt an, ein Attribut, das eine Zeichenfolge zurückgibt, *ValuePtr* muss ein Zeiger auf einen Puffer für die Zeichenfolge sein. Die maximale Länge der zurückgegebenen Zeichenfolge, einschließlich des Zeichens Null-Terminierung vorliegt, werden *Pufferlänge* Bytes.  
  
 Abhängig von das Attribut, eine Anwendung keinen zum Herstellen einer Verbindung vor dem Aufruf **SQLGetConnectAttr**. Aber wenn **SQLGetConnectAttr** wird aufgerufen, und das angegebene Attribut über keinen Standardwert und wurde nicht festgelegt wurde, durch einen vorherigen Aufruf von **SQLSetConnectAttr**, **SQLGetConnectAttr**gibt SQL_NO_DATA zurück.  
  
 Wenn *Attribut* ist SQL_ATTR_ ABLAUFVERFOLGUNG oder SQL_ATTR_ ABLAUFVERFOLGUNGSDATEI *ConnectionHandle* muss nicht gültig ist, und **SQLGetConnectAttr** nicht gibt SQL_ERROR oder SQL_ Zurück Wenn *ConnectionHandle* ist ungültig. Diese Attribute gelten für alle Verbindungen. **SQLGetConnectAttr** gibt SQL_ERROR oder SQL_INVALID_HANDLE zurück werden, wenn ein anderes Argument ungültig ist.  
  
 Obwohl eine Anwendung Anweisungsattribute festlegen kann, die sich mit **SQLSetConnectAttr**, eine Anwendung können keine **SQLGetConnectAttr** Anweisungsattribut Abrufen von Werten, die aufgerufen werden muss  **SQLGetStmtAttr** um die Einstellung der Anweisungsattribute abzurufen.  
  
 Sowohl für SQL_ATTR_AUTO_IPD SQL_ATTR_CONNECTION_DEAD Verbindungsattribute zurückgegeben werden können, durch einen Aufruf von **SQLGetConnectAttr** aber nicht festgelegt werden, durch einen Aufruf von **SQLSetConnectAttr**.  
  
> [!NOTE]  
>  Es gibt keine asynchrone Unterstützung für **SQLGetConnectAttr**. Bei der Implementierung **SQLGetConnectAttr**, ein Treiber kann die Leistung verbessern, indem minimiert die Anzahl der Fälle, in denen Informationen gesendet oder vom Server angefordert wird.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Die Einstellung für ein Anweisungsattribut zurückgeben|[SQLGetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Ein Verbindungsattribut festlegen|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Ein Umgebungsattribut festlegen|[SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Wenn eine Anweisungsattribut|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
