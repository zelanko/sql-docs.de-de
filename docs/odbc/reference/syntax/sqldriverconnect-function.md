---
title: SQLDriverConnect-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDriverConnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDriverConnect
helpviewer_keywords:
- SQLDriverConnect function [ODBC]
ms.assetid: e299be1d-5c74-4ede-b6a3-430eb189134f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d254fce8d7765c6248c6e060f2a225f595f804f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597175"
---
# <a name="sqldriverconnect-function"></a>SQLDriveConnect-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLDriverConnect** ist eine Alternative zum **SQLConnect**. Datenquellen, die als Argumente in drei weitere Verbindungsinformationen erfordern unterstützt **SQLConnect**, Dialogfelder, um die Benutzer alle Verbindungsinformationen, und Datenquellen, die nicht im System definiert sind Informationen.  
  
 **SQLDriverConnect** bietet die folgenden Verbindungsattribute:  
  
-   Herstellen einer Verbindungs mit einer Verbindungszeichenfolge mit dem-Datenquellennamen, eine oder mehrere Benutzer-IDs, eine oder mehrere Kennwörter und andere Informationen, die erforderlich sind von der Datenquelle an.  
  
-   Herstellen einer Verbindungs mit einem Teil der Verbindungszeichenfolge oder keine zusätzlichen Informationen; der Treiber-Manager und der Treiber können jede in diesem Fall den Benutzer zur Verbindung auffordern.  
  
-   Herstellen einer Verbindungs mit einer Datenquelle, die nicht in den Systeminformationen definiert ist. Wenn die Anwendung eine Teilverbindungszeichenfolge bereitstellt, kann der Treiber den Benutzer zur Verbindung auffordern.  
  
-   Herstellen einer Verbindungs mit einer Datenquelle mithilfe einer Verbindungszeichenfolge, die aus den Informationen in einer DSN-Datei erstellt.  
  
 Nachdem eine Verbindung hergestellt wurde, **SQLDriverConnect** gibt die vervollständigte Verbindungszeichenfolge zurück. Die Anwendung kann diese Zeichenfolge für die spätere verbindungsanforderungen verwenden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLDriverConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLHWND         WindowHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr,  
     SQLUSMALLINT    DriverCompletion);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *WindowHandle*  
 [Eingabe] Das Fensterhandle. Leitet die Anwendung kann das Handle des übergeordneten Fensters, falls zutreffend, oder ein null-Zeiger, wenn entweder das Fensterhandle ist nicht anwendbar oder **SQLDriverConnect** werden keine Dialogfelder angezeigt.  
  
 *InConnectionString*  
 [Eingabe] Eine vollständige Verbindungszeichenfolge (siehe die Syntax in "Kommentare"), ein Teil der Verbindungszeichenfolge oder eine leere Zeichenfolge.  
  
 *StringLength1*  
 [Eingabe] Länge der **InConnectionString*, in Zeichen, wenn die Zeichenfolge Unicode oder Bytes ist, wenn die Zeichenfolge ANSI oder DBCS ist.  
  
 *OutConnectionString*  
 [Ausgabe] Zeiger auf einen Puffer für die vollständige Verbindungszeichenfolge. Bei erfolgreicher Verbindung auf die Datenquelle enthält dieser Puffer vervollständigte Verbindungszeichenfolge. Anwendungen sollten mindestens 1.024 Zeichen für diesen Puffer zuordnen.  
  
 Wenn *OutConnectionString* NULL ist, *StringLength2Ptr* gibt die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer zurückgegeben verweist *OutConnectionString*.  
  
 *BufferLength*  
 [Eingabe] Länge der **OutConnectionString* Puffers in Zeichen.  
  
 *StringLength2Ptr*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe der Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen) zur Verfügung, die in zurückgegeben \* *OutConnectionString*. Die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als oder gleich *Pufferlänge*, wird die Verbindungszeichenfolge zumeist im abgeschlossen \* *OutConnectionString* wird abgeschnitten, um  *BufferLength* abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
 *DriverCompletion*  
 [Eingabe] Flag, die angibt, ob der Treiber-Manager oder die Treiber für Weitere Informationen zur Verbindung auffordern muss:  
  
 SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, sql_driver_complete_required lautet oder SQL_DRIVER_NOPROMPT.  
  
 (Weitere Informationen finden Sie auf "Kommentare".)  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA zurückgibt, wird SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDriverConnect** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit eine *fHandleType*SQL_HANDLE_DBC auf, und ein *hHandle* von *ConnectionHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLDriverConnect** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Puffer \* *OutConnectionString* nicht groß genug war, um die komplette Verbindungszeichenfolge und zurückzugeben, damit die Zeichenfolge abgeschnitten wurde. Die Länge der Verbindungszeichenfolge den ungekürzten wird zurückgegeben, **StringLength2Ptr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S00|Ungültiges Attribut der Verbindungszeichenfolge|Ein ungültiges Attribut-Schlüsselwort in der Verbindungszeichenfolge angegeben wurde (*InConnectionString*), aber der Treiber wurde trotzdem eine Verbindung mit der Datenquelle herstellen können. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber nicht den angegebenen Wert verweist die *ValuePtr* -Argument in **SQLSetConnectAttr** und einen ähnlichen Wert ersetzt. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S08|Fehler beim Speichern der Datei-DSN|Die Zeichenfolge in  *\*InConnectionString* enthalten eine **FILEDSN** -Schlüsselwort, aber die DSN-Datei wurde nicht gespeichert. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S09|Ungültiges Schlüsselwort|(DM) die Zeichenfolge in  *\*InConnectionString* enthalten eine **SAVEFILE** Schlüsselwort, nicht jedoch eine **Treiber** oder **FILEDSN** Schlüsselwort. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08001|Client kann keine Verbindung herstellen.|Der Treiber konnte nicht zum Herstellen einer Verbindung mit der Datenquelle.|  
