---
title: SQLBrowseConnect-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301340"
---
# <a name="sqlbrowseconnect-function"></a>SQLBrowseConnect-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLBrowseConnect** unterstützt eine iterative Methode zum Ermitteln und Aufzählen der Attribute und Attributwerte, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind. Jeder Aufruf von **SQLBrowseConnect** gibt aufeinanderfolgende Ebenen von Attributen und Attributwerten zurück. Wenn alle Ebenen aufgezählt wurden, wird eine Verbindung mit der Datenquelle abgeschlossen, und eine vollständige Verbindungszeichenfolge wird von **SQLBrowseConnect**zurückgegeben. Ein Rückgabecode von SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO gibt an, dass alle Verbindungsinformationen angegeben wurden und die Anwendung nun mit der Datenquelle verbunden ist.  
  
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
 [Eingabe] Durchsuchen der Verbindungszeichenfolge für Die Anforderung (siehe "*InConnectionString* Argument" in "Kommentare").  
  
 *StringLength1*  
 [Eingabe] Länge von **InConnectionString* in Zeichen.  
  
 *OutConnectionString*  
 [Ausgabe] Zeiger auf einen Zeichenpuffer, in dem die Verbindungszeichenfolge für das Suchergebnis zurückgegeben werden soll (siehe "*OutConnectionString* Argument" in "Kommentare").  
  
 Wenn *OutConnectionString* NULL ist, gibt *StringLength2Ptr* weiterhin die Gesamtzahl der Zeichen zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer von *OutConnectionString*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Länge des **OutConnectionString-Puffers* in Zeichen.  
  
 *StringLength2Ptr*  
 [Ausgabe] Die Gesamtzahl der Zeichen (ohne Null-Beendigung), \*die in *OutConnectionString*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer oder gleich *BufferLength*ist, wird die Verbindungszeichenfolge in \* *OutConnectionString* auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn SQLBrowseConnect SQL_ERROR, SQL_SUCCESS_WITH_INFO oder SQL_NEED_DATA **zurückgibt,** kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle von ConnectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLBrowseConnect** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der \*Puffer *OutConnectionString* war nicht groß genug, um die gesamte Suchergebnisverbindungszeichenfolge zurückzugeben, sodass die Zeichenfolge abgeschnitten wurde. Der Puffer **StringLength2Ptr* enthält die Länge der ungetraren Suchergebnis-Verbindungszeichenfolge. (Funktion gibt SQL_NEED_DATA zurück.)|  
