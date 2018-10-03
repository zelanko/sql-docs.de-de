---
title: SQLGetDiagRec-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDiagRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagRec
helpviewer_keywords:
- SQLGetDiagRec function [ODBC]
ms.assetid: ebdbac93-3d68-438f-8416-ef1f08e04269
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c4606c9f525517d51312fc9a105076691dcda682
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683025"
---
# <a name="sqlgetdiagrec-function"></a>SQLGetDiagRec-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC 3.0 Standardkompatibilität: ISO-92  
  
 **Zusammenfassung**  
 **SQLGetDiagRec** gibt die aktuellen Werte aus mehreren Feldern, der ein Diagnosedatensatz, die Fehler, Warnung und Statusinformationen enthält. Im Gegensatz zu **SQLGetDiagField**, womit eine diagnosefeld pro Aufruf **SQLGetDiagRec** gibt verschiedene, häufig verwendete Felder des ein Diagnosedatensatz, einschließlich SQLSTATE, der systemeigene Fehlercode, und der diagnosemeldung Text.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLGetDiagRec(  
     SQLSMALLINT     HandleType,  
     SQLHANDLE       Handle,  
     SQLSMALLINT     RecNumber,  
     SQLCHAR *       SQLState,  
     SQLINTEGER *    NativeErrorPtr,  
     SQLCHAR *       MessageText,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   TextLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Ein Handle-Typbezeichner, der den Typ des Handles wird beschrieben, für die Diagnose erforderlich sind. Dies muss eine der folgenden Ressourcen sein:  
  
-   SQL_HANDLE_DBC AUF  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV AUF  
  
-   SQL_HANDLE_STMT AUF  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur von der Treiber-Manager und Treiber verwendet. Anwendungen sollten nicht mit dieser Handletyp verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN, finden Sie unter [Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 [Eingabe] Ein Handle für die Diagnose Datenstruktur, die vom angegebenen Typ *HandleType*. Wenn *HandleType* SQL_HANDLE_ENV auf, wird *behandeln* kann entweder eine freigegebene oder ein nicht freigegebenes Umgebungshandle sein.  
  
 *RecNumber*  
 [Eingabe] Gibt an, den Status-Datensatz, der von dem die Anwendung Informationen sucht. Statusdatensätze werden von 1 nummeriert.  
  
 *SQLState*  
 [Ausgabe] Zeiger auf einen Puffer, in dem eine fünfstelligen SQLSTATE-Code (und das abschließende NULL-Zeichen) für die Diagnosedatensatz zurückgegeben *RecNumber*. Die ersten beiden Zeichen anzugeben, die Klasse; die folgenden drei Geben Sie an die-Unterklasse. Diese Informationen sind im Feld SQL_DIAG_SQLSTATE Diagnose enthalten. Weitere Informationen finden Sie unter [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md).  
  
 *NativeErrorPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in die den systemeigene Fehlercode für die Datenquelle zurückgegeben werden sollen. Diese Informationen sind im Feld SQL_DIAG_NATIVE Diagnose enthalten.  
  
 *MessageText*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die diagnosemeldung Zeichenfolge zurückgegeben. Diese Informationen sind im Feld SQL_DIAG_MESSAGE_TEXT Diagnose enthalten. Das Format der Zeichenfolge ist, finden Sie unter [Diagnosemeldungen](../../../odbc/reference/develop-app/diagnostic-messages.md).  
  
 Wenn *MessageText* NULL ist, *TextLengthPtr* gibt die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *MessageText*.  
  
 *BufferLength*  
 [Eingabe] Länge der **MessageText* -Puffers in Zeichen. Es gibt keine maximale Länge des Texts der Diagnose.  
  
 *TextLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe der Gesamtzahl der Zeichen, die (mit Ausnahme von der Anzahl von Zeichen, die für die Null-Terminierungszeichen erforderlich) zur Verfügung, die in zurückgegeben  *\*MessageText*. Ist die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als *Pufferlänge*, den Text der diagnosemeldung in  *\*MessageText* auf abgeschnitten *Pufferlänge* abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLGetDiagRec** veröffentlichen DiagnoseDatensätze nicht für sich selbst. Sie können die folgenden Rückgabewerte verwendet, um das Ergebnis seiner eigenen Ausführung zu melden:  
  
-   SQL_SUCCESS: Die Funktion wurde erfolgreich zurückgegeben Diagnoseinformationen zu erhalten.  
  
-   SQL_SUCCESS_WITH_INFO: Die \* *MessageText* Puffer war zu klein für die angeforderte diagnosemeldung. Es wurden keine DiagnoseDatensätze generiert. Um zu bestimmen, dass durch das Abschneiden aufgetreten ist, vergleichen Sie die Anwendung muss *Pufferlänge* auf die tatsächliche Anzahl von Bytes verfügbar ist, das wird **StringLengthPtr*.  
  
-   SQL_INVALID_HANDLE: Durch das Handle angegeben *HandleType* und *behandeln* war es sich nicht um ein gültiges Handle.  
  
-   SQL_ERROR: Eine der folgenden aufgetreten ist:  
  
    -   *RecNumber* war negativ oder 0.  
  
    -   *BufferLength* ist kleiner als 0 (null).  
  
    -   Wenn Sie asynchrone Benachrichtigung verwenden zu können, war der asynchrone Vorgang auf den Ziehpunkt nicht abgeschlossen werden.  
  
-   SQL_NO_DATA: *RecNumber* war größer als die Zahl der DiagnoseDatensätze, die für das Handle, das im angegebenen vorhanden waren *behandeln.* Die Funktion gibt SQL_NO_DATA auch für eine beliebige Positive *RecNumber* treten keine DiagnoseDatensätze für *behandeln*.  
  
## <a name="comments"></a>Kommentare  
 Ruft eine Anwendung in der Regel **SQLGetDiagRec** Wenn ein vorherigen Aufruf von einer ODBC-Funktion SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgegeben hat. Aber da eine ODBC-Funktion keine oder mehrere DiagnoseDatensätze jedes Mal buchen können sie aufgerufen wird, kann eine Anwendung aufrufen **SQLGetDiagRec** nach jedem Aufruf der ODBC-Funktion. Kann eine Anwendung aufrufen **SQLGetDiagRec** mehrere Male auf, um einige oder alle Datensätze in der Struktur diagnostische Daten zurückzugeben. ODBC erzwingt keine Begrenzung der Anzahl der DiagnoseDatensätze, die zu jedem Zeitpunkt gespeichert werden können.  
  
 **SQLGetDiagRec** kann nicht verwendet werden, um Felder aus dem Header der Struktur diagnostische Daten zurückzugeben. (Die *RecNumber* Argument muss größer als 0 sein.) Die Anwendung sollte Aufrufen **SQLGetDiagField** für diesen Zweck.  
  
 **SQLGetDiagRec** ruft nur die zuletzt angegebene Handle zugeordnete Diagnoseinformationen der *behandeln* Argument. Wenn die Anwendung eine andere ODBC-Funktion aufruft, mit Ausnahme der **SQLGetDiagRec**, **SQLGetDiagField**, oder **SQLError**, diagnostische Informationen aus den vorherigen Aufrufen auf der dasselbe Handle geht verloren.  
  
 Eine Anwendung kann gescannt werden. alle DiagnoseDatensätze von Schleifen, besitzt eine Schrittweite *RecNumber*, solange **SQLGetDiagRec** gibt SQL_SUCCESS zurück. Aufrufe von **SQLGetDiagRec** an den Header und der Datensatz nicht destruktiv sind. Die Anwendung kann Aufrufen **SQLGetDiagRec** erneut zu einem späteren Zeitpunkt zum Abrufen eines Felds aus einem Datensatz, wie lange wie keine andere Funktion, mit Ausnahme von **SQLGetDiagRec**, **SQLGetDiagField**, oder **SQLError**, in der Zwischenzeit aufgerufen wurde. Außerdem kann die Anwendung die gesamte Anzahl von Diagnosedatensätzen verfügbar abrufen, durch den Aufruf **SQLGetDiagField** zum Abrufen des Werts der SQL_DIAG_NUMBER-Feld, und klicken Sie dann aufrufen **SQLGetDiagRec**mit dieser Häufigkeit.  
  
 Eine Beschreibung der Felder der Struktur diagnostische Daten finden Sie unter [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md). Weitere Informationen finden Sie unter [mithilfe von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) und [Implementieren von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Aufrufen einer API als dem, der asynchron ausgeführt wird, wird HY010 generiert "Sequenzfehler Function". Allerdings kann nicht Error-Datensatzes nicht abgerufen werden, bevor der asynchrone Vorgang abgeschlossen ist.  
  
## <a name="handletype-argument"></a>HandleType-Argument  
 Jede Handletyp kann Diagnoseinformationen zugeordnet haben. Die *HandleType* Argument gibt den Handle der *behandeln* Argument.  
  
 Einige Felder Header und eines Eintrags können nicht für die Umgebung, Verbindung, anweisungs- und Deskriptorstatuswerte Handles zurückgegeben werden. Diese Handles, die für die ein Feld nicht anwendbar ist sind angegeben, in den Abschnitten "Headerfelder" und "Felder" Datensatz " [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
 Ein Aufruf von **SQLGetDiagRec** gibt SQL_INVALID_HANDLE zurück, wenn *HandleType* SQL_HANDLE_SENV, die einer freigegebenen Umgebungshandle bezeichnet wird. Aber wenn *HandleType* SQL_HANDLE_ENV auf, wird *behandeln* kann entweder eine freigegebene oder ein nicht freigegebenes Umgebungshandle sein.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Erhalten ein Feld ein Diagnosedatensatz oder ein Feld des Diagnose-Headers|[SQLGetDiagField-Funktion](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md)
