---
title: SQLBrowseConnect-Funktion | Microsoft-Dokumentation
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
apitype: dllExport
f1_keywords:
- SQLBrowseConnect
helpviewer_keywords:
- SQLBrowseConnect function [ODBC]
ms.assetid: b7f1be66-e6c7-4790-88ec-62b7662103c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d86f2aa373b120d2ecf1ea47b021b327fc57dc21
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651968"
---
# <a name="sqlbrowseconnect-function"></a>SQLBrowseConnect-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLBrowseConnect** unterstützt eine iterative Methode zum Erkennen und auflisten, die Attribute und Attributwerte für die Verbindung mit einer Datenquelle erforderlich sind. Jeder Aufruf von **SQLBrowseConnect** aufeinander folgenden Steuerungsebenen Attribute und Attributwerte zurückgibt. Wenn alle Ebenen wurde aufgelistet, eine Verbindung mit der Datenquelle abgeschlossen ist und eine vollständige Verbindungszeichenfolge, indem zurückgegeben wird **SQLBrowseConnect**. Ein Rückgabecode von SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO gibt an, dass alle Verbindungsinformationen angegeben wurde und die Anwendung jetzt mit der Datenquelle verbunden ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 [Eingabe] Durchsuchen Sie die Verbindungszeichenfolge für die Anforderung (finden Sie unter "*InConnectionString* Argument" in "Kommentare").  
  
 *StringLength1*  
 [Eingabe] Länge der **InConnectionString* in Zeichen.  
  
 *OutConnectionString*  
 [Ausgabe] Zeiger auf einen Puffer aus Zeichen in dem die Verbindungszeichenfolge der durchsuchen-Ergebnis zurückgegeben (finden Sie unter "*OutConnectionString* Argument" in "Kommentare").  
  
 Wenn *OutConnectionString* NULL ist, *StringLength2Ptr* gibt die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer zurückgegeben verweist *OutConnectionString*.  
  
 *BufferLength*  
 [Eingabe] Länge in Zeichen, der die **OutConnectionString* Puffer.  
  
 *StringLength2Ptr*  
 [Ausgabe] Die Gesamtzahl der Zeichen (Null-Terminierung) zur Verfügung, die in zurückgegeben \* *OutConnectionString*. Wenn die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als oder gleich ist *Pufferlänge*, die Verbindungszeichenfolge in \* *OutConnectionString* auf abgeschnitten  *BufferLength* abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLBrowseConnect** gibt SQL_ERROR, SQL_SUCCESS_WITH_INFO oder SQL_NEED_DATA zurückgegeben, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und ein *Handle des ConnectionHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLBrowseConnect** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Puffer \* *OutConnectionString* nicht groß genug war, um die Verbindungszeichenfolge für den gesamten durchsuchen Ergebnis und zurückzugeben, damit die Zeichenfolge abgeschnitten wurde. Der Puffer **StringLength2Ptr* enthält die Länge der Ergebniszeichenfolge Verbindung den ungekürzten durchsuchen. (Die Funktion wird SQL_NEED_DATA zurückgegeben.)|  