|01S00|Ungültiges Verbindungszeichenfolgenattribut|In der Verbindungszeichenfolge für die Suchanforderung (*InConnectionString*) wurde ein ungültiges Attributschlüsselwort angegeben. (Funktion gibt SQL_NEED_DATA zurück.)<br /><br /> In der Verbindungszeichenfolge für die Suchanforderung (*InConnectionString*) wurde ein Attributschlüsselwort angegeben, das nicht auf die aktuelle Verbindungsebene angewendet wird. (Funktion gibt SQL_NEED_DATA zurück.)|  
|01S02|Wert geändert|Der Treiber unterstützte den angegebenen Wert des *ValuePtr-Arguments* in **SQLSetConnectAttr** nicht und ersetzte einen ähnlichen Wert. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08001|Client kann keine Verbindung herstellen|Der Treiber konnte keine Verbindung mit der Datenquelle herstellen.|  
|08002|Verbindungsname wird verwendet|(DM) Die angegebene Verbindung wurde bereits verwendet, um eine Verbindung mit einer Datenquelle herzustellen, und die Verbindung war geöffnet.|  
|08004|Server hat die Verbindung abgelehnt|Die Datenquelle lehnte den Aufbau der Verbindung aus implementierungsdefinierten Gründen ab.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber eine Verbindung herstellen wollte, ist fehlgeschlagen, bevor die Verarbeitung durch die Funktion abgeschlossen wurde.|  
|28000|Ungültige Autorisierungsspezifikation|Entweder der Benutzerbezeichner oder die Autorisierungszeichenfolge oder beides, wie in der Verbindungszeichenfolge für die Suchanforderung (*InConnectionString*) angegeben, hat einschränkungen, die von der Datenquelle definiert wurden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|(DM) Der Treiber-Manager konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.<br /><br /> Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Ein asynchroner Vorgang wurde durch Aufrufen von [SQLCancelHandle Function](../../../odbc/reference/syntax/sqlcancelhandle-function.md)abgebrochen. Dann wurde die ursprüngliche Funktion erneut auf dem *ConnectionHandle*aufgerufen.<br /><br /> Ein Vorgang wurde abgebrochen, indem **SQLCancelHandle** für *das ConnectionHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen wurde.|  
|HY010|Funktionssequenzfehler|(DM) Eine asynchron ausführende Funktion (nicht diese) wurde für den *ConnectionHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der für das Argument *StringLength1* angegebene Wert war kleiner als 0 und entsprach nicht SQL_NTS.<br /><br /> (DM) Der für das Argument *BufferLength* angegebene Wert war kleiner als 0.|  
|HY114|Treiber unterstützt keine asynchrone Funktionsausführung auf Verbindungsebene|(DM) Die Anwendung aktivierte den asynchronen Vorgang am Verbindungshandle, bevor die Verbindung hergestellt wurde. Der Treiber unterstützt jedoch keinen asynchronen Vorgang am Verbindungshandle.|  
|HYT00|Timeout abgelaufen|Der Anmeldetimeoutzeitraum ist abgelaufen, bevor die Verbindung zur Datenquelle abgeschlossen wurde. Der Timeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der Treiber, der dem angegebenen Datenquellennamen entspricht, unterstützt die Funktion nicht.|  
|IM002|Datenquelle nicht gefunden und kein Standardtreiber angegeben|(DM) Der in der Verbindungszeichenfolge für die Suchanforderung (*InConnectionString*) angegebene Datenquellenname wurde in den Systeminformationen nicht gefunden, und es gab auch keine Standardtreiberspezifikation.<br /><br /> (DM) ODBC-Datenquelle und Standardtreiberinformationen konnten in den Systeminformationen nicht gefunden werden.|  
|IM003|Der angegebene Treiber konnte nicht geladen werden.|(DM) Der treiber, der in der Datenquellenspezifikation in den Systeminformationen aufgeführt ist oder durch das **SCHLÜSSELwort DRIVER** angegeben ist, wurde aus einem anderen Grund nicht gefunden oder konnte nicht geladen werden.|  
|IM004|**SQLAllocHandle** des Treibers auf SQL_HANDLE _ENV fehlgeschlagen|(DM) Während **SQLBrowseConnect**rief der Treiber-Manager die **SQLAllocHandle-Funktion** des Treibers mit einem *HandleType* von SQL_HANDLE_ENV und der Treiber gab einen Fehler zurück.|  
|IM005|**SQLAllocHandle** des Treibers auf SQL_HANDLE_DBC fehlgeschlagen|(DM) Während **SQLBrowseConnect**rief der Treiber-Manager die **SQLAllocHandle-Funktion** des Treibers mit einem *HandleType* von SQL_HANDLE_DBC und der Treiber gab einen Fehler zurück.|  
|IM006|**SQLSetConnectAttr** des Treibers fehlgeschlagen|(DM) Während **SQLBrowseConnect**rief der Treiber-Manager die **SQLSetConnectAttr-Funktion** des Treibers auf, und der Treiber gab einen Fehler zurück.|  
|IM009|Übersetzungs-DLL kann nicht geladen werden|Der Treiber konnte die Übersetzungs-DLL, die für die Datenquelle oder die Verbindung angegeben wurde, nicht laden.|  
|IM010|Datenquellenname zu lang|(DM) Der Attributwert für das DSN-Schlüsselwort war länger als SQL_MAX_DSN_LENGTH Zeichen.|  
|IM011|Treibername zu lang|(DM) Der Attributwert für das Schlüsselwort DRIVER war länger als 255 Zeichen.|  
|IM012|DRIVER-Schlüsselwortsyntaxfehler|(DM) Das Schlüsselwort-Wert-Paar für das SCHLÜSSELwort DRIVER enthielt einen Syntaxfehler.|  
|IM014|Der angegebene DSN enthält eine Architekturkonfliktübereinstimmung zwischen Treiber und Anwendung|(DM) 32-Bit-Anwendung verwendet eine DSN-Verbindung mit einem 64-Bit-Treiber; oder umgekehrt.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
|S1118|Treiber unterstützt keine asynchrone Benachrichtigung|Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, können Sie keine SQL_ATTR_ASYNC_DBC_EVENT oder SQL_ATTR_ASYNC_DBC_RETCODE_PTR festlegen.|  
  
