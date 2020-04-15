---
title: SQLAllocHandle-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 178e3fad1ec062dd7f812125da66b7e21a7a4f4b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290210"
---
# <a name="sqlallochandle-function"></a>SQLAllocHandle-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLAllocHandle** weist ein Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptor-Handle zu.  
  
> [!NOTE]  
>  Diese Funktion ist eine generische Funktion zum Zuweisen von Handles, die die ODBC 2.0-Funktionen **SQLAllocConnect**, **SQLAllocEnv**und **SQLAllocStmt**ersetzt. So ermöglichen Anwendungen, die **SQLAllocHandle** aufrufen, mit ODBC 2 zu arbeiten. *x-Treiber,* ein Aufruf von **SQLAllocHandle** wird im Treiber-Manager **SQLAllocConnect**, **SQLAllocEnv**oder **SQLAllocStmt**, zugeordnet. Weitere Informationen finden Sie unter "Kommentare". Weitere Informationen darüber, was der Treiber-Manager dieser Funktion zuordnet, wenn ein ODBC 3. *x-Anwendung* arbeitet mit einem ODBC 2. *x-Treiber,* siehe [Mapping-Ersatzfunktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLAllocHandle(  
      SQLSMALLINT   HandleType,  
      SQLHANDLE     InputHandle,  
      SQLHANDLE *   OutputHandlePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Der Typ des Handles, der von **SQLAllocHandle**zugewiesen werden soll. Dies muss einer der folgenden Werte sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur vom Treiber-Manager und -Treiber verwendet. Anwendungen sollten diesen Handletyp nicht verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [Entwickeln von Verbindungspool-Awareness in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *InputHandle*  
 [Eingabe] Das Eingabehandle, in dessen Kontext das neue Handle zugeordnet werden soll. Wenn *HandleType* SQL_HANDLE_ENV ist, ist dies SQL_NULL_HANDLE. Wenn *HandleType* SQL_HANDLE_DBC ist, muss dies ein Umgebungshandle sein, und wenn es sich um SQL_HANDLE_STMT oder SQL_HANDLE_DESC handelt, muss es sich um ein Verbindungshandle handelt.  
  
 *OutputHandlePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem das Handle an die neu zugewiesene Datenstruktur zurückgegeben werden soll.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_INVALID_HANDLE oder SQL_ERROR.  
  
 Wenn **SQLAllocHandle** beim Zuweisen eines anderen Handles als eines Umgebungshandles SQL_ERROR zurückgibt, wird *OutputHandlePtr* abhängig vom Wert von *HandleType*auf SQL_NULL_HDBC, SQL_NULL_HSTMT oder SQL_NULL_HDESC festgelegt, es sei denn, das Ausgabeargument ist ein Nullzeiger. Die Anwendung kann dann zusätzliche Informationen aus der Diagnosedatenstruktur abrufen, die dem Handle im *InputHandle-Argument* zugeordnet ist.  
  
## <a name="environment-handle-allocation-errors"></a>Umgebungsbehandlung von Zuordnungsfehlern  
 Die Umgebungszuordnung erfolgt sowohl innerhalb des Treiber-Managers als auch innerhalb jedes Treibers. Der von **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV zurückgegebene Fehler hängt von der Ebene ab, in der der Fehler aufgetreten ist.  
  
 Wenn der Treiber-Manager keinen Speicher für * \*OutputHandlePtr* zuweisen kann, wenn **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV aufgerufen wird, oder die Anwendung einen Nullzeiger für *OutputHandlePtr*bereitstellt, gibt **SQLAllocHandle** SQL_ERROR zurück. Der Treiber-Manager legt **OutputHandlePtr* auf SQL_NULL_HENV fest (es sei denn, die Anwendung hat einen Nullzeiger bereitgestellt, der SQL_ERROR zurückgibt). Es gibt kein Handle, mit dem zusätzliche Diagnoseinformationen verknüpft werden können.  
  
 Der Treiber-Manager ruft die Umgebungshandlezuweisungsfunktion auf Treiberebene erst auf, wenn die Anwendung **SQLConnect**, **SQLBrowseConnect**oder **SQLDriverConnect**aufruft. Wenn in der **SQLAllocHandle-Funktion** auf Treiberebene ein Fehler auftritt, gibt die Funktion **SQLConnect auf**Treiber-Manager-Ebene SQLConnect , **SQLBrowseConnect**oder **SQLDriverConnect** SQL_ERROR zurück. Die Diagnosedatenstruktur enthält SQLSTATE IM004 **(SqlAllocHandle** des Treibers ist fehlgeschlagen). Der Fehler wird für ein Verbindungshandle zurückgegeben.  
  
 Weitere Informationen zum Fluss von Funktionsaufrufen zwischen dem Treiber-Manager und einem Treiber finden Sie unter [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLAllocHandle** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit dem entsprechenden *HandleType* und *Handle* aufgerufen wird, der auf den Wert von *InputHandle*festgelegt ist. SQL_SUCCESS_WITH_INFO (aber nicht SQL_ERROR) können für das *OutputHandle-Argument* zurückgegeben werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLAllocHandle** zurückgegeben werden, und es werden die sqlSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) Das *HandleType-Argument* wurde SQL_HANDLE_STMT oder SQL_HANDLE_DESC, aber die durch das *InputHandle-Argument* angegebene Verbindung war nicht geöffnet. Der Verbindungsprozess muss erfolgreich abgeschlossen werden (und die Verbindung muss geöffnet sein), damit der Treiber eine Anweisung oder ein Deskriptor-Handle zuweisen kann.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im **MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|(DM) Der Treiber-Manager konnte dem angegebenen Handle keinen Speicher zuweisen.<br /><br /> Der Treiber konnte dem angegebenen Handle keinen Speicher zuweisen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) Das *OutputHandlePtr-Argument* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Das *HandleType-Argument* wurde SQL_HANDLE_DBC, und **SQLSetEnvAttr** wurde nicht aufgerufen, um das SQL_ODBC_VERSION-Umgebungsattribut festzulegen.<br /><br /> (DM) Eine asynchron ausgeführte Funktion wurde für das **InputHandle** aufgerufen und wurde immer noch ausgeführt, als die **SQLAllocHandle-Funktion** aufgerufen wurde, wobei **HandleType** auf SQL_HANDLE_STMT oder SQL_HANDLE_DESC festgelegt wurde.|  
|HY013|Speicherverwaltungsfehler|Das *HandleType-Argument* wurde SQL_HANDLE_DBC, SQL_HANDLE_STMT oder SQL_HANDLE_DESC. und der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY014|Grenzwert für die Anzahl der überschrittenen Griffe|Das treiberdefinierte Limit für die Anzahl der Handles, die für den typ des Handles zugewiesen werden können, der durch das *HandleType-Argument* angegeben wird, wurde erreicht.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) Das *HandleType-Argument* war nicht: SQL_HANDLE_ENV, SQL_HANDLE_DBC, SQL_HANDLE_STMT oder SQL_HANDLE_DESC.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Das *HandleType-Argument* wurde SQL_HANDLE_DESC und der Treiber war ein ODBC 2. *x-Treiber.*|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Das *HandleType-Argument* wurde SQL_HANDLE_STMT, und der Treiber war kein gültiger ODBC-Treiber.<br /><br /> (DM) Das *HandleType-Argument* wurde SQL_HANDLE_DESC, und der Treiber unterstützt das Zuweisen eines Deskriptorhandles nicht.|  
  
## <a name="comments"></a>Kommentare  
 **SQLAllocHandle** wird verwendet, um Handles für Umgebungen, Verbindungen, Anweisungen und Deskriptoren zuzuweisen, wie in den folgenden Abschnitten beschrieben. Allgemeine Informationen zu Handles finden Sie unter [Handles](../../../odbc/reference/develop-app/handles.md).  
  
 Mehrere Umgebungen, Verbindungen oder Anweisungshandle können von einer Anwendung gleichzeitig zugewiesen werden, wenn mehrere Zuweisungen vom Treiber unterstützt werden. In ODBC ist kein Grenzwert für die Anzahl der Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptorhandles definiert, die jederzeit zugewiesen werden können. Die Fahrer können die Anzahl eines bestimmten Grifftyps begrenzen, der gleichzeitig zugewiesen werden kann. Weitere Informationen finden Sie in der Treiberdokumentation.  
  
 Wenn die Anwendung **SQLAllocHandle** aufruft, wenn * \*OutputHandlePtr* auf ein bereits vorhandenes Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptor-Handle festgelegt ist, überschreibt der Treiber die dem *Handle*zugeordneten Informationen, es sei denn, die Anwendung verwendet Verbindungspooling (siehe "Zuweisen eines Umgebungsattributs für Verbindungspooling" weiter unten in diesem Abschnitt). Der Treiber-Manager überprüft nicht, ob das in * \*OutputHandlePtr* eingegebene *Handle* bereits verwendet wird, und überprüft auch nicht den vorherigen Inhalt eines Handles, bevor er sie überschreibt.  
  
> [!NOTE]  
>  Es ist falsch, dass die ODBC-Anwendungsprogrammierung **SQLAllocHandle** zweimal mit derselben Anwendungsvariablen aufruft, die für * \*OutputHandlePtr* definiert ist, ohne **SQLFreeHandle** aufzurufen, um das Handle freizugeben, bevor es neu zugewiesen wird. Das Überschreiben von ODBC-Handles auf diese Weise kann zu inkonsistentem Verhalten oder Fehlern seitens odBC-Treibern führen.  
  
 Auf Betriebssystemen, die mehrere Threads unterstützen, können Anwendungen dieselbe Umgebung, Verbindung, Anweisung oder Deskriptor-Handle auf verschiedenen Threads verwenden. Die Fahrer müssen daher den sicheren Multithreadzugriff auf diese Informationen unterstützen. eine Möglichkeit, dies zu erreichen, ist z. B. die Verwendung eines kritischen Abschnitts oder eines Semaphors. Weitere Informationen zum Gewinden finden Sie unter [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
 **SQLAllocHandle** legt das SQL_ATTR_ODBC_VERSION-Umgebungsattribut nicht fest, wenn es aufgerufen wird, ein Umgebungshandle zuzuweisen. Das Umgebungsattribut muss von der Anwendung festgelegt werden, oder SQLSTATE HY010 (Funktionssequenzfehler) wird zurückgegeben, wenn **SQLAllocHandle** aufgerufen wird, um ein Verbindungshandle zuzuweisen.  
  
 Für standardkonforme Anwendungen wird **SQLAllocHandle** **SQLAllocHandle** zur Kompilierungszeit zugeordnet. Der Unterschied zwischen diesen beiden Funktionen besteht darin, dass **SQLAllocHandleStd** das SQL_ATTR_ODBC_VERSION Umgebungsattribut auf SQL_OV_ODBC3 legt, wenn es aufgerufen wird, wenn das *HandleType-Argument* auf SQL_HANDLE_ENV festgelegt wird. Dies geschieht, da standardkonforme Anwendungen immer ODBC 3 sind. *x-Anwendungen.* Darüber hinaus erfordern die Standards nicht, dass die Anwendungsversion registriert wird. Dies ist der einzige Unterschied zwischen diesen beiden Funktionen; andernfalls sind sie identisch. **SQLAllocHandleStd** wird **SQLAllocHandle** im Treiber-Manager zugeordnet. Daher müssen Treiber von Drittanbietern **SQLAllocHandleStd**nicht implementieren.  
  
 ODBC 3.8-Anwendungen sollten Folgendes verwenden:  
  
-   **SQLAllocHandle und nicht SQLAllocHandleStd,** um ein Umgebungshandle zuzuweisen.  
  
-   **SQLSetEnvAttr,** um das SQL_ATTR_ODBC_VERSION Umgebungsattribut auf SQL_OV_ODBC3_80 festzulegen.  
  
## <a name="allocating-an-environment-handle"></a>Zuordnen eines Umgebungshandles  
 Ein Umgebungshandle bietet Zugriff auf globale Informationen, z. B. gültige Verbindungshandles und aktive Verbindungshandles. Allgemeine Informationen zu Umgebungshandles finden Sie unter [Umgebungshandles](../../../odbc/reference/develop-app/environment-handles.md).  
  
 Um ein Umgebungshandle anzufordern, ruft eine Anwendung **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV und einem *InputHandle* von SQL_NULL_HANDLE auf. Der Treiber weist Speicher für die Umgebungsinformationen zu und übergibt den Wert des zugeordneten Handles im * \*OutputHandlePtr-Argument* zurück. Die Anwendung übergibt den * \*OutputHandle-Wert* in allen nachfolgenden Aufrufen, die ein Environment Handle-Argument erfordern. Weitere Informationen finden Sie unter [Zuweisen des Umgebungshandles](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Wenn unter einem Treiber-Manager-Umgebungshandle bereits ein Treiberumgebungshandle vorhanden ist, wird **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV in diesem Treiber nicht aufgerufen, wenn eine Verbindung hergestellt wird, sondern nur **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DBC. Wenn das Umgebungshandle eines Treibers nicht unter dem Umgebungshandle des Treiber-Managers vorhanden ist, werden sowohl SQLAllocHandle mit einem HandleType von SQL_HANDLE_ENV als auch SQLAllocHandle mit einem HandleType von SQL_HANDLE_DBC im Treiber aufgerufen, wenn das erste Verbindungshandle der Umgebung mit dem Treiber verbunden ist.  
  
 Wenn der Treiber-Manager die **SQLAllocHandle-Funktion** mit einem *HandleType* von SQL_HANDLE_ENV verarbeitet, überprüft er das **Trace-Schlüsselwort** im Abschnitt [ODBC] der Systeminformationen. Wenn er auf 1 gesetzt ist, aktiviert der Treiber-Manager die Ablaufverfolgung für die aktuelle Anwendung. Wenn das Ablaufverfolgungsflag festgelegt ist, beginnt die Ablaufverfolgung, wenn das erste Umgebungshandle zugewiesen wird, und endet, wenn das letzte Umgebungshandle freigegeben wird. Weitere Informationen finden Sie unter [Konfigurieren von Datenquellen](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Nach dem Zuweisen eines Umgebungshandles muss eine Anwendung **SQLSetEnvAttr** für das Umgebungshandle aufrufen, um das SQL_ATTR_ODBC_VERSION Umgebungsattribut festzulegen. Wenn dieses Attribut nicht festgelegt ist, bevor **SQLAllocHandle** aufgerufen wird, um ein Verbindungshandle für die Umgebung zuzuweisen, gibt der Aufruf zum Zuweisen der Verbindung SQLSTATE HY010 (Funktionssequenzfehler) zurück. Weitere Informationen finden Sie unter [Deklarieren der ODBC-Version der Anwendung](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md).  
  
## <a name="allocating-shared-environments-for-connection-pooling"></a>Zuweisen freigegebener Umgebungen für das Verbindungspooling  
 Umgebungen können von mehreren Komponenten in einem einzigen Prozess gemeinsam genutzt werden. Eine gemeinsame Umgebung kann von mehreren Komponenten gleichzeitig verwendet werden. Wenn eine Komponente eine freigegebene Umgebung verwendet, kann sie gepoolte Verbindungen verwenden, die es ihr ermöglichen, eine vorhandene Verbindung zuzuweisen und zu verwenden, ohne diese Verbindung neu zu erstellen.  
  
 Bevor eine freigegebene Umgebung zugewiesen wird, die für das Verbindungspooling verwendet werden kann, muss eine Anwendung **SQLSetEnvAttr** aufrufen, um das SQL_ATTR_CONNECTION_POOLING-Umgebungsattribut auf SQL_CP_ONE_PER_DRIVER oder SQL_CP_ONE_PER_HENV festzulegen. **SQLSetEnvAttr** wird in diesem Fall aufgerufen, wobei *EnvironmentHandle* auf null gesetzt ist, wodurch das Attribut zu einem Attribut auf Prozessebene wird.  
  
 Nachdem das Verbindungspooling aktiviert wurde, ruft eine Anwendung **SQLAllocHandle** auf, wobei das *HandleType-Argument* auf SQL_HANDLE_ENV festgelegt ist. Die von diesem Aufruf zugewiesene Umgebung ist eine implizite freigegebene Umgebung, da das Verbindungspooling aktiviert wurde.  
  
 Wenn eine freigegebene Umgebung zugewiesen wird, wird die Umgebung, die verwendet wird, erst bestimmt, wenn **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DBC aufgerufen wird. An diesem Punkt versucht der Treiber-Manager, eine vorhandene Umgebung zu finden, die den von der Anwendung angeforderten Umgebungsattributen entspricht. Wenn keine solche Umgebung vorhanden ist, wird eine als gemeinsame Umgebung erstellt. Der Treiber-Manager verwaltet eine Verweisanzahl für jede freigegebene Umgebung. Die Anzahl wird bei der ersten Erstellung der Umgebung auf 1 gesetzt. Wenn eine übereinstimmende Umgebung gefunden wird, wird das Handle dieser Umgebung an die Anwendung zurückgegeben, und die Referenzanzahl wird erhöht. Ein auf diese Weise zugewiesenes Umgebungshandle kann in jeder ODBC-Funktion verwendet werden, die ein Umgebungshandle als Eingabeargument akzeptiert.  
  
## <a name="allocating-a-connection-handle"></a>Zuordnen eines Verbindungshandles  
 Ein Verbindungshandle bietet Zugriff auf Informationen, z. B. die gültigen Anweisungs- und Deskriptorhandles für die Verbindung und ob eine Transaktion derzeit geöffnet ist. Allgemeine Informationen zu Verbindungshandles finden Sie unter [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md).  
  
 Um ein Verbindungshandle anzufordern, ruft eine Anwendung **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DBC auf. Das *InputHandle-Argument* wird auf das Umgebungshandle festgelegt, das vom Aufruf von **SQLAllocHandle** zurückgegeben wurde, der dieses Handle zugewiesen hat. Der Treiber weist Speicher für die Verbindungsinformationen zu und übergibt den Wert des zugehörigen Handles in * \*OutputHandlePtr*zurück. Die Anwendung übergibt den * \*OutputHandlePtr-Wert* in allen nachfolgenden Aufrufen, die ein Verbindungshandle erfordern. Weitere Informationen finden Sie unter [Zuweisen eines Verbindungshandles](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md).  
  
 Der Treiber-Manager verarbeitet die **SQLAllocHandle-Funktion** und ruft die **SQLAllocHandle-Funktion** des Treibers auf, wenn die Anwendung **SQLConnect**, **SQLBrowseConnect**oder **SQLDriverConnect**aufruft. (Weitere Informationen finden Sie unter [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).)  
  
 Wenn das SQL_ATTR_ODBC_VERSION Umgebungsattribut nicht festgelegt ist, bevor **SQLAllocHandle** aufgerufen wird, um ein Verbindungshandle für die Umgebung zuzuweisen, gibt der Aufruf zum Zuweisen der Verbindung SQLSTATE HY010 (Funktionssequenzfehler) zurück.  
  
 Wenn eine Anwendung **SQLAllocHandle** aufruft, wobei das *InputHandle-Argument* auf SQL_HANDLE_DBC und auch auf ein freigegebenes Umgebungshandle festgelegt ist, versucht der Treiber-Manager, eine vorhandene freigegebene Umgebung zu finden, die den von der Anwendung festgelegten Umgebungsattributen entspricht. Wenn keine solche Umgebung vorhanden ist, wird eine mit einer Referenzanzahl (vom Treiber-Manager verwaltet) von 1 erstellt. Wenn eine übereinstimmende freigegebene Umgebung gefunden wird, wird dieses Handle an die Anwendung zurückgegeben, und die Referenzanzahl wird erhöht.  
  
 Die tatsächliche Verbindung, die verwendet wird, wird vom Treiber-Manager erst bestimmt, wenn **SQLConnect** oder **SQLDriverConnect** aufgerufen wird. Der Treiber-Manager verwendet die Verbindungsoptionen beim Aufruf von **SQLConnect** (oder die Verbindungsschlüsselwörter im Aufruf von **SQLDriverConnect**) und die Verbindungsattribute, die nach der Verbindungszuordnung festgelegt wurden, um zu bestimmen, welche Verbindung im Pool verwendet werden soll. Weitere Informationen finden Sie unter [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="allocating-a-statement-handle"></a>Zuordnen eines Anweisungshandles  
 Ein Anweisungshandle bietet Zugriff auf Anweisungsinformationen, z. B. Fehlermeldungen, den Cursornamen und Statusinformationen für die SQL-Anweisungsverarbeitung. Allgemeine Informationen zu Anweisungshandles finden Sie unter [Anweisungshandles](../../../odbc/reference/develop-app/statement-handles.md).  
  
 Um ein Anweisungshandle anzufordern, stellt eine Anwendung eine Verbindung mit einer Datenquelle her und ruft dann **SQLAllocHandle** auf, bevor sie SQL-Anweisungen sendet. In diesem Aufruf sollte *HandleType* auf SQL_HANDLE_STMT und *InputHandle* auf das Verbindungshandle festgelegt werden, das vom Aufruf von **SQLAllocHandle** zurückgegeben wurde, der dieses Handle zugewiesen hat. Der Treiber weist Speicher für die Anweisungsinformationen zu, ordnet das Anweisungshandle der angegebenen Verbindung zu und übergibt den Wert des zugeordneten Handles in * \*OutputHandlePtr*zurück. Die Anwendung übergibt den * \*OutputHandlePtr-Wert* in allen nachfolgenden Aufrufen, die ein Anweisungshandle erfordern. Weitere Informationen finden Sie unter [Zuweisen eines Anweisungshandles](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md).  
  
 Wenn das Anweisungshandle zugewiesen wird, weist der Treiber automatisch einen Satz von vier Deskriptoren zu und weist die Handles für diese Deskriptoren den SQL_ATTR_APP_ROW_DESC-, SQL_ATTR_APP_PARAM_DESC-, SQL_ATTR_IMP_ROW_DESC- und SQL_ATTR_IMP_PARAM_DESC-Anweisungsattributen zu. Diese werden als *implizit zugewiesene* Deskriptoren bezeichnet. Informationen zum expliziten Zuweisen eines Anwendungsdeskriptors finden Sie im folgenden Abschnitt "Zuweisen eines Deskriptorhandles".  
  
## <a name="allocating-a-descriptor-handle"></a>Zuweisen eines Deskriptor-Handles  
 Wenn eine Anwendung **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DESC aufruft, weist der Treiber einen Anwendungsdeskriptor zu. Diese werden als *explizit* zugewiesene Deskriptoren bezeichnet. Die Anwendung weist einen Treiber an, einen explizit zugewiesenen Anwendungsdeskriptor anstelle eines automatisch zugewiesenen für ein bestimmtes Anweisungshandle zu verwenden, indem die **SQLSetStmtAttr-Funktion** mit dem Attribut SQL_ATTR_APP_ROW_DESC oder SQL_ATTR_APP_PARAM_DESC aufgerufen wird. Ein Implementierungsdeskriptor kann nicht explizit zugewiesen werden, und es kann auch kein Implementierungsdeskriptor in einem **SQLSetStmtAttr-Funktionsaufruf** angegeben werden.  
  
 Explizit zugewiesene Deskriptoren sind einem Verbindungshandle anstelle eines Anweisungshandles zugeordnet (wie automatisch zugewiesene Deskriptoren). Deskriptoren bleiben nur dann reserviert, wenn eine Anwendung tatsächlich mit der Datenbank verbunden ist. Da explizit zugewiesene Deskriptoren einem Verbindungshandle zugeordnet sind, kann eine Anwendung einem explizit zugewiesenen Deskriptor mehr als einer Anweisung innerhalb einer Verbindung zuordnen. Ein implizit zugewiesener Anwendungsdeskriptor kann hingegen nicht mit mehr als einem Anweisungshandle verknüpft werden. (Es kann keinem anderen Anweisungshandle als dem, dem es zugewiesen wurde, zugeordnet werden.) Explizit zugewiesene Deskriptor-Handles können entweder von der Anwendung oder durch Aufrufen von **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DESC oder implizit, wenn die Verbindung geschlossen wird, explizit freigegeben werden.  
  
 Wenn der explizit zugewiesene Deskriptor freigegeben wird, wird der implizit zugewiesene Deskriptor erneut der Anweisung zugeordnet. (Der SQL_ATTR_APP_ROW_DESC oder SQL_ATTR_APP_PARAM_DESC Attribut für diese Anweisung wird erneut auf das implizit zugewiesene Deskriptor-Handle festgelegt.) Dies gilt für alle Anweisungen, die dem explizit zugewiesenen Deskriptor für die Verbindung zugeordnet waren.  
  
 Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [Beispiel ODBC-Programm](../../../odbc/reference/sample-odbc-program.md), [SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)und [SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Freiwerden eines Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptorhandles|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Festlegen eines Verbindungsattributs|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Festlegen eines Deskriptorfelds|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen eines Umgebungsattributs|[SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Festlegen eines Anweisungsattributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