|01S00|Ungültiges Attribut der Verbindungszeichenfolge|In der Verbindungszeichenfolge der durchsuchen-Anforderung wurde ein ungültiges Attribut-Schlüsselwort angegeben (*InConnectionString*). (Die Funktion wird SQL_NEED_DATA zurückgegeben.)<br /><br /> Ein Schlüsselwort wurde angegeben, in der Verbindungszeichenfolge der durchsuchen-Anforderung (*InConnectionString*), die gilt nicht für der aktuellen Verbindungsebene. (Die Funktion wird SQL_NEED_DATA zurückgegeben.)|  
|01S02|Der Wert wurde geändert|Der Treiber nicht den angegebenen Wert, der die *ValuePtr* -Argument in **SQLSetConnectAttr** und einen ähnlichen Wert ersetzt. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08001|Client kann keine Verbindung herstellen.|Der Treiber konnte nicht zum Herstellen einer Verbindung mit der Datenquelle.|  
|08002|Name der Verbindung verwendet|(DM) hatte bereits die angegebene Verbindung zum Herstellen einer Verbindung mit einer Datenquelle verwendet, und die Verbindung geöffnet wurde.|  
|08004|Der Server wies die Verbindung|Die Datenquelle die Herstellung der Verbindung festzulegenden Gründen zurückgewiesen Implementierung definiert.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, zu der der Treiber versucht hat, die Verbindung, konnte nicht vor der Verarbeitung für die Funktion abgeschlossen.|  
|28000|Ungültige Autorisierungsangabe|Fordern Sie die Benutzer-ID oder der autorisierungszeichenfolge oder beides, navigieren Sie im angegebenen Verbindungszeichenfolge (*InConnectionString*), von der Datenquelle definierte Einschränkungen verletzt.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber-Managers (DM) konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.<br /><br /> Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Ein asynchroner Vorgang wurde abgebrochen, durch den Aufruf [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md). Klicken Sie dann die ursprüngliche Funktion wurde erneut aufgerufen auf die *ConnectionHandle*.<br /><br /> Ein Vorgang wurde abgebrochen, durch den Aufruf **SQLCancelHandle** auf die *ConnectionHandle* von einem anderen Thread in einer multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *ConnectionHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) für Argument angegebene Wert *StringLength1* kleiner als 0 und nicht wurde SQL_NTS gleich.<br /><br /> (DM) für Argument angegebene Wert *Pufferlänge* war kleiner als 0.|  
|HY114|Verbindung auf asynchrone Ausführung der unterstützt Treiber nicht.|(DM) aktiviert die Anwendung den asynchronen Vorgang auf dem Verbindungshandle vor dem Herstellen der Verbindung. Allerdings unterstützt der Treiber nicht asynchronen Vorgang für Verbindungshandle.|  
|HYT00|Timeout abgelaufen|Des anmeldungstimeouts ist abgelaufen, bevor Sie die Verbindung mit der Datenquelle abgeschlossen. Das Timeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber, die der angegebene Name der Datenquelle für die Funktion nicht unterstützt.|  
|IM002|Datenquelle wurde nicht gefunden und kein Standardtreiber angegeben|(DM) der Name der Datenquelle angegeben, in der Verbindungszeichenfolge der durchsuchen-Anforderung (*InConnectionString*) wurde nicht gefunden, in den Systeminformationen, noch gab es eine Standard-Treiber-Spezifikation.<br /><br /> (DM) ODBC-Quelle und Standard-Treiber Dateninformationen wurde nicht gefunden werden, in den Systeminformationen.|  
|IM003|Angegebene Treiber konnte nicht geladen werden|(DM) der Treiber aufgeführt, die in der Angabe der Datenquelle in den Systeminformationen oder gemäß der **Treiber** Schlüsselwort wurde nicht gefunden oder konnte nicht in einem anderen Grund geladen werden.|  
|IM004|Der Treiber **SQLAllocHandle** auf SQL_HANDLE _ENV Fehler|(DM) während der **SQLBrowseConnect**, der Treiber-Manager Namens des Treibers **SQLAllocHandle** -Funktion mit einem *HandleType* SQL_HANDLE_ENV und der Treiber zurückgegeben ein Fehler.|  
|IM005|Der Treiber **SQLAllocHandle** auf SQL_HANDLE_DBC auf Fehler|(DM) während der **SQLBrowseConnect**, der Treiber-Manager Namens des Treibers **SQLAllocHandle** -Funktion mit einem *HandleType* SQL_HANDLE_DBC auf, und der Treiber zurückgegeben ein Fehler.|  
|IM006|Der Treiber **SQLSetConnectAttr** Fehler|(DM) während der **SQLBrowseConnect**, der Treiber-Manager Namens des Treibers **SQLSetConnectAttr** -Funktion und der Treiber hat einen Fehler zurückgegeben.|  
|IM009|Kann nicht geladen werden Konvertierungs-DLL|Der Treiber konnte den Konvertierungs-DLL zu laden, die für die Datenquelle oder für die Verbindung angegeben wurde.|  
|IM010|Der Datenquellenname ist zu lang.|(DM) war der Attributwert für das DSN-Schlüsselwort SQL_MAX_DSN_LENGTH Zeichen überschreitet.|  
|IM011|Der Treibername ist zu lang.|(DM) war der Attributwert für das DRIVER-Schlüsselwort, die länger als 255 Zeichen lang sein.|  
|IM012|Syntaxfehler für DRIVER-Schlüsselwort|(DM) das Schlüsselwort-Wert-Paar für das DRIVER-Schlüsselwort enthalten einen Syntaxfehler.|  
|IM014|Der angegebene DSN enthält einen architekturkonflikt zwischen dem Treiber und der Anwendung|(DM)-32-Bit-Anwendung verwendet einen DSN Herstellen einer Verbindung mit einer 64-Bit-Treiber. oder umgekehrt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
|S1118|Asynchrone Benachrichtigung unterstützt Treiber nicht.|Wenn der Treiber die asynchrone Benachrichtigung nicht unterstützt, können nicht Sie SQL_ATTR_ASYNC_DBC_EVENT oder SQL_ATTR_ASYNC_DBC_RETCODE_PTR festlegen.|  
  