## <a name="inconnectionstring-argument"></a>InConnectionString-Argument  
 Eine Verbindungszeichenfolge für Suchanfragen hat die folgende Syntax:  
  
 *connection-string* ::=`;` *attribut*[ ] &#124; *attribut* `;` *connection-string*;<br>
 *Attribut* ::= *attribut-keyword*`=`*attribut-value* `DRIVER=`&#124;`{`[`}`]*attribut-value*[ ]<br>
 *attribut-keyword* `DSN` ::= `UID` `PWD` &#124; &#124; *&#124;-treiber-defined-attribut-keyword*<br>
 *Attributwert* ::= *Zeichenzeichenfolge*<br>
 *driver-defined-attribute-keyword* ::= *Bezeichner*<br>
  
 wobei *die Zeichenfolge* null oder mehr Zeichen enthält; *Bezeichner* hat ein oder mehrere Zeichen; *attribut-keyword* wird nicht von groß vertraulich berücksichtigt. *Attributwert* kann die Groß-/Kleinschreibung berücksichtigen; und der Wert des **DSN-Schlüsselworts** besteht nicht nur aus Leerzeichen. Aufgrund der Grammatik von Verbindungszeichenfolgen und Initialisierungsdateien, Schlüsselwörtern und Attributwerten, die die Zeichen **[]{}(),;? enthalten. \*=!** sollte vermieden werden. Aufgrund der Grammatik in den Systeminformationen dürfen Schlüsselwörter und Datenquellennamen nicht den umgekehrten Schrägstrich (\\) enthalten. Für eine ODBC 2. *x-Treiber* sind geschweifte Klammern um den Attributwert für das Schlüsselwort DRIVER erforderlich.  
  
 Wenn Schlüsselwörter in der Verbindungszeichenfolge für die Suchanforderung wiederholt werden, verwendet der Treiber den Wert, der dem ersten Vorkommen des Schlüsselworts zugeordnet ist. Wenn die **Schlüsselwörter DSN** und **DRIVER** in derselben Verbindungszeichenfolge für Suchananfrage enthalten sind, verwenden der Treiber-Manager und der Treiber das Schlüsselwort, das zuerst angezeigt wird.  
  
 Informationen dazu, wie eine Anwendung eine Datenquelle oder einen Treiber auswählt, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
