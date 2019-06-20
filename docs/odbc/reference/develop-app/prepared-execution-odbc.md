---
title: Vorbereitete Ausführung ODBC | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7bd6bc8281dd6bdc3bcfbd437380b2d5269ee43
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199102"
---
# <a name="prepared-execution-odbc"></a>Vorbereitete Ausführungs-ODBC
Die vorbereitete Ausführung ist eine effiziente Möglichkeit, eine Anweisung mehrmals auszuführen. Die Anweisung zuerst kompiliert wurde, oder *vorbereitet,* in einer Access-Plan. Der Zugriff ist dann eine ausgeführt oder mehrmals zu einem späteren Zeitpunkt. Weitere Informationen zu Access-Plänen finden Sie unter [Verarbeiten einer SQL-Anweisung](../../../odbc/reference/processing-a-sql-statement.md).  
  
 Die vorbereitete Ausführung wird häufig von vertikaler und benutzerdefinierten Anwendungen verwendet, um die gleichen, parametrisierte SQL-Anweisung wiederholt auszuführen. Beispielsweise wird der folgende Code eine Anweisung aus, um die Preise für verschiedene Teile aktualisieren vorbereitet. Sie führt dann die Anweisung mehrmals mit unterschiedlichen Parameterwerten jeweils.  
  
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
  
 Vorbereitete Ausführung ist schneller als eine direkte Ausführung für Anweisungen, die mehr als einmal ausgeführt, in erster Linie verwendet werden, da die Anweisung nur einmal kompiliert wird. direkt ausgeführte Anweisungen werden jedes Mal kompiliert werden. Die vorbereitete Ausführung kann auch angeben, dass eine Reduzierung des Netzwerkverkehrs der Treiber ein planbezeichner Zugriff an die Datenquelle jedes Mal die Anweisung senden kann, anstatt eine gesamte SQL-Anweisung ausgeführt wird, da, wenn unterstützt den Datenquellenzugriff Bezeichner planen.  
  
 Die Metadaten für das Resultset nach dem die Anweisung vorbereitet ist, und bevor er ausgeführt wird, kann die Anwendung abrufen. Allerdings Rückgabe von Metadaten für vorbereitete, nicht ausgeführte Anweisungen ist für einige Treiber teuer und sollte von interoperablen Anwendungen ausführen können, wenn möglich vermieden werden. Weitere Informationen finden Sie unter [Ergebnismetadaten festgelegt](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 Die vorbereitete Ausführung sollte nicht für Anwendungen verwendet werden, die nur einmal ausgeführt werden. Für diese Anweisungen ist es etwas langsamer als eine direkte Ausführung, da es sich um einen zusätzlichen Aufruf der ODBC-Funktion erfordert.  
  
> [!IMPORTANT]  
>  Ein Commit oder Rollback einer Transaktion, entweder durch explizites Aufrufen von **SQLEndTran** oder im Autocommit Modus arbeiten, bewirkt, dass einige Datenquellen, um die Zugriffspläne für alle Anweisungen für eine Verbindung zu löschen. Weitere Informationen finden Sie unter den SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Optionen in der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung.  
  
 Zum Vorbereiten und Ausführen von Anweisungen, die Anwendung:  
  
1.  Aufrufe **SQLPrepare** und übergibt sie eine Zeichenfolge, die die SQL-Anweisung enthält.  
  
2.  Legt die Werte aller Parameter. Parameter können tatsächlich vor oder nach der Vorbereitung der Anweisung festgelegt werden. Weitere Informationen finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
3.  Aufrufe **SQLExecute** und führt zusätzliche Verarbeitung, die erforderlich sind, wie z. B. das Abrufen von Daten.  
  
4.  Wiederholen Sie Schritte 2 und 3, nach Bedarf.  
  
5.  Wenn **SQLPrepare** aufgerufen wird, wird den Treiber:  
  
    -   Ändert die SQL-Anweisung, um SQL-Grammatik für die Datenquelle zu verwenden, ohne die Anweisung zu analysieren. Dies schließt das Ersetzen der Escape-Sequenzen, die in beschriebenen [Escapesequenzen in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). Kann die Anwendung eine SQL-Anweisung geänderte Form durch den Aufruf abrufen **SQLNativeSql**. Escapesequenzen werden nicht ersetzt werden, wenn das SQL_ATTR_NOSCAN-Anweisungsattribut festgelegt ist.  
  
    -   Sendet die Anweisung mit der Datenquelle für die datenvorbereitung.  
  
    -   Speichert die zurückgegebenen Zugriff Plan-ID zur späteren Ausführung, (wenn es sich bei die Vorbereitung war erfolgreich) oder gibt Sie alle Fehler (wenn die Vorbereitung nicht erfüllt) zurück. Fehler sind Syntaxfehler z. B. SQLSTATE 42000 (Syntaxfehler oder zugriffsverletzung) und semantische Fehler wie z. B. SQLSTATE 42S02 (Basis-Tabelle oder Sicht wurde nicht gefunden).  
  
        > [!NOTE]  
        >  Einige Treiber Fehler nicht an diesem Punkt zurück, aber stattdessen zurücksenden, wenn die Anweisung ausgeführt wird oder Katalogfunktionen aufgerufen werden. Daher **SQLPrepare** scheinen erfolgreich ausgeführt wurden, wenn in der Tat es fehlgeschlagen ist.  
  
6.  Wenn **SQLExecute** aufgerufen wird, wird den Treiber:  
  
    -   Ruft die aktuellen Parameterwerte aus, und nach Bedarf konvertiert. Weitere Informationen finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
    -   Sendet die Bezeichner für den Zugriff und die konvertierten Parameterwerte an die Datenquelle an.  
  
    -   Gibt alle Fehler zurück. Hierbei handelt es sich um in der Regel zur Laufzeit Fehler, z. B. SQLSTATE 24000 (Ungültiger Cursorstatus). Einige Treiber zurückgeben syntaktischen und semantischen Fehler jedoch an diesem Punkt.  
  
 Wenn die Datenquelle die Vorbereitung der Anweisung nicht unterstützt, muss der Treiber im größtmöglichen Umfang emulieren. Z. B. der Treiber kann nichts bei **SQLPrepare** wird aufgerufen, und führen Sie direkte Ausführung der Anweisung beim **SQLExecute** aufgerufen wird.  
  
 Wenn die Datenquelle ohne Ausführung überprüft die Syntax unterstützt, kann der Treiber die Anweisung für die Überprüfung der beim Übermitteln **SQLPrepare** aufgerufen wird, und senden Sie die Anweisung für die Ausführung bei **SQLExecute** ist wird aufgerufen.  
  
 Wenn der Treiber anweisungsvorbereitung kann nicht zu emulieren, speichert Sie die Anweisung beim **SQLPrepare** aufgerufen wird, und übergibt sie zur Ausführung beim **SQLExecute** aufgerufen wird.  
  
 Da emulierten anweisungsvorbereitung nicht perfekt, **SQLExecute** können normalerweise von zurückgegebenen Fehler zurückzugeben, **SQLPrepare**.
