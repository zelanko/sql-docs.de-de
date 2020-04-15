---
title: Vorbereitete Ausführung ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- prepared execution [ODBC]
- SQL statements [ODBC], prepared execution
- SQL statements [ODBC], executing
ms.assetid: f08c8a98-31ee-48b2-9dbf-6f31c2166dbb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 147ca85b21296575ff55afbe66ab286cc4824fae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282310"
---
# <a name="prepared-execution-odbc"></a>Vorbereitete Ausführungs-ODBC
Die vorbereitete Ausführung ist eine effiziente Möglichkeit, eine Anweisung mehr als einmal auszuführen. Die Anweisung wird zuerst in einem Zugriffsplan zusammengestellt oder *vorbereitet.* Der Zugriffsplan wird dann ein oder mehrere Male zu einem späteren Zeitpunkt ausgeführt. Weitere Informationen zu Zugriffsplänen finden Sie unter [Verarbeiten einer SQL-Anweisung](../../../odbc/reference/processing-a-sql-statement.md).  
  
 Die vorbereitete Ausführung wird häufig von vertikalen und benutzerdefinierten Anwendungen verwendet, um dieselbe, parametrisierte SQL-Anweisung wiederholt auszuführen. Der folgende Code bereitet z. B. eine Anweisung vor, um die Preise verschiedener Teile zu aktualisieren. Anschließend wird die Anweisung mehrmals mit unterschiedlichen Parameterwerten ausgeführt.  
  