## <a name="outconnectionstring-argument"></a>OutConnectionString-Argument  
 Die Verbindungszeichenfolge für das Suchergebnis ist eine Liste von Verbindungsattributen. Ein Verbindungsattribut besteht aus einem Attributschlüsselwort und einem entsprechenden Attributwert. Die Verbindungszeichenfolge für das Suchergebnis hat die folgende Syntax:  
  
 *connection-string* ::=`;` *Attribut*[ ] &#124; *Attribut-Verbindungszeichenfolge* *attribute* `;`<br>
 *Attribut* ::=`*`[ ]*attribut-keyword*`=`*attribut-value*<br>
 *attribut-keyword* ::= *ODBC-attribute-keyword* &#124; *driver-defined-attribute-keyword*<br>
 *ODBC-attribut-keyword* =`UID` `PWD`&#124;`:`'[*localized-identifier*] *driver-defined-attribute-keyword* ::= *identifier*[`:`*localized-identifier*] *attribute-value* ::= `{` *attribute-value-list* `}` &#124; `?` (Die geschweiften Klammern sind literal; sie werden vom Treiber zurückgegeben.)<br>
 *attribut-value-list* ::= *character-string* [`:`*localized-character string*] &#124; *character-string* [`:`*localized-character string*] `,` *attribute-value-list*<br>
  
 wobei *Zeichen-String* und *lokalisierte Zeichenzeichenfolge* null oder mehr Zeichen haben; *Bezeichner* und *lokalisierter Bezeichner* haben ein oder mehrere Zeichen; *attribut-keyword* wird nicht von groß vertraulich berücksichtigt. und *Attributwert* kann die Groß-/Kleinschreibung berücksichtigen. Aufgrund der Grammatik von Verbindungszeichenfolgen und Initialisierungsdateien, Schlüsselwörtern, lokalisierten Bezeichnern und Attributwerten, die die Zeichen **[]{}(),;? enthalten. \*=!** sollte vermieden werden. Aufgrund der Grammatik in den Systeminformationen dürfen Schlüsselwörter und Datenquellennamen nicht den umgekehrten Schrägstrich (\\) enthalten.  
  
 Die Syntax der Suchergebniszeichenfolge wird gemäß den folgenden semantischen Regeln verwendet:  
  
-   Wenn ein Sternchen\*( ) einem *Attribut-Schlüsselwort*vorangeht, ist das *Attribut* optional und kann beim nächsten Aufruf von **SQLBrowseConnect**weggelassen werden.  
  
-   Die Attributschlüsselwörter **UID** und **PWD** haben dieselbe Bedeutung wie in **SQLDriverConnect**definiert.  
  
-   Ein *treiberdefiniertes Attribut-Schlüsselwort* benennt die Art des Attributs, für das ein Attributwert angegeben werden kann. Es kann sich z. B. **um SERVER**, **DATABASE**, **HOST**oder **DBMS handelt.**  
  
-   *ODBC-attribute-keywords* und *driver-defined-attribute-keywords* enthalten eine lokalisierte oder benutzerfreundliche Version des Schlüsselworts. Dies kann von Anwendungen als Bezeichnung in einem Dialogfeld verwendet werden. UID **UID**, **PWD**oder der *Bezeichner* allein müssen jedoch verwendet werden, wenn eine Suchanforderungszeichenfolge an den Treiber übergeben wird.  
  
-   Die*Attribut-Wert-Liste*ist eine Aufzählung von Istwerten, die für das entsprechende *Attribut-Schlüsselwort*gültig sind. Beachten Sie, dass{}die geschweiften Klammern ( ) keine Liste von Auswahlmöglichkeiten angeben; sie werden vom Fahrer zurückgegeben. Es kann sich z. B. um eine Liste von Servernamen oder um eine Liste von Datenbanknamen erfinden.  
  
-   Wenn der *Attributwert* ein einzelnes Fragezeichen (?) ist, entspricht ein einzelner Wert dem *Attribut-Schlüsselwort*. Beispiel: UID=JohnS; PWD=Sesam.  
  
-   Jeder Aufruf von **SQLBrowseConnect** gibt nur die Informationen zurück, die erforderlich sind, um die nächste Ebene des Verbindungsprozesses zu erfüllen. Der Treiber ordnet Statusinformationen dem Verbindungshandle zu, sodass der Kontext immer bei jedem Aufruf bestimmt werden kann.  
  
