---
title: Schreiben von ODBC 3.x-Anwendungen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288988"
---
# <a name="writing-odbc-3x-applications"></a>Schreiben von ODBC-3.x-Anwendungen
Wenn eine ODBC *2.x-Anwendung* auf ODBC *3.x*aktualisiert wird, sollte sie so geschrieben werden, dass sie sowohl mit ODBC *2.x-* als auch mit *3.x-Treibern* funktioniert. Die Anwendung sollte bedingten Code enthalten, um die Funktionen von ODBC *3.x* voll auszuschöpfen.  
  
 Das SQL_ATTR_ODBC_VERSION Umgebungsattribut sollte auf SQL_OV_ODBC2 festgelegt werden. Dadurch wird sichergestellt, dass sich der Treiber in Bezug auf die im Abschnitt [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md)beschriebenen Änderungen wie ein ODBC *2.x-Treiber* verhält.  
  
 Wenn die Anwendung eines der im Abschnitt [Neue Features](../../../odbc/reference/develop-app/new-features.md)beschriebenen Features verwendet, sollte bedingter Code verwendet werden, um zu bestimmen, ob es sich bei dem Treiber um einen ODBC *3.x-* oder ODBC *2.x-Treiber* handelt. Die Anwendung verwendet **SQLGetDiagField** und **SQLGetDiagRec,** um ODBC *3.x* SQLSTATEs zu erhalten, während Fehlerverarbeitung für diese bedingten Codefragmente. Die folgenden Punkte zur neuen Funktionalität sollten berücksichtigt werden:  
  
-   Eine Anwendung, die von der Änderung des Rowset-Größenverhaltens betroffen ist, sollte darauf achten, **SQLFetch** nicht aufzurufen, wenn die Arraygröße größer als 1 ist. Diese Anwendungen sollten Aufrufe von **SQLExtendedFetch** durch Aufrufe von **SQLSetStmtAttr** ersetzen, um das SQL_ATTR_ARRAY_STATUS_PTR-Anweisungsattribut und **SQLFetchScroll**festzulegen, sodass sie über allgemeinen Code verfügen, der sowohl mit ODBC *3.x-* als auch mit ODBC *2.x-Treibern* funktioniert. Da **SQLSetStmtAttr** mit SQL_ATTR_ROW_ARRAY_SIZE **SQLSetStmtAttr** mit SQL_ROWSET_SIZE für ODBC *2.x-Treiber* zugeordnet wird, können Anwendungen einfach SQL_ATTR_ROW_ARRAY_SIZE für ihre mehrreihigen Abrufvorgänge festlegen.  
  
-   Die meisten Anwendungen, die aktualisiert werden, sind nicht wirklich von Änderungen in SQLSTATE-Codes betroffen. Für die betroffenen Anwendungen können sie eine mechanische Suche durchführen und in den meisten Fällen mithilfe der Fehlerkonvertierungstabelle im Abschnitt "SQLSTATE Mapping" ersetzen, um ODBC *3.x-Fehlercodes* in ODBC *2.x-Codes* zu konvertieren. Da der ODBC *3.x-Treiber-Manager* die Zuordnung von ODBC *2.x* SQLSTATEs zu ODBC *3.x* SQLSTATEs durchführt, müssen diese Anwendungsautoren nur nach den ODBC *3.x* SQLSTATEs suchen und sich keine Gedanken über die Einbeziehung von ODBC *2.x* SQLSTATEs in bedingten Code machen.  
  
-   Wenn eine Anwendung Datums-, Uhrzeit- und Zeitstempeldatentypen stark verwendet, kann sich die Anwendung als ODBC *2.x-Anwendung* deklarieren und den vorhandenen Code verwenden, anstatt Konditionierungscode zu verwenden.  
  
 Das Upgrade sollte auch die folgenden Schritte umfassen:  
  
-   Rufen Sie **SQLSetEnvAttr** auf, bevor Sie eine Verbindung zuweisen, um das SQL_ATTR_ODBC_VERSION Umgebungsattribut auf SQL_OV_ODBC2 festzulegen.  
  
-   Ersetzen Sie alle Aufrufe von **SQLAllocEnv**, **SQLAllocConnect**oder **SQLAllocStmt** durch Aufrufe von **SQLAllocHandle** durch das entsprechende *HandleType-Argument* von SQL_HANDLE_ENV, SQL_HANDLE_DBC oder SQL_HANDLE_STMT.  
  
-   Ersetzen Sie alle Aufrufe von **SQLFreeEnv** oder **SQLFreeConnect** durch Aufrufe von **SQLFreeHandle** durch das entsprechende *HandleType-Argument* von SQL_HANDLE_DBC oder SQL_HANDLE_STMT.  
  
-   Ersetzen Sie alle Aufrufe von **SQLSetConnectOption** durch Aufrufe von **SQLSetConnectAttr**. Wenn Sie ein Attribut festlegen, dessen Wert eine Zeichenfolge ist, legen Sie das *StringLength-Argument* entsprechend fest. *Attributargument* von SQL_XXXX in SQL_ATTR_XXXX ändern.  
  
