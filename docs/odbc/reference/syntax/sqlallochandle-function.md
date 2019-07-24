---
title: Sqlzugechandle-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLAllocHandle
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLAllocHandle
helpviewer_keywords:
- SQLAllocHandle function [ODBC]
ms.assetid: 6e7fe420-8cf4-4e72-8dad-212affaff317
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2fcf08a4a55a7c65dbc94219ac908da83ea15bad
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344283"
---
# <a name="sqlallochandle-function"></a>SQLAllocHandle-Funktion
**Konformitäts**  
 Eingeführte Version: Konformität der ODBC 3,0-Standards: ISO 92  
  
 **Zusammenfassung**  
 **Sqlzugechandle** weist eine Umgebung, eine Verbindung, eine Anweisung oder ein Deskriptorhandle zu.  
  
> [!NOTE]  
>  Diese Funktion ist eine generische Funktion zum Zuordnen von Handles, die die ODBC 2,0-Funktionen **sqlzucconnect**, **sqlzuzuordcenv**und **sqlzuordcstmt**ersetzen. Damit Anwendungen Aufrufen **SQLAllocHandle** zum Arbeiten mit ODBC 2. *X* Treiber, die einen Aufruf von **SQLAllocHandle** zugeordnet ist, in der Treiber-Manager **SQLAllocConnect**, **SQLAllocEnv**, oder  **SQLAllocStmt**je nach Bedarf. Weitere Informationen finden Sie unter "comments". Weitere Informationen über welche des Treiber-Managers ordnet diese Funktion zu, wenn eine ODBC-3. *x* Anwendung arbeitet mit einer ODBC 2. *X* -Treiber verwenden, finden Sie unter [Zuordnen von Ersatzfunktionen für Abwärtskompatibilität-Kompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLAllocHandle(  
      SQLSMALLINT   HandleType,  
      SQLHANDLE     InputHandle,  
      SQLHANDLE *   OutputHandlePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 Der Der Typ des Handles, das von **sqlzuordchandle**zugewiesen werden soll. Muss einen der folgenden Werte aufweisen:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur vom Treiber-Manager und vom Treiber verwendet. Anwendungen sollten diesen Handlertyp nicht verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [entwickeln von Verbindungs Pool Informationen in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Input*  
 Der Das Eingabe Handle in, dessen Kontext das neue Handle zugewiesen werden soll. Wenn "SQL_HANDLE_ENV" den *Typ* "" hat, ist dies SQL_NULL_HANDLE. Wenn "SQL_HANDLE_DBC" den *Typ* "" hat, muss dies ein Umgebungs Handle sein, und wenn es SQL_HANDLE_STMT oder SQL_HANDLE_DESC ist, muss es sich um ein Verbindungs Handle handeln.  
  
 *OutputHandlePtr*  
 Ausgeben Ein Zeiger auf einen Puffer, in den das Handle für die neu zugeordnete Datenstruktur zurückgegeben werden soll.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_INVALID_HANDLE oder SQL_ERROR.  
  
 Wenn bei der Zuordnung eines anderen Handles als einem Umgebungs Handle " **sqlzuzuordchandle** SQL_ERROR" den Wert " *outputhandleptr* " auf "SQL_NULL_HDBC", "SQL_NULL_HSTMT" oder "SQL_NULL_HDESC" festlegt, je nach Wert von "tortype", es sei denn,  Das Ausgabe Argument ist ein NULL-Zeiger. Die Anwendung kann dann zusätzliche Informationen aus der Diagnosedaten Struktur abrufen, die dem Handle im *InputHandle* -Argument zugeordnet ist.  
  
## <a name="environment-handle-allocation-errors"></a>Zuordnungs Fehler bei der Umgebungs Behandlung  
 Die Umgebungs Zuordnung erfolgt im Treiber-Manager und innerhalb jedes Treibers. Der von **sqlzugechandle** mit dem *Typ* "SQL_HANDLE_ENV" zurückgegebene Fehler hängt von der Ebene ab, in der der Fehler aufgetreten ist.  
  
 Wenn der Treiber-Manager für  *\*outputhandleptr* keinen Arbeitsspeicher belegen kann, wenn **SQLAllocHandle** mit dem *Typ* "SQL_HANDLE_ENV" vom Typ "" aufgerufen wird, oder wenn die Anwendung einen NULL-Zeiger für *outputhandleptr*bereitstellt,  **Sqlzugechandle** gibt SQL_ERROR zurück. Der Treiber-Manager legt **outputhandleptr* auf SQL_NULL_HENV fest (es sei denn, die Anwendung hat einen NULL-Zeiger bereitgestellt, der SQL_ERROR zurückgibt). Es gibt kein Handle, mit dem zusätzliche Diagnoseinformationen verknüpft werden können.  
  
 Der Treiber-Manager ruft die Zuordnungs Funktion für Umgebungs Handles auf Treiber Ebene erst auf, wenn die Anwendung **SQLCONNECT**, **sqlbrowseconnetct**oder **SQLDriverConnect**aufruft. Wenn ein Fehler in der **sqlverteilchandle** -Funktion auf Treiber Ebene auftritt, gibt die Funktion " **SQLCONNECT**", " **sqlbrowseconnetct**" oder " **SQLDriverConnect** " auf Treiber-Manager-Ebene "SQL_ERROR" zurück. Die Diagnosedaten Struktur enthält SQLSTATE IM004 (Fehler bei der **sqlzuzuweisung** des Treibers). Der Fehler wird bei einem Verbindungs Handle zurückgegeben.  
  
 Weitere Informationen zum Ablauf von Funktionsaufrufen zwischen dem Treiber-Manager und einem Treiber finden Sie unter [SQLCONNECT-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlzuordchandle** "SQL_ERROR" oder "SQL_SUCCESS_WITH_INFO" zurückgibt, kann ein zugeordneter SQLSTATE *-Wert* durch Aufrufen von **SQLGetDiagRec** abgerufen werden, wobei der entsprechende Typ und das *handle* auf den Wert von *InputHandle festgelegt sind* . SQL_SUCCESS_WITH_INFO (aber nicht SQL_ERROR) kann für das *outputhandle* -Argument zurückgegeben werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **sqlzuzugerle** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, lautet SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) das  handlentypargument war SQL_HANDLE_STMT oder SQL_HANDLE_DESC, aber die vom *InputHandle* -Argument angegebene Verbindung war nicht geöffnet. Der Verbindungsprozess muss erfolgreich abgeschlossen werden (und die Verbindung muss geöffnet sein), damit der Treiber eine-Anweisung oder ein Deskriptorhandle zuordnen muss.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im **MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der Speicher Belegung|(DM) der Treiber-Manager konnte für das angegebene Handle keinen Arbeitsspeicher zuweisen.<br /><br /> Der Treiber konnte für das angegebene Handle keinen Arbeitsspeicher zuordnen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) das *outputhandleptr* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) das  handlentypargument war SQL_HANDLE_DBC, und **SQLSetEnvAttr** wurde nicht aufgerufen, um das SQL_ODBC_VERSION Environment-Attribut festzulegen.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das **InputHandle** aufgerufen und wurde noch ausgeführt, als die **sqlzuzuordchandle** -Funktion mit dem auf SQL_HANDLE_STMT oder SQL_HANDLE_DESC festgelegten "tortype" aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Das " *Lenker Type* "-Argument lautete SQL_HANDLE_DBC, SQL_HANDLE_STMT oder SQL_HANDLE_DESC; und der Funktions aufgerufene konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY014|Limit für die Anzahl von Handles überschritten|Die vom Treiber definierte Beschränkung für die Anzahl von Handles, die für den Typ des Handles zugeordnet werden kann, der durch das " *Lenker Type* "-Argument angegeben wird, wurde erreicht.|  
|HY092|Ungültiger Attribut/Options Bezeichner|(DM) das  handlentypargument ist nicht: SQL_HANDLE_ENV, SQL_HANDLE_DBC, SQL_HANDLE_STMT oder SQL_HANDLE_DESC.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Die *HandleType* Argument war SQL_HANDLE_DESC und der Treiber wurde von einer ODBC 2. *X* Treiber.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) das  handlentypargument war SQL_HANDLE_STMT, und der Treiber war kein gültiger ODBC-Treiber.<br /><br /> (DM) das  handlertypargument war SQL_HANDLE_DESC, und der Treiber unterstützt das Zuordnen eines Deskriptorhandles nicht.|  
  