|08002|Name der Verbindung verwendet|(DM) der angegebenen *ConnectionHandle* hatte bereits zum Herstellen einer Verbindung mit einer Datenquelle verwendet wurde und die Verbindung weiterhin geöffnet wurde.|  
|08004|Der Server wies die Verbindung|Die Datenquelle die Herstellung der Verbindung festzulegenden Gründen zurückgewiesen Implementierung definiert.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die der Treiber versucht wurde, eine Verbindung herstellen, die vor dem Fehler bei der **SQLDriverConnect** Verarbeitung von Funktion abgeschlossen.|  
|28000|Ungültige Autorisierungsangabe|Die Benutzer-ID oder der autorisierungszeichenfolge oder beides als in der Verbindungszeichenfolge angegebenen (*InConnectionString*), von der Datenquelle definierte Einschränkungen verletzt.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*SzMessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY000|Allgemeiner Fehler: Ungültige Datei-Dsn|(DM) die Zeichenfolge in **InConnectionString* ein Datei-DSN-Schlüsselwort enthalten, aber der Name der Datei ".DSN" wurde nicht gefunden.|  
|HY000|Allgemeiner Fehler: kann nicht erstellt werden Dateipuffer|(DM) die Zeichenfolge in **InConnectionString* ein Datei-DSN-Schlüsselwort enthalten, aber die DSN-Datei wurde nicht gelesen werden.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber-Manager wurde kein Speicher erforderlich, um die Unterstützung der Ausführung oder den Abschluss der **SQLDriverConnect** Funktion.<br /><br /> Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *ConnectionHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, die [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) aufgerufen wurde, auf die *ConnectionHandle*, und klicken Sie dann die **SQLDriverConnect** Funktion wurde erneut aufgerufen, auf die *ConnectionHandle*.<br /><br /> Or **SQLDriverConnect** Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancelHandle** aufgerufen wurde, auf die *ConnectionHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine andere asynchron ausgeführten Funktion (nicht **SQLDriverConnect**) wurde aufgerufen, die *ConnectionHandle* und wurde noch ausgeführt, wenn die **SQLDriverConnect** Funktion wurde aufgerufen.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Die **SQLDriverConnect** Funktionsaufruf konnte nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) für Argument angegebene Wert *StringLength1* kleiner als 0 und nicht wurde SQL_NTS gleich.<br /><br /> (DM) für Argument angegebene Wert *Pufferlänge* war kleiner als 0.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) die *DriverCompletion* Argument war SQL_DRIVER_PROMPT, und die *WindowHandle* Argument wurde ein null-Zeiger.|  
|HY110|Ungültiger Treiberabschluss.|(DM) der Wert für das Argument angegebene *DriverCompletion* war nicht gleich SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_NOPROMPT oder sql_driver_complete_required lautet.<br /><br /> (DM) Verbindungs-pooling aktiviert wurde, und der Wert für das Argument angegebene *DriverCompletion* war nicht gleich auf SQL_DRIVER_NOPROMPT.|  
|HYC00|Optionales Feature nicht implementiert.|Der Treiber unterstützt nicht die Version des ODBC-Verhalten, die die Anwendung angefordert hat.|  
|HYT00|Timeout abgelaufen|Des anmeldungstimeouts ist abgelaufen, bevor Sie die Verbindung mit der Datenquelle abgeschlossen. Das Timeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber, die der angegebene Name der Datenquelle für die Funktion nicht unterstützt.|  
|IM002|Datenquelle wurde nicht gefunden und kein Standardtreiber angegeben|(DM) die Datenquelle in der Verbindungszeichenfolge angegebenen Namen (*InConnectionString*) wurde nicht gefunden. in den Systeminformationen und gab es keine Standardspezifikation für den Treiber.<br /><br /> (DM) ODBC-Quelle und Standard-Treiber Dateninformationen wurde nicht gefunden werden, in den Systeminformationen.|  
|IM003|Angegebene Treiber konnte nicht geladen werden|(DM) der Treiber aufgeführt, die in der Angabe der Datenquelle in den Systeminformationen oder gemäß der **Treiber** Schlüsselwort wurde nicht gefunden oder konnte nicht in einem anderen Grund geladen werden.|  
|IM004|Der Treiber **SQLAllocHandle** auf SQL_HANDLE_ENV auf Fehler|(DM) während der **SQLDriverConnect**, der Treiber-Manager Namens des Treibers **SQLAllocHandle** -Funktion mit einem *fHandleType* SQL_HANDLE_ENV und der Treiber zurückgegeben ein Fehler.|  
|IM005|Der Treiber **SQLAllocHandle** auf SQL_HANDLE_DBC auf Fehler.|(DM) während der **SQLDriverConnect**, der Treiber-Manager Namens des Treibers **SQLAllocHandle** -Funktion mit einem *fHandleType* SQL_HANDLE_DBC auf, und der Treiber zurückgegeben ein Fehler.|  
|IM006|Der Treiber **SQLSetConnectAttr** Fehler|(DM) während der **SQLDriverConnect**, der Treiber-Manager Namens des Treibers **SQLSetConnectAttr** -Funktion und der Treiber hat einen Fehler zurückgegeben.|  
|IM007|Keine Datenquelle oder Treiber angegeben; Dialogfeld nicht zulässig|Kein Datenquellenname oder Treiber wurde in der Verbindungszeichenfolge angegeben und *DriverCompletion* SQL_DRIVER_NOPROMPT wurde.|  
|IM008|Dialogfehler|Der Treiber hat versucht, seine Anmeldungsdialogfeld anzuzeigen und Fehler.<br /><br /> *WindowHandle* wurde ein null-Zeiger und *DriverCompletion* war nicht SQL_DRIVER_NO_PROMPT.|  
|IM009|Kann nicht geladen werden Konvertierungs-DLL|Der Treiber konnte den Konvertierungs-DLL zu laden, die für die Datenquelle oder für die Verbindung angegeben wurde.|  
|IM010|Der Datenquellenname ist zu lang.|(DM) war der Attributwert für das DSN-Schlüsselwort SQL_MAX_DSN_LENGTH Zeichen überschreitet.|  
|IM011|Der Treibername ist zu lang.|(DM) das Attribut-Wert für die **Treiber** Schlüsselwort war länger als 255 Zeichen lang sein.|  
|IM012|Syntaxfehler für DRIVER-Schlüsselwort|(DM) der Schlüsselwort-Wert-Paar, für die **Treiber** Schlüsselwort enthalten einen Syntaxfehler.<br /><br /> (DM) die Zeichenfolge in  *\*InConnectionString* enthalten eine **FILEDSN** -Schlüsselwort, aber die DSN-Datei enthielt keine **Treiber** Schlüsselwort oder einen  **DSN** Schlüsselwort.|  
|IM014|Der angegebene DSN enthält einen architekturkonflikt zwischen dem Treiber und der Anwendung|(DM)-32-Bit-Anwendung verwendet einen DSN Herstellen einer Verbindung mit einer 64-Bit-Treiber. oder umgekehrt.|  
|IM015|Fehler des Treibers SQLDriverConnect auf SQL_HANDLE_DBC_INFO_HANDLE|Ein Treiber SQL_ERROR zurück, der Treiber-Manager für die Anwendung SQL_ERROR zurück, und die Verbindung schlägt fehl.<br /><br /> Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN, finden Sie unter [Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
|S1118|Asynchrone Benachrichtigung unterstützt Treiber nicht.|Wenn der Treiber die asynchrone Benachrichtigung nicht unterstützt, können nicht Sie SQL_ATTR_ASYNC_DBC_EVENT oder SQL_ATTR_ASYNC_DBC_RETCODE_PTR festlegen.|  
  
## <a name="comments"></a>Kommentare  
 Eine Verbindungszeichenfolge weist die folgende Syntax:  
  
 *Verbindungszeichenfolge* :: = *leeren Zeichenfolge*[;] &#124; *Attribut*[;] &#124; *Attribut*; *Verbindungszeichenfolgen*  
  
 *leeren Zeichenfolge* :: =*Attribut* :: = *-Schlüsselwort*=*Attribut / Wert* &#124; DRIVER = {[}] *Attribut-Wert*[}]  
  
 *Attribut-Schlüsselwort* :: DSN = &#124; UID &#124; PWD &#124; *-Treiber-definierten-Attribut-Schlüsselwort*  
  
 *Attribut-Wert* :: = *-Zeichenfolge*  
  
 *Treiber-definierten-Attribut-Schlüsselwort* :: = *Bezeichner*  
  
 in denen *zechenfolgen* ist NULL oder mehr Zeichen *Bezeichner* verfügt über eine oder mehrere Zeichen *-Schlüsselwort* wird nicht beachtet; *Attribut / Wert* möglicherweise beachtet werden soll; und der Wert von der **DSN** Schlüsselwort besteht nicht ausschließlich aus Leerzeichen.  
  
 Aufgrund Verbindung und Initialisierungsdateien Datei Grammatik, Schlüsselwörter und Attribut Werte, die die Zeichen enthalten **[]{}();? \*=! @** nicht eingeschlossen wird, mit Klammern sollte vermieden werden. Der Wert des der **DSN** -Schlüsselwort darf nicht ausschließlich aus Leerzeichen bestehen und darf keine führende Leerzeichen enthalten. Aufgrund der Grammatik der Systeminformationen, Schlüsselwörter und Namen von Datenquellen können nicht den umgekehrten Schrägstrich enthalten (\\) Zeichen.  
  
 Anwendungen müssen keine geschweiften Klammern, um den Wert des Attributs, nach dem Hinzufügen der **Treiber** Schlüsselwort, wenn das Attribut ein Semikolon (;) enthält, in diesem Fall die geschweiften Klammern sind erforderlich. Wenn der Wert des Attributs, den der Treiber empfängt geschweifte Klammern enthält, wird der Treiber sollte nicht entfernt, aber sollten Teil der zurückgegebenen Verbindungszeichenfolge sein.  
  
 Ein Zeichenfolgenwert DSN- oder Verbindungszeichenfolge in geschweifte Klammern eingeschlossen ({}), die keines der Zeichen enthält **[]{}();? \*=! @** wird an den Treiber unverändert übergeben. Wenn Sie diese Zeichen in einem Schlüsselwort zu verwenden, der Treiber-Manager einen Fehler zurück, bei der Arbeit mit Datei-DSNs jedoch übergibt die Verbindungszeichenfolge an den Treiber für reguläre Verbindungszeichenfolgen. Verwenden Sie eingebettete geschweiften Klammern in einem Schlüsselwortwert.  
  
 Die Verbindungszeichenfolge kann eine beliebige Anzahl von treiberdefinierten Schlüsselwörter enthalten. Da die **Treiber** Schlüsselwort keine Informationen aus der Systeminformationen verwendet, der Treiber muss genügend Schlüsselwörter definieren, sodass ein Treiber mit einer Datenquelle, die ausschließlich anhand der Informationen in der Verbindungszeichenfolge eine Verbindung herstellen kann. (Weitere Informationen finden Sie unter "Treiber Richtlinien" weiter unten in diesem Abschnitt.) Der Treiber wird definiert, welche Schlüsselwörter für die Verbindung mit der Datenquelle erforderlich sind.  
  
 Die folgende Tabelle beschreibt die Attributwerte von den **DSN**, **FILEDSN**, **Treiber**, **UID**, **PWD**, und **SAVEFILE** Schlüsselwörter.  
  
|Schlüsselwort|Attribut-Wert-Beschreibung|  
|-------------|---------------------------------|  
|**DSN**|Name einer Datenquelle, wie vom **SQLDataSources** oder das Dialogfeld Quellen von Daten von **SQLDriverConnect**.|  
|**DATEI-DSN**|Name einer Datei ".DSN" für die Datenquelle aus, die eine Verbindungszeichenfolge erstellt wird. Diese Datenquellen werden von Dateidatenquellen bezeichnet.|  
|**TREIBER**|Beschreibung des Treibers, vom dem **SQLDrivers** Funktion. Z. B. Rdb oder SQL Server.|  
|**UID**|Eine Benutzer-ID|  
|**PWD**|Das Kennwort für die Benutzer-ID oder eine leere Zeichenfolge, wenn es kein Kennwort für die Benutzer-ID (PWD =;).|  
|**SAVEFILE**|Der Dateiname, der eine DSN-Datei, in der die Attributwerte des Schlüsselwörter, die verwendet werden, Herstellen der Verbindungs vorhanden, erfolgreichen gespeichert werden soll.|  
  
 Weitere Informationen dazu, wie eine Anwendung eine Datenquelle oder Treiber auswählt, finden Sie unter [Auswählen einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Wenn keine Schlüsselwörter in der Verbindungszeichenfolge wiederholt werden, verwendet der Treiber den Wert mit dem ersten Vorkommen des Schlüsselworts. Wenn die **DSN** und **Treiber** Schlüsselwörter in derselben Verbindungszeichenfolge enthalten sind, die der Treiber-Manager und den Treiber verwenden, welches Schlüsselwort an erster Stelle steht.  
  
 Die **FILEDSN** und **DSN** Schlüsselwörter schließen sich gegenseitig: welches Schlüsselwort an erster Stelle steht, wird verwendet und diejenige, die zweite angezeigt wird, wird ignoriert. Die **FILEDSN** und **Treiber** Schlüsselwörter, auf der anderen Seite einander nicht. Wenn irgend eines Schlüsselwortes angezeigt wird, in einer Verbindungszeichenfolge mit **FILEDSN**, und klicken Sie dann den Wert des Attributs, der das Schlüsselwort in der Verbindungszeichenfolge den Wert des Attributs des derselben Schlüsselworts in der DSN-Datei verwendet wird.  
  
 Wenn die **FILEDSN** -Schlüsselwort wird verwendet, die Schlüsselwörter, die in einer DSN-Datei angegeben werden verwendet, um eine Verbindungszeichenfolge zu erstellen. (Weitere Informationen finden Sie unter "Datei Data Sources," weiter unten in diesem Abschnitt.) Die **UID** Schlüsselwort ist optional; eine DSN-Datei kann nur mit erstellt werden die **Treiber** Schlüsselwort. Die **PWD** Schlüsselwort wird nicht in einer DSN-Datei gespeichert. Das Standardverzeichnis für das Speichern und Laden von DSN-Datei werden eine Kombination von angegebene Pfad **CommonFileDir** in "hkey_local_machine\software\microsoft\" Windows\CurrentVersion und "ODBC\DataSources". (Würde CommonFileDir "C:\Program Files\Common Files", würde das Standardverzeichnis "C:\Programme\Microsoft c:\Programme\Gemeinsame Dateien\ODBC\Data Sources" sein.)  
  
> [!NOTE]  
>  Eine DSN-Datei kann bearbeitet werden, direkt durch Aufrufen der [SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md) und [SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md) Funktionen in die Installationsprogramm-DLL.  
  
 Wenn die **SAVEFILE** -Schlüsselwort wird verwendet, die Attributwerte im Herstellen der Verbindungs vorhanden, erfolgreichen verwendeten Schlüsselwörter werden als eine DSN-Datei mit dem Namen, der den Wert des Attributs gespeichert der **SAVEFILE** Schlüsselwort. Die **SAVEFILE** -Schlüsselwort muss verwendet werden, in Verbindung mit der **Treiber** -Schlüsselwort, das **FILEDSN** -Schlüsselwort oder für beide oder die Funktion gibt SQL_SUCCESS_WITH_INFO mit SQLSTATE 01S09 (ungültiges Schlüsselwort). Die **SAVEFILE** Schlüsselwort muss verwendet werden, bevor Sie die **Treiber** -Schlüsselwort in der Verbindungszeichenfolge oder die Ergebnisse nicht definiert.  
  
## <a name="driver-manager-guidelines"></a>Treiber-Manager-Richtlinien  
 Der Treiber-Manager erstellt eine Verbindungszeichenfolge für die Übergabe an den Treiber in der *InConnectionString* Argument des Treibers **SQLDriverConnect** Funktion. Der Treiber-Manager ändert nicht die *InConnectionString* Argument übergeben, von der Anwendung.  
  
 Die Aktion des Treiber-Managers ist auf Grundlage des Werts, der die *DriverCompletion* Argument:  
  
-   SQL_DRIVER_PROMPT: Wenn die Verbindungszeichenfolge entweder keine der **Treiber**, **DSN**, oder **FILEDSN** Schlüsselwort, das der Treiber-Manager zeigt das Dialogfeld "Datenquellen". Erstellt eine Verbindungszeichenfolge aus der Name der Datenquelle vom Dialogfeld zurückgegeben und allen anderen Schlüsselwörtern, die von der Anwendung übergeben. Wenn der Name der Datenquelle zurückgegeben werden, indem Sie das Dialogfeld leer ist, gibt der Treiber-Manager die Schlüsselwort-Wert-Paar DSN = Default. (Dieses Dialogfeld wird eine Datenquelle mit dem Namen "Default" nicht angezeigt.)  
  
-   SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED festgelegt ist: Wenn von der Anwendung angegebene Verbindungszeichenfolge enthält die **DSN** -Schlüsselwort, der Treiber-Manager kopiert die Verbindungszeichenfolge, die von der Anwendung angegeben. Anderenfalls wird die gleichen Aktionen wie beim *DriverCompletion* SQL_DRIVER_PROMPT ist.  
  
-   SQL_DRIVER_NOPROMPT: Der Treiber-Manager kopiert die Verbindungszeichenfolge, die von der Anwendung angegeben.  
  
 Wenn von der Anwendung angegebene Verbindungszeichenfolge enthält die **Treiber** -Schlüsselwort, der Treiber-Manager kopiert die Verbindungszeichenfolge, die von der Anwendung angegeben.  
  
 Verwenden die Verbindungszeichenfolge, die sie erstellt hat, der Treiber-Manager bestimmt den zu verwendenden Treiber eine Verbindung mit diesen Treiber her und übergibt die Verbindungszeichenfolge, die sie erstellt hat, an den Treiber; Weitere Informationen zur Interaktion zwischen der Treiber-Manager und der Treiber finden Sie im Abschnitt "Kommentare" im [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md). Wenn die Verbindungszeichenfolge keine der **Treiber** -Schlüsselwort, bestimmt der Treiber-Manager, welcher Treiber wie folgt verwenden:  
  
1.  Wenn die Verbindungszeichenfolge enthält die **DSN** -Schlüsselwort, ruft der Treiber-Manager ab, der Treiber die Datenquelle die Systeminformationen zugeordnet.  
  
2.  Wenn die Verbindungszeichenfolge keine der **DSN** -Schlüsselwort oder die Datenquelle nicht gefunden wird, ruft der Treiber-Manager ab, der Treiber die Standarddatenquelle aus den Systeminformationen zugeordnet. (Weitere Informationen finden Sie unter [Standard Unterschlüssel](../../../odbc/reference/install/default-subkey.md).) Der Treiber-Manager ändert den Wert für die **DSN** Schlüsselwort in der Verbindungszeichenfolge auf "Standard".  
  
3.  Wenn die **DSN** Schlüsselwort in der Verbindungszeichenfolge auf "Standard" festgelegt ist, wird der Treiber-Manager ruft des Treibers die Standarddatenquelle aus den Systeminformationen zugeordnet.  
  
4.  Wenn die Datenquelle wurde nicht gefunden, und die Standarddatenquelle wurde nicht gefunden, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE IM002 (Datenquelle wurde nicht gefunden und kein Standardtreiber angegeben).  
  
## <a name="file-data-sources"></a>Dateidatenquellen  
 Wenn die Verbindungszeichenfolge durch die Anwendung im Aufruf angegeben **SQLDriverConnect** enthält die **FILEDSN** -Schlüsselwort, und dieses Schlüsselwort wird nicht ersetzt, entweder durch die **DSN**oder **Treiber** -Schlüsselwort, und klicken Sie dann auf den Treiber-Manager erstellt eine Verbindungszeichenfolge, die anhand der Informationen in die DSN-Datei und die *InConnectionString* Argument. Der Treiber-Manager wird wie folgt aus:  
  
1.  Überprüft, ob der Dateiname, der die DSN-Datei gültig ist. Wenn nicht der Fall, SQL_ERROR mit SQLSTATE IM014 wird (Ungültiger Name der Datei-DSN). Der Dateiname ist eine leere Zeichenfolge ("") und SQL_DRIVER_NOPROMPT ist nicht angegeben wird, und klicken Sie dann die **File-Open** Dialogfeld wird angezeigt. Wenn der Dateiname einen gültigen Pfad aber kein Dateiname oder ein ungültiger Dateiname enthält und SQL_DRIVER_NOPROMPT nicht angegeben ist, und klicken Sie dann die **File-Open** Dialogfeld wird angezeigt, mit dem aktuellen Verzeichnis im Dateinamen angegebene festgelegt. Der Dateiname ist eine leere Zeichenfolge ("") oder der Dateiname enthält einen gültigen Pfad aber kein Dateiname oder ein ungültiger Dateiname, SQL_DRIVER_NOPROMPT angegeben wird, und dann wird SQL_ERROR mit SQLSTATE IM014 zurückgegeben (Ungültiger Name der Datei-DSN).  
  
2.  Liest alle Schlüsselwörter im Abschnitt [ODBC] die DSN-Datei an. Wenn die **Treiber** Schlüsselwort ist nicht vorhanden, wird SQL_ERROR mit SQLSTATE IM012 (Driver-Schlüsselwort Syntaxfehler), mit Ausnahme von, in denen die DSN-Datei ist Dateidatenquelle und enthält daher nur die **DSN** Schlüsselwort.  
  
     Wenn die Datei als Datenquelle Dateidatenquelle ist, liest der Treiber-Manager den Wert der **DSN** Schlüsselwort und nach Bedarf für die Datenquelle Benutzer oder Systemkonto verweist der Dateidatenquelle verbindet. Schritte 3 bis 5 werden nicht ausgeführt.  
  
3.  Erstellt eine Verbindungszeichenfolge für den Treiber an. Die Verbindungszeichenfolge der Treiber ist die Kombination der Schlüsselwörter, die in der Datei ".DSN" angegeben und in die ursprüngliche Verbindungszeichenfolge für die Anwendung angegeben. Regeln für die Erstellung der Schlüsselwörter, die sich überlappen die Treiber-Verbindungszeichenfolge werden wie folgt aus:  
  
    -   Wenn die **Treiber** Schlüsselwort vorhanden ist, in der Verbindungszeichenfolge der Anwendung und den Treibern, die gemäß der **Treiber** -Schlüsselwörter sind nicht in die DSN-Datei und die Verbindungszeichenfolge der Anwendung, und klicken Sie dann die Treiberinformationen in der Datei ".DSN" wird ignoriert, und die Treiberinformationen in der Verbindungszeichenfolge der Anwendung verwendet. Wenn die Treiber, wird angegeben die **Treiber** Schlüsselwort entsprechen den in der DSN-Datei und die Verbindungszeichenfolge der Anwendung, und wobei alle Schlüsselwörter überlappen, in der Verbindungszeichenfolge der Anwendung angegeben haben Vorrang vor denen in der DSN-Datei angegeben.  
  
    -   In der neuen Verbindungszeichenfolge die **FILEDSN** Schlüsselwort wird gelöscht.  
  
4.  Lädt den Treiber anhand der im Registrierungseintrag HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST an. INI\\< Treibername\>\Driver, in denen \<Treibername > wird angegeben, indem die **Treiber** Schlüsselwort.  
  
5.  Wird dem Treiber die neue Verbindungszeichenfolge übergeben.  
  
 Beispiele für DSN-Dateien, finden Sie unter [Herstellen einer Verbindung mithilfe von Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md).  
  
## <a name="savefile-keyword"></a>SAVEFILE-Schlüsselwort  
 Wenn von der Anwendung angegebene Verbindungszeichenfolge enthält die **SAVEFILE** -Schlüsselwort, und klicken Sie dann auf den Treiber-Manager speichert Sie die Verbindungszeichenfolge in einer DSN-Datei. Der Treiber-Manager wird wie folgt aus:  
  
1.  Überprüft, ob der Dateiname der Datei ".DSN" als den Wert des Attributs enthalten die **SAVEFILE** -Schlüsselwort ist gültig. Wenn nicht der Fall, SQL_ERROR mit SQLSTATE IM014 wird (Ungültiger Name der Datei-DSN). Die Gültigkeit des Dateinamens wird durch Benennungsregeln der standardmäßige bestimmt. Der Dateiname ist eine leere Zeichenfolge ("") und die *DriverCompletion* Argument nicht SQL_DRIVER_NOPROMPT, wird der Dateiname ist ungültig. Wenn der Dateiname bereits, wenn vorhanden ist *DriverCompletion* SQL_DRIVER_NOPROMPT lautet, wird die Datei überschrieben. Wenn *DriverCompletion* ist SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE oder sql_driver_complete_required lautet, ein Dialogfeld fordert den Benutzer an, ob die Datei überschrieben werden soll. Wenn keine eingegeben wird, und klicken Sie dann die **Datei zu speichern,** Dialogfeld wird angezeigt.  
  
2.  Wenn der Treiber gibt SQL_SUCCESS zurück, der Dateiname keine leere Zeichenfolge war, und der Treiber-Manager die Verbindungsinformationen, die zurückgegeben werden schreibt, der *OutConnectionString* Argument für die angegebene Datei mit dem angegebenen Format in Abschnitt "Verbindungszeichenfolgen" weiter oben in diesem Abschnitt.  
  
3.  Wenn der Treiber gibt SQL_SUCCESS zurück, und der Dateiname eine leere Zeichenfolge wurde (""), und der Treiber-Manager ruft dann die **Datei zu speichern,** Standarddialogfeld mit der *Hwnd* angegeben und schreibt die Verbindungsinformationen im zurückgegebenen *OutConnectionString* in die Datei in das Standarddialogfeld Datei zu speichern, mit dem im Abschnitt "Verbindungszeichenfolgen" weiter oben in diesem Abschnitt angegebenen Format angegeben.  
  
4.  Wenn der Treiber SQL_SUCCESS zurückgegeben wird, wird die *OutConnectionString* Argument mit der Verbindungszeichenfolge der Anwendung.  
  
5.  Wenn der Treiber gibt SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück, gibt der Treiber-Manager SQLSTATE an die Anwendung zurück.  
  
## <a name="driver-guidelines"></a>Treiber-Richtlinien  
 Der Treiber überprüft, ob die Verbindungszeichenfolge, die vom Treiber-Manager an sie übergebenen enthält die **DSN** oder **Treiber** Schlüsselwort. Wenn die Verbindungszeichenfolge enthält die **Treiber** -Schlüsselwort, der Treiber kann nicht abrufen von Informationen über die Datenquelle aus der Systeminformationen. Wenn die Verbindungszeichenfolge enthält die **DSN** Schlüsselwort oder enthält keine der **DSN** oder **Treiber** -Schlüsselwort, der Treiber kann Informationen über die Datenquelle abrufen aus den Systeminformationen wie folgt:  
  
1.  Wenn die Verbindungszeichenfolge enthält die **DSN** Schlüsselwort, das der Treiber Ruft die Informationen für die angegebene Datenquelle ab.  
  
2.  Wenn die Verbindungszeichenfolge keine der **DSN** -Schlüsselwort, das die angegebene Datenquelle wurde nicht gefunden, oder die **DSN** Schlüsselwort auf "Standard" festgelegt ist, ruft der Treiber die Informationen für die Standarddatenquelle .  
  
 Der Treiber verwendet, alle Informationen, die über die Systeminformationen zu erweitern, die Informationen in der Verbindungszeichenfolge übergeben abgerufen wird. Wenn die Informationen in den Systeminformationen Informationen in der Verbindungszeichenfolge dupliziert, verwendet der Treiber die Informationen in der Verbindungszeichenfolge.  
  
 Basierend auf den Wert der *DriverCompletion*, der Treiber fordert den Benutzer für die Verbindungsinformationen, z. B. Benutzer-ID und Kennwort, und eine Verbindung mit der Datenquelle her:  
  
-   SQL_DRIVER_PROMPT: Der Treiber zeigt ein Dialogfeld, verwenden die Werte aus den Verbindungsinformationen für String und System als Anfangswerte (sofern vorhanden). Wenn der Benutzer das Dialogfeld schließt, verbindet sich der Treiber mit der Datenquelle. Er erstellt auch eine Verbindungszeichenfolge aus dem Wert des der **DSN** oder **Treiber** -Schlüsselwort in \* *InConnectionString* und die Informationen zurückgegeben, die von der Das Dialogfeld. Es wird diese Verbindungszeichenfolge in der **OutConnectionString* Puffer.  
  
-   SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED festgelegt ist: Wenn die Verbindungszeichenfolge genügend Informationen enthält, und diese Informationen korrekt ist, verbindet der Treiber auf die Datenquelle und die Kopien \* *InConnectionString*zu \* *OutConnectionString*. Wenn alle Informationen fehlen oder sind falsch ist, verwendet der Treiber die gleichen Aktionen wie beim *DriverCompletion* ist SQL_DRIVER_PROMPT, außer dass bei *DriverCompletion* SQL_DRIVER_COMPLETE_ ist ERFORDERLICH, deaktiviert der Treiber die Steuerelemente für alle Informationen, die für die Verbindung mit der Datenquelle nicht erforderlich.  
  
-   SQL_DRIVER_NOPROMPT: Wenn die Verbindungszeichenfolge genügend Informationen enthält, der Treiber stellt eine Verbindung her auf die Datenquelle und die Kopien \* *InConnectionString* zu \* *OutConnectionString*. Andernfalls gibt der Treiber SQL_ERROR für **SQLDriverConnect**.  
  
 Bei erfolgreichen Verbindung mit der Datenquelle der Treiber auch setzt \* *StringLength2Ptr* der Länge der die ausgegebene Verbindungszeichenfolge, die für die zurückzugebenden in verfügbar ist **OutConnectionString*.  
  
 Wenn der Benutzer ein Dialogfeld angezeigt, die von der Treiber-Manager oder den Treiber storniert **SQLDriverConnect** SQL_NO_DATA zurückgibt.  
  
 Informationen darüber, wie der Treiber-Manager und der Treiber während des Verbindungsprozesses interagieren, finden Sie unter [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Wenn ein Treiber unterstützt **SQLDriverConnect**, muss der Treiber-Schlüsselwort Teil die Systeminformationen für den Treiber enthalten die **ConnectFunctions** Schlüsselwort mit dem zweiten Zeichen "Y" festgelegt.  
  
## <a name="connecting-when-connection-pooling-is-enabled"></a>Herstellen einer Verbindung, wenn Verbindungspooling aktiviert ist  
 Verbindungspooling ermöglicht einer Anwendung, die eine Verbindung wiederzuverwenden, die bereits erstellt wurde. Wenn **SQLDriverConnect** aufgerufen wird, wird der Treiber-Manager versucht, zum Herstellen der Verbindung über eine Verbindung, die Teil eines Pools von Verbindungen in einer Umgebung, die für das Verbindungspooling festgelegt wurde. Weitere Informationen zum Verbindungspooling finden Sie unter [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Eine Anwendung kann die SQL_ATTR_RESET_CONNECTION festlegen, vor dem Aufrufen von SQLDisconnect für eine Verbindung, Verbindungspooling aktiviert ist. Weitere Informationen finden Sie unter [SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Die folgenden Einschränkungen gelten, wenn eine Anwendung ruft **SQLDriverConnect** für eine gepoolte Verbindung die Verbindung:  
  
-   Kein Verbindungs-pooling Verarbeitung erfolgt bei der **SAVEFILE** -Schlüsselwort in der Verbindungszeichenfolge angegeben ist.  
  
-   Wenn Verbindungspooling aktiviert ist, **SQLDriverConnect** kann aufgerufen werden, nur mit einer *DriverCompletion* Argument von SQL_DRIVER_NOPROMPT; Wenn **SQLDriverConnect** aufgerufen wird Bei einem anderen *DriverCompletion*, SQLSTATE HY110 (Ungültiger Treiberabschluss) zurückgegeben werden.  
  
## <a name="connection-attributes"></a>Verbindungsattribute  
 Das Verbindungsattribut SQL_ATTR_LOGIN_TIMEOUT, legen Sie mithilfe von **SQLSetConnectAttr**, definiert die Anzahl von Sekunden zu warten, bis eine anmeldeanforderung, mit der eine erfolgreiche Verbindung vom Treiber abzuschließen, bevor Sie an die Anwendung zurückgegeben. Wenn der Benutzer aufgefordert wird, um die Verbindungszeichenfolge abzuschließen, beginnt eine Wartezeit für jede Anforderung für die Anmeldung, wenn der Treiber den Verbindungsprozess wird gestartet.  
  
 Der Treiber die Verbindung im Zugriffsmodus SQL_MODE_READ_WRITE wird standardmäßig geöffnet. Um den Zugriffsmodus SQL_MODE_READ_ONLY festzulegen, muss die Anwendung aufrufen **SQLSetConnectAttr** mit dem Attribut SQL_ATTR_ACCESS_MODE vor dem Aufruf **SQLDriverConnect**.  
  
 Wenn eine Standardbibliothek für die Übersetzung in die Systeminformationen für die Datenquelle angegeben ist, wird Sie von der Treiber geladen. Einer anderen übersetzungsbibliothek geladen werden kann, durch den Aufruf **SQLSetConnectAttr** mit dem SQL_ATTR_TRANSLATE_LIB-Attribut. Eine Übersetzungsoption kann angegeben werden, durch den Aufruf **SQLSetConnectAttr** mit der Option SQL_ATTR_TRANSLATE_OPTION.  
  
 Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
```  
// SQLDriverConnect_ref.cpp  
// compile with: odbc32.lib user32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
  
   SQLCHAR OutConnStr[255];  
   SQLSMALLINT OutConnStrLen;  
  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            retcode = SQLDriverConnect( // SQL_NULL_HDBC  
               hdbc,   
               desktopHandle,   
               (SQLCHAR*)"driver=SQL Server",   
               _countof("driver=SQL Server"),  
               OutConnStr,  
               255,   
               &OutConnStrLen,  
               SQL_DRIVER_PROMPT );  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {                 
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 Siehe auch [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ein Handle zuordnen|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Ermitteln und Aufzählen von Werten, die für die Verbindung mit einer Datenquelle|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Trennen von einer Datenquelle|[SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Zurückgeben von Beschreibungen der Treiber und Attribute|[SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Ein Handle freigeben|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Ein Verbindungsattribut festlegen|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