-   Ersetzen Sie alle Aufrufe von **SQLGetConnectOption** durch Aufrufe von **SQLGetConnectAttr**. Wenn Sie ein Zeichenfolgen- oder Binärattribut abrufen, legen Sie *BufferLength* auf den entsprechenden Wert fest, und übergeben Sie ein *StringLength-Argument.* *Attributargument* von SQL_XXXX in SQL_ATTR_XXXX ändern.  
  
-   Ersetzen Sie alle Aufrufe von **SQLSetStmtOption** durch Aufrufe von **SQLSetStmtAttr**. Wenn Sie ein Attribut festlegen, dessen Wert eine Zeichenfolge ist, legen Sie das *StringLength-Argument* entsprechend fest. *Attributargument* von SQL_XXXX in SQL_ATTR_XXXX ändern.  
  
-   Ersetzen Sie alle Aufrufe von **SQLGetStmtOption** durch Aufrufe von **SQLGetStmtAttr**. Wenn Sie ein Zeichenfolgen- oder Binärattribut abrufen, legen Sie *BufferLength* auf den entsprechenden Wert fest, und übergeben Sie ein *StringLength-Argument.* *Attributargument* von SQL_XXXX in SQL_ATTR_XXXX ändern.  
  
-   Ersetzen Sie alle Aufrufe von **SQLTransact** durch Aufrufe von **SQLEndTran**. Wenn das rechtsgültigste Handle im **SQLTransact-Aufruf** ein Umgebungshandle ist, sollte ein *HandleType-Argument* von SQL_HANDLE_ENV im **SQLEndTran-Aufruf** mit dem entsprechenden *Handle-Argument* verwendet werden. Wenn das rechtsgültigste Handle in Ihrem **SQLTransact-Aufruf** ein Verbindungshandle ist, sollte ein *HandleType-Argument* von SQL_HANDLE_DBC im **SQLEndTran-Aufruf** mit dem entsprechenden *Handle-Argument* verwendet werden.  
  
-   Ersetzen Sie alle Aufrufe von **SQLColAttributes** durch Aufrufe von **SQLColAttribute**. Wenn das *FieldIdentifier-Argument* entweder SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE oder SQL_COLUMN_LENGTH ist, ändern Sie nichts anderes als den Namen der Funktion. Wenn dies nicht der Fall ist, ändern Sie *FieldIdentifier* von SQL_COLUMN_XXXX in SQL_DESC_XXXX. Wenn *FieldIdentifier* SQL_DESC_CONCISE_TYPE ist und der Datentyp ein Datetime-Datentyp ist, ändern Sie ihn in den entsprechenden ODBC *3.x-Datentyp.*  
  
-   Wenn Blockcursor, scrollbare Cursor oder beides verwendet werden, führt die Anwendung die folgenden Schritte aus:  
  
    -   Legt die Rowsetgröße, den Cursortyp und die Cursorparallelität mithilfe von **SQLSetStmtAttr**fest.  
  
    -   Ruft **SQLSetStmtAttr** auf, um SQL_ATTR_ROW_STATUS_PTR so festzulegen, dass es auf ein Array von Statusdatensätzen zeigt.  
  
    -   Ruft **SQLSetStmtAttr** auf, um SQL_ATTR_ROWS_FETCHED_PTR so festzulegen, dass es auf einen SQLINTEGER verweisen.  
  
    -   Führt die erforderlichen Bindungen aus und führt die SQL-Anweisung aus.  
  
    -   Ruft **SQLFetchScroll** in einer Schleife auf, um Zeilen abzurufen und sich im Resultset zu bewegen.  
  
    -   Wenn sie nach Lesezeichen abrufen möchte, ruft die Anwendung **SQLSetStmtAttr** auf, um SQL_ATTR_FETCH_BOOKMARK_PTR auf eine Variable festzulegen, die die Textmarke für die Zeile enthält, die sie abrufen möchte, und ruft **SQLFetchScroll** mit dem *FetchOrientation-Argument* SQL_FETCH_BOOKMARK auf.  
  
-   Wenn Sie Arrays von Parametern verwenden, führt die Anwendung die folgenden Schritte aus:  
  
    -   Ruft **SQLSetStmtAttr** auf, um das SQL_ATTR_PARAMSET_SIZE-Attribut auf die Größe des Parameterarrays festzulegen.  
  
    -   Ruft **SQLSetStmtAttr** auf, um SQL_ATTR_ROWS_PROCESSED_PTR so festzulegen, dass es auf eine interne UDWORD-Variable angibt.  
  
    -   Führt ggf. vorbereitende, bindende und ausgeführte Vorgänge aus.  
  
    -   Wenn die Ausführung aus irgendeinem Grund angehalten wird (z. B. SQL_NEED_DATA), kann die "aktuelle" Parameterzeile gefunden werden, indem die Position überprüft wird, auf die SQL_ATTR_ROWS_PROCESSED_PTR.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Zuordnen von Ersatzfunktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Aufrufen von SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Aufrufen von SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Aufrufen von SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Cursorbibliotheksvorgänge](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Zuordnen der Informationstypen „Cursor Attributes1“](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
