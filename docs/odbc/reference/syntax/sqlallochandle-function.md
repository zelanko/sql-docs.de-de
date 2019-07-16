---
title: SQLAllocHandle-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLAllocHandle
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLAllocHandle
helpviewer_keywords:
- SQLAllocHandle function [ODBC]
ms.assetid: 6e7fe420-8cf4-4e72-8dad-212affaff317
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3f4f82a24e594a25b0b1ec9bbeab2256624ae6e9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036252"
---
# <a name="sqlallochandle-function"></a>SQLAllocHandle-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standardkompatibilität: ISO 92  
  
 **Zusammenfassung**  
 **SQLAllocHandle** reserviert ein Handle-Umgebung, Verbindung, Anweisung oder -Deskriptor.  
  
> [!NOTE]  
>  Diese Funktion ist eine generische Funktion zum Zuordnen von Handles, die die ODBC 2.0-Funktionen ersetzt **SQLAllocConnect**, **SQLAllocEnv**, und **SQLAllocStmt**. Damit Anwendungen Aufrufen **SQLAllocHandle** zum Arbeiten mit ODBC 2. *X* Treiber, die einen Aufruf von **SQLAllocHandle** zugeordnet ist, in der Treiber-Manager **SQLAllocConnect**, **SQLAllocEnv**, oder  **SQLAllocStmt**je nach Bedarf. Weitere Informationen finden Sie unter "Kommentare". Weitere Informationen über welche des Treiber-Managers ordnet diese Funktion zu, wenn eine ODBC-3. *x* Anwendung arbeitet mit einer ODBC 2. *X* -Treiber verwenden, finden Sie unter [Zuordnen von Ersatzfunktionen für Abwärtskompatibilität-Kompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLAllocHandle(  
      SQLSMALLINT   HandleType,  
      SQLHANDLE     InputHandle,  
      SQLHANDLE *   OutputHandlePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Der Typ des Handles von zugeordnet werden **SQLAllocHandle**. Dabei muss es sich um einen der folgenden Werte sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur von der Treiber-Manager und Treiber verwendet. Anwendungen sollten nicht mit dieser Handletyp verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN, finden Sie unter [Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *InputHandle*  
 [Eingabe] Das eingabehandle in das Kontext ist das neue Handle zugeordnet werden. Wenn *HandleType* SQL_HANDLE_ENV auf, ist dies die SQL_NULL_HANDLE ist. Wenn *HandleType* ist SQL_HANDLE_DBC auf, dies muss ein Umgebungshandle und wenn es SQL_HANDLE_STMT auf oder SQL_HANDLE_DESC handelt, muss es sein, dass ein Verbindungshandle.  
  
 *OutputHandlePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem das Handle zu der neu zugewiesenen Datenstruktur zurückgegeben.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_INVALID_HANDLE oder SQL_ERROR zurück.  
  
 Wenn ein Handle als ein Umgebungshandle zuordnen, wenn **SQLAllocHandle** gibt SQL_ERROR zurück, wird *OutputHandlePtr* SQL_NULL_HDBC, SQL_NULL_HSTMT oder SQL_NULL_HDESC, je nach den Wert des *HandleType*, es sei denn, das ausgabeargument ein null-Zeiger ist. Die Anwendung kann zusätzliche Informationen aus der Diagnosedaten-Struktur, die das Handle im zugeordneten erhalten die *InputHandle* Argument.  
  
## <a name="environment-handle-allocation-errors"></a>Aufgrund von Zuordnungsfehlern der Umgebung Handle  
 Umgebung Zuordnung tritt innerhalb des Treiber-Managers und innerhalb jeder Treiber. Der zurückgegebene Fehler **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_ENV auf, abhängig von der Ebene, in dem der Fehler aufgetreten ist.  
  
 Wenn der Treiber-Manager für die speicherbelegung kann nicht  *\*OutputHandlePtr* beim **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_ENV auf, aufgerufen wird, oder die Anwendung enthält einen null-Zeiger für *OutputHandlePtr*, **SQLAllocHandle** gibt SQL_ERROR zurück. Der Treiber-Manager legt **OutputHandlePtr* zu SQL_NULL_HENV (es sei denn, die die Anwendung einen null-Zeiger, die SQL_ERROR zurückgibt bereitgestellt). Es gibt kein Handle mit dem zusätzliche Diagnoseinformationen zugeordnet werden soll.  
  
 Der Treiber-Manager wird nicht die Zuordnungsfunktion für auf Treiberebene Umgebung Handle aufgerufen, bis die Anwendung ruft **SQLConnect**, **SQLBrowseConnect**, oder **SQLDriverConnect**. Wenn ein Fehler, in der Treiber auftritt **SQLAllocHandle** -Funktion, und klicken Sie dann auf der Ebene der Treiber-Manager **SQLConnect**, **SQLBrowseConnect**, oder  **SQLDriverConnect** Funktion gibt SQL_ERROR zurück. Die Diagnosedaten-Struktur enthält SQLSTATE IM004 (des Treibers **SQLAllocHandle** Fehler). Der Fehler wird für ein Verbindungshandle zurückgegeben.  
  
 Weitere Informationen zu den Fluss der Funktionsaufrufe zwischen der Treiber-Manager und einem Treiber, finden Sie unter [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLAllocHandle** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit dem entsprechenden *HandleType* und *behandeln* legen Sie auf den Wert der *InputHandle*. SQL_SUCCESS_WITH_INFO (aber nicht als SQL_ERROR) zurückgegeben werden kann, für die *OutputHandle* Argument. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLAllocHandle** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) die *HandleType* Argument war SQL_HANDLE_STMT auf oder SQL_HANDLE_DESC, aber die Verbindung angegeben wird, durch die *InputHandle* Argument konnte nicht geöffnet werden. Der Verbindungsprozess erfolgreich abgeschlossen werden muss (und die Verbindung muss geöffnet sein) für den Treiber an, ordnen eine Anweisung oder der Deskriptor behandelt.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in der **MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber-Managers (DM) konnte nicht für das angegebene Handle Arbeitsspeicher belegt werden.<br /><br /> Der Treiber konnte nicht für das angegebene Handle Arbeitsspeicher belegt werden.|  
|HY009|Ungültige Verwendung eines null-Zeiger|(DM) die *OutputHandlePtr* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) die *HandleType* Argument war SQL_HANDLE_DBC auf, und **SQLSetEnvAttr** nicht aufgerufen wurde, um das SQL_ODBC_VERSION Umgebung-Attribut festgelegt.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, die **InputHandle** und wurde noch ausgeführt, wenn die **SQLAllocHandle** Funktion aufgerufen wurde, wobei **HandleType** festlegen SQL_HANDLE_STMT auf oder SQL_HANDLE_DESC.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Die *HandleType* Argument war SQL_HANDLE_DBC auf, SQL_HANDLE_STMT auf oder SQL_HANDLE_DESC; und der Funktionsaufruf konnte nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichenden Arbeitsspeicher konnte nicht zugegriffen werden Bedingungen.|  
|HY014|Grenzwert für die Anzahl von Handles wurde überschritten|Vom Treiber definierte Grenzwert für die Anzahl der Handles, die den Typ des Handles verwendet werden kann, angegeben durch die *HandleType* Argument wurde erreicht.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) die *HandleType* Argument war nicht: SQL_HANDLE_ENV auf, SQL_HANDLE_DBC auf, SQL_HANDLE_STMT auf, oder SQL_HANDLE_DESC.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die *HandleType* Argument war SQL_HANDLE_DESC und der Treiber wurde von einer ODBC 2. *X* Treiber.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) die *HandleType* Argument SQL_HANDLE_STMT auf, und der Treiber nicht wurde ein gültiger ODBC-Treiber.<br /><br /> (DM) die *HandleType* Argument war SQL_HANDLE_DESC und der Treiber unterstützt nicht das Zuordnen einer Deskriptorhandles.|  
  
