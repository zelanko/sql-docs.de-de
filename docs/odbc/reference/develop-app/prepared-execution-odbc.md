---
title: Vorbereitete Ausführung von ODBC | Microsoft-Dokumentation
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
ms.openlocfilehash: 2107ca1eeecc6fad24311c5bce629784ae4ceff0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68023281"
---
# <a name="prepared-execution-odbc"></a>Vorbereitete Ausführungs-ODBC
Die vorbereitete Ausführung ist eine effiziente Möglichkeit, eine Anweisung mehrmals auszuführen. Die-Anweisung wird zuerst in einen Zugriffs Plan kompiliert oder *vorbereitet* . Der Zugriffs Plan wird dann einmal oder mehrmals zu einem späteren Zeitpunkt ausgeführt. Weitere Informationen zu Zugriffs Plänen finden Sie unter [Verarbeiten einer SQL-Anweisung](../../../odbc/reference/processing-a-sql-statement.md).  
  
 Die vorbereitete Ausführung wird häufig von vertikalen und benutzerdefinierten Anwendungen verwendet, um dieselbe, parametrisierte SQL-Anweisung wiederholt auszuführen. Der folgende Code bereitet z. b. eine-Anweisung vor, um die Preise verschiedener Teile zu aktualisieren. Die Anweisung führt die Anweisung dann mehrmals mit verschiedenen Parameterwerten aus.  
  
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
  
 Die vorbereitete Ausführung ist schneller als die direkte Ausführung für Anweisungen, die mehrmals ausgeführt werden, hauptsächlich, weil die Anweisung nur einmal kompiliert wird. direkt ausgeführte Anweisungen werden jedes Mal kompiliert, wenn Sie ausgeführt werden. Durch die vorbereitete Ausführung kann auch der Netzwerkverkehr reduziert werden, da der Treiber bei jeder Ausführung der Anweisung einen Zugriffs Plan Bezeichner an die Datenquelle senden kann, anstatt eine gesamte SQL-Anweisung zu erstellen, wenn die Datenquelle Zugriffs Plan Bezeichner unterstützt.  
  
 Die Anwendung kann die Metadaten für das Resultset abrufen, nachdem die Anweisung vorbereitet wurde und bevor Sie ausgeführt wird. Die Rückgabe von Metadaten für vorbereitete, nicht ausgeführte Anweisungen ist jedoch für einige Treiber teuer und sollte nach Möglichkeit von interoperablen Anwendungen vermieden werden. Weitere Informationen finden Sie unter [Resultsetmetadaten](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 Die vorbereitete Ausführung sollte nicht für Anwendungen verwendet werden, die nur einmal ausgeführt werden. Bei solchen Anweisungen ist die Ausführung etwas langsamer als bei der direkten Ausführung, da ein zusätzlicher ODBC-Funktions Aufrufvorgang erforderlich ist.  
  
> [!IMPORTANT]  
>  Das Ausführen eines Commits oder Rollbacks einer Transaktion durch explizites Aufrufen von **SQLEndTran** oder durcharbeiten im Autocommit-Modus bewirkt, dass einige Datenquellen die Zugriffs Pläne für alle Anweisungen in einer Verbindung löschen. Weitere Informationen finden Sie in den Optionen SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion.  
  
 Zum Vorbereiten und Ausführen einer-Anweisung führt die Anwendung Folgendes aus:  
  
1.  Ruft **SQLPrepare** auf und übergibt ihm eine Zeichenfolge, die die SQL-Anweisung enthält.  
  
2.  Legt die Werte von Parametern fest. Parameter können vor oder nach der Vorbereitung der Anweisung festgelegt werden. Weitere Informationen finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
3.  Ruft **SQLExecute** auf und führt ggf. erforderliche zusätzliche Verarbeitungsschritte aus, z. b. das Abrufen von Daten.  
  
4.  Wiederholt die Schritte 2 und 3 nach Bedarf.  
  
5.  Wenn **SQLPrepare** aufgerufen wird, gibt der Treiber Folgendes an:  
  
    -   Ändert die SQL-Anweisung so, dass die SQL-Grammatik der Datenquelle verwendet wird, ohne die-Anweisung zu verwenden. Dies umfasst das Ersetzen der in Escapesequenzen [in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)beschriebenen Escapesequenzen. Die Anwendung kann das geänderte Formular einer SQL-Anweisung abrufen, indem **SQLNativeSql**aufgerufen wird. Escapesequenzen werden nicht ersetzt, wenn das SQL_ATTR_NOSCAN-Anweisungs Attribut festgelegt ist.  
  
    -   Sendet die-Anweisung zur Vorbereitung an die Datenquelle.  
  
    -   Speichert den zurückgegebenen Zugriffs Plan Bezeichner für die spätere Ausführung (wenn die Vorbereitung erfolgreich war) oder gibt alle Fehler zurück (wenn die Vorbereitung nicht durchgeführt werden konnte). Zu den Fehlern zählen syntaktische Fehler wie SQLSTATE 42000 (Syntax Fehler oder Zugriffsverletzung) und Semantik Fehler, wie z. b. SQLSTATE 42s02 (Basistabelle oder Sicht nicht gefunden).  
  
        > [!NOTE]  
        >  Einige Treiber geben an dieser Stelle keine Fehler zurück, sondern geben Sie zurück, wenn die Anweisung ausgeführt wird oder Katalog Funktionen aufgerufen werden. Daher erscheint **SQLPrepare** möglicherweise als erfolgreich, wenn es tatsächlich fehlgeschlagen ist.  
  
6.  Wenn **SQLExecute** aufgerufen wird, wird der Treiber:  
  
    -   Ruft die aktuellen Parameterwerte ab und konvertiert sie nach Bedarf. Weitere Informationen finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
    -   Sendet den Zugriffs Plan Bezeichner und die konvertierten Parameterwerte an die Datenquelle.  
  
    -   Gibt alle Fehler zurück. Dabei handelt es sich im Allgemeinen um Laufzeitfehler, z. b. SQLSTATE 24000 (Ungültiger Cursor Zustand). An dieser Stelle geben einige Treiber jedoch syntaktische und semantische Fehler zurück.  
  
 Wenn die Datenquelle die Anweisungs Vorbereitung nicht unterstützt, muss der Treiber Sie so weit wie möglich emulieren. Beispielsweise kann der Treiber beim Aufrufen von **SQLPrepare** keine Aktion ausführen und dann die Anweisung ausführen, wenn **SQLExecute** aufgerufen wird.  
  
 Wenn die Datenquelle die Syntax Überprüfung ohne Ausführung unterstützt, sendet der Treiber möglicherweise die-Anweisung zur Überprüfung, wann **SQLPrepare** aufgerufen wird, und sendet die Anweisung für die Ausführung, wenn **SQLExecute** aufgerufen wird.  
  
 Wenn der Treiber die Anweisungs Vorbereitung nicht emulieren kann, speichert er die Anweisung beim Aufrufen von **SQLPrepare** und sendet Sie zur Ausführung, wenn **SQLExecute** aufgerufen wird.  
  
 Da die Vorbereitung der emulierten Anweisung nicht perfekt ist, kann **SQLExecute** alle Fehler zurückgeben, die normalerweise von **SQLPrepare**zurückgegeben werden.
