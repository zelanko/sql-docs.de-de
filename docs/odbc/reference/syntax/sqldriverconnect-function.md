---
description: SQLDriveConnect-Funktion
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6abdafe0a01d5c8182c5427c45545930c84e08e4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476143"
---
# <a name="sqldriverconnect-function"></a>SQLDriveConnect-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLDriverConnect** ist eine Alternative zu **SQLCONNECT**. Es werden Datenquellen unterstützt, die mehr Verbindungsinformationen benötigen als die drei Argumente in **SQLCONNECT**, Dialogfeldern, um den Benutzer zur Eingabe von allen Verbindungsinformationen und Datenquellen aufzufordern, die nicht in den Systeminformationen definiert sind.  
  
 **SQLDriverConnect** stellt die folgenden Verbindungs Attribute bereit:  
  
-   Stellen Sie eine Verbindung mithilfe einer Verbindungs Zeichenfolge her, die den Datenquellen Namen, eine oder mehrere Benutzer-IDs, ein oder mehrere Kenn Wörter und andere Informationen enthält, die von der Datenquelle benötigt werden.  
  
-   Herstellen einer Verbindung mithilfe einer partiellen Verbindungs Zeichenfolge oder ohne zusätzliche Informationen in diesem Fall können der Treiber-Manager und der Treiber alle den Benutzer zur Eingabe von Verbindungsinformationen auffordern.  
  
-   Stellen Sie eine Verbindung mit einer Datenquelle her, die nicht in den Systeminformationen definiert ist. Wenn die Anwendung eine partielle Verbindungs Zeichenfolge bereitstellt, kann der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordern.  
  