## <a name="comments"></a>Kommentare  
 **SQLAllocHandle** wird zum Zuordnen von Handles für Umgebungen, Verbindungen, Anweisungen und Deskriptoren verwendet, wie in den folgenden Abschnitten beschrieben. Allgemeine Informationen zu Handles finden Sie unter [Handles](../../../odbc/reference/develop-app/handles.md).  
  
 Mehrere Umgebungen, Verbindungen oder Anweisungs Handles können jeweils von einer Anwendung zugeordnet werden, wenn mehrere Zuordnungen vom Treiber unterstützt werden. In ODBC wird keine Beschränkung für die Anzahl der Umgebungs-, Verbindungs-, Anweisungs-oder Deskriptorhandles definiert, die zu einem beliebigen Zeitpunkt zugeordnet werden können. Treiber können eine Beschränkung für die Anzahl eines bestimmten Handles erzwingen, die gleichzeitig zugewiesen werden kann. Weitere Informationen finden Sie in der Treiber Dokumentation.  
  
 Wenn die Anwendung **sqlzuordchandle** aufruft, wobei  *\*outputhandleptr* auf eine Umgebung, eine Verbindung, eine Anweisung oder einen Deskriptorhandle festgelegt ist, die bereits vorhanden ist, überschreibt der Treiber die mit dem Handle verknüpften Informationen. , es sei denn, die Anwendung verwendet das Verbindungspooling (siehe "Zuordnen eines Umgebungs Attributs für Verbindungspooling" weiter unten in diesem Abschnitt). Der Treiber-Manager überprüft nicht, ob das in  *\*"outputhandleptr* " eingegebene *handle* bereits verwendet wird, und überprüft auch nicht den vorherigen Inhalt eines Handles, bevor es überschrieben wird.  
  
