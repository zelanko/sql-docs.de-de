---
title: SQLDriverConnect-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 88ec70d68b46beca97fd6b0d758e21aab5d4f4b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302771"
---
# <a name="sqldriverconnect-function"></a>SQLDriveConnect-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLDriverConnect** ist eine Alternative zu **SQLConnect**. Es unterstützt Datenquellen, die mehr Verbindungsinformationen als die drei Argumente in **SQLConnect**erfordern, Dialogfelder, um den Benutzer zu allen Verbindungsinformationen aufzufordern, und Datenquellen, die nicht in den Systeminformationen definiert sind.  
  
 **SQLDriverConnect** stellt die folgenden Verbindungsattribute bereit:  
  
-   Stellen Sie eine Verbindung mithilfe einer Verbindungszeichenfolge her, die den Datenquellennamen, eine oder mehrere Benutzer-IDs, ein oder mehrere Kennwörter und andere informationen enthält, die für die Datenquelle erforderlich sind.  
  
-   Herstellen einer Verbindung mithilfe einer partiellen Verbindungszeichenfolge oder ohne zusätzliche Informationen; In diesem Fall können der Treiber-Manager und der Treiber den Benutzer jeweils zur Eingabe von Verbindungsinformationen auffordern.  
  
-   Stellen Sie eine Verbindung zu einer Datenquelle her, die nicht in den Systeminformationen definiert ist. Wenn die Anwendung eine partielle Verbindungszeichenfolge bereitstellt, kann der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordern.  
  