-   Stellen Sie eine Verbindung mit einer Datenquelle her, indem Sie eine aus den Informationen in einer DSN-Datei erstellte Verbindungs Zeichenfolge verwenden.  
  
 Nachdem eine Verbindung hergestellt wurde, gibt **SQLDriverConnect** die abgeschlossene Verbindungs Zeichenfolge zurück. Die Anwendung kann diese Zeichenfolge für nachfolgende Verbindungsanforderungen verwenden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
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
 Der Fenster handle. Die Anwendung kann ggf. das Handle des übergeordneten Fensters übergeben oder einen NULL-Zeiger, wenn entweder das Fenster Handle nicht anwendbar ist oder wenn **SQLDriverConnect** keine Dialogfelder enthält.  
  
 *InConnectionString*  
 Der Eine vollständige Verbindungs Zeichenfolge (siehe die Syntax in "comments"), eine partielle Verbindungs Zeichenfolge oder eine leere Zeichenfolge.  
  
 *StringLength1*  
 Der Länge von **InConnectionString*, in Zeichen, wenn die Zeichenfolge Unicode ist, oder bytes, wenn die Zeichenfolge ANSI oder DBCS ist.  
  
 *Outconnectionstring*  
 Ausgeben Zeiger auf einen Puffer für die abgeschlossene Verbindungs Zeichenfolge. Bei erfolgreicher Verbindung mit der Ziel Datenquelle enthält dieser Puffer die abgeschlossene Verbindungs Zeichenfolge. Anwendungen sollten für diesen Puffer mindestens 1.024 Zeichen zuordnen.  
  
 Wenn *outconnectionstring* gleich NULL ist, gibt *StringLength2Ptr* weiterhin die Gesamtzahl der Zeichen zurück (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den von *outconnectionstring*verwiesen wird.  
  
 *BufferLength*  
 Der Länge des **outconnectionstring* -Puffers in Zeichen.  
  
 *StringLength2Ptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (ausgenommen des NULL-Beendigungs Zeichens) zurückgegeben werden soll, die in \* *outconnectionstring*zurückgegeben werden können. Wenn die Anzahl der zurück zugebende Zeichen größer als oder gleich *BufferLength*ist, wird die abgeschlossene Verbindungs Zeichenfolge in \* *outconnectionstring* auf *BufferLength* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
 *DriverCompletion*  
 Der Flag, das angibt, ob der Treiber-Manager oder Treiber weitere Verbindungsinformationen anfordern muss:  
  
 SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED oder SQL_DRIVER_NOPROMPT.  
  
 (Weitere Informationen finden Sie unter "Kommentare").  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDriverConnect** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *ftortype* SQL_HANDLE_DBC und einem *hHandle* von *connectionHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLDriverConnect** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Der Puffer \* *outconnectionstring* war nicht groß genug, um die gesamte Verbindungs Zeichenfolge zurückzugeben, daher wurde die Verbindungs Zeichenfolge abgeschnitten. Die Länge der nicht abgeschnittene Verbindungs Zeichenfolge wird in **StringLength2Ptr*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S00|Ungültiges Verbindungs Zeichen folgen Attribut.|In der Verbindungs Zeichenfolge (*InConnectionString*) wurde ein ungültiges Attribut Schlüsselwort angegeben, aber der Treiber war trotzdem in der Lage, eine Verbindung mit der Datenquelle herzustellen. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s02 entsprechen|Optionswert geändert|Der Treiber hat den angegebenen Wert, auf den das *ValuePtr* -Argument in **SQLSetConnectAttr** zeigt, nicht unterstützt und einen ähnlichen Wert ersetzt. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s08|Fehler beim Speichern des Datei-DSN|Die Zeichenfolge in * \* InConnectionString* enthielt ein **FILEDSN** -Schlüsselwort, aber die DSN-Datei wurde nicht gespeichert. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s09|Ungültiges Schlüsselwort|(DM) die Zeichenfolge in * \* InConnectionString* enthielt ein **SaveFile** -Schlüsselwort, aber keinen **Treiber** oder ein **FILEDSN** -Schlüsselwort. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08001|Der Client kann keine Verbindung herstellen.|Der Treiber konnte keine Verbindung mit der Datenquelle herstellen.|  
|08002|Der Verbindungs Name wird verwendet.|(DM) das angegebene *connectionHandle* wurde bereits verwendet, um eine Verbindung mit einer Datenquelle herzustellen, und die Verbindung war immer noch geöffnet.|  
|08004|Der Server hat die Verbindung abgelehnt.|Die Datenquelle hat die Einrichtung der Verbindung aus Implementierungs Gründen abgelehnt.|  
|08S01|Kommunikations Verbindungsfehler|Der Kommunikationslink zwischen dem Treiber und der Datenquelle, mit dem der Treiber eine Verbindung herzustellen versuchte, ist fehlgeschlagen, bevor die **SQLDriverConnect** -Funktion die Verarbeitung abgeschlossen hat.|  
|28000|Ungültige Autorisierungs Spezifikation|Entweder die Benutzer-ID oder die Autorisierungs Zeichenfolge, wie in der Verbindungs Zeichenfolge (*InConnectionString*) angegeben, verstoßen die von der Datenquelle definierten Einschränkungen.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* szmessagetext* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY000|Allgemeiner Fehler: Ungültiger Datei-DSN.|(DM) die Zeichenfolge in **InConnectionString* enthielt ein FILEDSN-Schlüsselwort, aber der Name der DSN-Datei wurde nicht gefunden.|  
|HY000|Allgemeiner Fehler: der Datei Puffer kann nicht erstellt werden.|(DM) die Zeichenfolge in **InConnectionString* enthielt ein FILEDSN-Schlüsselwort, aber die DSN-Datei war nicht lesbar.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber-Manager konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der **SQLDriverConnect** -Funktion erforderlich ist.<br /><br /> Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *connectionHandle*aktiviert. Die Funktion wurde aufgerufen, und vor der Ausführung der Ausführung wurde die [sqlcancelhandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) für *connectionHandle*aufgerufen, und anschließend wurde die **SQLDriverConnect** -Funktion für *connectionHandle*erneut aufgerufen.<br /><br /> Oder die **SQLDriverConnect** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **sqlcancelhandle** für *connectionHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine andere asynchron ausgeführte Funktion (nicht **SQLDriverConnect**) wurde für *connectionHandle* aufgerufen und wird noch ausgeführt, als die **SQLDriverConnect** -Funktion aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der **SQLDriverConnect** -Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der für das Argument *StringLength1* angegebene Wert war kleiner als 0 (null) und war nicht gleich SQL_NTS.<br /><br /> (DM) der für das Argument *BufferLength* angegebene Wert war kleiner als 0 (null).|  
|HY092|Ungültiger Attribut/Options Bezeichner|(DM) das *DriverCompletion* -Argument wurde SQL_DRIVER_PROMPT, und das *WindowHandle* -Argument war ein NULL-Zeiger.|  
|HY110|Ungültiger Treiber Abschluss.|(DM) der für das Argument *DriverCompletion* angegebene Wert war nicht gleich SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED oder SQL_DRIVER_NOPROMPT.<br /><br /> (DM) das Verbindungspooling wurde aktiviert, und der für das Argument *DriverCompletion* angegebene Wert war nicht gleich SQL_DRIVER_NOPROMPT.|  
|HYC00|Optionales Feature nicht implementiert|Der Treiber unterstützt nicht die von der Anwendung angeforderte Version des ODBC-Verhaltens.|  
|HYT00|Timeout abgelaufen|Der Anmeldungs Timeout Zeitraum ist abgelaufen, bevor die Verbindung mit der Datenquelle abgeschlossen wurde. Der Timeout Zeitraum wird mithilfe von **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der Treiber, der dem angegebenen Datenquellen Namen entspricht, unterstützt die-Funktion nicht.|  
|IM002|Die Datenquelle wurde nicht gefunden und es wurde kein Standardtreiber angegeben.|(DM) der in der Verbindungs Zeichenfolge (*InConnectionString*) angegebene Datenquellen Name wurde in den Systeminformationen nicht gefunden, und es gab keine Standardtreiber Spezifikation.<br /><br /> (DM) ODBC-Datenquelle und Standardtreiber Informationen konnten in den Systeminformationen nicht gefunden werden.|  
|IM003|Der angegebene Treiber konnte nicht geladen werden.|(DM) der in der Datenquellen Spezifikation in den Systeminformationen oder durch das **Treiber** Schlüsselwort angegebene Treiber wurde nicht gefunden oder konnte aus einem anderen Grund nicht geladen werden.|  
|IM004|Fehler beim Treiber " **sqlzugewiesene CHandle** " auf SQL_HANDLE_ENV|(DM) bei der **SQLDriverConnect**-Funktion hat der Treiber-Manager die **sqlzuweisung** -Funktion des Treibers mit einem *ftortype* von SQL_HANDLE_ENV aufgerufen, und der Treiber hat einen Fehler zurückgegeben.|  
|IM005|Fehler beim Treiber von **sqlzugewiesene CHandle** auf SQL_HANDLE_DBC.|(DM) bei der **SQLDriverConnect**-Funktion hat der Treiber-Manager die **sqlzuweisung** -Funktion des Treibers mit einem *ftortype* von SQL_HANDLE_DBC aufgerufen, und der Treiber hat einen Fehler zurückgegeben.|  
|IM006|Fehler bei ' **SQLSetConnectAttr** ' des Treibers.|(DM) während der **SQLDriverConnect**-Funktion hat der Treiber-Manager die **SQLSetConnectAttr** -Funktion des Treibers aufgerufen, und der Treiber hat einen Fehler zurückgegeben.|  
|IM007|Es wurden keine Datenquellen oder Treiber angegeben. Dialogfeld unzulässig|In der Verbindungs Zeichenfolge wurde kein Datenquellen Name oder-Treiber angegeben, und der *DriverCompletion* wurde SQL_DRIVER_NOPROMPT.|  
|IM008|Dialog Fehler|Der Treiber hat versucht, das Anmelde Dialogfeld anzuzeigen und ist fehlgeschlagen.<br /><br /> *WindowHandle* war ein NULL-Zeiger, und der *DriverCompletion* war nicht SQL_DRIVER_NO_PROMPT.|  
|IM009|Übersetzungs-DLL kann nicht geladen werden.|Der Treiber konnte die Übersetzungs-DLL, die für die Datenquelle oder die Verbindung angegeben wurde, nicht laden.|  
|IM010|Der Datenquellen Name ist zu lang.|(DM) der Attribut Wert für das DSN-Schlüsselwort ist länger als SQL_MAX_DSN_LENGTH Zeichen.|  
|IM011|Der Treiber Name ist zu lang.|(DM) der Attribut Wert für das **Treiber** Schlüsselwort ist länger als 255 Zeichen.|  
|IM012|Syntax Fehler für Treiber Schlüsselwort|(DM) das Schlüsselwort-Wert-Paar für das **Treiber** Schlüsselwort enthielt einen Syntax Fehler.<br /><br /> (DM) die Zeichenfolge in * \* InConnectionString* enthielt ein **FILEDSN** -Schlüsselwort, aber die DSN-Datei enthielt kein **Treiber** Schlüsselwort oder **DSN** -Schlüsselwort.|  
|IM014|Der angegebene DSN enthält einen Architektur Konflikt zwischen dem Treiber und der Anwendung.|(DM) 32-Bit-Anwendung verwendet einen DSN, der eine Verbindung mit einem 64-Bit-Treiber herstellt. oder umgekehrt.|  
|IM015|Fehler des Treibers SQLDriverConnect auf SQL_HANDLE_DBC_INFO_HANDLE|Wenn ein Treiber SQL_ERROR zurückgibt, wird der Treiber-Manager SQL_ERROR an die Anwendung zurückgegeben, und die Verbindung wird nicht hergestellt.<br /><br /> Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [entwickeln von Verbindungs Pool Informationen in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
|S1118|Der Treiber unterstützt keine asynchrone Benachrichtigung.|Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, können Sie SQL_ATTR_ASYNC_DBC_EVENT oder SQL_ATTR_ASYNC_DBC_RETCODE_PTR nicht festlegen.|  
  
## <a name="comments"></a>Kommentare  
 Eine Verbindungs Zeichenfolge weist die folgende Syntax auf:  
  
 *Connection-String* :: = *empty-string*[;] &#124; *Attribut*[;] &#124; *Attribut*; *Verbindungs Zeichenfolge*  
  
 *empty-string* :: =*Attribute* :: = *Attribute-Keywords* = *Attribute-Value* &#124; Driver = [{]*Attribut-Wert*[}]  
  
 *Attribute-Keywords* :: = DSN &#124; UID &#124; pwd &#124; *Driver-defined-Attribute-Schlüsselwort*  
  
 *Attribute-Value* :: = *Zeichenfolge*  
  
 *Driver-defined-Attribute-Keywords* :: = *Identifier*  
  
 , wenn die *Zeichenfolge* NULL oder mehr Zeichen enthält. der *Bezeichner* weist mindestens ein Zeichen auf. beim *Attribut Schlüsselwort* wird die Groß-/Kleinschreibung nicht beachtet. bei *Attribut Wert* kann die Groß-/Kleinschreibung beachtet werden. und der Wert des **DSN** -Schlüssel Worts besteht nicht ausschließlich aus Leerzeichen.  
  
 Aufgrund der Verbindungs Zeichenfolge und der Initialisierungsdatei Grammatik, Schlüsselwörter und Attributwerte, die die Zeichen **[] {} (),;? \* =! @** ist nicht in geschweifte Klammern eingeschlossen. Der Wert des **DSN** -Schlüssel Worts darf nicht nur aus Leerzeichen bestehen und darf keine führenden Leerzeichen enthalten. Aufgrund der Grammatik der Systeminformationen dürfen Schlüsselwörter und Datenquellen Namen keinen umgekehrten Schrägstrich () enthalten \\ .  
  
 Anwendungen müssen nach dem **Treiber** Schlüsselwort keine geschweiften Klammern um den Attribut Wert hinzufügen, es sei denn, das Attribut enthält ein Semikolon (;). in diesem Fall sind die geschweiften Klammern erforderlich. Wenn der vom Treiber empfangene Attribut Wert geschweifte Klammern enthält, sollte der Treiber Sie nicht entfernen, sondern muss Teil der zurückgegebenen Verbindungs Zeichenfolge sein.  
  
 Ein DSN-oder Verbindungs Zeichen folgen Wert, der in geschweifte Klammern ( {} ) eingeschlossen ist, die ein beliebiges Zeichen **[] {} (),;? \* =! @** wird intakt an den Treiber übermittelt. Wenn diese Zeichen jedoch in einem Schlüsselwort verwendet werden, gibt der Treiber-Manager beim Arbeiten mit Datei-DSNs einen Fehler zurück, übergibt jedoch die Verbindungs Zeichenfolge an den Treiber für reguläre Verbindungs Zeichenfolgen. Vermeiden Sie die Verwendung eingebetteter Klammern in einem Schlüsselwort Wert.  
  
 Die Verbindungs Zeichenfolge kann eine beliebige Anzahl von Treiber definierten Schlüsselwörtern enthalten. Da das **Treiber** Schlüsselwort keine Informationen aus den Systeminformationen verwendet, muss der Treiber genügend Schlüsselwörter definieren, damit ein Treiber nur mit den Informationen in der Verbindungs Zeichenfolge eine Verbindung mit einer Datenquelle herstellen kann. (Weitere Informationen finden Sie unter "Treiber Richtlinien" weiter unten in diesem Abschnitt.) Der Treiber definiert, welche Schlüsselwörter erforderlich sind, um eine Verbindung mit der Datenquelle herzustellen.  
  
 In der folgenden Tabelle werden die Attributwerte der Schlüsselwörter **DSN**, **FILEDSN**, **Driver**, **UID**, **pwd**und **SaveFile** beschrieben.  
  
|Schlüsselwort|Attribut Wert Beschreibung|  
|-------------|---------------------------------|  
|**DSN**|Der Name einer Datenquelle, wie von **SQLDataSources** oder dem Dialogfeld Datenquellen von **SQLDriverConnect**zurückgegeben.|  
|**FILEDSN**|Der Name einer DSN-Datei, aus der eine Verbindungs Zeichenfolge für die Datenquelle erstellt wird. Diese Datenquellen werden als Datei Datenquellen bezeichnet.|  
|**Trei**|Die Beschreibung des Treibers, wie von der **SQLDrivers** -Funktion zurückgegeben. Beispielsweise RDB oder SQL Server.|  
|**UID**|Eine Benutzer-ID.|  
|**PWD**|Das Kennwort für die Benutzer-ID oder eine leere Zeichenfolge, wenn kein Kennwort für die Benutzer-ID (PWD =;) vorhanden ist.|  
|**SaveFile**|Der Dateiname einer DSN-Datei, in der die Attributwerte von Schlüsselwörtern, die zum Herstellen der aktuellen, erfolgreichen Verbindung verwendet werden, gespeichert werden sollen.|  
  
 Informationen dazu, wie eine Anwendung eine Datenquelle oder einen Treiber auswählt, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Wenn Schlüsselwörter in der Verbindungs Zeichenfolge wiederholt werden, verwendet der Treiber den Wert, der mit dem ersten Vorkommen des Schlüssel Worts verknüpft ist. Wenn die **DSN** -und **Treiber** Schlüsselwörter in derselben Verbindungs Zeichenfolge enthalten sind, wird der Treiber-Manager und der Treiber zuerst das jeweils angezeigte Schlüsselwort verwenden.  
  
 Die Schlüsselwörter " **FILEDSN** " und " **DSN** " schließen sich gegenseitig aus: welches Schlüsselwort zuerst angezeigt wird, wird verwendet, und das zweite wird ignoriert. Die Schlüsselwörter " **FILEDSN** " und " **Driver** " hingegen schließen sich nicht gegenseitig aus. Wenn ein beliebiges Schlüsselwort in einer Verbindungs Zeichenfolge mit **FILEDSN**angezeigt wird, wird der Attribut Wert des Schlüssel Worts in der Verbindungs Zeichenfolge anstelle des Attribut Werts desselben Schlüssel Worts in der DSN-Datei verwendet.  
  
 Wenn das **FILEDSN** -Schlüsselwort verwendet wird, werden die in einer DSN-Datei angegebenen Schlüsselwörter verwendet, um eine Verbindungs Zeichenfolge zu erstellen. (Weitere Informationen finden Sie unter "Datei Datenquellen" weiter unten in diesem Abschnitt.) Das **UID** -Schlüsselwort ist optional. eine DSN-Datei kann nur mit dem **Treiber** Schlüsselwort erstellt werden. Das **pwd** -Schlüsselwort wird nicht in einer DSN-Datei gespeichert. Das Standardverzeichnis zum Speichern und Laden einer DSN-Datei ist eine Kombination aus dem Pfad, der von **commonfiledir** in HKEY_LOCAL_MACHINE \software\microsoft\ Windows\CurrentVersion und "odbc\datasources" angegeben wird. (Wenn commonfiledir "c:\Programme\Gemeinsame Dateien" lauten, lautet das Standardverzeichnis "c:\Programme\Gemeinsame Dateien\ODBC\Data Sources".)  
  
> [!NOTE]  
>  Eine DSN-Datei kann direkt bearbeitet werden, indem die Funktionen [sqllofiledsn](../../../odbc/reference/syntax/sqlreadfiledsn-function.md) und [sqlschreitefiledsn](../../../odbc/reference/syntax/sqlwritefiledsn-function.md) in der Installationsprogramm-dll aufgerufen werden.  
  
 Wenn das Schlüsselwort " **SaveFile** " verwendet wird, werden die Attributwerte von Schlüsselwörtern, die zum Herstellen der aktuellen, erfolgreichen Verbindung verwendet werden, als DSN-Datei mit dem Namen des Attribut Werts des **SaveFile** -Schlüssel Worts gespeichert. Das Schlüsselwort " **SaveFile** " muss in Verbindung mit dem **Treiber** Schlüsselwort, dem **FILEDSN** -Schlüsselwort oder beidem verwendet werden, oder die Funktion gibt SQL_SUCCESS_WITH_INFO mit SQLSTATE 01s09 (ungültiges Schlüsselwort) zurück. Das Schlüsselwort " **SaveFile** " muss vor dem **Treiber** Schlüsselwort in der Verbindungs Zeichenfolge angezeigt werden, oder die Ergebnisse sind nicht definiert.  
  
## <a name="driver-manager-guidelines"></a>Leitfaden für Treiber-Manager  
 Der Treiber-Manager erstellt eine Verbindungs Zeichenfolge, die an den Treiber im *InConnectionString* -Argument der **SQLDriverConnect** -Funktion des Treibers übergeben werden soll. Der Treiber-Manager ändert das *InConnectionString* -Argument nicht, das von der Anwendung an ihn übermittelt wurde.  
  
 Die Aktion des Treiber-Managers basiert auf dem Wert des *DriverCompletion* -Arguments:  
  
-   SQL_DRIVER_PROMPT: Wenn die Verbindungs Zeichenfolge weder das **Treiber**-, **DSN**-oder **FILEDSN** -Schlüsselwort enthält, zeigt der Treiber-Manager das Dialogfeld Datenquellen an. Er erstellt eine Verbindungs Zeichenfolge aus dem Datenquellen Namen, der vom Dialogfeld zurückgegeben wird, und allen anderen, von der Anwendung an ihn über gebenden Schlüsselwörtern. Wenn der vom Dialogfeld zurückgegebene Datenquellen Name leer ist, gibt der Treiber-Manager das Schlüsselwort-Wert-Paar DSN = default an. (In diesem Dialogfeld wird keine Datenquelle mit dem Namen "Default" angezeigt.)  
  
-   SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED: Wenn die von der Anwendung angegebene Verbindungs Zeichenfolge das **DSN** -Schlüsselwort enthält, kopiert der Treiber-Manager die von der Anwendung angegebene Verbindungs Zeichenfolge. Andernfalls werden die gleichen Aktionen wie bei SQL_DRIVER_PROMPT von " *DriverCompletion* " durchführt.  
  
-   SQL_DRIVER_NOPROMPT: der Treiber-Manager kopiert die von der Anwendung angegebene Verbindungs Zeichenfolge.  
  
 Wenn die von der Anwendung angegebene Verbindungs Zeichenfolge das **Treiber** Schlüsselwort enthält, kopiert der Treiber-Manager die von der Anwendung angegebene Verbindungs Zeichenfolge.  
  
 Mithilfe der erstellten Verbindungs Zeichenfolge bestimmt der Treiber-Manager den zu verwendenden Treiber, stellt eine Verbindung mit diesem Treiber her und übergibt die erstellte Verbindungs Zeichenfolge an den Treiber. Weitere Informationen zur Interaktion des Treiber-Managers und des Treibers finden Sie im Abschnitt "Kommentare" in der [SQLCONNECT-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md). Wenn die Verbindungs Zeichenfolge das **Treiber** Schlüsselwort nicht enthält, bestimmt der Treiber-Manager den zu verwendenden Treiber wie folgt:  
  
1.  Wenn die Verbindungs Zeichenfolge das **DSN** -Schlüsselwort enthält, ruft der Treiber-Manager den Treiber ab, der der Datenquelle aus den Systeminformationen zugeordnet ist.  
  
2.  Wenn die Verbindungs Zeichenfolge das **DSN** -Schlüsselwort nicht enthält oder die Datenquelle nicht gefunden wird, ruft der Treiber-Manager den Treiber ab, der der Standarddaten Quelle aus den Systeminformationen zugeordnet ist. (Weitere Informationen finden Sie unter [Standard Unterschlüssel](../../../odbc/reference/install/default-subkey.md).) Der Treiber-Manager ändert den Wert des **DSN** -Schlüssel Worts in der Verbindungs Zeichenfolge in "Default".  
  
3.  Wenn das **DSN** -Schlüsselwort in der Verbindungs Zeichenfolge auf "Default" festgelegt ist, ruft der Treiber-Manager den Treiber ab, der der Standarddaten Quelle aus den Systeminformationen zugeordnet ist.  
  
4.  Wenn die Datenquelle nicht gefunden wird und die Standarddaten Quelle nicht gefunden wird, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE IM002 zurück (die Datenquelle wurde nicht gefunden, und es wurde kein Standardtreiber angegeben).  
  
## <a name="file-data-sources"></a>Dateidatenquellen  
 Wenn die von der Anwendung im Befehl **SQLDriverConnect** angegebene Verbindungs Zeichenfolge das **FILEDSN** -Schlüsselwort enthält und dieses Schlüsselwort nicht durch das **DSN** -oder **Treiber** Schlüsselwort ersetzt wird, erstellt der Treiber-Manager mithilfe der Informationen in der DSN-Datei und des *InConnectionString* -Arguments eine Verbindungs Zeichenfolge. Der Treiber-Manager wird wie folgt fortgesetzt:  
  
1.  Überprüft, ob der Dateiname der DSN-Datei gültig ist. Wenn dies nicht der Fall ist, wird SQL_ERROR mit SQLSTATE IM014 (Ungültiger Name des Datei-DSN) zurückgegeben. Wenn der Dateiname eine leere Zeichenfolge ("") ist und SQL_DRIVER_NOPROMPT nicht angegeben ist, wird das Dialogfeld **Datei öffnen** angezeigt. Wenn der Dateiname einen gültigen Pfad, aber keinen Dateinamen oder einen ungültigen Dateinamen enthält und SQL_DRIVER_NOPROMPT nicht angegeben ist, wird das Dialogfeld **Datei öffnen** angezeigt, in dem das aktuelle Verzeichnis auf das im Dateinamen angegebene Verzeichnis festgelegt ist. Wenn der Dateiname eine leere Zeichenfolge ("") ist oder der Dateiname einen gültigen Pfad, aber keinen Dateinamen oder einen ungültigen Dateinamen enthält, und SQL_DRIVER_NOPROMPT angegeben ist, wird SQL_ERROR mit SQLSTATE IM014 (Ungültiger Name der Datei-DSN) zurückgegeben.  
  
2.  Liest alle Schlüsselwörter im Abschnitt [ODBC] der DSN-Datei. Wenn das **Driver** -Schlüsselwort nicht vorhanden ist, wird SQL_ERROR mit SQLSTATE IM012 (Treiber-Schlüsselwort Syntax Fehler) zurückgegeben, es sei denn, die DSN-Datei ist nicht mehr verfügbar und enthält daher nur das **DSN** -Schlüsselwort.  
  
     Wenn die Datei Datenquelle nicht Share fähig ist, liest der Treiber-Manager den Wert des **DSN** -Schlüssel Worts und stellt nach Bedarf eine Verbindung mit der Benutzer-oder Systemdaten Quelle her, auf die von der nicht Share baren Datei Datenquelle verwiesen wird. Die Schritte 3 bis 5 werden nicht ausgeführt.  
  
3.  Erstellt eine Verbindungs Zeichenfolge für den Treiber. Die Verbindungs Zeichenfolge des Treibers ist die Vereinigung der in der DSN-Datei angegebenen Schlüsselwörter und der in der ursprünglichen Anwendungs Verbindungs Zeichenfolge angegebenen Schlüsselwörter. Die Regeln für die Erstellung der Treiber Verbindungs Zeichenfolge, in der Schlüsselwörter überlappen, lauten wie folgt:  
  
    -   Wenn das **Treiber** Schlüsselwort in der Verbindungs Zeichenfolge der Anwendung vorhanden ist und die von den **Treiber** Schlüsselwörtern angegebenen Treiber in der DSN-Datei und der Verbindungs Zeichenfolge der Anwendung nicht identisch sind, werden die Treiber Informationen in der DSN-Datei ignoriert und die Treiber Informationen in der Anwendungs Verbindungs Zeichenfolge verwendet. Wenn die vom **Treiber** Schlüsselwort angegebenen Treiber in der DSN-Datei und in der Verbindungs Zeichenfolge der Anwendung identisch sind, wenn sich alle Schlüsselwörter überlappen, haben diejenigen, die in der Anwendungs Verbindungs Zeichenfolge angegeben sind, Vorrang vor den in der DSN-Datei angegebenen.  
  
    -   In der neuen Verbindungs Zeichenfolge wird das **FILEDSN** -Schlüsselwort gelöscht.  
  
4.  Der Treiber wird geladen, indem der Registrierungs Eintrag HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST.INI\\<Treiber Name \> \Driver durchsucht wird, wobei \<Driver Name> durch das **Treiber** Schlüsselwort angegeben wird.  
  
5.  Übergibt den Treiber an die neue Verbindungs Zeichenfolge.  
  
 Beispiele für DSN-Dateien finden Sie unter [Herstellen einer Verbindung mithilfe von Datei Datenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md).  
  
## <a name="savefile-keyword"></a>SaveFile-Schlüsselwort  
 Wenn die von der Anwendung angegebene Verbindungs Zeichenfolge das **SaveFile** -Schlüsselwort enthält, speichert der Treiber-Manager die Verbindungs Zeichenfolge in einer DSN-Datei. Der Treiber-Manager wird wie folgt fortgesetzt:  
  
1.  Überprüft, ob der Dateiname der DSN-Datei, die als Attribut Wert des Schlüssel Worts **SaveFile** enthalten ist, gültig ist. Wenn dies nicht der Fall ist, wird SQL_ERROR mit SQLSTATE IM014 (Ungültiger Name des Datei-DSN) zurückgegeben. Die Gültigkeit des Datei namens wird durch standardmäßige System Benennungs Regeln bestimmt. Wenn der Dateiname eine leere Zeichenfolge ("") ist und das *DriverCompletion* -Argument nicht SQL_DRIVER_NOPROMPT ist, ist der Dateiname gültig. Wenn der Dateiname bereits vorhanden ist, wird die Datei überschrieben, wenn *DriverCompletion* SQL_DRIVER_NOPROMPT wird. Wenn *DriverCompletion* SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED ist, wird der Benutzer in einem Dialogfeld aufgefordert anzugeben, anzugeben, ob die Datei überschrieben werden soll. Wenn kein eingegeben wird, wird das Dialogfeld **Datei speichern** angezeigt.  
  
2.  Wenn der Treiber SQL_SUCCESS zurückgibt und der Dateiname keine leere Zeichenfolge ist, schreibt der Treiber-Manager die im *outconnectionstring* -Argument zurückgegebenen Verbindungsinformationen in die angegebene Datei mit dem im Abschnitt "Verbindungs Zeichenfolgen" weiter oben in diesem Abschnitt angegebenen Format.  
  
3.  Wenn der Treiber SQL_SUCCESS zurückgibt und der Dateiname eine leere Zeichenfolge ("") war, ruft der Treiber-Manager das Dialogfeld " **Datei speichern** (allgemein)" mit dem angegebenen *HWND* auf und schreibt die in " *outconnectionstring* " zurückgegebenen Verbindungsinformationen in die Datei, die im Abschnitt "Verbindungs Zeichenfolgen" weiter oben in diesem Abschnitt angegeben ist.  
  
4.  Wenn der Treiber SQL_SUCCESS zurückgibt, wird das *outconnectionstring* -Argument zurückgegeben, das die Verbindungs Zeichenfolge für die Anwendung enthält.  
  
5.  Wenn der Treiber SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgibt, gibt der Treiber-Manager SQLSTATE an die Anwendung zurück.  
  
## <a name="driver-guidelines"></a>Treiber Richtlinien  
 Der Treiber überprüft, ob die Verbindungs Zeichenfolge, die vom Treiber-Manager an ihn übermittelt wurde, das Schlüsselwort **DSN** oder **Treiber** enthält Wenn die Verbindungs Zeichenfolge das **Treiber** Schlüsselwort enthält, kann der Treiber keine Informationen über die Datenquelle aus den Systeminformationen abrufen. Wenn die Verbindungs Zeichenfolge das **DSN** -Schlüsselwort enthält oder weder das **DSN** -noch das **Driver** -Schlüsselwort enthält, kann der Treiber Informationen über die Datenquelle wie folgt aus den Systeminformationen abrufen:  
  
1.  Wenn die Verbindungs Zeichenfolge das **DSN** -Schlüsselwort enthält, ruft der Treiber die Informationen für die angegebene Datenquelle ab.  
  
2.  Wenn die Verbindungs Zeichenfolge das **DSN** -Schlüsselwort nicht enthält, die angegebene Datenquelle nicht gefunden wurde oder das **DSN** -Schlüsselwort auf "Default" festgelegt ist, ruft der Treiber die Informationen für die Standarddaten Quelle ab.  
  
 Der Treiber verwendet alle Informationen, die er aus den Systeminformationen abruft, um die an ihn abgerufenen Informationen in der Verbindungs Zeichenfolge zu erweitern. Wenn die Informationen in den Systeminformationen die Informationen in der Verbindungs Zeichenfolge duplizieren, verwendet der Treiber die Informationen in der Verbindungs Zeichenfolge.  
  
 Basierend auf dem Wert von *DriverCompletion*fordert der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auf, z. b. die Benutzer-ID und das Kennwort, und stellt eine Verbindung mit der Datenquelle her:  
  
-   SQL_DRIVER_PROMPT: der Treiber zeigt ein Dialogfeld an, in dem die Werte aus der Verbindungs Zeichenfolge und die Systeminformationen (sofern vorhanden) als Anfangswerte verwendet werden. Wenn der Benutzer das Dialogfeld verlässt, stellt der Treiber eine Verbindung mit der Datenquelle her. Außerdem wird eine Verbindungs Zeichenfolge aus dem Wert des **DSN** oder **Treiber** Schlüsselworts in \* *InConnectionString* und der Informationen, die vom Dialogfeld zurückgegeben werden, erstellt. Diese Verbindungs Zeichenfolge wird im **outconnectionstring* -Puffer platziert.  
  
-   SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED: Wenn die Verbindungs Zeichenfolge genügend Informationen enthält und diese Informationen korrekt sind, stellt der Treiber eine Verbindung mit der Datenquelle her und kopiert \* *InConnectionString* in \* *outconnectionstring*. Wenn Informationen fehlen oder nicht korrekt sind, führt der Treiber dieselben Aktionen aus wie bei SQL_DRIVER_PROMPT von " *DriverCompletion* ", mit dem Unterschied, dass der Treiber die Steuerelemente für alle Informationen deaktiviert, die zum Herstellen einer Verbindung mit der Datenquelle nicht erforderlich sind, wenn der *DriverCompletion* SQL_DRIVER_COMPLETE_REQUIRED ist.  
  
-   SQL_DRIVER_NOPROMPT: Wenn die Verbindungs Zeichenfolge genügend Informationen enthält, stellt der Treiber eine Verbindung mit der Datenquelle her und kopiert \* *InConnectionString* in \* *outconnectionstring*. Andernfalls gibt der Treiber SQL_ERROR für **SQLDriverConnect**zurück.  
  
 Bei erfolgreicher Verbindung mit der Datenquelle legt der Treiber auch \* *StringLength2Ptr* auf die Länge der Ausgabe Verbindungs Zeichenfolge fest, die in **outconnectionstring*zurückgegeben werden kann.  
  
 Wenn der Benutzer ein Dialogfeld abbricht, das vom Treiber-Manager oder vom Treiber angezeigt wird, gibt **SQLDriverConnect** SQL_NO_DATA zurück.  
  
 Informationen dazu, wie der Treiber-Manager und der Treiber während des Verbindungs Vorgangs interagieren, finden Sie unter [SQLCONNECT-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Wenn ein Treiber **SQLDriverConnect**unterstützt, muss der Treiber Schlüsselwortbereich der Systeminformationen für den Treiber das **connectfunctions** -Schlüsselwort enthalten, bei dem das zweite Zeichen auf "Y" festgelegt ist.  
  
## <a name="connecting-when-connection-pooling-is-enabled"></a>Verbindung wird hergestellt, wenn Verbindungs Pooling aktiviert ist  
 Das Verbindungspooling ermöglicht einer Anwendung, eine bereits erstellte Verbindung wiederzuverwenden. Wenn **SQLDriverConnect** aufgerufen wird, versucht der Treiber-Manager, die Verbindung mithilfe einer Verbindung herzustellen, die zu einem Pool von Verbindungen in einer Umgebung gehört, die für das Verbindungspooling vorgesehen ist. Weitere Informationen zum Verbindungspooling finden Sie unter [SQLCONNECT-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Eine Anwendung kann SQL_ATTR_RESET_CONNECTION festlegen, bevor SQLDisconnect für eine Verbindung aufgerufen wird, bei der das Pooling aktiviert ist. Weitere Informationen finden Sie unter [SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Die folgenden Einschränkungen gelten, wenn eine Anwendung **SQLDriverConnect** aufruft, um eine Verbindung mit einer gepoolten Verbindung herzustellen:  
  
-   Wenn das Schlüsselwort " **SaveFile** " in der Verbindungs Zeichenfolge angegeben wird, wird keine Verbindungspooling-Verarbeitung durchgeführt.  
  
-   Wenn das Verbindungspooling aktiviert ist, kann **SQLDriverConnect** nur mit einem *DriverCompletion* -Argument von SQL_DRIVER_NOPROMPT aufgerufen werden. Wenn **SQLDriverConnect** mit einem anderen *DriverCompletion*aufgerufen wird, wird SQLSTATE HY110 (ungültiger Treiber Abschluss) zurückgegeben.  
  
## <a name="connection-attributes"></a>Verbindungsattribute  
 Das SQL_ATTR_LOGIN_TIMEOUT Verbindungs Attribut, das mithilfe von **SQLSetConnectAttr**festgelegt wird, definiert die Anzahl der Sekunden, die gewartet werden soll, bis eine Anmelde Anforderung mit einer erfolgreichen Verbindung des Treibers abgeschlossen ist, bevor Sie an die Anwendung zurückgegeben wird. Wenn der Benutzer aufgefordert wird, die Verbindungs Zeichenfolge abzuschließen, beginnt eine Wartezeit für jede Anmelde Anforderung, wenn der Treiber den Verbindungsvorgang startet.  
  
 Der Treiber öffnet die Verbindung standardmäßig im SQL_MODE_READ_WRITE Zugriffsmodus. Um den Zugriffsmodus auf SQL_MODE_READ_ONLY festzulegen, muss die Anwendung **SQLSetConnectAttr** mit dem SQL_ATTR_ACCESS_MODE-Attribut aufrufen, bevor **SQLDriverConnect**aufgerufen wird.  
  
 Wenn eine Standard Übersetzungs Bibliothek in den Systeminformationen für die Datenquelle angegeben ist, wird Sie vom Treiber geladen. Eine andere Übersetzungs Bibliothek kann durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_TRANSLATE_LIB-Attribut geladen werden. Eine Übersetzungs Option kann durch Aufrufen von **SQLSetConnectAttr** mit der SQL_ATTR_TRANSLATE_OPTION-Option angegeben werden.  
  
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
  
 Siehe auch [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuordnen eines Handles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Ermitteln und Auflisten von Werten, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Trennen der Verbindung mit einer Datenquelle|[SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Zurückgeben von Treiber Beschreibungen und-Attributen|[SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Freigeben eines Handles|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Festlegen eines Verbindungs Attributs|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