## <a name="inconnectionstring-argument"></a>InConnectionString-Argument  
 Eine Verbindungszeichenfolge der durchsuchen-Anforderung hat die folgende Syntax:  
  
 *Verbindungszeichenfolge* :: = *Attribut*[`;`] &#124; *Attribut* `;` *Verbindungszeichenfolge*;<br>
 *Attribut* :: = *-Schlüsselwort*`=`*Attribut / Wert* &#124; `DRIVER=`[`{`]*Attribut / Wert-*[`}`]<br>
 *Attribut-Schlüsselwort* :: = `DSN` &#124; `UID` &#124; `PWD` &#124; *-Treiber-definierten-Attribut-Schlüsselwort*<br>
 *Attribut-Wert* :: = *-Zeichenfolge*<br>
 *Treiber-definierten-Attribut-Schlüsselwort* :: = *Bezeichner*<br>
  
 in denen *zechenfolgen* ist NULL oder mehr Zeichen *Bezeichner* verfügt über eine oder mehrere Zeichen *-Schlüsselwort* wird nicht beachtet; *Attribut / Wert* möglicherweise beachtet werden soll; und der Wert von der **DSN** Schlüsselwort besteht nicht ausschließlich aus Leerzeichen. Aufgrund Verbindung und Initialisierungsdateien Datei Grammatik, Schlüsselwörter und Attribut Werte, die die Zeichen enthalten **[]{}();? \*=! @** sollte vermieden werden. Aufgrund der Grammatik in den Systeminformationen, Schlüsselwörter und Namen von Datenquellen können nicht den umgekehrten Schrägstrich enthalten (\\) Zeichen. Für eine ODBC-2. *x* Treiber, geschweifte Klammern sind erforderlich, um den Attributwert für das DRIVER-Schlüsselwort.  
  
 Wenn keine Schlüsselwörter in der Verbindungszeichenfolge der durchsuchen-Anforderung wiederholt werden, verwendet der Treiber den Wert mit dem ersten Vorkommen des Schlüsselworts. Wenn die **DSN** und **Treiber** Schlüsselwörter in die gleiche Verbindungszeichenfolge für den Durchsuchen-Anforderung enthalten sind, die Treiber-Manager und Treiber verwenden, welches Schlüsselwort an erster Stelle steht.  
  
 Weitere Informationen dazu, wie eine Anwendung eine Datenquelle oder Treiber auswählt, finden Sie unter [Auswählen einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
## <a name="outconnectionstring-argument"></a>OutConnectionString-Argument  
 Die Verbindungszeichenfolge der durchsuchen-Ergebnis ist eine Liste der Verbindungsattribute. Ein Verbindungsattribut besteht aus einem Attribut-Schlüsselwort und Wert eines entsprechenden. Die Verbindungszeichenfolge der durchsuchen-Ergebnis weist die folgende Syntax:  
  
 *Verbindungszeichenfolge* :: = *Attribut*[`;`] &#124; *Attribut* `;` *Verbindungszeichenfolgen*<br>
 *Attribut* :: = [`*`]*-Schlüsselwort*`=`*Attribut / Wert*<br>
 *Attribut-Schlüsselwort* :: = *ODBC-Attribut-Schlüsselwort* &#124; *-Treiber-definierten-Attribut-Schlüsselwort*<br>
 *ODBC-Attribut-Schlüsselwort* = {`UID` &#124; `PWD`} [`:`*lokalisierter Bezeichner*] *-definierten-Attribut-Schlüsselwort Driver* :: = *Bezeichner*[`:`*lokalisierter Bezeichner*] *Attribut / Wert* :: = `{` *Attribut-Wert-Liste* `}` &#124; `?` (Die geschweiften Klammern sind literal; sie werden vom Treiber zurückgegebene.)<br>
 *attribute-value-list* ::= *character-string* [`:`*localized-character string*] &#124; *character-string* [`:`*localized-character string*] `,` *attribute-value-list*<br>
  
 in denen *zechenfolgen* und *lokalisierte Zeichenfolgen* haben NULL oder mehr Zeichen *Bezeichner* und *lokalisierter Bezeichner* haben Sie eine oder mehrere Zeichen *-Schlüsselwort* wird nicht beachtet; und *Attribut / Wert* möglicherweise Groß-/Kleinschreibung beachtet. Aufgrund der Verbindung Zeichenfolge und die Initialisierung Datei Grammatik, Schlüsselwörter, lokalisierte Bezeichner und Attributwerte, die die Zeichen enthalten **[]{}();? \*=! @** sollte vermieden werden. Aufgrund der Grammatik in den Systeminformationen, Schlüsselwörter und Namen von Datenquellen können nicht den umgekehrten Schrägstrich enthalten (\\) Zeichen.  
  
 Die Verbindungszeichenfolgensyntax zum Durchsuchen von Ergebnis, wird anhand der folgenden semantischen Regeln verwendet:  
  
-   Wenn ein Sternchen (\*) vorangestellt ist ein *-Schlüsselwort*, *Attribut* ist optional und kann ausgelassen werden, in dem nächsten Aufruf von **SQLBrowseConnect**.  
  
-   Die Attribut-Schlüsselwörter **UID** und **PWD** haben dieselbe Bedeutung, gemäß **SQLDriverConnect**.  
  
-   Ein *-definierten-Attribut-Schlüsselwort Driver* benennt die Art des Attributs für den Attributwert angegeben werden kann. Beispielsweise ist es möglicherweise **SERVER**, **Datenbank**, **HOST**, oder **DBMS**.  
  
-   *ODBC-Attribut-Schlüsselwörter* und *-Treiber-definierte-Attribut-Schlüsselwörter* enthalten eine lokalisierte oder benutzerfreundliche Version des Schlüsselworts. Dies kann von Anwendungen als eine Bezeichnung in einem Dialogfeld verwendet werden. Allerdings **UID**, **PWD**, oder die *Bezeichner* allein muss verwendet werden, wenn eine Zeichenfolge der durchsuchen-Anforderung an den Treiber übergeben.  
  
-   Die {*Attribut-Wert-Liste*} ist eine Enumeration von tatsächlichen Werten für das entsprechende gültige *-Schlüsselwort*. Beachten Sie, dass die geschweiften Klammern ({}) eine Liste mit Auswahlmöglichkeiten geben nicht an; sie werden vom Treiber zurückgegeben. Beispielsweise kann es eine Liste der Namen der Server oder eine Liste der Datenbanknamen sein.  
  
-   Wenn die *Attribut / Wert* ist ein einzelnes Question Mark (?), ein einzelnen Wert entspricht der *-Schlüsselwort*. Z. B. UID = JohnS; PWD = Sesame.  
  
-   Jeder Aufruf von **SQLBrowseConnect** gibt nur die Informationen, die erforderlich sind, um die nächste Ebene von den Verbindungsprozess zu erfüllen. Der Treiber ordnet dem Verbindungshandle Zustandsinformationen, damit der Kontext immer bei jedem Aufruf bestimmt werden kann.  
  
## <a name="using-sqlbrowseconnect"></a>SQLBrowseConnect verwenden  
 **SQLBrowseConnect** erfordert eine zugeordnete Verbindung. Der Treiber-Manager lädt den Treiber, die angegeben wurde oder, der in der Verbindungszeichenfolge der anfänglichen durchsuchen-Anforderung angegebene Datenquellenname entspricht; Informationen, wenn dies geschieht, finden Sie im Abschnitt "Kommentare" im [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md). Der Treiber kann während der der durchsuchen-Prozess eine Verbindung mit der Datenquelle herstellen. Wenn **SQLBrowseConnect** gibt SQL_ERROR zurück, ausstehende Verbindungen werden beendet und die Verbindung wird in einem nicht verbundenen Zustand zurückgegeben.  
  
> [!NOTE]  
>  **SQLBrowseConnect** Verbindungspooling nicht unterstützt. Wenn **SQLBrowseConnect** wird aufgerufen, während das Verbindungspooling aktiviert ist, SQLSTATE HY000 (Allgemeine Fehler) zurückgegeben.  
  
 Wenn **SQLBrowseConnect** heißt zum ersten Mal bei einer Verbindung, die Verbindungszeichenfolge der durchsuchen-Anforderung enthalten muss die **DSN** Schlüsselwort oder **Treiber** Schlüsselwort. Wenn die Verbindungszeichenfolge der durchsuchen-Anforderung enthält die **DSN** Schlüsselwort, das der Treiber-Manager sucht nach der Angabe einer entsprechenden Datenquelle in den Systeminformationen:  
  
-   Wenn der Treiber-Manager der Angabe der entsprechenden Datenquelle gefunden wird, lädt er die zugehörige Treiber-DLL; der Treiber kann Informationen über die Datenquelle aus der Systeminformationen abrufen.  
  
-   Wenn der Treiber-Manager der Angabe der zugehörigen Datenquelle nicht finden kann, sucht nach der Angabe der standardmäßigen Datenquelle und lädt die zugehörige Treiber-DLL; der Treiber kann Informationen über die Standarddatenquelle aus den Systeminformationen abrufen. "DEFAULT" werden für den DSN an den Treiber übergeben.  
  
-   Wenn der Treiber-Manager wurde der Angabe der zugehörigen Datenquelle nicht gefunden, und es keine standardmäßige datenquellenspezifikation gibt, wird SQL_ERROR mit SQLSTATE IM002 (Datenquelle wurde nicht gefunden und kein Standardtreiber angegeben).  
  
 Wenn die Verbindungszeichenfolge der durchsuchen-Anforderung enthält die **Treiber** Schlüsselwort, das der Treiber-Manager lädt die angegebenen Treiber; er versucht nicht, eine Datenquelle in den Systeminformationen zu suchen. Da die **Treiber** Schlüsselwort keine Informationen aus der Systeminformationen verwendet, der Treiber muss genügend Schlüsselwörter definieren, sodass ein Treibers eine Verbindung mit einer Datenquelle, die nur die Informationen in den Verbindungszeichenfolgen der durchsuchen-Anforderung mit herstellen kann.  
  
 Bei jedem Aufruf **SQLBrowseConnect**, die Anwendung die Attributwerte für die Verbindung angibt, in der Verbindungszeichenfolge der durchsuchen-Anforderung. Der Treiber gibt aufeinander folgenden Steuerungsebenen Attribute und Attributwerte in der Verbindungszeichenfolge der durchsuchen-Ergebnis zurück. Es wird SQL_NEED_DATA zurückgegeben, solange es Verbindungsattribute, die noch nicht in der Verbindungszeichenfolge der durchsuchen-Anforderung aufgelistet wurden. Die Anwendung verwendet den Inhalt der Ergebniszeichenfolge Verbindung navigieren Sie zum Erstellen der Verbindungszeichenfolge des suchen-Anforderung für den nächsten Aufruf von **SQLBrowseConnect**. Alle erforderlichen Attribute (die nicht durch ein Sternchen in vorangestellt der *OutConnectionString* Argument) enthalten sein müssen, in dem nächsten Aufruf von **SQLBrowseConnect**. Beachten Sie, dass die Anwendung den Inhalt des vorherigen durchsuchen-Ergebnis-Verbindungszeichenfolgen verwenden kann, wenn die aktuelle Verbindungszeichenfolge für den Durchsuchen-Anforderung zu erstellen. Das heißt, kann nicht es unterschiedliche Werte für Attribute in der vorherigen Ebenen festgelegt angeben.  
  
 Wenn alle Ebenen der Verbindung und die zugehörigen Attribute aufgelistet wurden, der Treiber gibt SQL_SUCCESS zurück, die Verbindung mit der Datenquelle abgeschlossen ist und eine vollständigen Verbindungszeichenfolge wird an die Anwendung zurückgegeben. Die Verbindungszeichenfolge ist die Verwendung in Verbindung mit **SQLDriverConnect**, mit der Option SQL_DRIVER_NOPROMPT zu, um eine andere Verbindung herzustellen. Die vollständige Verbindungszeichenfolge kann nicht verwendet werden, in einen anderen Aufruf **SQLBrowseConnect**, aber wenn **SQLBrowseConnect** erneut aufrufen würden, die gesamte Sequenz von Aufrufen musste wiederholt werden.  
  
 **SQLBrowseConnect** auch wird SQL_NEED_DATA zurückgegeben, wenn während des Prozesses durchsuchen; z. B. einen ungültigen Kennwort- oder Schlüsselwort der von der Anwendung bereitgestellten wiederherstellbar,-Fehler vorliegen. Wenn SQL_NEED_DATA zurückgegeben und die Verbindungszeichenfolge der durchsuchen-Ergebnis bleibt unverändert und wird ein Fehler ist aufgetreten und die Anwendung aufrufen kann **SQLGetDiagRec** den SQLSTATE für Durchsuchen-Time-Fehler zurückgegeben. Dies ermöglicht die Anwendung so korrigieren Sie das Attribut und weiterhin die Schaltfläche zum Durchsuchen.  
  
 Eine Anwendung kann den Durchsuchen-Prozess zu einem beliebigen Zeitpunkt beenden, durch den Aufruf **SQLDisconnect**. Der Treiber alle ausstehenden Verbindungen beendet und die Verbindung zu einem nicht verbundenen Zustand zurückgegeben.  
  
 Wenn asynchrone Vorgänge, auf dem Verbindungshandle aktiviert sind **SQLBrowseConnect** möglicherweise auch SQL_STILL_EXECUTING zurück. Wenn SQL_NEED_DATA zurückgegeben wird, muss eine Anwendung verwenden **SQLDisconnect** zum Abbrechen des Prozesses durchsuchen. Wenn **SQLBrowseConnect** gibt SQL_STILL_EXECUTING, eine Anwendung verwendet soll **SQLCancelHandle** , den aktuellen Vorgang abzubrechen. Aufrufen von **SQLCancelHandle** , nachdem die Funktion gibt SQL_NEED_DATA hat keine Auswirkungen.  
  
 Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md).  
  
 Wenn ein Treiber unterstützt **SQLBrowseConnect**, Abschnitt Schlüsselwort Treiber in den Systeminformationen für den Treiber darf die **ConnectFunctions** Schlüsselwort mit dem dritten Zeichen festgelegt wird, in "Y".  
  
## <a name="code-example"></a>Codebeispiel  
  
> [!NOTE]  
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben `Trusted_Connection=yes` anstelle von Benutzer-ID und Kennwort-Informationen in der Verbindungszeichenfolge.  
  
 Im folgenden Beispiel eine Anwendung ruft **SQLBrowseConnect** wiederholt. Jedes Mal **SQLBrowseConnect** wird SQL_NEED_DATA zurückgegeben, übergibt Back Informationen zu den Daten, es in muss \* *OutConnectionString*. Die Anwendung leitet *OutConnectionString* an die Routine **GetUserInput** (nicht dargestellt). **GetUserInput** die Informationen analysiert, erstellt und zeigt ein Dialogfeld an und gibt zurück, die vom Benutzer im eingegebenen Informationen \* *InConnectionString*. Die Anwendung übergibt die Informationen des Benutzers an den Treiber in den nächsten Aufruf von **SQLBrowseConnect**. Nachdem die Anwendung alle erforderlichen Informationen für den Treiber für die Verbindung mit der Datenquelle angegeben hat **SQLBrowseConnect** gibt SQL_SUCCESS zurück, und die Anwendung fortgesetzt wird.  
  
 Ein ausführlicheres Beispiel zur verbindungsherstellung mit einer SQL Server-Treiber, durch den Aufruf **SQLBrowseConnect**, finden Sie unter [SQL Server-Suchbeispiel](../../../odbc/reference/develop-app/sql-server-browsing-example.md).  
  
 Um auf die Daten zu Quelle Sales verbinden, können z. B. die folgenden Aktionen ausgeführt. Die Anwendung übergibt zuerst die folgende Zeichenfolge, die **SQLBrowseConnect**:  
  
```  
"DSN=Sales"  
```  
  
 Der Treiber-Manager lädt den Treiber die Datenquelle Sales zugeordnet. Es ruft dann die vom Treibers **SQLBrowseConnect** -Funktion mit den gleichen Argumenten, die sie von der Anwendung empfangen. Gibt die folgende Zeichenfolge in der Treiber **OutConnectionString*:  
  
```  
"HOST:Server={red,blue,green};UID:ID=?;PWD:Password=?"  
```  
  
 Die Anwendung übergibt diese Zeichenfolge der **GetUserInput** routinemäßig ausgeführt werden, die ein Dialogfeld, das erstellt fordert den Benutzer zum Auswählen des Servers Rot, Blau oder Grün und eine Benutzer-ID und ein Kennwort eingeben. Der routinemäßige übergibt die folgende benutzerdefinierten Informationen erneut \* *InConnectionString*, die an die Anwendung übergibt **SQLBrowseConnect**:  
  
```  
"HOST=red;UID=Smith;PWD=Sesame"  
```  
  
 **SQLBrowseConnect** verwendet diese Informationen zum Verbinden mit dem roten Server als Smith mit dem Kennwort Sesame werden soll, und gibt anschließend die folgende Zeichenfolge **OutConnectionString*:  
  
```  
"*DATABASE:Database={SalesEmployees,SalesGoals,SalesOrders}"  
```  
  
 Die Anwendung übergibt diese Zeichenfolge der **GetUserInput** routinemäßig ausgeführt werden, die ein Dialogfeld, das erstellt fordert den Benutzer auf eine Datenbank auszuwählen. Der Benutzer wählt Empdata und die Anwendung ruft **SQLBrowseConnect** ein letztes Mal mit dieser Zeichenfolge:  
  
```  
"DATABASE=SalesOrders"  
```  
  
 Dies ist der letzte Teil der Informationen, die der Treiber, die eine Verbindung mit der Datenquelle herstellen muss. **SQLBrowseConnect** gibt SQL_SUCCESS zurück, und **OutConnectionString* vervollständigte Verbindungszeichenfolge enthält:  
  
```  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Zuordnen eines Verbindungshandles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Trennen von einer Datenquelle|[SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle mit einer Zeichenfolge oder eines Dialogfelds Verbindungsdialogfeld|[SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Zurückgeben von Beschreibungen der Treiber und Attribute|[SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Freigeben eines Verbindungshandles|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