-   Stellen Sie eine Verbindung zu einer Datenquelle mithilfe einer Verbindungszeichenfolge her, die aus den Informationen in einer Dsn-Datei erstellt wurde.  
  
 Nachdem eine Verbindung hergestellt wurde, gibt **SQLDriverConnect** die abgeschlossene Verbindungszeichenfolge zurück. Die Anwendung kann diese Zeichenfolge für nachfolgende Verbindungsanforderungen verwenden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
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
 [Eingabe] Fenstergriff. Die Anwendung kann ggf. das Handle des übergeordneten Fensters oder einen Nullzeiger übergeben, wenn entweder das Fensterhandle nicht anwendbar ist oder **SQLDriverConnect** keine Dialogfelder anzeigt.  
  
 *InConnectionString*  
 [Eingabe] Eine vollständige Verbindungszeichenfolge (siehe Syntax in "Kommentare"), eine partielle Verbindungszeichenfolge oder eine leere Zeichenfolge.  
  
 *StringLength1*  
 [Eingabe] Länge von **InConnectionString*, in Zeichen, wenn die Zeichenfolge Unicode ist, oder Bytes, wenn Die Zeichenfolge ANSI oder DBCS ist.  
  
 *OutConnectionString*  
 [Ausgabe] Zeiger auf einen Puffer für die abgeschlossene Verbindungszeichenfolge. Bei erfolgreicher Verbindung mit der Zieldatenquelle enthält dieser Puffer die abgeschlossene Verbindungszeichenfolge. Anwendungen sollten mindestens 1.024 Zeichen für diesen Puffer zuweisen.  
  
 Wenn *OutConnectionString* NULL ist, gibt *StringLength2Ptr* weiterhin die Gesamtzahl der Zeichen zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer von *OutConnectionString*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Länge des **OutConnectionString-Puffers* in Zeichen.  
  
 *StringLength2Ptr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (mit Ausnahme \*des Null-Beendigungszeichens) zurückgegeben werden soll, die in *OutConnectionString*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer oder gleich *BufferLength* \*ist, wird die abgeschlossene Verbindungszeichenfolge in *OutConnectionString* auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
 *DriverCompletion*  
 [Eingabe] Flag, das angibt, ob der Treiber-Manager oder -Treiber weitere Verbindungsinformationen anfordern muss:  
  
 SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED oder SQL_DRIVER_NOPROMPT.  
  
 (Weitere Informationen finden Sie unter "Kommentare.")  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDriverConnect** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *fHandleType* von SQL_HANDLE_DBC und einem *hHandle* von *ConnectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLDriverConnect** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der \*Puffer *OutConnectionString* war nicht groß genug, um die gesamte Verbindungszeichenfolge zurückzugeben, sodass die Verbindungszeichenfolge abgeschnitten wurde. Die Länge der nicht abgeschnittenen Verbindungszeichenfolge wird in **StringLength2Ptr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S00|Ungültiges Verbindungszeichenfolgenattribut|In der Verbindungszeichenfolge (*InConnectionString*) wurde ein ungültiges Attributschlüsselwort angegeben, der Treiber konnte jedoch trotzdem eine Verbindung mit der Datenquelle herstellen. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber unterstützte nicht den angegebenen Wert, auf den das *ValuePtr-Argument* in **SQLSetConnectAttr** zeigt, und ersetzte einen ähnlichen Wert. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S08|Fehler beim Speichern der Datei DSN|Die Zeichenfolge in * \*InConnectionString* enthielt ein **FILEDSN-Schlüsselwort,** aber die .dsn-Datei wurde nicht gespeichert. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S09|Ungültiges Schlüsselwort|(DM) Die Zeichenfolge in * \*InConnectionString* enthielt ein **SAVEFILE-Schlüsselwort,** aber kein **DRIVER-** oder **FILEDSN-Schlüsselwort.** (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08001|Client kann keine Verbindung herstellen|Der Treiber konnte keine Verbindung mit der Datenquelle herstellen.|  
|08002|Verbindungsname wird verwendet|(DM) Das angegebene *ConnectionHandle* wurde bereits verwendet, um eine Verbindung mit einer Datenquelle herzustellen, und die Verbindung war noch offen.|  
|08004|Server hat die Verbindung abgelehnt|Die Datenquelle lehnte den Aufbau der Verbindung aus implementierungsdefinierten Gründen ab.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber eine Verbindung herstellen wollte, ist fehlgeschlagen, bevor die **SQLDriverConnect-Funktion** die Verarbeitung abgeschlossen hat.|  
|28000|Ungültige Autorisierungsspezifikation|Entweder der Benutzerbezeichner oder die Autorisierungszeichenfolge oder beides, wie in der Verbindungszeichenfolge (*InConnectionString*) angegeben, hat einschränkungen, die von der Datenquelle definiert wurden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*szMessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY000|Allgemeiner Fehler: Ungültige Datei dsn|(DM) Die Zeichenfolge in **InConnectionString* enthielt ein FILEDSN-Schlüsselwort, aber der Name der .dsn-Datei wurde nicht gefunden.|  
|HY000|Allgemeiner Fehler: Dateipuffer kann nicht erstellt werden|(DM) Die Zeichenfolge in **InConnectionString* enthielt ein FILEDSN-Schlüsselwort, aber die .dsn-Datei war nicht lesbar.|  
|HY001|Speicherzuweisungsfehler|Der Treiber-Manager konnte den erforderlichen Arbeitsspeicher nicht zuweisen, um die Ausführung oder den Abschluss der **SQLDriverConnect-Funktion** zu unterstützen.<br /><br /> Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *den ConnectionHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde die [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) für den *ConnectionHandle*aufgerufen, und dann wurde die **SQLDriverConnect-Funktion** erneut im *ConnectionHandle*aufgerufen.<br /><br /> Oder die **SQLDriverConnect-Funktion** wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancelHandle** für das *ConnectionHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Eine weitere asynchron ausgeführte Funktion (nicht **SQLDriverConnect**) wurde für den *ConnectionHandle* aufgerufen und wurde noch ausgeführt, als die **SQLDriverConnect-Funktion** aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der **SQLDriverConnect-Funktionsaufruf** konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der für das Argument *StringLength1* angegebene Wert war kleiner als 0 und entsprach nicht SQL_NTS.<br /><br /> (DM) Der für das Argument *BufferLength* angegebene Wert war kleiner als 0.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) Das *Argument DriverCompletion* wurde SQL_DRIVER_PROMPT, und das *WindowHandle-Argument* war ein Nullzeiger.|  
|HY110|Ungültiger Treiberabschluss|(DM) Der für das Argument *DriverCompletion* angegebene Wert entsprach nicht SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED oder SQL_DRIVER_NOPROMPT.<br /><br /> (DM) Das Verbindungspooling wurde aktiviert, und der für das Argument *DriverCompletion* angegebene Wert entsprach nicht SQL_DRIVER_NOPROMPT.|  
|HYC00|Optionale Funktion nicht implementiert|Der Treiber unterstützt nicht die Version des ODBC-Verhaltens, die von der Anwendung angefordert wurde.|  
|HYT00|Timeout abgelaufen|Der Anmeldetimeoutzeitraum ist abgelaufen, bevor die Verbindung zur Datenquelle abgeschlossen wurde. Der Timeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der Treiber, der dem angegebenen Datenquellennamen entspricht, unterstützt die Funktion nicht.|  
|IM002|Datenquelle nicht gefunden und kein Standardtreiber angegeben|(DM) Der in der Verbindungszeichenfolge (*InConnectionString*) angegebene Datenquellenname wurde in den Systeminformationen nicht gefunden, und es gab keine Standardtreiberspezifikation.<br /><br /> (DM) ODBC-Datenquelle und Standardtreiberinformationen konnten in den Systeminformationen nicht gefunden werden.|  
|IM003|Der angegebene Treiber konnte nicht geladen werden.|(DM) Der treiber, der in der Datenquellenspezifikation in den Systeminformationen aufgeführt ist oder durch das **SCHLÜSSELwort DRIVER** angegeben ist, wurde aus einem anderen Grund nicht gefunden oder konnte nicht geladen werden.|  
|IM004|**SQLAllocHandle** des Treibers auf SQL_HANDLE_ENV fehlgeschlagen|(DM) Während **SQLDriverConnect**rief der Treiber-Manager die **SQLAllocHandle-Funktion** des Treibers mit einem *fHandleType* von SQL_HANDLE_ENV und der Treiber gab einen Fehler zurück.|  
|IM005|**SQLAllocHandle** des Treibers auf SQL_HANDLE_DBC fehlgeschlagen.|(DM) Während **SQLDriverConnect**rief der Treiber-Manager die **SQLAllocHandle-Funktion** des Treibers mit einem *fHandleType* von SQL_HANDLE_DBC und der Treiber gab einen Fehler zurück.|  
|IM006|**SQLSetConnectAttr** des Treibers fehlgeschlagen|(DM) Während **SQLDriverConnect**rief der Treiber-Manager die **SQLSetConnectAttr-Funktion** des Treibers auf, und der Treiber gab einen Fehler zurück.|  
|IM007|Es wurde keine Datenquelle oder ein Treiber angegeben; Dialog verboten|In der Verbindungszeichenfolge wurde kein Datenquellenname oder -treiber angegeben, und *DriverCompletion* wurde SQL_DRIVER_NOPROMPT.|  
|IM008|Dialog fehlgeschlagen|Der Treiber hat versucht, das Anmeldedialogfeld anzuzeigen, und ist fehlgeschlagen.<br /><br /> *WindowHandle* war ein Nullzeiger, und *DriverCompletion* war nicht SQL_DRIVER_NO_PROMPT.|  
|IM009|Übersetzungs-DLL kann nicht geladen werden|Der Treiber konnte die Übersetzungs-DLL, die für die Datenquelle oder die Verbindung angegeben wurde, nicht laden.|  
|IM010|Datenquellenname zu lang|(DM) Der Attributwert für das DSN-Schlüsselwort war länger als SQL_MAX_DSN_LENGTH Zeichen.|  
|IM011|Treibername zu lang|(DM) Der Attributwert für das **Schlüsselwort DRIVER** war länger als 255 Zeichen.|  
|IM012|DRIVER-Schlüsselwortsyntaxfehler|(DM) Das Schlüsselwort-Wert-Paar für das **SCHLÜSSELwort DRIVER** enthielt einen Syntaxfehler.<br /><br /> (DM) Die Zeichenfolge in * \*InConnectionString* enthielt ein **FILEDSN-Schlüsselwort,** aber die .dsn-Datei enthielt kein **DRIVER-Schlüsselwort** oder ein **DSN-Schlüsselwort.**|  
|IM014|Der angegebene DSN enthält eine Architekturkonfliktübereinstimmung zwischen Treiber und Anwendung|(DM) 32-Bit-Anwendung verwendet eine DSN-Verbindung mit einem 64-Bit-Treiber; oder umgekehrt.|  
|IM015|SQLDriverConnect des Treibers auf SQL_HANDLE_DBC_INFO_HANDLE fehlgeschlagen|Wenn ein Treiber SQL_ERROR zurückkehrt, kehrt der Treiber-Manager SQL_ERROR an die Anwendung zurück, und die Verbindung schlägt fehl.<br /><br /> Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [Entwickeln von Verbindungspool-Awareness in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
|S1118|Treiber unterstützt keine asynchrone Benachrichtigung|Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, können Sie keine SQL_ATTR_ASYNC_DBC_EVENT oder SQL_ATTR_ASYNC_DBC_RETCODE_PTR festlegen.|  
  
## <a name="comments"></a>Kommentare  
 Eine Verbindungszeichenfolge hat die folgende Syntax:  
  
 *connection-string* ::= *empty-string*[;] &#124; *Attribut*[;] &#124; *Attribut*; *Verbindungszeichenfolge*  
  
 *empty-string* ::=*Attribut* ::= *attribut-keyword*=*attribut-value* &#124; DRIVER=[']*attribut-value*[']  
  
 *attribut-keyword* ::= DSN &#124; UID &#124; PWD &#124; *driver-defined-attribute-keyword*  
  
 *Attributwert* ::= *Zeichenzeichenfolge*  
  
 *driver-defined-attribute-keyword* ::= *Bezeichner*  
  
 wobei *die Zeichenfolge* null oder mehr Zeichen enthält; *Bezeichner* hat ein oder mehrere Zeichen; *attribut-keyword* wird nicht von groß vertraulich berücksichtigt. *Attributwert* kann die Groß-/Kleinschreibung berücksichtigen; und der Wert des **DSN-Schlüsselworts** besteht nicht nur aus Leerzeichen.  
  
 Aufgrund der Grammatik von Verbindungszeichenfolgen und Initialisierungsdateien, Schlüsselwörtern und Attributwerten, die die Zeichen **[]{}(),;? enthalten. Nicht \*** mit Geschweifungen eingeschlossen, sollte vermieden werden. Der Wert des **DSN-Schlüsselworts** darf nicht nur aus Leerzeichen bestehen und sollte keine führenden Leerzeichen enthalten. Aufgrund der Grammatik der Systeminformationen dürfen Schlüsselwörter und Datenquellennamen\\nicht den umgekehrten Schrägstrich ( ) enthalten.  
  
 Anwendungen müssen keine geschweiften Klammern um den Attributwert nach dem **SCHLÜSSELDRIVER** hinzufügen, es sei denn, das Attribut enthält ein Semikolon (;), in diesem Fall sind die geschweiften Klammern erforderlich. Wenn der Attributwert, den der Treiber empfängt, geschweifte Klammern enthält, sollte der Treiber diese nicht entfernen, sondern Teil der zurückgegebenen Verbindungszeichenfolge sein.  
  
 Ein DSN- oder Verbindungszeichenfolgenwert,{}der mit geschweiften Klammern ( ) eingeschlossen ist und eines der Zeichen **[]{}(),;? enthält. \*=!** wird intakt an den Fahrer übergeben. Wenn Sie diese Zeichen jedoch in einem Schlüsselwort verwenden, gibt der Treiber-Manager einen Fehler beim Arbeiten mit Datei-DSNs zurück, übergibt jedoch die Verbindungszeichenfolge an den Treiber für reguläre Verbindungszeichenfolgen. Vermeiden Sie die Verwendung eingebetteter geschweiften Klammern in einem Schlüsselwortwert.  
  
 Die Verbindungszeichenfolge kann eine beliebige Anzahl von treiberdefinierten Schlüsselwörtern enthalten. Da das **SCHLÜSSELwort DRIVER** keine Informationen aus den Systeminformationen verwendet, muss der Treiber genügend Schlüsselwörter definieren, damit ein Treiber eine Verbindung mit einer Datenquelle herstellen kann, nur mit den Informationen in der Verbindungszeichenfolge. (Weitere Informationen finden Sie unter "Treiberrichtlinien" weiter unten in diesem Abschnitt.) Der Treiber definiert, welche Schlüsselwörter zum Herstellen einer Verbindung mit der Datenquelle erforderlich sind.  
  
 In der folgenden Tabelle werden die Attributwerte der Schlüsselwörter **DSN**, **FILEDSN**, **DRIVER**, **UID**, **PWD**und **SAVEFILE** beschrieben.  
  
|Schlüsselwort|Attributwertbeschreibung|  
|-------------|---------------------------------|  
|**Dsn**|Name einer Datenquelle, die von **SQLDataSources** oder dem Datenquellendialogfeld von **SQLDriverConnect**zurückgegeben wird.|  
|**FILEDSN**|Name einer Dsn-Datei, aus der eine Verbindungszeichenfolge für die Datenquelle erstellt wird. Diese Datenquellen werden als Dateidatenquellen bezeichnet.|  
|**Treiber**|Beschreibung des Treibers, der von der **SQLDrivers-Funktion** zurückgegeben wird. Beispiel: Rdb oder SQL Server.|  
|**UID**|Eine Benutzer-ID.|  
|**Pwd**|Das Kennwort, das der Benutzer-ID entspricht, oder eine leere Zeichenfolge, wenn kein Kennwort für die Benutzer-ID vorhanden ist (PWD=;).|  
|**Savefile**|Der Dateiname einer Dsn-Datei, in der die Attributwerte von Schlüsselwörtern gespeichert werden sollen, die bei der Erstellung der aktuellen, erfolgreichen Verbindung verwendet werden sollen.|  
  
 Informationen dazu, wie eine Anwendung eine Datenquelle oder einen Treiber auswählt, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Wenn Schlüsselwörter in der Verbindungszeichenfolge wiederholt werden, verwendet der Treiber den Wert, der dem ersten Vorkommen des Schlüsselworts zugeordnet ist. Wenn die Schlüsselwörter **DSN** und **DRIVER** in derselben Verbindungszeichenfolge enthalten sind, verwenden der Treiber-Manager und der Treiber das Schlüsselwort, das zuerst angezeigt wird.  
  
 Die **Schlüsselwörter FILEDSN** und **DSN** schließen sich gegenseitig aus: Welches Schlüsselwort zuerst angezeigt wird, wird verwendet, und das Schlüsselwort, das als zweites erscheint, wird ignoriert. Die Schlüsselwörter **FILEDSN** und **DRIVER** schließen sich dagegen nicht gegenseitig aus. Wenn ein Schlüsselwort in einer Verbindungszeichenfolge mit **FILEDSN**angezeigt wird, wird der Attributwert des Schlüsselworts in der Verbindungszeichenfolge anstelle des Attributwerts desselben Schlüsselworts in der Dsn-Datei verwendet.  
  
 Wenn das **Schlüsselwort FILEDSN** verwendet wird, werden die in einer DsN-Datei angegebenen Schlüsselwörter zum Erstellen einer Verbindungszeichenfolge verwendet. (Weitere Informationen finden Sie unter "Dateidatenquellen" weiter unten in diesem Abschnitt.) Das **UID-Schlüsselwort** ist optional. Eine .dsn-Datei kann nur mit dem **Schlüsselwort DRIVER** erstellt werden. Das **Schlüsselwort PWD** wird nicht in einer Dsn-Datei gespeichert. Das Standardverzeichnis zum Speichern und Laden einer .dsn-Datei ist eine Kombination aus dem Pfad, der von **CommonFileDir** in HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-Windows-CurrentVersion und "ODBC-DataSources" angegeben wird. (Wenn CommonFileDir "C:-Programmdateien, allgemeine Dateien" wäre, wäre das Standardverzeichnis "C:-Programmdateien, "Gemeinsame Dateien", "ODBC-Datenquellen".)  
  
> [!NOTE]  
>  Eine .dsn-Datei kann direkt bearbeitet werden, indem die Funktionen [SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md) und [SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md) in der Installations-DLL aufgerufen werden.  
  
 Wenn das **Schlüsselwort SAVEFILE** verwendet wird, werden die Attributwerte von Schlüsselwörtern, die bei der Erstellung der Gegenwart verwendet werden, als .dsn-Datei mit dem Namen des Attributwerts des **Schlüsselworts SAVEFILE** gespeichert. Das **Schlüsselwort SAVEFILE** muss in Verbindung mit dem **Schlüsselwort DRIVER,** dem **SCHLÜSSELwort FILEDSN** oder beidem verwendet werden, oder die Funktion gibt SQL_SUCCESS_WITH_INFO mit SQLSTATE 01S09 (Invalid-Schlüsselwort) zurück. Das **Schlüsselwort SAVEFILE** muss vor dem **SCHLÜSSELwort DRIVER** in der Verbindungszeichenfolge angezeigt werden, da die Ergebnisse nicht definiert sind.  
  
## <a name="driver-manager-guidelines"></a>Driver Manager-Richtlinien  
 Der Treiber-Manager erstellt eine Verbindungszeichenfolge, die an den Treiber im *InConnectionString-Argument* der **SQLDriverConnect-Funktion** des Treibers übergeben wird. Der Treiber-Manager ändert das *InConnectionString-Argument,* das von der Anwendung an ihn übergeben wurde, nicht.  
  
 Die Aktion des Treiber-Managers basiert auf dem Wert des *DriverCompletion-Arguments:*  
  
-   SQL_DRIVER_PROMPT: Wenn die Verbindungszeichenfolge weder das Schlüsselwort **DRIVER**, **DSN**oder **FILEDSN** enthält, zeigt der Treiber-Manager das Dialogfeld Datenquellen an. Es erstellt eine Verbindungszeichenfolge aus dem Datenquellennamen, der vom Dialogfeld zurückgegeben wird, und allen anderen Schlüsselwörtern, die von der Anwendung an ihn übergeben werden. Wenn der vom Dialogfeld zurückgegebene Datenquellenname leer ist, gibt der Treiber-Manager das Schlüsselwort-Wert-Paar DSN=Default an. (In diesem Dialogfeld wird keine Datenquelle mit dem Namen "Standard" angezeigt.)  
  
-   SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED: Wenn die von der Anwendung angegebene Verbindungszeichenfolge das **DSN-Schlüsselwort** enthält, kopiert der Treiber-Manager die von der Anwendung angegebene Verbindungszeichenfolge. Andernfalls werden dieselben Aktionen ausgeführt wie bei *SQL_DRIVER_PROMPT DriverCompletion.*  
  
-   SQL_DRIVER_NOPROMPT: Der Treiber-Manager kopiert die von der Anwendung angegebene Verbindungszeichenfolge.  
  
 Wenn die von der Anwendung angegebene Verbindungszeichenfolge das **Schlüsselwort DRIVER** enthält, kopiert der Treiber-Manager die von der Anwendung angegebene Verbindungszeichenfolge.  
  
 Mithilfe der von ihm erstellten Verbindungszeichenfolge bestimmt der Treiber-Manager, welcher Treiber verwendet werden soll, stellt eine Verbindung mit diesem Treiber her und übergibt die Verbindungszeichenfolge, die er erstellt hat, an den Treiber. Weitere Informationen zur Interaktion zwischen Treiber-Manager und Treiber finden Sie im Abschnitt "Kommentare" in der [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md). Wenn die Verbindungszeichenfolge nicht das **Schlüsselwort DRIVER** enthält, bestimmt der Treiber-Manager, welcher Treiber wie folgt verwendet werden soll:  
  
1.  Wenn die Verbindungszeichenfolge das **DSN-Schlüsselwort** enthält, ruft der Treiber-Manager den der Datenquelle zugeordneten Treiber aus den Systeminformationen ab.  
  
2.  Wenn die Verbindungszeichenfolge nicht das **DSN-Schlüsselwort** enthält oder die Datenquelle nicht gefunden wird, ruft der Treiber-Manager den Treiber ab, der der Standarddatenquelle zugeordnet ist, aus den Systeminformationen. (Weitere Informationen finden Sie unter [Standardunterschlüssel](../../../odbc/reference/install/default-subkey.md).) Der Treiber-Manager ändert den Wert des **DSN-Schlüsselworts** in der Verbindungszeichenfolge in "DEFAULT".  
  
3.  Wenn das **DSN-Schlüsselwort** in der Verbindungszeichenfolge auf "DEFAULT" festgelegt ist, ruft der Treiber-Manager den Treiber ab, der der Standarddatenquelle zugeordnet ist, aus den Systeminformationen.  
  
4.  Wenn die Datenquelle nicht gefunden und die Standarddatenquelle nicht gefunden wird, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE IM002 zurück (Datenquelle wurde nicht gefunden, und es wurde kein Standardtreiber angegeben).  
  
## <a name="file-data-sources"></a>Dateidatenquellen  
 Wenn die von der Anwendung im Aufruf von **SQLDriverConnect** angegebene Verbindungszeichenfolge das **Schlüsselwort FILEDSN** enthält und dieses Schlüsselwort weder durch das **DSN-** noch durch das **DRIVER-Schlüsselwort** ersetzt wird, erstellt der Treiber-Manager eine Verbindungszeichenfolge unter Verwendung der Informationen in der .dsn-Datei und dem *InConnectionString-Argument.* Der Treiber-Manager fährt wie folgt vor:  
  
1.  Überprüft, ob der Dateiname der .dsn-Datei gültig ist. Ist dies nicht der Fall, wird SQL_ERROR mit SQLSTATE IM014 (Ungültiger Name der Datei DSN) zurückgegeben. Wenn der Dateiname eine leere Zeichenfolge ("") ist und SQL_DRIVER_NOPROMPT nicht angegeben ist, wird das Dialogfeld **Dateiöffnen** angezeigt. Wenn der Dateiname einen gültigen Pfad, aber keinen Dateinamen oder einen ungültigen Dateinamen enthält und SQL_DRIVER_NOPROMPT nicht angegeben ist, wird das Dialogfeld **Dateiöffnen** mit dem aktuellen Verzeichnis angezeigt, das auf das im Dateinamen angegebene Verzeichnis festgelegt ist. Wenn der Dateiname eine leere Zeichenfolge ("") ist oder der Dateiname einen gültigen Pfad, aber keinen Dateinamen oder einen ungültigen Dateinamen enthält und SQL_DRIVER_NOPROMPT angegeben wird, wird SQL_ERROR mit SQLSTATE IM014 (Ungültiger Name der Datei DSN) zurückgegeben.  
  
2.  Liest alle Schlüsselwörter im Abschnitt [ODBC] der .dsn-Datei. Wenn das **Schlüsselwort DRIVER** nicht vorhanden ist, gibt es SQL_ERROR mit SQLSTATE IM012 (Driver-Schlüsselwortsyntaxfehler) zurück, es sei denn, die .dsn-Datei kann nicht mehr gemeinsam frei und enthält daher nur das **DSN-Schlüsselwort.**  
  
     Wenn die Dateidatenquelle nicht mehr gemeinsam verwendet werden kann, liest der Treiber-Manager den Wert des **DSN-Schlüsselworts** und stellt bei Bedarf eine Verbindung mit der Benutzer- oder Systemdatenquelle her, auf die die nicht gemeinsam nutzende Dateidatenquelle zeigt. Die Schritte 3 bis 5 werden nicht ausgeführt.  
  
3.  Erstellt eine Verbindungszeichenfolge für den Treiber. Die Treiberverbindungszeichenfolge ist die Vereinigung der Schlüsselwörter, die in der Dsn-Datei angegeben sind, und der Schlüsselwörter, die in der ursprünglichen Anwendungsverbindungszeichenfolge angegeben sind. Regeln für die Konstruktion der Treiberverbindungszeichenfolge, bei der sich Schlüsselwörter überlappen, lauten wie folgt:  
  
    -   Wenn das **Schlüsselwort DRIVER** in der Anwendungsverbindungszeichenfolge vorhanden ist und die von den DRIVER-Schlüsselwörtern angegebenen Treiber in der DsN-Datei und der Anwendungsverbindungszeichenfolge nicht identisch sind, werden die Treiberinformationen in der DSN-Datei ignoriert und die Treiberinformationen in der Anwendungsverbindungszeichenfolge verwendet. **DRIVER** Wenn die vom **Schlüsselwort DRIVER** angegebenen Treiber in der Dsn-Datei und der Verbindungszeichenfolge der Anwendung identisch sind, haben die in der Anwendungsverbindungszeichenfolge angegebenen Schlüsselwörter Vorrang vor den in der DSN-Datei angegebenen.  
  
    -   In der neuen Verbindungszeichenfolge wird das **Schlüsselwort FILEDSN** eliminiert.  
  
4.  Lädt den Treiber, indem sie im Registrierungseintrag HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCINST. INI\\<\>Driver Name \<,Treiber, bei dem Driver Name> durch das **DRIVER-Schlüsselwort** angegeben wird.  
  
5.  Übergibt dem Treiber die neue Verbindungszeichenfolge.  
  
 Beispiele für .dsn-Dateien finden Sie unter [Verbinden mit Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md).  
  
## <a name="savefile-keyword"></a>SAVEFILE Schlüsselwort  
 Wenn die von der Anwendung angegebene Verbindungszeichenfolge das **Schlüsselwort SAVEFILE** enthält, speichert der Treiber-Manager die Verbindungszeichenfolge in einer .dsn-Datei. Der Treiber-Manager fährt wie folgt vor:  
  
1.  Überprüft, ob der Dateiname der als Attributwert des **Schlüsselworts SAVEFILE** enthaltenen .dsn-Datei gültig ist. Ist dies nicht der Fall, wird SQL_ERROR mit SQLSTATE IM014 (Ungültiger Name der Datei DSN) zurückgegeben. Die Gültigkeit des Dateinamens wird durch Standardsystembenennungsregeln bestimmt. Wenn der Dateiname eine leere Zeichenfolge ("") ist und das *Argument DriverCompletion* nicht SQL_DRIVER_NOPROMPT ist, ist der Dateiname gültig. Wenn der Dateiname bereits vorhanden ist, wird die Datei überschrieben, wenn *DriverCompletion* SQL_DRIVER_NOPROMPT ist. Wenn *DriverCompletion* SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED ist, wird der Benutzer in einem Dialogfeld aufgefordert, anzugeben, ob die Datei überschrieben werden soll. Wenn Nein eingegeben wird, wird das Dialogfeld **Dateispeichern** angezeigt.  
  
2.  Wenn der Treiber SQL_SUCCESS zurückgibt und der Dateiname keine leere Zeichenfolge war, schreibt der Treiber-Manager die im *OutConnectionString-Argument* zurückgegebenen Verbindungsinformationen in die angegebene Datei mit dem Format, das im Abschnitt "Verbindungszeichenfolgen" weiter oben in diesem Abschnitt angegeben ist.  
  
3.  Wenn der Treiber SQL_SUCCESS zurückgibt und der Dateiname eine leere Zeichenfolge ("") war, ruft der Treiber-Manager das allgemeine Dialogfeld **Dateispeichern** mit dem angegebenen *hwnd* auf und schreibt die in *OutConnectionString* zurückgegebenen Verbindungsinformationen in die Datei, die im allgemeinen Dialogfeld Datei speichern mit dem format unten in diesem Abschnitt angegebenen Format angegeben ist.  
  
4.  Wenn der Treiber SQL_SUCCESS zurückgibt, gibt er das *OutConnectionString-Argument* zurück, das die Verbindungszeichenfolge für die Anwendung enthält.  
  
5.  Wenn der Treiber SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgibt, gibt der Treiber-Manager den SQLSTATE an die Anwendung zurück.  
  
## <a name="driver-guidelines"></a>Treiberrichtlinien  
 Der Treiber überprüft, ob die vom Treiber-Manager an ihn übergebene Verbindungszeichenfolge das **Schlüsselwort DSN** oder **DRIVER** enthält. Wenn die Verbindungszeichenfolge das **Schlüsselwort DRIVER** enthält, kann der Treiber keine Informationen über die Datenquelle aus den Systeminformationen abrufen. Wenn die Verbindungszeichenfolge das **DSN-Schlüsselwort** enthält oder weder das **DSN-** noch das **DRIVER-Schlüsselwort** enthält, kann der Treiber wie folgt Informationen über die Datenquelle aus den Systeminformationen abrufen:  
  
1.  Wenn die Verbindungszeichenfolge das **DSN-Schlüsselwort** enthält, ruft der Treiber die Informationen für die angegebene Datenquelle ab.  
  
2.  Wenn die Verbindungszeichenfolge nicht das **DSN-Schlüsselwort** enthält, die angegebene Datenquelle nicht gefunden wird oder das **DSN-Schlüsselwort** auf "DEFAULT" festgelegt ist, ruft der Treiber die Informationen für die Standarddatenquelle ab.  
  
 Der Treiber verwendet alle Informationen, die er aus den Systeminformationen abruft, um die Informationen zu erweitern, die ihm in der Verbindungszeichenfolge übergeben werden. Wenn die Informationen in den Systeminformationen Informationen in der Verbindungszeichenfolge duplizieren, verwendet der Treiber die Informationen in der Verbindungszeichenfolge.  
  
 Basierend auf dem Wert von *DriverCompletion*fordert der Treiber den Benutzer zur Eingabe von Verbindungsinformationen wie Benutzer-ID und Kennwort auf und stellt eine Verbindung mit der Datenquelle her:  
  
-   SQL_DRIVER_PROMPT: Der Treiber zeigt ein Dialogfeld an, in dem die Werte aus der Verbindungszeichenfolge und Systeminformationen (falls vorhanden) als Anfangswerte verwendet werden. Wenn der Benutzer das Dialogfeld verlässt, stellt der Treiber eine Verbindung mit der Datenquelle her. Außerdem wird eine Verbindungszeichenfolge aus dem Wert des **Schlüsselworts DSN** oder **DRIVER** in \* *InConnectionString* und den aus dem Dialogfeld zurückgegebenen Informationen erstellt. Diese Verbindungszeichenfolge wird im **OutConnectionString-Puffer* platziert.  
  
-   SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED: Wenn die Verbindungszeichenfolge genügend Informationen enthält und diese Informationen korrekt \*sind, \*stellt der Treiber eine Verbindung mit der Datenquelle her und kopiert *InConnectionString* in *OutConnectionString*. Wenn Informationen fehlen oder falsch sind, führt der Treiber dieselben Aktionen aus wie beim *SQL_DRIVER_PROMPT DriverCompletion,* mit der Ausnahme, dass der Treiber, wenn *DriverCompletion* SQL_DRIVER_COMPLETE_REQUIRED ist, die Steuerelemente für alle Informationen deaktiviert, die nicht zum Herstellen einer Verbindung mit der Datenquelle erforderlich sind.  
  
-   SQL_DRIVER_NOPROMPT: Wenn die Verbindungszeichenfolge genügend Informationen enthält, stellt \*der Treiber \*eine Verbindung mit der Datenquelle her und kopiert *InConnectionString* in *OutConnectionString*. Andernfalls gibt der Treiber SQL_ERROR für **SQLDriverConnect**zurück.  
  
 Bei erfolgreicher Verbindung mit der Datenquelle \*legt der Treiber auch *StringLength2Ptr* auf die Länge der Ausgabeverbindungszeichenfolge fest, die in **OutConnectionString*zurückgegeben werden kann.  
  
 Wenn der Benutzer ein Dialogfeld abbricht, das vom Treiber-Manager oder vom Treiber angezeigt wird, gibt **SQLDriverConnect** SQL_NO_DATA zurück.  
  
 Informationen dazu, wie der Treiber-Manager und der Treiber während des Verbindungsvorgangs interagieren, finden Sie unter [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Wenn ein Treiber **SQLDriverConnect**unterstützt, muss der Schlüsselwortabschnitt des Treibers der Systeminformationen für den Treiber das **Schlüsselwort ConnectFunctions** mit dem zweiten Zeichensatz auf "Y" enthalten.  
  
## <a name="connecting-when-connection-pooling-is-enabled"></a>Herstellen einer Verbindung, wenn das Verbindungspooling aktiviert ist  
 Durch das Verbindungspooling kann eine Anwendung eine bereits erstellte Verbindung wiederverwenden. Wenn **SQLDriverConnect** aufgerufen wird, versucht der Treiber-Manager, die Verbindung mithilfe einer Verbindung herzustellen, die Teil eines Verbindungspools in einer Umgebung ist, die für das Verbindungspooling vorgesehen ist. Weitere Informationen zum Verbindungspooling finden Sie unter [SQLConnect Function](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Eine Anwendung kann SQL_ATTR_RESET_CONNECTION festlegen, bevor SQLDisconnect für eine Verbindung aufgerufen wird, bei der das Pooling aktiviert ist. Weitere Informationen finden Sie unter [SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Die folgenden Einschränkungen gelten, wenn eine Anwendung **SQLDriverConnect** aufruft, um eine Verbindung mit einer gepoolten Verbindung herzustellen:  
  
-   Es wird keine Verbindungspooling-Verarbeitung durchgeführt, wenn das **Schlüsselwort SAVEFILE** in der Verbindungszeichenfolge angegeben wird.  
  
-   Wenn das Verbindungspooling aktiviert ist, kann **SQLDriverConnect** nur mit dem *DriverCompletion-Argument* von SQL_DRIVER_NOPROMPT aufgerufen werden. Wenn **SQLDriverConnect** mit anderen *DriverCompletion*aufgerufen wird, wird SQLSTATE HY110 (Invalid driver completion) zurückgegeben.  
  
## <a name="connection-attributes"></a>Verbindungsattribute  
 Das SQL_ATTR_LOGIN_TIMEOUT Verbindungsattribut, das mit **SQLSetConnectAttr**festgelegt wird, definiert die Anzahl der Sekunden, die gewartet werden soll, bis eine Anmeldeanforderung mit einer erfolgreichen Verbindung durch den Treiber abgeschlossen ist, bevor sie zur Anwendung zurückkehrt. Wenn der Benutzer aufgefordert wird, die Verbindungszeichenfolge abzuschließen, beginnt eine Wartezeit für jede Anmeldeanforderung, wenn der Treiber den Verbindungsprozess startet.  
  
 Der Treiber öffnet die Verbindung standardmäßig im SQL_MODE_READ_WRITE Zugriffsmodus. Um den Zugriffsmodus auf SQL_MODE_READ_ONLY festzulegen, muss die Anwendung **SQLSetConnectAttr** mit dem Attribut SQL_ATTR_ACCESS_MODE aufrufen, bevor **SIE SQLDriverConnect**aufruft.  
  
 Wenn in den Systeminformationen für die Datenquelle eine Standardübersetzungsbibliothek angegeben ist, lädt der Treiber sie. Eine andere Übersetzungsbibliothek kann geladen werden, indem **SQLSetConnectAttr** mit dem Attribut SQL_ATTR_TRANSLATE_LIB aufgerufen wird. Eine Übersetzungsoption kann durch Aufrufen von **SQLSetConnectAttr** mit der Option SQL_ATTR_TRANSLATE_OPTION angegeben werden.  
  
 Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
```cpp  
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
  
 Siehe auch [Beispiel ODBC-Programm](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuweisen eines Griffs|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Ermitteln und Aufzählen von Werten, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Trennen der Verbindung zu einer Datenquelle|[SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Zurückgeben von Treiberbeschreibungen und -attributen|[SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Befreien eines Griffs|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Festlegen eines Verbindungsattributs|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