> [!NOTE]  
>  Es ist eine falsche ODBC-Anwendungsprogrammierung zum erneuten Aufrufen von **sqlzuordchandle** mit der gleichen Anwendungsvariablen, die für  *\*outputhandleptr* definiert ist, ohne dass **SQLFreeHandle** aufgerufen wird, um das Handle vor der erneuten Zuordnung freizugeben. . Das Überschreiben von ODBC-Handles auf diese Weise kann zu inkonsistenten Verhalten oder Fehlern im Rahmen der ODBC-Treiber führen.  
  
 Bei Betriebssystemen, die mehrere Threads unterstützen, können Anwendungen die gleiche Umgebung, Verbindung, Anweisung oder das Deskriptorhandle für verschiedene Threads verwenden. Treiber müssen daher sicheren, Multithread-Zugriff auf diese Informationen unterstützen. eine Möglichkeit, dies zu erreichen, ist z. b. die Verwendung eines kritischen Abschnitts oder eines Semaphors. Weitere Informationen zum Threading finden Sie unter [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
 **SQLAllocHandle** legt das SQL_ATTR_ODBC_VERSION Environment-Attribut nicht fest, wenn es aufgerufen wird, um ein Umgebungs Handle zuzuordnen. das Umgebungs Attribut muss von der Anwendung festgelegt werden, oder SQLSTATE HY010 (Funktions Sequenz Fehler) wird zurückgegeben, wenn **SQLAllocHandle** aufgerufen wird, um ein Verbindungs Handle zuzuordnen.  
  
 Bei Standard kompatiblen Anwendungen wird sqlzuzuordchandle zum Zeitpunkt der Kompilierung sqlzuordchandlestd zugeordnet. Der Unterschied zwischen diesen beiden Funktionen besteht darin, dass **sqlzuordchandlestd** das SQL_ATTR_ODBC_VERSION Environment-Attribut auf SQL_OV_ODBC3 festlegt, wenn es aufgerufen wird, wobei das " *Lenker Type* "-Argument auf SQL_HANDLE_ENV gesetzt ist. Dies geschieht, da standardkonforme Anwendungen immer ODBC 3 sind. *x* -Anwendungen. Außerdem ist es für die Standards nicht erforderlich, dass die Anwendungs Version registriert wird. Dies ist der einzige Unterschied zwischen diesen beiden Funktionen. Andernfalls sind Sie identisch. **Sqlzuzuordchandlestd** ist im Treiber-Manager **sqlzuordchandle** zugeordnet. Daher müssen Treiber von Drittanbietern **sqlverteilchandlestd**nicht implementieren.  
  
 ODBC 3,8-Anwendungen sollten Folgendes verwenden:  
  
-   **SQLAllocHandle und nicht sqlallochandlestd** zum Zuordnen eines Umgebungs Handles.  
  
-   **SQLSetEnvAttr** , um das SQL_ATTR_ODBC_VERSION Environment-Attribut auf SQL_OV_ODBC3_80 festzulegen.  
  
## <a name="allocating-an-environment-handle"></a>Zuordnen eines Umgebungshandles  
 Ein Umgebungs Handle ermöglicht den Zugriff auf globale Informationen, wie z. b. gültige Verbindungs Handles und aktive Verbindungs Handles. Allgemeine Informationen zu Umgebungs Handles finden Sie unter [Umgebungs Handles](../../../odbc/reference/develop-app/environment-handles.md).  
  
 Um ein Umgebungs Handle anzufordern, ruft eine Anwendung **sqlzugewiesene CHandle** mit dem *Typ* SQL_HANDLE_ENV und einem *InputHandle* von SQL_NULL_HANDLE auf. Der Treiber ordnet Speicher für die Umgebungs Informationen zu und übergibt den Wert des zugeordneten Handles an das  *\*outputhandleptr* -Argument zurück. Die Anwendung übergibt den  *\*outputhandle* -Wert in allen nachfolgenden Aufrufen, die ein Umgebungs Handle-Argument erfordern. Weitere Informationen finden Sie unter [Zuordnen des Umgebungs Handles](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Wenn im Umgebungs Handle eines Treiber-Managers bereits ein Umgebungs Handle eines Treibers vorhanden ist, wird **sqlzugewiesene CHandle** mit dem  SQL_HANDLE_ENV-Handlertyp nicht in diesem Treiber aufgerufen, wenn eine Verbindung hergestellt wird, sondern nur **sqlzugechandle** . mit dem *Typ* "SQL_HANDLE_DBC". Wenn das Umgebungs Handle eines Treibers unter dem Umgebungs Handle des Treiber-Managers nicht vorhanden ist, werden sowohl sqlzugewiesene CHandle mit dem Typ "SQL_HANDLE_ENV" als auch "sqlzuweisung" mit dem Typ "SQL_HANDLE_DBC" im Treiber aufgerufen, wenn die erste Verbindung das Handle der Umgebung ist mit dem Treiber verbunden.  
  
 Wenn der Treiber-Manager die **sqlzugechandle** -Funktion mit dem *Typ* "SQL_HANDLE_ENV" verarbeitet, überprüft er das **Trace** -Schlüsselwort im Abschnitt [ODBC] der Systeminformationen. Wenn Sie auf 1 festgelegt ist, aktiviert der Treiber-Manager die Ablauf Verfolgung für die aktuelle Anwendung. Wenn das Ablaufverfolgungsflag festgelegt ist, wird die Ablauf Verfolgung gestartet, wenn das erste Umgebungs Handle zugewiesen wird und endet, wenn das letzte Umgebungs Handle freigegeben wird Weitere Informationen finden Sie unter [Konfigurieren von Datenquellen](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Nachdem ein Umgebungs Handle zugeordnet wurde, muss eine Anwendung **SQLSetEnvAttr** für das Umgebungs Handle aufzurufen, um das SQL_ATTR_ODBC_VERSION Environment-Attribut festzulegen. Wenn dieses Attribut nicht festgelegt wird, bevor **SQLAllocHandle** aufgerufen wird, um ein Verbindungs Handle in der Umgebung zuzuordnen, gibt der Aufruf zum Zuordnen der Verbindung SQLSTATE HY010 (Funktions Sequenz Fehler) zurück. Weitere Informationen finden Sie unter [Deklarieren der ODBC-Version der Anwendung](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md).  
  
## <a name="allocating-shared-environments-for-connection-pooling"></a>Zuordnen von freigegebenen Umgebungen für Verbindungs Pooling  
 Umgebungen können in einem einzelnen Prozess von mehreren Komponenten gemeinsam genutzt werden. Eine freigegebene Umgebung kann von mehreren Komponenten gleichzeitig verwendet werden. Wenn eine Komponente eine freigegebene Umgebung verwendet, kann Sie in einem Pool zusammengefasste Verbindungen verwenden, die es Ihnen ermöglichen, eine vorhandene Verbindung zuzuordnen und zu verwenden, ohne diese Verbindung neu erstellen zu müssen.  
  
 Vor dem Zuordnen einer freigegebenen Umgebung, die für das Verbindungspooling verwendet werden kann, muss eine Anwendung **SQLSetEnvAttr** aufzurufen, um das SQL_ATTR_CONNECTION_POOLING Environment-Attribut auf SQL_CP_ONE_PER_DRIVER oder SQL_CP_ONE_PER_HENV festzulegen. **SQLSetEnvAttr** wird in diesem Fall mit dem auf NULL festgelegten *environmenthandle* aufgerufen, wodurch das Attribut ein Attribut auf Prozessebene ist.  
  
 Nachdem das Verbindungspooling aktiviert wurde, ruft eine Anwendung **sqlzuordchandle** auf, wobei das " *Lenker Type* "-Argument auf SQL_HANDLE_ENV festgelegt ist. Die durch diesen-Befehl zugeordnete Umgebung ist eine implizite freigegebene Umgebung, da Verbindungspooling aktiviert wurde.  
  
 Wenn eine freigegebene Umgebung zugeordnet wird, wird die Umgebung, die verwendet wird, erst dann bestimmt, wenn **sqlzuzuordchandle** mit dem *Typ* "SQL_HANDLE_DBC" aufgerufen wird. An diesem Punkt versucht der Treiber-Manager, eine vorhandene Umgebung zu finden, die mit den von der Anwendung angeforderten Umgebungs Attributen übereinstimmt. Wenn keine solche Umgebung vorhanden ist, wird eine solche Umgebung als freigegebene Umgebung erstellt. Der Treiber-Manager verwaltet einen Verweis Zähler für jede freigegebene Umgebung. die Anzahl wird bei der ersten Erstellung der Umgebung auf 1 festgelegt. Wenn eine übereinstimmende Umgebung gefunden wird, wird das Handle dieser Umgebung an die Anwendung zurückgegeben, und der Verweis Zähler wird inkrementiert. Ein Umgebungs Handle, das auf diese Weise zugeordnet ist, kann in jeder ODBC-Funktion verwendet werden, die ein Umgebungs Handle als Eingabe Argument annimmt.  
  
## <a name="allocating-a-connection-handle"></a>Zuordnen eines Verbindungshandles  
 Ein Verbindungs Handle ermöglicht den Zugriff auf Informationen wie z. b. die gültige-Anweisung und Deskriptorhandles für die Verbindung und ob derzeit eine Transaktion geöffnet ist. Allgemeine Informationen zu Verbindungs Handles finden Sie unter [Verbindungs Handles](../../../odbc/reference/develop-app/connection-handles.md).  
  
 Um ein Verbindungs Handle anzufordern, ruft eine Anwendung **sqlzugewiesene CHandle** mit dem "SQL_HANDLE_DBC"- *Typ* auf. Das *InputHandle* -Argument wird auf das Umgebungs Handle festgelegt, das vom **sqlzugewieschandle** -Befehl zurückgegeben wurde, der das Handle zugeordnet hat. Der Treiber ordnet Speicher für die Verbindungsinformationen zu und übergibt den Wert des zugeordneten Handles an  *\*outputhandleptr*zurück. Die Anwendung übergibt den  *\*outputhandleptr* -Wert in allen nachfolgenden Aufrufen, die ein Verbindungs Handle erfordern. Weitere Informationen finden Sie unter [Zuordnen eines Verbindungs Handles](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md).  
  
 Der Treiber-Manager verarbeitet die **sqlverbinchandle** -Funktion und ruft die **sqlzuweisung** -Funktion des Treibers auf, wenn die Anwendung **SQLCONNECT**, **sqlbrowseconnetct**oder **SQLDriverConnect**aufruft. (Weitere Informationen finden Sie unter [SQLCONNECT-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).)  
  
 Wenn das SQL_ATTR_ODBC_VERSION-Umgebungs Attribut nicht festgelegt wird, bevor **SQLAllocHandle** aufgerufen wird, um ein Verbindungs Handle in der Umgebung zuzuordnen, gibt der Aufruf zum Zuordnen der Verbindung SQLSTATE HY010 (Funktions Sequenz Fehler) zurück.  
  
 Wenn eine Anwendung **sqlzuordchandle** aufruft, wobei das *InputHandle* -Argument auf SQL_HANDLE_DBC und auch auf ein frei gegebenes Umgebungs Handle festgelegt ist, versucht der Treiber-Manager, eine vorhandene freigegebene Umgebung zu finden, die mit den Umgebungs Attributen übereinstimmt. wird von der Anwendung festgelegt. Wenn keine solche Umgebung vorhanden ist, wird eine solche Umgebung mit einem Verweis Zähler (verwaltet vom Treiber-Manager) von 1 erstellt. Wenn eine übereinstimmende freigegebene Umgebung gefunden wird, wird dieses Handle an die Anwendung zurückgegeben und der Verweis Zähler erhöht.  
  
 Die tatsächlich verwendete Verbindung wird erst vom Treiber-Manager bestimmt, wenn **SQLCONNECT** oder **SQLDriverConnect** aufgerufen wird. Der Treiber-Manager verwendet die Verbindungsoptionen im Befehl **SQLCONNECT** (oder die Verbindungs Schlüsselwörter im Befehl **SQLDriverConnect**) und die Verbindungs Attribute, die nach der Verbindungs Zuweisung festgelegt sind, um zu bestimmen, welche Verbindung im Pool verwendet wird. sollte verwendet werden. Weitere Informationen finden Sie unter [SQLCONNECT-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="allocating-a-statement-handle"></a>Zuordnen eines Anweisungshandles  
 Ein Anweisungs Handle ermöglicht den Zugriff auf Anweisungs Informationen, wie z. b. Fehlermeldungen, den Cursor Namen und Statusinformationen für die Verarbeitung von SQL-Anweisungen. Allgemeine Informationen zu Anweisungs Handles finden Sie unter [Anweisungs Handles](../../../odbc/reference/develop-app/statement-handles.md).  
  
 Um ein Anweisungs Handle anzufordern, stellt eine Anwendung eine Verbindung mit einer Datenquelle her und ruft dann **sqlzugewiesene CHandle** auf, bevor SQL-Anweisungen übermittelt werden. In diesem-Befehl  sollte "tortype" auf "SQL_HANDLE_STMT" und " *InputHandle* " auf das Verbindungs Handle festgelegt werden, das vom **sqlzugewieschandle** -Befehl zurückgegeben wurde, der das Handle zugeordnet hat. Der Treiber ordnet Speicher für die Anweisungs Informationen zu, ordnet das Anweisungs Handle der angegebenen Verbindung zu und übergibt den Wert des zugeordneten Handles in  *\*outputhandleptr*zurück. Die Anwendung übergibt den  *\*outputhandleptr* -Wert in allen nachfolgenden Aufrufen, die ein Anweisungs Handle erfordern. Weitere Informationen finden Sie unter [Zuordnen eines Anweisungs Handles](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md).  
  
 Wenn das Anweisungs Handle zugeordnet ist, ordnet der Treiber automatisch einen Satz von vier Deskriptoren zu und weist die Handles für diese Deskriptoren den SQL_ATTR_APP_ROW_DESC-, SQL_ATTR_APP_PARAM_DESC-, SQL_ATTR_IMP_ROW_DESC-und SQL_ATTR_IMP_PARAM_DESC- Anweisungs Attribute. Diese werden als *implizit* zugeordnete Deskriptoren bezeichnet. Informationen zum expliziten Zuordnen eines Anwendungs Deskriptors finden Sie im folgenden Abschnitt "Zuordnen eines Deskriptorhandles".  
  
## <a name="allocating-a-descriptor-handle"></a>Zuordnen eines Deskriptorhandles  
 Wenn eine Anwendung **sqlzugewiesene CHandle** mit dem "SQL_HANDLE_DESC"- *Typ* aufruft, ordnet der Treiber einen Anwendungs Deskriptor zu. Diese werden als *explizit* zugeordnete Deskriptoren bezeichnet. Die Anwendung weist einen Treiber an, einen explizit zugewiesenen Anwendungs Deskriptor anstelle eines automatisch zugewiesenen Anwendungs Deskriptors zu verwenden, indem er die **SQLSetStmtAttr** -Funktion mit dem SQL_ATTR_APP_ROW_DESC-oder SQL_ATTR_APP_-Element aufruft. PARAM_DESC-Attribut. Ein Implementierungs Deskriptor kann nicht explizit zugeordnet werden, und es kann auch kein Implementierungs Deskriptor in einem **SQLSetStmtAttr** -Funktions Aufrufsatz angegeben werden.  
  
 Explizit zugeordnete Deskriptoren sind einem Verbindungs Handle anstelle eines Anweisungs Handles (wie automatisch zugeordnete Deskriptoren) zugeordnet. Deskriptoren bleiben nur reserviert, wenn eine Anwendung tatsächlich mit der Datenbank verbunden ist. Da explizit zugeordnete Deskriptoren einem Verbindungs Handle zugeordnet sind, kann eine Anwendung einen explizit zugeordneten Deskriptor mit mehr als einer Anweisung innerhalb einer Verbindung verknüpfen. Ein implizit zugeordneter Anwendungs Deskriptor kann dagegen nicht mehr als einem Anweisungs Handle zugeordnet werden. (Es kann nicht mit einem anderen Anweisungs Handle als dem zugeordnet werden, dem es zugeordnet wurde.) Explizit zugeordnete Deskriptorhandles können explizit entweder von der Anwendung oder durch Aufrufen von **SQLFreeHandle** mit dem *Typ* "SQL_HANDLE_DESC" oder implizit, wenn die Verbindung geschlossen wird, freigegeben werden.  
  
 Wenn der explizit zugeordnete Deskriptor freigegeben wird, wird der implizit zugeordnete Deskriptor wieder der Anweisung zugeordnet. (Das SQL_ATTR_APP_ROW_DESC-oder SQL_ATTR_APP_PARAM_DESC-Attribut für diese Anweisung wird erneut auf das implizit zugeordnete Deskriptorhandle festgelegt.) Dies gilt für alle-Anweisungen, die dem explizit zugeordneten Deskriptor der Verbindung zugeordnet wurden.  
  
 Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Weitere Informationen finden Sie unter [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md), [sqlbrowseconnetct-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), [SQLCONNECT-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)und [sqlsetcurrsorname-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Freigeben einer Umgebung, einer Verbindung, einer Anweisung oder eines Deskriptorhandles|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Festlegen eines Verbindungs Attributs|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Festlegen eines deskriptorfelds|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen eines Umgebungs Attributs|[SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Festlegen eines Anweisungs Attributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