## <a name="comments"></a>Kommentare  
 **SQLAllocHandle** wird zum Zuordnen von Handles für Umgebungen, die Verbindungen, Anweisungen und Deskriptoren, wie in den folgenden Abschnitten beschrieben. Allgemeine Informationen zu Handles finden Sie unter [Handles](../../../odbc/reference/develop-app/handles.md).  
  
 Mehr als eine Umgebung, Verbindung oder Anweisung Handle kann von einer Anwendung zu einem Zeitpunkt zugeordnet werden, wenn mehrere Zuordnungen, die vom Treiber unterstützt werden. In ODBC ist keine Begrenzung definiert, auf der Anzahl der Umgebung, Verbindung, Anweisung oder Deskriptorhandles, die zu jedem Zeitpunkt zugeordnet werden können. Treiber können es sich um einen Grenzwert für die Nummer eines bestimmten Typs des Handles verursachen, die zu einem Zeitpunkt zugeordnet werden können; Weitere Informationen finden Sie unter der Treiberdokumentation.  
  
 Wenn die Anwendung ruft **SQLAllocHandle** mit  *\*OutputHandlePtr* legen Sie auf eine Umgebung, Verbindung, Anweisung oder Deskriptorhandles, die bereits vorhanden ist, der Treiber überschreibt die Informationen im Zusammenhang mit der *behandeln*, es sei denn, die Anwendung Connection pooling (siehe "Zuordnen von einer Umgebung-Attribut für Verbindungspooling" weiter unten in diesem Abschnitt) verwendet. Der Treiber-Manager überprüft nicht, um festzustellen, ob die *behandeln* in eingegebenen  *\*OutputHandlePtr* wird bereits verwendet wird, noch wird Überprüfen Sie den vorherigen Inhalt eines Handles, bevor diese überschrieben werden .  
  
