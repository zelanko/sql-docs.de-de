---
title: Sqlbrowseconnetct-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBrowseConnect
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBrowseConnect
helpviewer_keywords:
- SQLBrowseConnect function [ODBC]
ms.assetid: b7f1be66-e6c7-4790-88ec-62b7662103c0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607b0d764a694098a23111e9d7f4ce9755ea982d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301340"
---
# <a name="sqlbrowseconnect-function"></a>SQLBrowseConnect-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **Sqlbrowseconnetct** unterstützt eine iterative Methode zum Ermitteln und Auflisten der Attribute und Attributwerte, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind. Jeder-Befehl von **sqlbrowseconnetct** gibt aufeinanderfolgende Ebenen von Attributen und Attributwerten zurück. Wenn alle Ebenen aufgezählt wurden, wird eine Verbindung mit der Datenquelle hergestellt, und eine vollständige Verbindungs Zeichenfolge wird von **sqlbrowseconnetct**zurückgegeben. Der Rückgabecode SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO gibt an, dass alle Verbindungsinformationen angegeben wurden und die Anwendung jetzt mit der Datenquelle verbunden ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLBrowseConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *InConnectionString*  
 Der Such Verbindungs Zeichenfolge durchsuchen (siehe "*InConnectionString* -Argument" in "comments").  
  
 *StringLength1*  
 Der Länge von **InConnectionString* in Zeichen.  
  
 *Outconnectionstring*  
 Ausgeben Zeiger auf einen Zeichen Puffer, in den die Verbindungs Zeichenfolge für das Durchsuchen zurückgegeben werden soll (siehe "*outconnectionstring* -Argument" in "comments").  
  
 Wenn *outconnectionstring* gleich NULL ist, gibt *StringLength2Ptr* weiterhin die Gesamtzahl der Zeichen zurück (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den von *outconnectionstring*verwiesen wird.  
  
 *Pufferlänge*  
 Der Länge (in Zeichen) des **outconnectionstring* -Puffers.  
  
 *StringLength2Ptr*  
 Ausgeben Die Gesamtanzahl der Zeichen (mit Ausnahme der NULL-Beendigung), die \*in *outconnectionstring*zurückgegeben werden können. Wenn die Anzahl der zurück zugebende Zeichen größer als oder gleich *BufferLength*ist, wird die Verbindungs Zeichenfolge in \* *outconnectionstring* auf *BufferLength* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlbrowseconnetct** SQL_ERROR, SQL_SUCCESS_WITH_INFO oder SQL_NEED_DATA zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *Handle von connectionHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **sqlbrowseconnetct** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Der Puffer \* *outconnectionstring* war nicht groß genug, um die gesamte Verbindungs Zeichenfolge zum Durchsuchen von Ergebnissen zurückzugeben, sodass die Zeichenfolge abgeschnitten wurde. Der Puffer **StringLength2Ptr* enthält die Länge der nicht abgeschnittene Suchergebnis-Verbindungs Zeichenfolge. (Die Funktion gibt SQL_NEED_DATA zurück.)|  
|01S00|Ungültiges Verbindungs Zeichen folgen Attribut.|In der Verbindungs Zeichenfolge zum Durchsuchen von Anforderungen (*InConnectionString*) wurde ein ungültiges Attribut Schlüsselwort angegeben. (Die Funktion gibt SQL_NEED_DATA zurück.)<br /><br /> In der Verbindungs Zeichenfolge für die Such Anforderung (*InConnectionString*), die nicht auf die aktuelle Verbindungs Ebene angewendet wird, wurde ein Attribut Schlüsselwort angegeben. (Die Funktion gibt SQL_NEED_DATA zurück.)|  
|01s02 entsprechen|Wert geändert|Der Treiber hat den angegebenen Wert des *ValuePtr* -Arguments in **SQLSetConnectAttr** nicht unterstützt und ersetzt einen ähnlichen Wert. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08001|Der Client kann keine Verbindung herstellen.|Der Treiber konnte keine Verbindung mit der Datenquelle herstellen.|  
|08002|Der Verbindungs Name wird verwendet.|(DM) die angegebene Verbindung wurde bereits verwendet, um eine Verbindung mit einer Datenquelle herzustellen, und die Verbindung wurde geöffnet.|  
|08004|Der Server hat die Verbindung abgelehnt.|Die Datenquelle hat die Einrichtung der Verbindung aus Implementierungs Gründen abgelehnt.|  
|08S01|Kommunikations Verbindungsfehler|Der Kommunikationslink zwischen dem Treiber und der Datenquelle, mit dem der Treiber eine Verbindung herstellen wollte, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|28000|Ungültige Autorisierungs Spezifikation|Entweder die Benutzer-ID oder die Autorisierungs Zeichenfolge oder beides, wie in der Verbindungs Zeichenfolge für das Durchsuchen von Anforderungen (*InConnectionString*) angegeben, verletzt die von der Datenquelle definierten Einschränkungen.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|(DM) der Treiber-Manager konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.<br /><br /> Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Ein asynchroner Vorgang wurde durch Aufrufen der [sqlcancelhandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md)abgebrochen. Anschließend wurde die ursprüngliche Funktion für *connectionHandle*erneut aufgerufen.<br /><br /> Ein Vorgang wurde abgebrochen, indem **sqlcancelhandle** für *connectionHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen wurde.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für *connectionHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der für das Argument *StringLength1* angegebene Wert war kleiner als 0 (null) und war nicht gleich SQL_NTS.<br /><br /> (DM) der für das Argument *BufferLength* angegebene Wert war kleiner als 0 (null).|  
|HY114|Der Treiber unterstützt keine asynchrone Funktions Ausführung auf Verbindungs Ebene.|(DM) die Anwendung hat den asynchronen Vorgang für das Verbindungs Handle aktiviert, bevor die Verbindung hergestellt wird. Der Treiber unterstützt jedoch keinen asynchronen Vorgang für das Verbindungs Handle.|  
|HYT00|Timeout abgelaufen|Der Anmeldungs Timeout Zeitraum ist abgelaufen, bevor die Verbindung mit der Datenquelle abgeschlossen wurde. Der Timeout Zeitraum wird mithilfe von **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der Treiber, der dem angegebenen Datenquellen Namen entspricht, unterstützt die-Funktion nicht.|  
|IM002|Die Datenquelle wurde nicht gefunden und es wurde kein Standardtreiber angegeben.|(DM) der in der Verbindungs Zeichenfolge für das Durchsuchen von Anforderungen (*InConnectionString*) angegebene Datenquellen Name wurde in den Systeminformationen nicht gefunden, und es gab keine Standardtreiber Spezifikation.<br /><br /> (DM) ODBC-Datenquelle und Standardtreiber Informationen konnten in den Systeminformationen nicht gefunden werden.|  
|IM003|Der angegebene Treiber konnte nicht geladen werden.|(DM) der in der Datenquellen Spezifikation in den Systeminformationen oder durch das **Treiber** Schlüsselwort angegebene Treiber wurde nicht gefunden oder konnte aus einem anderen Grund nicht geladen werden.|  
|IM004|Fehler des Treibers **sqlzugewiesene CHandle** auf SQL_HANDLE _ENV|(DM) während **sqlbrowseconnetct**hat der Treiber-Manager die **sqlzuweisung** -Funktion des Treibers mit dem *Handlertyp* SQL_HANDLE_ENV aufgerufen, und der Treiber hat einen Fehler zurückgegeben.|  
|IM005|Fehler beim Treiber " **sqlzugewiesene CHandle** " auf SQL_HANDLE_DBC|(DM) während **sqlbrowseconnetct**hat der Treiber-Manager die **sqlzuweisung** -Funktion des Treibers mit dem *Handlertyp* SQL_HANDLE_DBC aufgerufen, und der Treiber hat einen Fehler zurückgegeben.|  
|IM006|Fehler bei ' **SQLSetConnectAttr** ' des Treibers.|(DM) während **sqlbrowseconnetct**hat der Treiber-Manager die **SQLSetConnectAttr** -Funktion des Treibers aufgerufen, und der Treiber hat einen Fehler zurückgegeben.|  
|IM009|Übersetzungs-DLL kann nicht geladen werden.|Der Treiber konnte die Übersetzungs-DLL, die für die Datenquelle oder die Verbindung angegeben wurde, nicht laden.|  
|IM010|Der Datenquellen Name ist zu lang.|(DM) der Attribut Wert für das DSN-Schlüsselwort ist länger als SQL_MAX_DSN_LENGTH Zeichen.|  
|IM011|Der Treiber Name ist zu lang.|(DM) der Attribut Wert für das Treiber Schlüsselwort ist länger als 255 Zeichen.|  
|IM012|Syntax Fehler für Treiber Schlüsselwort|(DM) das Schlüsselwort-Wert-Paar für das Treiber Schlüsselwort enthielt einen Syntax Fehler.|  
|IM014|Der angegebene DSN enthält einen Architektur Konflikt zwischen dem Treiber und der Anwendung.|(DM) 32-Bit-Anwendung verwendet einen DSN, der eine Verbindung mit einem 64-Bit-Treiber herstellt. oder umgekehrt.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
|S1118|Der Treiber unterstützt keine asynchrone Benachrichtigung.|Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, können Sie SQL_ATTR_ASYNC_DBC_EVENT oder SQL_ATTR_ASYNC_DBC_RETCODE_PTR nicht festlegen.|  
  
## <a name="inconnectionstring-argument"></a>InConnectionString-Argument  
 Eine Verbindungs Zeichenfolge zum Durchsuchen von Anforderungen hat die folgende Syntax:  
  
 *Connection-String* :: = *Attribute*[`;`] &#124; *Attribut* `;` *Connection-String*;<br>
 *Attribute* :: = *Attribute-Schlüsselwort*`=`*Attribut-Wert* &#124; `DRIVER=`[`{`]*Attribut-Wert*[`}`]<br>
 *Attribute-Keywords* :: = `DSN` &#124; `UID` &#124; `PWD` &#124; *Driver-defined-Attribute-Schlüsselwort*<br>
 *Attribute-Value* :: = *Zeichenfolge*<br>
 *Driver-defined-Attribute-Keywords* :: = *Identifier*<br>
  
 , wenn die *Zeichenfolge* NULL oder mehr Zeichen enthält. der *Bezeichner* weist mindestens ein Zeichen auf. beim *Attribut Schlüsselwort* wird die Groß-/Kleinschreibung nicht beachtet. bei *Attribut Wert* kann die Groß-/Kleinschreibung beachtet werden. und der Wert des **DSN** -Schlüssel Worts besteht nicht ausschließlich aus Leerzeichen. Aufgrund der Verbindungs Zeichenfolge und der Initialisierungsdatei Grammatik, Schlüsselwörter und Attributwerte, die die Zeichen **[]{}(),;? = \*! @** sollte vermieden werden. Aufgrund der Grammatik in den Systeminformationen dürfen Schlüsselwörter und Datenquellen Namen keinen umgekehrten Schrägstrich (\\) enthalten. Für ODBC 2. *x* -Treiber, geschweifte Klammern sind um den Attribut Wert für das Treiber Schlüsselwort erforderlich.  
  
 Wenn Schlüsselwörter in der Verbindungs Zeichenfolge für das Durchsuchen von Anforderungen wiederholt werden, verwendet der Treiber den Wert, der dem ersten Vorkommen des Schlüssel Worts zugeordnet ist. Wenn die **DSN** -und **Treiber** Schlüsselwörter in derselben Verbindungs Zeichenfolge für die Such Anforderung enthalten sind, verwenden der Treiber-Manager und der Treiber das Schlüsselwort First.  
  
 Informationen dazu, wie eine Anwendung eine Datenquelle oder einen Treiber auswählt, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
## <a name="outconnectionstring-argument"></a>Outconnectionstring-Argument  
 Die Verbindungs Zeichenfolge zum Durchsuchen von Ergebnissen ist eine Liste von Verbindungs Attributen. Ein Verbindungs Attribut besteht aus einem Attribut Schlüsselwort und einem entsprechenden Attribut Wert. Die Verbindungs Zeichenfolge für das Durchsuchen hat die folgende Syntax:  
  
 *Connection-String* :: = *Attribute*[`;`] &#124; *Attribut* `;` *Verbindungs Zeichenfolge*<br>
 *Attribute* :: = [`*`]*Attribut-Schlüsselwort*`=`*Attribut-Wert*<br>
 *Attribute-Keywords* :: = *ODBC-Attribute-Schlüsselwort* &#124; *Driver-defined-Attribute-Keywords*<br>
 *ODBC-Attribute-Keywords* = {`UID` &#124; `PWD`} [`:`*lokalisierter Bezeichner*] *Driver-defined-Attribute-Keywords* :: *= Identifier*[`:`*lokalisierter-Identifier*] *Attribut-Wert* : `{` : = *Attribute-Wert-List* `}` &#124; `?` (die geschweiften Klammern sind Literale; Sie werden vom Treiber zurückgegeben.)<br>
 *Attribute-Value-List* :: = *Zeichen* Folge [`:`*lokalisierte Zeichenfolge*] &#124; *Zeichenfolge* [`:`*lokalisierte Zeichenfolge*] `,` *Attribut-Wert-List*<br>
  
 , wenn *Zeichenfolge Zeichen* und *lokalisierte Zeichen* folgen NULL oder mehr Zeichen aufweisen. der *Bezeichner* und der *lokalisierte-Bezeichner* haben mindestens ein Zeichen. beim *Attribut Schlüsselwort* wird die Groß-/Kleinschreibung nicht beachtet. beim *Attribut-Wert* kann die Groß-/Kleinschreibung beachtet werden. Aufgrund von Verbindungs Zeichenfolgen-und Initialisierungsdatei Grammatik, Schlüsselwörtern, lokalisierten bezeichnerwerten und Attributwerten, die die Zeichen **[]{}(),;? = \*! @** sollte vermieden werden. Aufgrund der Grammatik in den Systeminformationen dürfen Schlüsselwörter und Datenquellen Namen keinen umgekehrten Schrägstrich (\\) enthalten.  
  
 Die Syntax zum Durchsuchen von Ergebnis Verbindungs Zeichenfolgen wird gemäß den folgenden semantischen Regeln verwendet:  
  
-   Wenn ein Sternchen (\*) einem *attributsschlüsselwort*vorangestellt ist, ist das *Attribut* optional und kann beim nächsten **sqlbrowseconnetct**-Befehl ausgelassen werden.  
  
-   Die Attribut Schlüsselwörter **UID** und **pwd** haben dieselbe Bedeutung wie in **SQLDriverConnect**definiert.  
  
-   Ein *Treiber definiertes attributschlüsselwort* benennt den Attributtyp, für den ein Attribut Wert angegeben werden kann. Beispielsweise könnte Server, **Database**, **Host**oder **DBMS** **verwendet**werden.  
  
-   *ODBC-Attribute-Keywords* und *Driver-defined-Attribute-Keywords* enthalten eine lokalisierte oder benutzerfreundliche Version des Schlüssel Worts. Dies kann von Anwendungen als Bezeichnung in einem Dialogfeld verwendet werden. Allerdings muss **UID**, **pwd**oder der *Bezeichner* allein verwendet werden, wenn eine Such Anforderungs Zeichenfolge an den Treiber übergeben wird.  
  
-   "{*Attribute-Value-List*}" ist eine Enumeration der tatsächlichen Werte, die für das entsprechende *Attribut Schlüsselwort*gültig sind. Beachten Sie, dass die{}geschweiften Klammern () keine Auswahlliste angeben. Sie werden vom Treiber zurückgegeben. Beispielsweise kann es sich um eine Liste von Servernamen oder eine Liste von Datenbanknamen handeln.  
  
-   Wenn der *Attribut Wert* ein einzelnes Fragezeichen (?) ist, entspricht ein einzelner Wert dem *Attribut Schlüsselwort*. Beispiel: UID = Johns; PWD = Sesam.  
  
-   Jeder **sqlbrowseconnetct** -Befehl gibt nur die Informationen zurück, die erforderlich sind, um die nächste Ebene des Verbindungs Vorgangs zu erfüllen. Der Treiber ordnet Zustandsinformationen dem Verbindungs Handle zu, sodass der Kontext immer bei jedem-Rückruf bestimmt werden kann.  
  
## <a name="using-sqlbrowseconnect"></a>Verwenden von sqlbrowseconnetct  
 **Sqlbrowseconnetct** erfordert eine zugeordnete Verbindung. Der Treiber-Manager lädt den in oder angegebenen Treiber, der mit dem in der ursprünglichen Verbindungs Zeichenfolge für die Such Anforderung angegebenen Datenquellen Namen übereinstimmt. Weitere Informationen zu diesem Zeitpunkt finden Sie im Abschnitt "Kommentare" in der [SQLCONNECT-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md). Der Treiber kann während des Such Vorgangs eine Verbindung mit der Datenquelle herstellen. Wenn **sqlbrowseconnetct** SQL_ERROR zurückgibt, werden ausstehende Verbindungen beendet, und die Verbindung wird wieder hergestellt.  
  
> [!NOTE]  
>  **Sqlbrowseconnetct** unterstützt kein Verbindungspooling. Wenn **sqlbrowseconnetct** aufgerufen wird, während das Verbindungspooling aktiviert ist, wird SQLSTATE HY000 (allgemeiner Fehler) zurückgegeben.  
  
 Wenn **sqlbrowseconnetct** zum ersten Mal für eine Verbindung aufgerufen wird, muss die Verbindungs Zeichenfolge zum Durchsuchen von Anforderungen das **DSN** -Schlüsselwort oder das **Treiber** Schlüsselwort enthalten. Wenn die Verbindungs Zeichenfolge zum Durchsuchen von Anforderungen das **DSN** -Schlüsselwort enthält, sucht der Treiber-Manager eine entsprechende Datenquellen Spezifikation in den Systeminformationen:  
  
-   Wenn der Treiber-Manager die entsprechende Datenquellen Spezifikation findet, lädt er die zugehörige Treiber-DLL. der Treiber kann Informationen über die Datenquelle aus den Systeminformationen abrufen.  
  
-   Wenn der Treiber-Manager die entsprechende Datenquellen Spezifikation nicht finden kann, sucht er die standardmäßige Datenquellen Spezifikation und lädt die zugehörige Treiber-DLL. der Treiber kann Informationen über die Standarddaten Quelle aus den Systeminformationen abrufen. "Default" wird an den Treiber für den DSN übermittelt.  
  
-   Wenn der Treiber-Manager die entsprechende Datenquellen Spezifikation nicht finden kann und keine standardmäßige Datenquellen Spezifikation vorhanden ist, wird SQL_ERROR mit SQLSTATE IM002 zurückgegeben (die Datenquelle wurde nicht gefunden, und es wurde kein Standardtreiber angegeben).  
  
 Wenn die Verbindungs Zeichenfolge zum Durchsuchen von Anforderungen das **Treiber** Schlüsselwort enthält, lädt der Treiber-Manager den angegebenen Treiber. Es wird nicht versucht, eine Datenquelle in den Systeminformationen zu finden. Da das **Treiber** Schlüsselwort keine Informationen aus den Systeminformationen verwendet, muss der Treiber genügend Schlüsselwörter definieren, damit ein Treiber nur mithilfe der Informationen in den Verbindungs Zeichenfolgen für das Durchsuchen von Anforderungen eine Verbindung mit einer Datenquelle herstellen kann.  
  
 Bei jedem Aufrufen von **sqlbrowseconnetct**gibt die Anwendung die Verbindungs Attributwerte in der Verbindungs Zeichenfolge für die Such Anforderung an. Der Treiber gibt aufeinanderfolgende Ebenen von Attributen und Attributwerten in der Verbindungs Zeichenfolge zum Durchsuchen von Ergebnissen zurück. Es wird SQL_NEED_DATA zurückgegeben, solange Verbindungs Attribute vorhanden sind, die noch nicht in der Verbindungs Zeichenfolge für die Such Anforderung aufgelistet wurden. Die Anwendung verwendet den Inhalt der Verbindungs Zeichenfolge zum Durchsuchen von Ergebnissen, um die Verbindungs Zeichenfolge für die Such Anforderung für den nächsten **sqlbrowseconnetct**-Befehl zu erstellen. Alle obligatorischen Attribute (die nicht mit einem Sternchen im *outconnectionstring* -Argument vorangestellt sind) müssen im nächsten **sqlbrowseconnetct**-Befehl enthalten sein. Beachten Sie, dass die Anwendung den Inhalt vorheriger Verbindungs Zeichenfolgen zum Durchsuchen von Ergebnissen beim Aufbau der aktuellen Verbindungs Zeichenfolge für Suchanforderungen nicht verwenden kann Das heißt, es können keine unterschiedlichen Werte für Attribute angegeben werden, die in vorherigen Ebenen festgelegt wurden.  
  
 Wenn alle Ebenen der Verbindung und ihre zugeordneten Attribute aufgezählt wurden, gibt der Treiber SQL_SUCCESS zurück, die Verbindung mit der Datenquelle ist abgeschlossen, und eine vollständige Verbindungs Zeichenfolge wird an die Anwendung zurückgegeben. Die Verbindungs Zeichenfolge eignet sich für die Verwendung von in Verbindung mit **SQLDriverConnect**mit der SQL_DRIVER_NOPROMPT-Option zum Herstellen einer anderen Verbindung. Die vollständige Verbindungs Zeichenfolge kann jedoch nicht in einem anderen Befehl von **sqlbrowseconnetct**verwendet werden. Wenn **sqlbrowseconnetct** erneut aufgerufen wurde, müsste die gesamte Sequenz von Aufrufen wiederholt werden.  
  
 **Sqlbrowseconnetct** gibt auch SQL_NEED_DATA zurück, wenn während des durch Suchvorgangs wiederherstellbare, nicht schwerwiegende Fehler auftreten. beispielsweise ein ungültiges Kennwort oder Attribut Schlüsselwort, das von der Anwendung angegeben wird. Wenn SQL_NEED_DATA zurückgegeben wird und die Verbindungs Zeichenfolge zum Durchsuchen von Ergebnissen unverändert ist, ist ein Fehler aufgetreten, und die Anwendung kann **SQLGetDiagRec** aufrufen, um SQLSTATE für Such Fehler zurückzugeben. Dadurch kann die Anwendung das Attribut korrigieren und das Durchsuchen fortsetzen.  
  
 Eine Anwendung kann den browseinsprozess jederzeit durch Aufrufen von **SQLDisconnect**beenden. Der Treiber beendet alle ausstehenden Verbindungen und gibt die Verbindung mit dem Status "nicht verbunden" zurück.  
  
 Wenn asynchrone Vorgänge für das Verbindungs Handle aktiviert sind, gibt **sqlbrowseconnetct** möglicherweise auch SQL_STILL_EXECUTING zurück. Wenn SQL_NEED_DATA zurückgegeben wird, muss die Anwendung **SQLDisconnect** verwenden, um den durchsuchenprozess abzubrechen. Wenn **sqlbrowseconnetct** SQL_STILL_EXECUTING zurückgibt, sollte eine Anwendung **sqlcancelhandle** verwenden, um den Vorgang abzubrechen, der ausgeführt wird. Wenn Sie **sqlcancelhandle** aufrufen, nachdem die Funktion zurückgegeben SQL_NEED_DATA hat keine Auswirkung.  
  
 Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit sqlbrowseconnetct](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md).  
  
 Wenn ein Treiber **sqlbrowseconnetct**unterstützt, muss der Treiber Schlüsselwortbereich in den Systeminformationen für den Treiber das **connectfunctions** -Schlüsselwort enthalten, bei dem das dritte Zeichen auf "Y" festgelegt ist.  
  
## <a name="code-example"></a>Codebeispiel  
  
> [!NOTE]  
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unter `Trusted_Connection=yes` stützt, sollten Sie anstelle von Benutzer-ID-und Kenn Wort Informationen in der Verbindungs Zeichenfolge angeben.  
  
 Im folgenden Beispiel ruft eine Anwendung **sqlbrowseconnetct** wiederholt auf. Jedes Mal, wenn **sqlbrowseconnetct** SQL_NEED_DATA zurückgibt, werden Informationen zu den Daten zurückgegeben \*, die in *outconnectionstring*benötigt werden. Die Anwendung übergibt *outconnectionstring* an die **GetUserInput** -Routine (nicht angezeigt). **GetUserInput** analysiert die Informationen, erstellt und zeigt ein Dialogfeld an und gibt die Informationen zurück, die vom Benutzer in \* *InConnectionString*eingegeben wurden. Die Anwendung übergibt die Informationen des Benutzers beim nächsten **sqlbrowseconnetct**-aufrufsbefehl an den Treiber. Nachdem die Anwendung alle erforderlichen Informationen für den Treiber bereitgestellt hat, um eine Verbindung mit der Datenquelle herzustellen, gibt **sqlbrowseconnetct** SQL_SUCCESS zurück, und die Anwendung wird fortgesetzt.  
  
 Ein ausführlicheres Beispiel für das Herstellen einer Verbindung mit einem SQL Server-Treiber durch Aufrufen von **sqlbrowseconnetct**finden Sie unter [SQL Server Browsing-Beispiel](../../../odbc/reference/develop-app/sql-server-browsing-example.md).  
  
 Um z. b. eine Verbindung mit der Datenquellen Verkäufe herzustellen, können die folgenden Aktionen ausgeführt werden. Zuerst übergibt die Anwendung die folgende Zeichenfolge an **sqlbrowseconnetct**:  
  
```  
"DSN=Sales"  
```  
  
 Der Treiber-Manager lädt den Treiber, der mit den Datenquellen Verkäufen verknüpft ist. Anschließend wird die **sqlbrowseconnetct** -Funktion des Treibers mit denselben Argumenten aufgerufen, die Sie von der Anwendung erhalten hat. Der Treiber gibt die folgende Zeichenfolge in **outconnectionstring*zurück:  
  
```  
"HOST:Server={red,blue,green};UID:ID=?;PWD:Password=?"  
```  
  
 Die Anwendung übergibt diese Zeichenfolge an die **GetUserInput** -Routine, die ein Dialogfeld erstellt, in dem der Benutzer aufgefordert wird, den roten, blauen oder grünen Server auszuwählen und eine Benutzer-ID und ein Kennwort einzugeben. Die Routine übergibt die folgenden benutzerdefinierten Informationen in \* *InConnectionString*zurück, die die Anwendung an **sqlbrowseconnetct**übergibt:  
  
```  
"HOST=red;UID=Smith;PWD=Sesame"  
```  
  
 **Sqlbrowseconnetct** verwendet diese Informationen zum Herstellen einer Verbindung mit dem roten Server als Smith mit dem Kennwort Sesam und gibt dann die folgende Zeichenfolge in **outconnectionstring*zurück:  
  
```  
"*DATABASE:Database={SalesEmployees,SalesGoals,SalesOrders}"  
```  
  
 Die Anwendung übergibt diese Zeichenfolge an die **GetUserInput** -Routine, die ein Dialogfeld erstellt, in dem der Benutzer aufgefordert wird, eine Datenbank auszuwählen. Der Benutzer wählt EmpData aus, und die Anwendung ruft **sqlbrowseconnetct** mit der folgenden Zeichenfolge ab:  
  
```  
"DATABASE=SalesOrders"  
```  
  
 Dies ist die letzte Information, die der Treiber zum Herstellen einer Verbindung mit der Datenquelle benötigt. **Sqlbrowseconnetct** gibt SQL_SUCCESS zurück, und **outconnectionstring* enthält die vollständige Verbindungs Zeichenfolge:  
  
```cpp  
// SQLBrowseConnect_Function.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
#define BRWS_LEN 100  
SQLHENV henv;  
SQLHDBC hdbc;  
SQLHSTMT hstmt;  
SQLRETURN retcode;  
SQLCHAR szConnStrIn[BRWS_LEN], szConnStrOut[BRWS_LEN];  
SQLSMALLINT cbConnStrOut;  
  
void GetUserInput(SQLCHAR * szConnStrOut, SQLCHAR * szConnStrIn) {}  
  
int main() {  
   // Allocate the environment handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);        
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
      // Set the version environment attribute.  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
         // Allocate the connection handle.  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            // Call SQLBrowseConnect until it returns a value other than SQL_NEED_DATA   
            // (pass data source name the first time).  If SQL_NEED_DATA is returned, call GetUserInput   
            // (not shown) to build a dialog from the values in szConnStrOut.  The user-supplied values   
            // are returned in szConnStrIn, which is passed in the next call to SQLBrowseConnect.  
  
            strcpy_s((char*)szConnStrIn, _countof(szConnStrIn), "DSN=Sales");  
            do {  
               retcode = SQLBrowseConnect(hdbc, szConnStrIn, SQL_NTS,  
                  szConnStrOut, BRWS_LEN, &cbConnStrOut);  
               if (retcode == SQL_NEED_DATA)  
                  GetUserInput(szConnStrOut, szConnStrIn);  
            } while (retcode == SQL_NEED_DATA);  
  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){  
  
               // Allocate the statement handle.  
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                  // Process data after successful connection  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               SQLDisconnect(hdbc);  
            }  
         }  
         SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
      }  
   }  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Zuordnen eines Verbindungs Handles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Trennen der Verbindung mit einer Datenquelle|[SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungs Zeichenfolge oder ein Dialogfeld|[SQLDriveConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Zurückgeben von Treiber Beschreibungen und-Attributen|[SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Freigeben eines Verbindungs Handles|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