## <a name="using-sqlbrowseconnect"></a>Verwenden von SQLBrowseConnect  
 **SQLBrowseConnect** erfordert eine zugewiesene Verbindung. Der Treiber-Manager lädt den Treiber, der in angegeben wurde oder dem Datenquellennamen entspricht, der in der verbindungszeichenfolge für die anfängliche Suchanforderung angegeben ist. Informationen dazu, wann dies geschieht, finden Sie im Abschnitt "Kommentare" in [SQLConnect Function](../../../odbc/reference/syntax/sqlconnect-function.md). Der Treiber kann während des Browservorgangs eine Verbindung mit der Datenquelle herstellen. Wenn **SQLBrowseConnect** SQL_ERROR zurückgibt, werden ausstehende Verbindungen beendet, und die Verbindung wird in einen nicht verbundenen Zustand zurückgeführt.  
  
> [!NOTE]  
>  **SQLBrowseConnect** unterstützt das Verbindungspooling nicht. Wenn **SQLBrowseConnect** aufgerufen wird, während das Verbindungspooling aktiviert ist, wird SQLSTATE HY000 (Allgemeiner Fehler) zurückgegeben.  
  
 Wenn **SQLBrowseConnect** zum ersten Mal für eine Verbindung aufgerufen wird, muss die Verbindungszeichenfolge für Suchanforderungen das **DSN-Schlüsselwort** oder das **DRIVER-Schlüsselwort** enthalten. Wenn die Verbindungszeichenfolge für suchanforderung das **DSN-Schlüsselwort** enthält, sucht der Treiber-Manager eine entsprechende Datenquellenspezifikation in den Systeminformationen:  
  
-   Wenn der Treiber-Manager die entsprechende Datenquellenspezifikation findet, lädt er die zugehörige Treiber-DLL. Der Treiber kann Informationen über die Datenquelle aus den Systeminformationen abrufen.  
  
-   Wenn der Treiber-Manager die entsprechende Datenquellenspezifikation nicht finden kann, sucht er die Standarddatenquellenspezifikation und lädt die zugehörige Treiber-DLL. Der Treiber kann Informationen über die Standarddatenquelle aus den Systeminformationen abrufen. "DEFAULT" wird an den Treiber für den DSN übergeben.  
  
