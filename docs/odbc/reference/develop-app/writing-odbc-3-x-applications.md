---
title: Schreiben von ODBC 3.x-Anwendungen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 93c8510bb23bb57244590a472073fc882f9fe64f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208454"
---
# <a name="writing-odbc-3x-applications"></a>Schreiben von ODBC-3.x-Anwendungen
Wenn eine ODBC-2. *x* Anwendung wird aktualisiert, um ODBC 3. *X*, sodass Funktionsweise mit ODBC 2 geschrieben werden sollen. *X* und 3. *X* Treiber. Die Anwendung sollte bedingten Code, um die ODBC 3. nutzen integrieren. *x* Funktionen.  
  
 Umgebungsattributs SQL_ATTR_ODBC_VERSION sollte auf SQL_OV_ODBC2 festgelegt werden. Dadurch wird sichergestellt, dass der Treiber wie einer ODBC 2. verhält *.x* Treiber in Bezug auf die Änderungen, die im Abschnitt beschriebenen [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Wenn die Anwendung eines der Features, die im Abschnitt beschriebenen verwenden [neue Features](../../../odbc/reference/develop-app/new-features.md), bedingter Code sollte verwendet werden, um festzustellen, ob der Treiber eine ODBC-3 ist. *X* oder ODBC 2.*.x* Treiber. Die Anwendung verwendet **SQLGetDiagField** und **SQLGetDiagRec** ODBC 3. abrufen. *X* SQLSTATEs während der Durchführung der Fehler beim Verarbeiten dieser Fragmente bedingten Code. Die folgenden Punkte bezüglich der neuen Funktionalität sollte berücksichtigt werden:  
  
-   Eine Anwendung, die von der Änderung im Verhalten der Rowset-Größe betroffenen vorsichtig nicht aufzurufende **SQLFetch** Wenn die Arraygröße ist größer als 1. Ersetzen Sie diese Anwendungen sollten Aufrufe **SQLExtendedFetch** mit Aufrufen von **SQLSetStmtAttr** das SQL_ATTR_ARRAY_STATUS_PTR-Anweisungsattribut festgelegt und **SQLFetchScroll**, sodass sie gemeinsamen Code verfügen, die mit den beiden ODBC 3. funktioniert. *x* und ODBC-2. *X* Treiber. Da **SQLSetStmtAttr** mit SQL_ATTR_ROW_ARRAY_SIZE zugeordnet **SQLSetStmtAttr** mit SQL_ROWSET_SIZE setzen ODBC 2. *X* Treiber, Anwendungen können die SQL_ATTR_ROW_ARRAY_SIZE für die Einfügung mehrerer Zeilen Abrufvorgänge einfach festlegen.  
  
-   Die meisten Anwendungen, die gerade aktualisiert werden, sind nicht tatsächlich von Änderungen in SQLSTATE-Codes betroffen. Bei Anwendungen, die betroffen sind, können sie mechanischen suchen und Ersetzen Sie in den meisten Fällen mithilfe von Konvertierungstabelle für die Fehler im Abschnitt "SQLSTATE-Zuordnungen" ODBC 3. zu konvertieren. *x* Fehlercodes ODBC 2.*.x* Codes. Da die ODBC 3.*.x* führt-Treiber-Manager die Zuordnung von ODBC 2. *X* SQLSTATEs zu ODBC 3. *X* SQLSTATEs diese Anwendungsentwickler benötigen nur die Kontrollkästchen für die ODBC 3. *X* SQLSTATEs und keine Sorgen, einschließlich der ODBC 2. *X* SQLSTATEs in bedingten Code.  
  
-   Wenn eine Anwendung gute Möglichkeit zur Verwendung von Date, Time und Timestamp-Datentypen, kann die Anwendung selbst werden von einer ODBC 2. deklarieren. *x* -Anwendung und zur Verwendung vorhandener code anstelle der Klimaanlage Code.  
  
 Das Upgrade sollte auch die folgenden Schritte umfassen:  
  
-   Rufen Sie **SQLSetEnvAttr** vor der Zuordnung von eine Verbindung zum SQL_OV_ODBC2 umgebungsattributs SQL_ATTR_ODBC_VERSION fest.  
  
-   Ersetzen Sie alle Aufrufe **SQLAllocEnv**, **SQLAllocConnect**, oder **SQLAllocStmt** mit Aufrufen von **SQLAllocHandle** mit dem entsprechenden *HandleType* Argument SQL_HANDLE_ENV auf, SQL_HANDLE_DBC auf oder SQL_HANDLE_STMT auf.  
  
-   Ersetzen Sie alle Aufrufe **SQLFreeEnv** oder **SQLFreeConnect** mit Aufrufen von **SQLFreeHandle** mit dem entsprechenden *HandleType* Argument SQL_HANDLE_DBC auf oder SQL_HANDLE_STMT auf.  
  
-   Ersetzen Sie alle Aufrufe **SQLSetConnectOption** mit Aufrufen von **SQLSetConnectAttr**. Wenn ein Attribut, dessen Wert festlegen. eine Zeichenfolge ist, legen Sie die *StringLength* Argument entsprechend. Änderung *Attribut* Argument von SQL_XXXX in SQL_ATTR_XXXX.  
  
-   Ersetzen Sie alle Aufrufe **SQLGetConnectOption** mit Aufrufen von **SQLGetConnectAttr**. Wenn eine Zeichenfolge oder ein binäres Attribut angezeigt werden soll, legen Sie *Pufferlänge* auf den entsprechenden Wert und übergeben Sie einen *StringLength* Argument. Änderung *Attribut* Argument von SQL_XXXX in SQL_ATTR_XXXX.  
  
-   Ersetzen Sie alle Aufrufe **SQLSetStmtOption** mit Aufrufen von **SQLSetStmtAttr**. Wenn ein Attribut, dessen Wert festlegen. eine Zeichenfolge ist, legen Sie die *StringLength* Argument entsprechend. Änderung *Attribut* Argument von SQL_XXXX in SQL_ATTR_XXXX.  
  
-   Ersetzen Sie alle Aufrufe **SQLGetStmtOption** mit Aufrufen von **SQLGetStmtAttr**. Wenn eine Zeichenfolge oder ein binäres Attribut angezeigt werden soll, legen Sie *Pufferlänge* auf den entsprechenden Wert und übergeben Sie einen *StringLength* Argument. Änderung *Attribut* Argument von SQL_XXXX in SQL_ATTR_XXXX.  
  
-   Ersetzen Sie alle Aufrufe **SQLTransact** mit Aufrufen von **SQLEndTran**. Wenn der äußersten rechten gültiges Handle in die **SQLTransact** Aufruf ist ein Umgebungshandle eine *HandleType* Argument SQL_HANDLE_ENV auf sollte verwendet werden, der **SQLEndTran** rufen Sie mit die entsprechende *behandeln* Argument. Wenn der äußersten rechten gültiges Handle in Ihre **SQLTransact** Aufruf ist ein Verbindungshandle ein *HandleType* Argument SQL_HANDLE_DBC auf, im verwendet werden soll die **SQLEndTran** mit aufrufen die entsprechende *behandeln* Argument.  
  
-   Ersetzen Sie alle Aufrufe **SQLColAttributes** mit Aufrufen von **SQLColAttribute**. Wenn die *FieldIdentifier* Argument ist einem SQL_COLUMN_PRECISION SQL_COLUMN_SCALE oder SQL_COLUMN_LENGTH, verändern sich etwas anderes als den Namen der Funktion nicht. Ändern Sie die *FieldIdentifier* aus SQL_COLUMN_XXXX zu SQL_DESC_XXXX. Wenn *FieldIdentifier* SQL_DESC_CONCISE_TYPE und der Datentyp Datetime-Datentyp, wechseln Sie in der entsprechenden ODBC 3.*.x* -Datentyp.  
  
-   Wenn Sie Blockcursor, scrollfähige Cursor oder beides verwenden zu können, führt die Anwendung Folgendes aus:  
  
    -   Legt die Rowsetgröße Cursortyp und Cursor Concurrency mit **SQLSetStmtAttr**.  
  
    -   Aufrufe **SQLSetStmtAttr** SQL_ATTR_ROW_STATUS_PTR auf ein Array der Statusdatensätze festlegen.  
  
    -   Aufrufe **SQLSetStmtAttr** festzulegende SQL_ATTR_ROWS_FETCHED_PTR fest, um auf eine SQLINTEGER zu verweisen.  
  
    -   Führt die erforderlichen Bindungen aus, und der SQL-Anweisung ausführt.  
  
    -   Aufrufe **SQLFetchScroll** in einer Schleife, um Zeilen abzurufen, und Navigieren in das Ergebnis festgelegt.  
  
    -   Wenn es durch Lesezeichen abrufen möchte, um die Anwendung ruft **SQLSetStmtAttr** SQL_ATTR_FETCH_BOOKMARK_PTR auf eine Variable festgelegt wird, die enthält das Lesezeichen für die Zeile, die abgerufen werden sollen, und ruft **SQLFetchScroll** mit einem *FetchOrientation* Argument von sql_fetch_bookmark auf.  
  
-   Wenn Sie Arrays von Parametern verwenden, führt die Anwendung Folgendes aus:  
  
    -   Aufrufe **SQLSetStmtAttr** das Attribut verweist SQL_ATTR_PARAMSET_SIZE auf die Größe des Parameterarrays zu festgelegt.  
  
    -   Aufrufe **SQLSetStmtAttr** SQL_ATTR_ROWS_PROCESSED_PTR auf eine interne UDWORD Variable festlegen.  
  
    -   Führt vorzubereiten, zu binden und Vorgänge nach Bedarf ausführen.  
  
    -   Wenn aus irgendeinem Grund (z. B. SQL_NEED_DATA) Ausführung angehalten wird, können diese Parameter die "aktuelle" Zeile finden, durch den Speicherort verweist SQL_ATTR_ROWS_PROCESSED_PTR überprüfen.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Zuordnen von Ersatzfunktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Aufrufen von SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Aufrufen von SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Aufrufen von SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Cursorbibliotheksvorgänge](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Zuordnen der Informationstypen „Cursor Attributes1“](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
