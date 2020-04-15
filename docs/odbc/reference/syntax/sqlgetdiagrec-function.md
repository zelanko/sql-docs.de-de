---
title: SQLGetDiagRec-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39069526e254903509ddfef00b7bd4844f3d9e10
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285380"
---
# <a name="sqlgetdiagrec-function"></a>SQLGetDiagRec-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDiagRec** gibt die aktuellen Werte mehrerer Felder eines Diagnosedatensatzes zurück, der Fehler-, Warnungs- und Statusinformationen enthält. Im Gegensatz zu **SQLGetDiagField**, das ein Diagnosefeld pro Aufruf zurückgibt, gibt **SQLGetDiagRec** mehrere häufig verwendete Felder eines Diagnosedatensatzes zurück, einschließlich SQLSTATE, dem systemeigenen Fehlercode und dem Diagnosemeldungstext.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
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
 [Eingabe] Ein Handletypbezeichner, der den Typ des Handles beschreibt, für den eine Diagnose erforderlich ist. Dies muss eine der folgenden Ressourcen sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur vom Treiber-Manager und -Treiber verwendet. Anwendungen sollten diesen Handletyp nicht verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [Entwickeln von Verbindungspool-Awareness in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 [Eingabe] Ein Handle für die Diagnosedatenstruktur des von *HandleType*angegebenen Typs . Wenn *HandleType* SQL_HANDLE_ENV ist, kann *Handle* entweder ein freigegebenes oder ein nicht freigegebenes Umgebungshandle sein.  
  
 *RecNumber*  
 [Eingabe] Gibt den Statusdatensatz an, aus dem die Anwendung Informationen sucht. Statusdatensätze werden von 1 nummeriert.  
  
 *Sqlstate*  
 [Ausgabe] Zeiger auf einen Puffer, in dem ein fünfstelliger SQLSTATE-Code (und das Beenden von NULL) für den Diagnosedatensatz *RecNumber*zurückgegeben wird. Die ersten beiden Zeichen geben die Klasse an. die nächsten drei geben die Unterklasse an. Diese Informationen sind im Diagnosefeld SQL_DIAG_SQLSTATE enthalten. Weitere Informationen finden Sie unter [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md).  
  
 *NativeErrorPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem der systemeigene Fehlercode zurückgegeben werden soll, der für die Datenquelle spezifisch ist. Diese Informationen sind im SQL_DIAG_NATIVE Diagnosefeld enthalten.  
  
 *MessageText*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die Textzeichenfolge für Diagnosenachrichten zurückgegeben werden soll. Diese Informationen sind im SQL_DIAG_MESSAGE_TEXT Diagnosefeld enthalten. Das Format der Zeichenfolge finden Sie unter [Diagnosemeldungen](../../../odbc/reference/develop-app/diagnostic-messages.md).  
  
 Wenn *MessageText* NULL ist, gibt *TextLengthPtr* weiterhin die Gesamtzahl der Zeichen zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer von *MessageText*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Länge des **MessageText-Puffers* in Zeichen. Es ist keine maximale Länge des Diagnosenachrichtentextes vorhanden.  
  
 *TextLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (mit Ausnahme der Anzahl der Zeichen, die für das Null-Beendigungszeichen erforderlich sind) zurückgegeben werden soll, die in * \*MessageText*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer als *BufferLength*ist, wird der Diagnosenachrichtentext in * \*MessageText* auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLGetDiagRec** stellt keine Diagnosedatensätze für sich selbst bereit. Es verwendet die folgenden Rückgabewerte, um das Ergebnis seiner eigenen Ausführung zu melden:  
  
-   SQL_SUCCESS: Die Funktion hat erfolgreich Diagnoseinformationen zurückgegeben.  
  
-   SQL_SUCCESS_WITH_INFO: \*Der *MessageText-Puffer* war zu klein, um die angeforderte Diagnosenachricht zu enthalten. Es wurden keine Diagnosedatensätze generiert. Um zu ermitteln, dass eine Kürzung erfolgt ist, muss die Anwendung *BufferLength* mit der tatsächlichen Anzahl der verfügbaren Bytes vergleichen, die in **StringLengthPtr*geschrieben wird.  
  
-   SQL_INVALID_HANDLE: Das von *HandleType* und *Handle* angegebene Handle war kein gültiges Handle.  
  
-   SQL_ERROR: Einer der folgenden Fehler ist aufgetreten:  
  
    -   *RecNumber* war negativ oder 0.  
  
    -   *BufferLength* war kleiner als Null.  
  
    -   Bei Verwendung einer asynchronen Benachrichtigung war der asynchrone Vorgang für das Handle nicht abgeschlossen.  
  
-   SQL_NO_DATA: *RecNumber* war größer als die Anzahl der Diagnosedatensätze, die für das in Handle angegebene Handle vorhanden *waren.* Die Funktion gibt auch SQL_NO_DATA für eine positive *RecNumber* zurück, wenn keine Diagnosedatensätze für *Handle*vorhanden sind.  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung ruft **SQLGetDiagRec** in der Regel auf, wenn ein vorheriger Aufruf einer ODBC-Funktion SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde. Da jedoch jede ODBC-Funktion bei jedem Aufruf von Null oder mehr Diagnosedatensätzen buchen kann, kann eine Anwendung **SQLGetDiagRec** nach jedem ODBC-Funktionsaufruf aufrufen. Eine Anwendung kann **SQLGetDiagRec** mehrmals aufrufen, um einige oder alle Datensätze in der Diagnosedatenstruktur zurückzugeben. ODBC legt keine Begrenzung für die Anzahl der Diagnosedatensätze fest, die gleichzeitig gespeichert werden können.  
  
 **SQLGetDiagRec** kann nicht verwendet werden, um Felder aus dem Header der Diagnosedatenstruktur zurückzugeben. (Das *RecNumber-Argument* muss größer als 0 sein.) Die Anwendung sollte zu diesem Zweck **SQLGetDiagField** aufrufen.  
  
 **SQLGetDiagRec** ruft nur die Diagnoseinformationen ab, die zuletzt dem Handle zugeordnet sind, das im *Handle-Argument* angegeben ist. Wenn die Anwendung eine andere ODBC-Funktion mit Ausnahme von **SQLGetDiagRec**, **SQLGetDiagField**oder **SQLError**aufruft, gehen alle Diagnoseinformationen aus den vorherigen Aufrufen desselben Handles verloren.  
  
 Eine Anwendung kann alle Diagnosedatensätze scannen, indem sie *RecNumber*indieadien und inkrementiert, solange **SQLGetDiagRec** SQL_SUCCESS zurückgibt. Aufrufe von **SQLGetDiagRec** sind für die Header- und Datensatzfelder zerstörungsfrei. Die Anwendung kann **SQLGetDiagRec** zu einem späteren Zeitpunkt erneut aufrufen, um ein Feld aus einem Datensatz abzurufen, solange keine andere Funktion außer **SQLGetDiagRec**, **SQLGetDiagField**oder **SQLError**in der Zwischenzeit aufgerufen wurde. Die Anwendung kann auch eine Anzahl der Gesamtanzahl der verfügbaren Diagnosedatensätze abrufen, indem sie **SQLGetDiagField** aufruft, um den Wert des Feldes SQL_DIAG_NUMBER abzurufen, und dann **SQLGetDiagRec** mehrmals aufruft.  
  
 Eine Beschreibung der Felder der Diagnosedatenstruktur finden Sie unter [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md). Weitere Informationen finden Sie unter [Verwenden von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) und [Implementieren von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Wenn Sie eine andere API als die, die asynchron ausgeführt wird, aufrufen, wird HY010 "Funktionssequenzfehler" generiert. Der Fehlerdatensatz kann jedoch nicht abgerufen werden, bevor der asynchrone Vorgang abgeschlossen ist.  
  
## <a name="handletype-argument"></a>HandleType-Argument  
 Jedem Handlestyp können Diagnoseinformationen zugeordnet sein. Das *HandleType-Argument* gibt den Handle-Typ des *Handle-Arguments* an.  
  
 Einige Header- und Datensatzfelder können nicht für Umgebungs-, Verbindungs-, Anweisungs- und Deskriptorhandles zurückgegeben werden. Die Handles, für die kein Feld gilt, sind in den Abschnitten "Headerfelder" und "Felder aufzeichnen" in [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)angegeben.  
  
 Ein Aufruf von **SQLGetDiagRec** gibt SQL_INVALID_HANDLE zurück, wenn *HandleType* SQL_HANDLE_SENV ist, was ein freigegebenes Umgebungshandle bezeichnet. Wenn *HandleType* jedoch SQL_HANDLE_ENV ist, kann *Handle* entweder ein freigegebenes oder ein nicht freigegebenes Umgebungshandle sein.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen eines Felds eines Diagnosedatensatzes oder eines Felds des Diagnoseheaders|[SQLGetDiagField-Funktion](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md)