-   Wenn der Treiber-Manager die entsprechende Datenquellenspezifikation nicht finden kann und keine Standarddatenquellenspezifikation vorhanden ist, gibt er SQL_ERROR mit SQLSTATE IM002 zurück (Datenquelle wurde nicht gefunden und kein Standardtreiber angegeben).  
  
 Wenn die Verbindungszeichenfolge für die Suchanforderung das **Schlüsselwort DRIVER** enthält, lädt der Treiber-Manager den angegebenen Treiber. Es wird nicht versucht, eine Datenquelle in den Systeminformationen zu finden. Da das **SCHLÜSSELwort DRIVER** keine Informationen aus den Systeminformationen verwendet, muss der Treiber genügend Schlüsselwörter definieren, damit ein Treiber eine Verbindung mit einer Datenquelle herstellen kann, indem er nur die Informationen in den Verbindungszeichenfolgen für suchanforderungverwendet.  
  
 Bei jedem Aufruf von **SQLBrowseConnect**gibt die Anwendung die Verbindungsattributwerte in der Verbindungszeichenfolge für Suchanforderungen an. Der Treiber gibt aufeinanderfolgende Ebenen von Attributen und Attributwerten in der Verbindungszeichenfolge für das Suchergebnis zurück. Es wird SQL_NEED_DATA zurückgegeben, solange Verbindungsattribute vorhanden sind, die noch nicht in der Verbindungszeichenfolge für Suchanforderungszeichenfolgen aufgezählt wurden. Die Anwendung verwendet den Inhalt der Verbindungszeichenfolge zum Durchsuchen von Resultaden, um die Verbindungszeichenfolge für die Suchanforderung für den nächsten Aufruf von **SQLBrowseConnect**zu erstellen. Alle obligatorischen Attribute (die nicht einem Sternchen im *OutConnectionString-Argument* vorangestellt sind) müssen beim nächsten Aufruf von **SQLBrowseConnect**enthalten sein. Beachten Sie, dass die Anwendung beim Erstellen der aktuellen Suchanforderungsverbindungszeichenfolge den Inhalt der vorherigen Suchergebnisverbindungszeichenfolgen nicht verwenden kann. Das heißt, es können keine unterschiedlichen Werte für Attribute angegeben werden, die in früheren Ebenen festgelegt wurden.  
  
 Wenn alle Verbindungsebenen und die zugehörigen Attribute aufgezählt wurden, gibt der Treiber SQL_SUCCESS zurück, die Verbindung zur Datenquelle ist abgeschlossen, und eine vollständige Verbindungszeichenfolge wird an die Anwendung zurückgegeben. Die Verbindungszeichenfolge eignet sich zur Verwendung in Verbindung mit **SQLDriverConnect**mit der Option SQL_DRIVER_NOPROMPT zum Herstellen einer anderen Verbindung. Die vollständige Verbindungszeichenfolge kann jedoch nicht in einem anderen Aufruf von **SQLBrowseConnect**verwendet werden. Wenn **SQLBrowseConnect** erneut aufgerufen würde, müsste die gesamte Reihenfolge der Aufrufe wiederholt werden.  
  
 **SQLBrowseConnect** gibt auch SQL_NEED_DATA zurück, wenn während des Suchvorgangs wiederherstellbare, nicht schwerwiegende Fehler auftreten. z. B. ein ungültiges Kennwort oder Attributschlüsselwort, das von der Anwendung bereitgestellt wird. Wenn SQL_NEED_DATA zurückgegeben wird und die Verbindungszeichenfolge für das Suchergebnis unverändert bleibt, ist ein Fehler aufgetreten, und die Anwendung kann **SQLGetDiagRec** aufrufen, um SQLSTATE für Suchzeitfehler zurückzugeben. Dadurch kann die Anwendung das Attribut korrigieren und die Suche fortsetzen.  
  
 Eine Anwendung kann den Suchvorgang jederzeit beenden, indem sie **SQLDisconnect aufruft.** Der Treiber beendet alle ausstehenden Verbindungen und gibt die Verbindung in einen nicht verbundenen Zustand zurück.  
  
 Wenn asynchrone Vorgänge für das Verbindungshandle aktiviert sind, gibt **SQLBrowseConnect** möglicherweise auch SQL_STILL_EXECUTING zurück. Wenn sie SQL_NEED_DATA zurückgibt, muss eine Anwendung **SQLDisconnect** verwenden, um den Suchvorgang abzubrechen. Wenn **SQLBrowseConnect** SQL_STILL_EXECUTING zurückgibt, sollte eine Anwendung **SQLCancelHandle** verwenden, um den laufenden Vorgang abzubrechen. Aufrufen von **SQLCancelHandle,** nachdem die Funktion zurückgegeben wird, SQL_NEED_DATA keine Auswirkungen hat.  
  
 Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md).  
  
 Wenn ein Treiber **SQLBrowseConnect**unterstützt, muss der Schlüsselwortabschnitt driver in den Systeminformationen für den Treiber das **Schlüsselwort ConnectFunctions** mit dem dritten Zeichensatz auf "Y" enthalten.  
  
## <a name="code-example"></a>Codebeispiel  
  
