---
title: Schreiben von ODBC 3. x-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], about upgrading
- ODBC drivers [ODBC], backward compatibility
- upgrading applications [ODBC]
- compatibility [ODBC], upgrading applications
- application upgrades [ODBC]
- upgrading applications [ODBC], about upgrading
- backward compatibility [ODBC], upgrading applications
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ba48d76babcaa5fcc49a541088f7c4cc349b569
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81288988"
---
# <a name="writing-odbc-3x-applications"></a>Schreiben von ODBC-3.x-Anwendungen
Wenn eine ODBC *2. x* -Anwendung auf ODBC *3. x*aktualisiert wird, sollte Sie so geschrieben werden, dass Sie sowohl mit ODBC *2. x* -als auch mit *3. x* -Treibern funktioniert. Die Anwendung sollte bedingten Code einschließen, um die ODBC *3. x* -Features in vollem Umfang nutzen zu können.  
  
 Das SQL_ATTR_ODBC_VERSION-Umgebungs Attribut sollte auf SQL_OV_ODBC2 festgelegt werden. Dadurch wird sichergestellt, dass sich der Treiber wie ein ODBC *2. x* -Treiber in Bezug auf die im Abschnitt " [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md)" beschriebenen Änderungen verhält.  
  
 Wenn die Anwendung eine der im Abschnitt [neue Features](../../../odbc/reference/develop-app/new-features.md)beschriebenen Features verwendet, sollte bedingter Code verwendet werden, um zu bestimmen, ob der Treiber ein ODBC *3. x* -oder ODBC *2. x* -Treiber ist. Die Anwendung verwendet **SQLGetDiagField** und **SQLGetDiagRec** zum Abrufen von ODBC *3. x* Sqlstates bei der Fehler Verarbeitung in diesen bedingten Code Fragmenten. Die folgenden Punkte bezüglich der neuen Funktionalität sollten berücksichtigt werden:  
  
-   Eine von der Änderung des rowsetgrößenverhaltens betroffene Anwendung sollte darauf achten, **SQLFetch** nicht aufzurufen, wenn die Array Größe größer als 1 ist. Diese Anwendungen sollten Aufrufe von **SQLExtendedFetch** durch Aufrufe von **SQLSetStmtAttr** ersetzen, um das SQL_ATTR_ARRAY_STATUS_PTR-Anweisungs Attribut und **SQLFetchScroll**festzulegen, sodass Sie gemeinsamen Code haben, der sowohl mit ODBC *3. x* -als auch mit ODBC *2. x* -Treibern funktioniert. Da **SQLSetStmtAttr** mit SQL_ATTR_ROW_ARRAY_SIZE **SQLSetStmtAttr** mit SQL_ROWSET_SIZE für ODBC *2. x* -Treiber zugeordnet wird, können Anwendungen einfach SQL_ATTR_ROW_ARRAY_SIZE für die mehrzeiligen Abruf Vorgänge festlegen.  
  
-   Die meisten Anwendungen, für die ein Upgrade durchgeführt wird, werden von Änderungen in SQLSTATE Codes nicht beeinträchtigt. Bei Anwendungen, die betroffen sind, können Sie in den meisten Fällen eine mechanische Suche durchführen und in den meisten Fällen die Fehler Konvertierungstabelle im Abschnitt "SQLSTATE Mapping" verwenden, um ODBC *3. x* -Fehlercodes in ODBC *2. x* -Codes zu konvertieren. Da der ODBC *3. x* -Treiber-Manager die Zuordnung von ODBC *2. x* Sqlstates zu ODBC *3. x* Sqlstates durchführt, müssen diese Anwendungs Schreiber nur nach ODBC *3. x* Sqlstates suchen und sich keine Gedanken darüber machen, ODBC *2. x* SQLStates in bedingtem Code einzubeziehen.  
  
-   Wenn eine Anwendung die Datentypen "Date", "Time" und "Zeitstempel" optimal verwendet, kann die Anwendung sich selbst als ODBC *2. x* -Anwendung deklarieren und Ihren vorhandenen Code anstelle der Verwendung von kondiingcode verwenden.  
  
 Das Upgrade sollte auch die folgenden Schritte umfassen:  
  
-   Nennen Sie **SQLSetEnvAttr** , bevor Sie eine Verbindung zuordnen, um das SQL_ATTR_ODBC_VERSION-Umgebungs Attribut auf SQL_OV_ODBC2 festzulegen.  
  
-   Ersetzen Sie alle Aufrufe von **sqlzucenv**, **sqlzugcconnect**oder **sqlzugcstmt** durch Aufrufe von **sqlzuordchandle** durch Aufrufe von "SQL_HANDLE_ENV", "SQL_HANDLE_DBC" oder "SQL_HANDLE_STMT". *HandleType*  
  
-   Ersetzen Sie alle Aufrufe von **sqlfreeerv** oder **sqlfreeconnect** durch Aufrufe von **SQLFreeHandle durch Aufrufe von SQLFreeHandle** durch *das entsprechende Handler* -Argument von SQL_HANDLE_DBC oder SQL_HANDLE_STMT.  
  
-   Ersetzen Sie alle Aufrufe von **SQLSetConnectOption** durch Aufrufe von **SQLSetConnectAttr**. Wenn Sie ein Attribut festlegen, dessen Wert eine Zeichenfolge ist, legen Sie das *StringLength* -Argument entsprechend fest. Ändern Sie das *Attribut* Argument von SQL_XXXX in SQL_ATTR_XXXX.  
  