> [!NOTE]  
>  Falsche ODBC-Anwendung programmieren aufrufen, ist **SQLAllocHandle** doppelt so groß wie klicken Sie mit der gleichen Anwendungsvariablen, die für definiert  *\*OutputHandlePtr* ohne  **SQLFreeHandle** auf das Handle frei, bevor Sie es erneut zugewiesen werden. Überschreiben von ODBC können Handles auf diese Weise Fehler seitens der ODBC-Treiber zu inkonsistentem Verhalten führen.  
  
 Auf Betriebssystemen, die mehrere Threads zu unterstützen, können Anwendungen dasselbe Handle-Umgebung, Verbindung, Anweisung oder -Deskriptor in verschiedenen Threads verwenden. Treiber müssen sichere, Multithreaded-Zugriff auf diese Informationen aus diesem Grund unterstützen; eine Möglichkeit, dies zu erreichen, z. B. ist mithilfe eines kritischen Abschnitts oder ein Semaphor. Weitere Informationen zu threading, finden Sie unter [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
 **SQLAllocHandle** SQL_ATTR_ODBC_VERSION umgebungsattributs wird nicht festgelegt, wenn sie aufgerufen wird, ein Umgebungshandle; muss umgebungsattributs festgelegt werden, von der Anwendung oder ein SQLSTATE HY010 (Fehler bei Funktionssequenz) werden. zurückgegeben wird, wenn **SQLAllocHandle** wird aufgerufen, um ein Verbindungshandle zuzuordnen.  
  
 Für den Standards entsprechende Anwendungen **SQLAllocHandle** zugeordnet **SQLAllocHandleStd** zum Zeitpunkt der Kompilierung. Der Unterschied zwischen diesen beiden Funktionen besteht darin, die **SQLAllocHandleStd** umgebungsattributs SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 fest legt fest, wenn sie mit aufgerufen wird die *HandleType* -Argument auf SQL festgelegt _HANDLE_ENV. Dies geschieht, da es sich bei den Standards entsprechende Anwendungen immer ODBC 3. sind. *x* Anwendungen. Darüber hinaus erfordern die Standards keine Version der Anwendung registriert werden. Dies ist der einzige Unterschied zwischen diese beiden Funktionen; Andernfalls sind sie identisch. **SQLAllocHandleStd** zugeordnet **SQLAllocHandle** innerhalb des Treiber-Managers. Aus diesem Grund Drittanbieter-Treiber keine implementieren **SQLAllocHandleStd**.  
  
 Es sollten ODBC 3.8-Anwendungen verwenden:  
  
-   **SQLAllocHandle und nicht SQLAllocHandleStd** ein Umgebungshandle zuordnen.  
  
-   **SQLSetEnvAttr** umgebungsattributs SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3_80 festgelegt.  
  
## <a name="allocating-an-environment-handle"></a>Zuordnen eines Umgebungshandles  
 Ein Umgebungshandle ermöglicht den Zugriff auf globale Informationen wie z. B. gültige Verbindungshandles und aktiver Verbindungshandles. Allgemeine Informationen zu Umgebungshandles, finden Sie unter [Umgebungshandles](../../../odbc/reference/develop-app/environment-handles.md).  
  
 Um ein Umgebungshandle anzufordern, eine Anwendung ruft **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_ENV auf, und ein *InputHandle* von SQL_NULL_HANDLE. Der Treiber belegt Speicher für die Informationen zur ausführungsumgebung und übergibt der Wert des zugeordneten Handles zurück, in der  *\*OutputHandlePtr* Argument. Die Anwendung übergibt die  *\*OutputHandle* Wert bei allen nachfolgenden Aufrufen, die Umgebung Handle Argument erforderlich. Weitere Informationen finden Sie unter [zuordnen, die Umgebung behandeln](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Unter Umgebungshandle einen Treiber-Manager, wenn es bereits vorhanden Umgebungshandle des Treibers, klicken Sie dann ist **SQLAllocHandle** mit einer *HandleType* SQL_HANDLE_ENV auf, wird in diesen Treiber nicht aufgerufen wenn ein Verbindung wird hergestellt, nur **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_DBC auf. Wenn das Umgebungshandle des Treibers unter der Treiber-Manager-Umgebungshandle nicht vorhanden ist, die sowohl SQLAllocHandle mit einem HandleTyp SQL_HANDLE_ENV auf, als auch SQLAllocHandle mit einem HandleType SQL_HANDLE_DBC auf werden im Treiber aufgerufen wenn die erste Verbindung Handle der Umgebung, die an den Treiber verbunden ist.  
  
 Wenn der Treiber-Manager verarbeitet die **SQLAllocHandle** -Funktion mit einem *HandleType* SQL_HANDLE_ENV auf, überprüft er die **Ablaufverfolgung** Schlüsselwort im Abschnitt [ODBC] des Systems Informationen. Wenn es auf 1 festgelegt ist, aktiviert der Treiber-Manager die Ablaufverfolgung für die aktuelle Anwendung. Wenn das Trace-Flag festgelegt ist, startet die Ablaufverfolgung, wenn das erste Umgebungshandle zugeordnet ist, und endet, wenn die des letzten Umgebungshandles aufgehoben wird. Weitere Informationen finden Sie unter [Konfigurieren von Datenquellen](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Nach dem Zuordnen eines Umgebungshandles, eine Anwendung aufrufen muss **SQLSetEnvAttr** auf das Umgebungshandle umgebungsattributs SQL_ATTR_ODBC_VERSION festlegen. Wenn dieses Attribut nicht festgelegt ist, bevor Sie **SQLAllocHandle** wird aufgerufen, um ein Verbindungshandle zuordnen in der Umgebung gibt der Aufruf zum Reservieren von den SQLSTATE HY010 zurück (Sequenzfehler funktionieren). Weitere Informationen finden Sie unter [Deklarieren der ODBC-Version der Anwendung](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md).  
  
## <a name="allocating-shared-environments-for-connection-pooling"></a>Zuordnen von freigegebene Umgebungen für das Verbindungspooling  
 Umgebungen können zwischen mehreren Komponenten auf einem einzelnen Prozess gemeinsam genutzt werden. Eine freigegebene Umgebung kann gleichzeitig von mehreren Komponenten verwendet werden. Wenn eine Komponente eine freigegebene Umgebung verwendet wird, können sie Verbindungen in einem Pool, verwenden die ermöglichen, die reserviert werden und eine vorhandene Verbindung verwenden, ohne die Verbindung neu zu erstellen.  
  
 Vor dem Zuordnen einer freigegebenen Umgebung, die für das Verbindungspooling verwendet werden kann, muss eine Anwendung aufrufen **SQLSetEnvAttr** umgebungsattributs SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER oder SQL_CP_ONE_PER_ festlegen HENV. **SQLSetEnvAttr** wird in diesem Fall mit aufgerufen *EnvironmentHandle* auf Null gesetzt, wodurch dem Attribut ein Attribut auf Prozessebene.  
  
 Nachdem der Verbindungs-pooling aktiviert wurde, eine Anwendung ruft **SQLAllocHandle** mit der *HandleType* -Argument auf SQL_HANDLE_ENV auf festgelegt. Eine implizite freigegebenen Umgebung kann von die Umgebung, die durch diesen Aufruf zugeordnet ist, werden, weil Verbindungs-pooling aktiviert wurde.  
  
 Wenn eine freigegebene Umgebung zugeordnet ist, wird die Umgebung, die verwendet werden, nicht bis bestimmt **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, aufgerufen wird. An diesem Punkt versucht der Treiber-Manager, eine vorhandene Umgebung zu finden, die von der Anwendung angeforderte Umgebungsattribute entspricht, ein. Wenn keine Umgebung dieser Art vorhanden ist, wird eine als einer freigegebenen Umgebung erstellt. Der Treiber-Manager verwaltet einen Verweiszähler für jedes freigegebenen Umgebung. die Anzahl die wird auf 1 festgelegt, wenn die Umgebung erstellt wird. Wenn eine entsprechende Umgebung gefunden wird, das Handle für diese Umgebung für die Anwendung zurückgegeben, und der Verweiszähler wird inkrementiert. Ein Umgebungshandle zugeordnet, die auf diese Weise kann in eine ODBC-Funktion verwendet werden, die ein Umgebungshandle als Eingabeargument akzeptiert.  
  
## <a name="allocating-a-connection-handle"></a>Zuordnen eines Verbindungshandles  
 Ein Verbindungshandle bietet Zugriff auf Informationen, z. B. die gültige Anweisung ein, und öffnen Sie die Deskriptorhandles für die Verbindung und gibt an, ob eine Transaktion aktuell ist. Allgemeine Informationen zu Verbindungshandles, finden Sie unter [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md).  
  
 Um ein Verbindungshandle anzufordern, eine Anwendung ruft **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_DBC auf. Die *InputHandle* Argument festgelegt ist, um das Umgebungshandle, die durch den Aufruf zurückgegeben wurde **SQLAllocHandle** , die dieses Handle zugeordnet. Der Treiber belegt Speicher für die Verbindungsinformationen und übergibt der Wert des zugeordneten Handles wieder  *\*OutputHandlePtr*. Die Anwendung übergibt die  *\*OutputHandlePtr* Wert bei allen nachfolgenden Aufrufen, die ein Verbindungshandle zu erfordern. Weitere Informationen finden Sie unter [zuordnen, eine Verbindung behandeln](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md).  
  
 Der Treiber-Manager verarbeitet die **SQLAllocHandle** Funktion, und Aufrufe des Treibers **SQLAllocHandle** funktionieren, wenn die Anwendung ruft **SQLConnect**, **SQLBrowseConnect**, oder **SQLDriverConnect**. (Weitere Informationen finden Sie unter [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).)  
  
 Wenn umgebungsattributs SQL_ATTR_ODBC_VERSION nicht festgelegt ist, bevor Sie **SQLAllocHandle** wird aufgerufen, um ein Verbindungshandle zuordnen in der Umgebung gibt der Aufruf zum Reservieren von den SQLSTATE HY010 zurück (Sequence-Funktion (Fehler).  
  
 Wenn eine Anwendung ruft **SQLAllocHandle** mit der *InputHandle* Argument auf SQL_HANDLE_DBC festgelegt wird und auch auf einer freigegebenen Umgebungshandle festlegen, versucht Sie, dass der Treiber-Manager finden Sie einen vorhandenen freigegebenen Umgebung, die der Umgebungsattribute festlegen, die von der Anwendung entspricht. Wenn keine Umgebung dieser Art vorhanden ist, wird eine mit einer Verweisanzahl von 1 (verwaltet durch den Treiber-Manager) erstellt. Wenn ein entsprechender freigegeben Environment wurde gefunden, dieses Handle an die Anwendung zurückgegeben wird, und dessen Verweiszähler erhöht wird.  
  
 Die eigentliche Verbindung, die verwendet werden, richtet sich nicht vom Treiber-Manager bis **SQLConnect** oder **SQLDriverConnect** aufgerufen wird. Der Treiber-Manager verwendet die Verbindungsoptionen im Aufruf von **SQLConnect** (oder die Verbindungsschlüsselwörter im Aufruf von **SQLDriverConnect**) und die Verbindungsattribute festlegen, nach der Zuordnung der Verbindung um Bestimmen Sie, welche Verbindung im Pool verwendet werden soll. Weitere Informationen finden Sie unter [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="allocating-a-statement-handle"></a>Zuordnen eines Anweisungshandles  
 Ein Anweisungshandle ermöglicht den Zugriff auf Anweisungsinformationen, z. B. Fehlermeldungen, Name des Cursors und Statusinformationen für die Verarbeitung von SQL-Anweisung. Allgemeine Informationen zu Anweisungshandles, finden Sie unter [Anweisungshandles](../../../odbc/reference/develop-app/statement-handles.md).  
  
 Um ein Anweisungshandle anzufordern, eine Anwendung eine Verbindung mit einer Datenquelle her und ruft dann **SQLAllocHandle** vor SQL-Anweisungen absenden. In diesem Aufruf *HandleType* sollte auf SQL_HANDLE_STMT festgelegt werden und *InputHandle* sollte festgelegt werden, um das Verbindungshandle, die durch den Aufruf zurückgegeben wurde **SQLAllocHandle** die dieses Handle zugeordnet. Der Treiber belegt Speicher für die Anweisungsinformationen, ordnet die angegebene Verbindung, und übergibt der Wert des zugeordneten Handles zurück, in das Anweisungshandle  *\*OutputHandlePtr*. Die Anwendung übergibt die  *\*OutputHandlePtr* Wert bei allen nachfolgenden Aufrufen, die ein Anweisungshandle erfordern. Weitere Informationen finden Sie unter [Zuordnen einer Anweisungshandle](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md).  
  
 Wenn das Anweisungshandle zugeordnet ist, der Treiber automatisch ordnet einen Satz von vier Deskriptoren und weist die Handles für diese Deskriptoren der SQL_ATTR_APP_ROW_DESC SQL_ATTR_APP_PARAM_DESC, SQL_ATTR_IMP_ROW_DESC und SQL_ATTR_IMP_PARAM_DESC Anweisungsattribute. Diese werden als bezeichnet *implizit* Deskriptoren zugeordnet. Um einen Anwendungsdienst-Deskriptor explizit zuzuordnen, finden Sie unter den folgenden Abschnitt "Zuweisen von einem Deskriptorhandles."  
  
## <a name="allocating-a-descriptor-handle"></a>Ein Deskriptorhandle zuordnen  
 Wenn eine Anwendung ruft **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DESC, weist der Treiber einen Anwendungsdienst-Deskriptor. Diese werden als bezeichnet *explizit* Deskriptoren zugeordnet. Die Anwendung leitet einen Treiber einen explizit zugewiesene Anwendungsdienst-Deskriptor für ein Handle für die angegebene Anweisung statt ein automatisch zugewiesener durch Aufrufen der **SQLSetStmtAttr** -Funktion mit dem SQL_ATTR_APP_ROW_DESC oder SQL_ATTR_APP_PARAM_DESC-Attribut. Ein Deskriptor für die Implementierung nicht explizit zugeordnet werden können, noch kann in ein Deskriptor Implementierung angegeben werden ein **SQLSetStmtAttr** Funktionsaufruf.  
  
 Explizit zugewiesene Deskriptoren sind ein Verbindungshandle, anstatt ein Anweisungshandle zugeordnet, (wie automatisch zugewiesene Deskriptoren). Deskriptoren bleiben weiter zugeordnet, nur, wenn eine Anwendung tatsächlich mit der Datenbank verbunden ist. Da explizit zugewiesene Deskriptoren ein Verbindungshandle zugeordnet sind, kann eine Anwendung mehr als eine Anweisung innerhalb einer Verbindung einen explizit zugewiesenen Deskriptor zuordnen. Ein implizit zugewiesene Anwendungsdienst-Deskriptor, kann nicht auf der anderen Seite mehr als ein Anweisungshandle zugeordnet werden. (Es kann keine Anweisungshandle als diejenige, die sie für zugewiesen wurde zugeordnet werden.) Explizit zugewiesene Deskriptorhandles können explizit freigegeben werden, von der Anwendung oder durch Aufrufen **SQLFreeHandle** mit einer *HandleType* SQL_HANDLE_DESC oder implizit, wenn die Verbindung ist geschlossen.  
  
 Wenn der explizit zugewiesene Deskriptor freigegeben wird, ist implizit zugewiesene Deskriptor erneut die Anweisung zugeordnet werden. (Das Attribut SQL_ATTR_APP_ROW_DESC oder SQL_ATTR_APP_PARAM_DESC für diese Anweisung wird erneut auf die implizit zugeordneten Deskriptorhandles festgelegt.) Dies gilt für alle Anweisungen, die für die Verbindung mit der explizit zugewiesene verknüpft waren.  
  
 Weitere Informationen zu den sicherheitsbeschreibungen, finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md), [SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md), und [SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Eine Umgebung, Verbindung, Anweisung oder Deskriptor Handle freigeben|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Ein Verbindungsattribut festlegen|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Festlegen von einem Beschreibungsfeld|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Ein Umgebungsattribut festlegen|[SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Wenn eine Anweisungsattribut|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