> [!NOTE]  
>  Wenn Sie eine Verbindung zu einem Datenquellenanbieter herstellen, `Trusted_Connection=yes` der die Windows-Authentifizierung unterstützt, sollten Sie anstelle von Benutzer-ID- und Kennwortinformationen in der Verbindungszeichenfolge angeben.  
  
 Im folgenden Beispiel ruft eine Anwendung **SQLBrowseConnect** wiederholt auf. Jedes Mal, **wenn SQLBrowseConnect** SQL_NEED_DATA zurückgibt, gibt \*es Informationen über die Daten zurück, die es in *OutConnectionString*benötigt. Die Anwendung übergibt *OutConnectionString* an ihre Routine **GetUserInput** (nicht angezeigt). **GetUserInput** analysiert die Informationen, erstellt und zeigt ein Dialogfeld an \*und gibt die vom Benutzer in *InConnectionString*eingegebenen Informationen zurück. Die Anwendung übergibt die Benutzerinformationen an den Treiber beim nächsten Aufruf von **SQLBrowseConnect**. Nachdem die Anwendung alle erforderlichen Informationen für den Treiber bereitgestellt hat, um eine Verbindung mit der Datenquelle herzustellen, gibt **SQLBrowseConnect** SQL_SUCCESS zurück, und die Anwendung wird fortgesetzt.  
  
 Ein detaillierteres Beispiel für die Verbindung mit einem SQL Server-Treiber durch Aufrufen von **SQLBrowseConnect**finden Sie unter [SQL Server Browsing Example](../../../odbc/reference/develop-app/sql-server-browsing-example.md).  
  
 Um z. B. eine Verbindung mit der Datenquelle Sales herzustellen, können die folgenden Aktionen auftreten. Zunächst übergibt die Anwendung die folgende Zeichenfolge an **SQLBrowseConnect:**  
  
```  
"DSN=Sales"  
```  
  
 Der Treiber-Manager lädt den Treiber, der der Datenquelle Sales zugeordnet ist. Anschließend wird die **SQLBrowseConnect-Funktion** des Treibers mit den gleichen Argumenten aufgesendet, die er von der Anwendung erhalten hat. Der Treiber gibt die folgende Zeichenfolge in **OutConnectionString*zurück:  
  
```  
"HOST:Server={red,blue,green};UID:ID=?;PWD:Password=?"  
```  
  
 Die Anwendung übergibt diese Zeichenfolge an die **GetUserInput-Routine,** die ein Dialogfeld erstellt, in dem der Benutzer aufgefordert wird, den roten, blauen oder grünen Server auszuwählen und eine Benutzer-ID und ein Kennwort einzugeben. Die Routine übergibt die folgenden \*benutzerdefinierten Informationen in *InConnectionString*zurück, die die Anwendung an **SQLBrowseConnect**übergibt:  
  
```  
"HOST=red;UID=Smith;PWD=Sesame"  
```  
  
 **SQLBrowseConnect** verwendet diese Informationen, um eine Verbindung mit dem roten Server als Smith mit dem Kennwort Sesame herzustellen, und gibt dann die folgende Zeichenfolge in **OutConnectionString*zurück:  
  
```  
"*DATABASE:Database={SalesEmployees,SalesGoals,SalesOrders}"  
```  
  
 Die Anwendung übergibt diese Zeichenfolge an die **GetUserInput-Routine,** die ein Dialogfeld erstellt, in dem der Benutzer aufgefordert wird, eine Datenbank auszuwählen. Der Benutzer wählt empdata aus, und die Anwendung ruft **SQLBrowseConnect** ein letztes Mal mit dieser Zeichenfolge auf:  
  
```  
"DATABASE=SalesOrders"  
```  
  
 Dies ist die letzte Information, die der Treiber benötigt, um eine Verbindung mit der Datenquelle herzustellen. **SQLBrowseConnect** gibt SQL_SUCCESS zurück, und **OutConnectionString* enthält die abgeschlossene Verbindungszeichenfolge:  
  
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
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuweisen eines Verbindungshandles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Trennen der Verbindung zu einer Datenquelle|[SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungszeichenfolge oder ein Dialogfeld|[SQLDriveConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Zurückgeben von Treiberbeschreibungen und -attributen|[SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Befreien eines Verbindungsgriffs|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