-   Ersetzen Sie alle Aufrufe von **SQLGetConnectOption** durch Aufrufe von **SQLGetConnectAttr**. Wenn Sie eine Zeichenfolge oder ein binäres Attribut erhalten, legen Sie *BufferLength* auf den entsprechenden Wert fest, und übergeben Sie ein *StringLength* -Argument. Ändern Sie das *Attribut* Argument von SQL_XXXX in SQL_ATTR_XXXX.  
  
-   Ersetzen Sie alle Aufrufe von **SQLSetStmtOption** durch Aufrufe von **SQLSetStmtAttr**. Wenn Sie ein Attribut festlegen, dessen Wert eine Zeichenfolge ist, legen Sie das *StringLength* -Argument entsprechend fest. Ändern Sie das *Attribut* Argument von SQL_XXXX in SQL_ATTR_XXXX.  
  
-   Ersetzen Sie alle Aufrufe von **SQLGetStmtOption** durch Aufrufe von **SQLGetStmtAttr**. Wenn Sie eine Zeichenfolge oder ein binäres Attribut erhalten, legen Sie *BufferLength* auf den entsprechenden Wert fest, und übergeben Sie ein *StringLength* -Argument. Ändern Sie das *Attribut* Argument von SQL_XXXX in SQL_ATTR_XXXX.  
  
-   Ersetzen Sie alle Aufrufe von **SQLTransact** durch Aufrufe von **SQLEndTran**. Wenn das äußteste Rechte Handle im **SQLTransact** -Befehl ein Umgebungs Handle ist, sollte im **SQLEndTran** -Befehl mit dem entsprechenden *handle* -Argument ein " *Lenker Type* "-SQL_HANDLE_ENV Argument verwendet werden. Wenn das äußteste äußteste Handle in Ihrem **SQLTransact** -Befehl ein Verbindungs Handle ist, sollte im **SQLEndTran** -Befehl mit dem entsprechenden *handle* -Argument ein " *Lenker Type* "-SQL_HANDLE_DBC Argument verwendet werden.  
  
-   Ersetzen Sie alle Aufrufe von **SQLColAttribute** durch Aufrufe von **SQLColAttribute**. Wenn das *fieldidentifier* -Argument entweder SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE oder SQL_COLUMN_LENGTH ist, ändern Sie nichts anderes als den Namen der Funktion. Wenn nicht, ändern Sie *fieldidentifier* von SQL_COLUMN_XXXX in SQL_DESC_XXXX. Wenn *fieldidentifier* SQL_DESC_CONCISE_TYPE und der Datentyp ein DateTime-Datentyp ist, wechseln Sie in den entsprechenden ODBC *3. x* -Datentyp.  
  
-   Bei Verwendung von Blockcursorn, scrollfähigen Cursorn oder beidem führt die Anwendung Folgendes aus:  
  
    -   Legt die Rowsetgröße, den Cursortyp und die Cursor Parallelität mithilfe von **SQLSetStmtAttr**fest.  
  
    -   Ruft **SQLSetStmtAttr** auf, um SQL_ATTR_ROW_STATUS_PTR festzulegen, um auf ein Array von Status Datensätzen zu verweisen.  
  
    -   Ruft **SQLSetStmtAttr** auf, um SQL_ATTR_ROWS_FETCHED_PTR festzulegen, dass auf einen SQLINTEGER-Wert verweist.  
  
    -   Führt die erforderlichen Bindungen aus und führt die SQL-Anweisung aus.  
  
    -   Ruft **SQLFetchScroll** in einer Schleife auf, um Zeilen abzurufen und im Resultset zu verschieben.  
  
    -   Wenn Sie ein Lesezeichen abrufen möchten, ruft die Anwendung **SQLSetStmtAttr** auf, um SQL_ATTR_FETCH_BOOKMARK_PTR auf eine Variable festzulegen, die das Lesezeichen für die abzurufende Zeile enthält, und ruft **SQLFetchScroll** mit einem *FetchOrientation* -Argument von SQL_FETCH_BOOKMARK auf.  
  
-   Wenn Parameter Arrays verwendet werden, führt die Anwendung die folgenden Schritte aus:  
  
    -   Ruft **SQLSetStmtAttr** auf, um das SQL_ATTR_PARAMSET_SIZE-Attribut auf die Größe des Parameter Arrays festzulegen.  
  
    -   Ruft **SQLSetStmtAttr** auf, um SQL_ATTR_ROWS_PROCESSED_PTR festzulegen, um auf eine interne udword-Variable zu verweisen.  
  
    -   Führt Vorbereitungs-, Bindungs-und Ausführungs Vorgänge nach Bedarf aus.  
  
    -   Wenn die Ausführung aus irgendeinem Grund angehalten wird (z. b. SQL_NEED_DATA), kann Sie die "aktuelle" Zeile der Parameter ermitteln, indem Sie den Speicherort überprüft, auf den SQL_ATTR_ROWS_PROCESSED_PTR verweist.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Zuordnen von Ersatzfunktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Aufrufen von SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Aufrufen von SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Aufrufen von SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Cursorbibliotheksvorgänge](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Zuordnen der Informationstypen „Cursor Attributes1“](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