```  
SQLREAL       Price;  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0, PriceInd = 0;  
  
// Prepare a statement to update salaries in the Employees table.  
SQLPrepare(hstmt, "UPDATE Parts SET Price = ? WHERE PartID = ?", SQL_NTS);  
  
// Bind Price to the parameter for the Price column and PartID to  
// the parameter for the PartID column.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &PartID, 0, &PartIDInd);  
  
// Repeatedly execute the statement.  
while (GetPrice(&PartID, &Price)) {  
   SQLExecute(hstmt);  
}  
```  
  
 Die vorbereitete Ausführung ist schneller als die direkte Ausführung für Anweisungen, die mehr als einmal ausgeführt werden, hauptsächlich weil die Anweisung nur einmal kompiliert wird. Direkt ausgeführte Anweisungen werden bei jeder Ausführung kompiliert. Die vorbereitete Ausführung kann auch zu einer Verringerung des Netzwerkverkehrs führen, da der Treiber bei jeder Ausführung der Anweisung einen Zugriffsplanbezeichner an die Datenquelle senden kann, anstatt eine gesamte SQL-Anweisung, wenn die Datenquelle Zugriffsplanbezeichner unterstützt.  
  
 Die Anwendung kann die Metadaten für das Resultset abrufen, nachdem die Anweisung vorbereitet und ausgeführt wurde. Das Zurückgeben von Metadaten für vorbereitete, nicht ausgeführte Anweisungen ist jedoch für einige Treiber teuer und sollte nach Möglichkeit durch interoperable Anwendungen vermieden werden. Weitere Informationen finden Sie unter [Ergebnissatzmetadaten](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 Die vorbereitete Ausführung sollte nicht für Anwendungen verwendet werden, die nur einmal ausgeführt werden. Für solche Anweisungen ist sie etwas langsamer als die direkte Ausführung, da ein zusätzlicher ODBC-Funktionsaufruf erforderlich ist.  
  
> [!IMPORTANT]  
>  Das Commit oder Rollback einer Transaktion, entweder durch explizites Aufrufen von **SQLEndTran** oder durch Arbeiten im Autocommit-Modus, bewirkt, dass einige Datenquellen die Zugriffspläne für alle Anweisungen für eine Verbindung löschen. Weitere Informationen finden Sie in den Optionen SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR in der [SQLGetInfo-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
 Um eine Anweisung vorzubereiten und auszuführen, wird die Anwendung:  
  
1.  Ruft **SQLPrepare** auf und übergibt ihm eine Zeichenfolge, die die SQL-Anweisung enthält.  
  
2.  Legt die Werte aller Parameter fest. Parameter können tatsächlich vor oder nach der Vorbereitung der Anweisung festgelegt werden. Weitere Informationen finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
3.  Ruft **SQLExecute** auf und führt alle erforderlichen zusätzlichen Verarbeitungen durch, z. B. das Abrufen von Daten.  
  
4.  Wiederholt die Schritte 2 und 3 bei Bedarf.  
  
5.  Wenn **SQLPrepare** aufgerufen wird, lautet der Treiber:  
  
    -   Ändert die SQL-Anweisung, um die SQL-Grammatik der Datenquelle zu verwenden, ohne die Anweisung zu analysieren. Dazu gehört das Ersetzen der Escape-Sequenzen, die in [Escape Sequences in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)beschrieben werden. Die Anwendung kann die geänderte Form einer SQL-Anweisung abrufen, indem sie **SQLNativeSql aufruft.** Escapesequenzen werden nicht ersetzt, wenn das SQL_ATTR_NOSCAN-Anweisungsattribut festgelegt ist.  
  
    -   Sendet die Anweisung zur Vorbereitung an die Datenquelle.  
  
    -   Speichert den zurückgegebenen Zugriffsplanbezeichner für die spätere Ausführung (falls die Vorbereitung erfolgreich war) oder gibt Fehler zurück (wenn die Vorbereitung fehlgeschlagen ist). Zu den Fehlern gehören syntaktische Fehler wie SQLSTATE 42000 (Syntaxfehler oder Zugriffsverletzung) und semantische Fehler wie SQLSTATE 42S02 (Basistabelle oder Ansicht nicht gefunden).  
  
        > [!NOTE]  
        >  Einige Treiber geben an dieser Stelle keine Fehler zurück, sondern sie, wenn die Anweisung ausgeführt wird oder wenn Katalogfunktionen aufgerufen werden. Daher scheint **SQLPrepare** erfolgreich zu sein, wenn es tatsächlich fehlgeschlagen ist.  
  
6.  Wenn **SQLExecute** aufgerufen wird, lautet der Treiber:  
  
    -   Ruft die aktuellen Parameterwerte ab und konvertiert sie bei Bedarf. Weitere Informationen finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
    -   Sendet den Zugriffsplanbezeichner und konvertierte Parameterwerte an die Datenquelle.  
  
    -   Gibt alle Fehler zurück. Dies sind im Allgemeinen Laufzeitfehler wie SQLSTATE 24000 (Ungültiger Cursorstatus). Einige Treiber geben jedoch an dieser Stelle syntaktische und semantische Fehler zurück.  
  
 Wenn die Datenquelle die Anweisungsvorbereitung nicht unterstützt, muss der Treiber sie so weit wie möglich emulieren. Der Treiber kann z. B. nichts tun, wenn **SQLPrepare** aufgerufen wird, und führt dann die direkte Ausführung der Anweisung durch, wenn **SQLExecute** aufgerufen wird.  
  
 Wenn die Datenquelle Syntaxprüfungen ohne Ausführung unterstützt, sendet der Treiber möglicherweise die Anweisung zur Überprüfung, wenn SQLPrepare aufgerufen **wird,** und sendet die Anweisung zur Ausführung, wenn **SQLExecute** aufgerufen wird.  
  
 Wenn der Treiber die Anweisungsvorbereitung nicht emulieren kann, speichert er die Anweisung, wenn **SQLPrepare** aufgerufen wird, und sendet sie zur Ausführung, wenn **SQLExecute** aufgerufen wird.  
  
 Da die Emulierte Anweisungsvorbereitung nicht perfekt ist, kann **SQLExecute** alle Fehler zurückgeben, die normalerweise von **SQLPrepare**zurückgegeben werden.
