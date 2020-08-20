---
description: SQLGetDiagRec-Funktion
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7f141891292fb80d53ba06e03329b66cbc8b826e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461013"
---
# <a name="sqlgetdiagrec-function"></a>SQLGetDiagRec-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDiagRec** gibt die aktuellen Werte mehrerer Felder eines Diagnosedaten Satzes zurück, der Fehler-, Warnungs-und Statusinformationen enthält. Im Gegensatz zu **SQLGetDiagField**, das ein Diagnose Feld pro-Befehl zurückgibt, gibt **SQLGetDiagRec** einige häufig verwendete Felder eines Diagnosedaten Satzes zurück, einschließlich SQLSTATE, den systemeigenen Fehlercode und den Text der Diagnose Meldung.  
  
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
 Der Ein Handle-Typbezeichner, der den Typ des Handles beschreibt, für den eine Diagnose erforderlich ist. Dies muss eine der folgenden Ressourcen sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur vom Treiber-Manager und vom Treiber verwendet. Anwendungen sollten diesen Handlertyp nicht verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [entwickeln von Verbindungs Pool Informationen in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 Der Ein Handle für die Diagnosedaten Struktur des Typs, der durch den *Handlertyp*angegeben wird. Wenn " *Lenker Type* " SQL_HANDLE_ENV ist, kann *handle* entweder ein frei Gegebenes oder ein nicht gemeinsam genutztes Umgebungs Handle sein.  
  
 *RecNumber*  
 Der Gibt den Statusdaten Satz an, von dem die Anwendung Informationen sucht. Status Datensätze sind von 1 nummeriert.  
  
 *SQLSTATE*  
 Ausgeben Ein Zeiger auf einen Puffer, in den ein fünfstelliger SQLSTATE-Code (und das Beenden von null) für die *wiedergabenummer*des Diagnosedaten Satzes zurückgegeben werden soll. Die ersten beiden Zeichen geben die Klasse an. die nächsten drei weisen auf die Unterklasse hin. Diese Informationen sind im Feld SQL_DIAG_SQLSTATE Diagnose enthalten. Weitere Informationen finden Sie unter [Sqlstates](../../../odbc/reference/develop-app/sqlstates.md).  
  
 *Nativeerrorptr*  
 Ausgeben Zeiger auf einen Puffer, in den der systemeigene Fehlercode zurückgegeben werden soll, der spezifisch für die Datenquelle ist. Diese Informationen sind im Feld SQL_DIAG_NATIVE Diagnose enthalten.  
  
 *MessageText*  
 Ausgeben Zeiger auf einen Puffer, in den die Text Zeichenfolge der Diagnose Meldung zurückgegeben werden soll. Diese Informationen sind im Feld SQL_DIAG_MESSAGE_TEXT Diagnose enthalten. Das Format der Zeichenfolge finden Sie unter [Diagnosemeldungen](../../../odbc/reference/develop-app/diagnostic-messages.md).  
  
 Wenn *MessageText* NULL ist, gibt *Textlängen PTR* weiterhin die Gesamtzahl der Zeichen zurück (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den von *MessageText*verwiesen wird.  
  
 *BufferLength*  
 Der Länge des **MessageText* -Puffers in Zeichen. Es gibt keine maximale Länge für den Text der Diagnose Nachricht.  
  
 *Textverlänptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen zurückgegeben werden soll (ausgenommen der Anzahl der Zeichen, die für das NULL-Beendigungs Zeichen erforderlich sind), die in * \* MessageText*zurückgegeben werden können. Wenn die Anzahl der zurück zugebende Zeichen größer als *BufferLength*ist, wird der Text der Diagnose Nachricht in * \* MessageText* auf *BufferLength* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLGetDiagRec** sendet keine Diagnosedaten Sätze für sich selbst. Die folgenden Rückgabewerte werden verwendet, um das Ergebnis der eigenen Ausführung zu melden:  
  
-   SQL_SUCCESS: die Funktion hat erfolgreich Diagnoseinformationen zurückgegeben.  
  
-   SQL_SUCCESS_WITH_INFO: der \* *MessageText* -Puffer war zu klein, um die angeforderte Diagnose Meldung zu speichern. Es wurden keine Diagnosedaten Sätze generiert. Um zu ermitteln, ob ein Abschneiden aufgetreten ist, muss die Anwendung *BufferLength* mit der tatsächlichen Anzahl der verfügbaren Bytes vergleichen, die in **stringlengthptr*geschrieben wird.  
  
-   SQL_INVALID_HANDLE: das Handle, das von " *Lenker Type* " und " *handle* " angegeben wird, war kein gültiges Handle.  
  
-   SQL_ERROR: eine der folgenden Fehler ist aufgetreten:  
  
    -   Die *neuzahl* war negativ oder 0.  
  
    -   *BufferLength* war kleiner als 0 (null).  
  
    -   Bei Verwendung der asynchronen Benachrichtigung war der asynchrone Vorgang für das Handle nicht beendet.  
  
-   SQL_NO_DATA: *die Anzahl der* Diagnosedaten Sätze, die für das in handle angegebene Handle vorhanden waren, war größer als die Anzahl der Diagnosedaten Sätze *.* Die Funktion gibt auch SQL_NO_DATA für jede positive *remenge* zurück, wenn keine Diagnosedaten Sätze für das *handle*vorhanden sind.  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung ruft normalerweise **SQLGetDiagRec** auf, wenn ein vorheriger Aufruf einer ODBC-Funktion SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgegeben hat. Da jede ODBC-Funktion bei jedem Aufruf NULL oder mehr Diagnosedaten Sätze veröffentlichen kann, kann eine Anwendung nach jedem ODBC-Funktionsaufruf **SQLGetDiagRec** aufrufen. Eine Anwendung kann **SQLGetDiagRec** mehrmals aufrufen, um einige oder alle Datensätze in der Diagnosedaten Struktur zurückzugeben. ODBC schränkt die Anzahl der Diagnosedaten Sätze ein, die zu einem beliebigen Zeitpunkt gespeichert werden können.  
  
 **SQLGetDiagRec** kann nicht zum Zurückgeben von Feldern aus dem Header der Diagnosedaten Struktur verwendet werden. (Das *RecNumber* -Argument muss größer als 0 sein.) Die Anwendung sollte zu diesem Zweck **SQLGetDiagField** aufrufen.  
  
 **SQLGetDiagRec** ruft nur die Diagnoseinformationen ab, die zuletzt mit dem im *handle* -Argument angegebenen Handle verknüpft sind. Wenn die Anwendung eine andere ODBC-Funktion aufruft, mit Ausnahme von **SQLGetDiagRec**, **SQLGetDiagField**oder **SQLError**, gehen alle Diagnoseinformationen aus den vorherigen Aufrufen desselben Handles verloren.  
  
 Eine Anwendung kann alle Diagnosedaten Sätze durch Schleifen Scannen und die *RecNumber*erhöhen, sofern **SQLGetDiagRec** SQL_SUCCESS zurückgibt. Aufrufe von **SQLGetDiagRec** sind für die Header-und Daten Satz Felder nicht schädlich. Die Anwendung kann **SQLGetDiagRec** zu einem späteren Zeitpunkt erneut aufrufen, um ein Feld aus einem Datensatz abzurufen, solange keine andere Funktion mit Ausnahme von **SQLGetDiagRec**, **SQLGetDiagField**oder **SQLError**in der Zwischenzeit aufgerufen wurde. Die Anwendung kann auch die Anzahl der verfügbaren Diagnosedaten Sätze abrufen, indem **SQLGetDiagField** aufgerufen wird, um den Wert des SQL_DIAG_NUMBER Felds abzurufen und dann **SQLGetDiagRec** mehrmals aufzurufenden.  
  
 Eine Beschreibung der Felder der Diagnosedaten Struktur finden Sie unter [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md). Weitere Informationen finden Sie unter [Verwenden von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) und [Implementieren von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Wenn eine andere API aufgerufen wird, als die, die asynchron ausgeführt wird, wird HY010 "Function Sequence Error" generiert. Der Fehler Daten Satz kann jedoch erst abgerufen werden, wenn der asynchrone Vorgang abgeschlossen ist.  
  
## <a name="handletype-argument"></a>Lenker-Typargument  
 Jedem Handlertyp können Diagnoseinformationen zugeordnet werden. Das " *Lenker Type* "-Argument gibt den Handlertyp des *handle* -Arguments an.  
  
 Einige Header-und Daten Satz Felder können für die Umgebungs-, Verbindungs-, Anweisungs-und Deskriptorhandles nicht zurückgegeben werden. Die Handles, für die ein Feld nicht anwendbar ist, werden in den Abschnitten "Header Felder" und "Daten Satz Felder" in [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)angegeben.  
  
 Ein-Befehl von **SQLGetDiagRec** gibt SQL_INVALID_HANDLE zurück, wenn der *Handlertyp* SQL_HANDLE_SENV ist, der ein frei gegebenes Umgebungs Handle bezeichnet. Wenn allerdings der *Handlertyp* SQL_HANDLE_ENV ist, kann *handle* entweder ein frei Gegebenes oder ein nicht gemeinsam genutztes Umgebungs Handle sein.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen eines Felds eines Diagnosedaten Satzes oder eines Felds des Diagnose Headers|[SQLGetDiagField-Funktion](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Header Dateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md)
