---
title: 'Anhang B: ODBC-Status Übergangs Tabellen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC]
- transitioning states [ODBC], about state transitions
- state transitions [ODBC], about state transitions
ms.assetid: 15088dbe-896f-4296-b397-02bb3d0ac0fb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7ceb128aec3a4cbe5ef7180483eb2a033ae57138
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67996250"
---
# <a name="appendix-b-odbc-state-transition-tables"></a>Anhang B: ODBC-Statusübergangstabellen
Die Tabellen in diesem Anhang veranschaulichen, wie ODBC-Funktionen Übergänge der Umgebungs-, Verbindungs-, Anweisungs-und deskriptorzustände verursachen. Der Zustand der Umgebung, der Verbindung, der Anweisung oder des Deskriptors gibt in der Regel an, wann Funktionen aufgerufen werden können, die den entsprechenden Typ des Handles (Umgebung, Verbindung, Anweisung oder Deskriptor) verwenden. Die Umgebungs-, Verbindungs-, Anweisungs-und deskriptorzustände überlappen sich ungefähr wie in den folgenden Abbildungen dargestellt. Beispielsweise ist die genaue Überlappung der Verbindungszustände C5 und C6 und der Anweisungs Status S1 bis S12 Datenquellen abhängig, da Transaktionen zu unterschiedlichen Zeiten in verschiedenen Datenquellen beginnen und der deskriptorstatus D1i (implizit zugeordneter Deskriptor) von abhängt. der Status der Anweisung, der der Deskriptor zugeordnet ist, während State D1e (explizit zugeordneter Deskriptor) unabhängig vom Status einer beliebigen Anweisung ist. Eine Beschreibung jedes Zustands finden Sie unter [Umgebungs Übergänge](../../../odbc/reference/appendixes/environment-transitions.md), [Verbindungs Übergänge](../../../odbc/reference/appendixes/connection-transitions.md), [Anweisungs Übergänge](../../../odbc/reference/appendixes/statement-transitions.md)und [deskriptorübergänge](../../../odbc/reference/appendixes/descriptor-transitions.md)weiter unten in diesem Anhang.  
  
 Die Umgebungs-und Verbindungszustände überlappen sich wie folgt:  
  
 ![Umgebungs- und Verbindungsstatuswerte überlappen](../../../odbc/reference/appendixes/media/app01.gif "app01")  
  
 Die Verbindungs-und Anweisungs Zustände überlappen sich wie folgt:  
  
 ![Verbindungs- und Anweisungsstatuswerte überlappen](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 Die Anweisungs-und deskriptorzustände überlappen sich wie folgt:  
  
 ![Anweisungs- und Deskriptorstatuswerte überlappen](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 Die Verbindungs-und deskriptorzustände überlappen sich wie folgt:  
  
 ![Verbindungs- und Deskriptorstatuswerte überlappen](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 Jeder Eintrag in einer Übergangs Tabelle kann einen der folgenden Werte aufweisen:  
  
-   **--**-Der Status ist nach dem Ausführen der Funktion unverändert.  
  
-   **Fresser**  

     **_n_** , **C_n_**, **S_n_** oder **D_n_** -die Umgebung, die Verbindung, die Anweisung oder der deskriptorzustand werden in den angegebenen Zustand verschoben.  
 
-   **(IH)** : an die Funktion wurde ein ungültiges Handle übermittelt. Wenn das Handle ein NULL-Handle oder ein gültiges Handle des falschen Typs war, z. b. wurde ein Verbindungs Handle bei erforderlicher Angabe eines Anweisungs Handles übermittelt, gibt die Funktion SQL_INVALID_HANDLE zurück. Andernfalls ist das Verhalten nicht definiert und wahrscheinlich schwerwiegend. Dieser Fehler wird nur angezeigt, wenn dies das einzige mögliche Ergebnis des Aufruf der Funktion im angegebenen Zustand ist. Dieser Fehler ändert den Status nicht und wird vom Treiber-Manager immer erkannt, wie in Klammern angegeben.  
  
-   **NS** -nächster Zustand. Der Anweisungs Übergang ist identisch mit dem, wenn die Anweisung die asynchronen Zustände nicht durchlaufen hat. Nehmen wir beispielsweise an, dass eine Anweisung, die ein Resultset erstellt, den Status "S11" aus dem Status "S1" erhält, weil **sqlexSQL_STILL_EXECUTING EC** Die NS-Notation im Zustand "S11" bedeutet, dass die Übergänge für die-Anweisung mit denen für eine Anweisung im Status S1 identisch sind, die ein Resultset erstellt. Wenn **SQLExecDirect** einen Fehler zurückgibt, verbleibt die Anweisung im Status S1. Wenn dies erfolgreich ist, wird die Anweisung in den Status "S5" verschoben. Wenn Daten benötigt werden, wird die Anweisung in den Status S8 verschoben; Wenn Sie noch ausgeführt wird, bleibt Sie im Zustand "S11".  

-   **_XXXXX_** oder **(*XXXXX*)** : ein SQLSTATE, der mit der Übergangs Tabelle verknüpft ist. Sqlstates, die vom Treiber-Manager erkannt werden, werden in Klammern eingeschlossen. Die Funktion hat SQL_ERROR und den angegebenen SQLSTATE zurückgegeben, aber der Zustand ändert sich nicht. Wenn z. b. **SQLExecute** vor **SQLPrepare**aufgerufen wird, wird SQLSTATE HY010 (Funktions Sequenz Fehler) zurückgegeben.  

> [!NOTE]  
>  In den Tabellen werden keine Fehler angezeigt, die sich nicht auf die Übergangs Tabellen, die den Status nicht ändern, nicht ändern. Wenn **SQLAllocHandle** beispielsweise im Umgebungszustand E1 aufgerufen wird und SQLSTATE HY001 (Speicher Belegungs Fehler) zurückgibt, verbleibt die Umgebung im Zustand E1. Dies wird in der Umgebungs Übergangs Tabelle für **sqlzuweisung**nicht angezeigt.  
  
 Wenn die Umgebung, die Verbindung, die Anweisung oder der Deskriptor in mehr als einen Zustand wechseln kann, wird jeder mögliche Status angezeigt, und mindestens eine Fußnote erläutert die Bedingungen, unter denen die einzelnen Übergänge stattfinden. Die folgenden Fußnoten können in jeder Tabelle angezeigt werden.  
  
|Fußnote|Bedeutung|  
|--------------|-------------|  
|b|Vor oder nach. Der Cursor befindet sich vor dem Anfang des Resultsets oder nach dem Ende des Resultsets.|  
|c|Aktuelle Funktion. Die aktuelle Funktion wurde asynchron ausgeführt.|  
|d|Benötigen Sie Daten. Die Funktion, die SQL_NEED_DATA zurückgegeben.|  
|e|Fehler. Die Funktion, die SQL_ERROR zurückgegeben.|  
|i|Ungültige Zeile. Der Cursor wurde auf einer Zeile im Resultset positioniert, und entweder wurde die Zeile gelöscht, oder bei einem Vorgang für die Zeile ist ein Fehler aufgetreten. Wenn das Zeilen Status Array vorhanden war, war der Wert im Zeilen Status Array für die Zeile SQL_ROW_DELETED oder SQL_ROW_ERROR. (Auf das Zeilen Status Array wird durch das SQL_ATTR_ROW_STATUS_PTR Statement-Attribut verwiesen.)|  
|NF|Nicht gefunden: Die Funktion, die SQL_NO_DATA zurückgegeben. Dies gilt nicht, wenn **SQLExecDirect**, **SQLExecute**oder **SQLParamData** SQL_NO_DATA nach dem Ausführen einer durchsuchten Update-oder DELETE-Anweisung zurückgibt.|  
|np|Nicht vorbereitet. Die Anweisung wurde nicht vorbereitet.|  
|Nr.|Keine Ergebnisse. Die Anweisung erstellt kein Resultset oder hat kein Resultset erstellt.|  
|o|Andere Funktion. Eine andere Funktion wurde asynchron ausgeführt.|  
|p|Vorbereitete. Die Anweisung wurde vorbereitet.|  
|r|Ergebnisse. Mit der-Anweisung wird ein (möglicherweise leeres) Resultset erstellt.|  
|s|Erfolg. Die Funktion, die SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgegeben wurde.|  
|v|Gültige Zeile. Der Cursor wurde in einer Zeile im Resultset positioniert, und die Zeile wurde erfolgreich eingefügt, erfolgreich aktualisiert, oder ein anderer Vorgang in der Zeile wurde erfolgreich abgeschlossen. Wenn das Zeilen Status Array vorhanden war, lautete der Wert im Zeilen Status Array für die Zeile SQL_ROW_ADDED, SQL_ROW_SUCCESS oder SQL_ROW_UPDATED. (Auf das Zeilen Status Array wird durch das SQL_ATTR_ROW_STATUS_PTR Statement-Attribut verwiesen.)|  
|x|Ausführ. Die Funktion, die SQL_STILL_EXECUTING zurückgegeben.|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 In diesem Beispiel ist die Zeile in der Umgebungs Status Übergangs Tabelle für **SQLFreeHandle** , wenn der- *Typ* SQL_HANDLE_ENV lautet, wie folgt.  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Teilte|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|IH|E0|HY010|  
  
 Wenn **SQLFreeHandle** im Umgebungs Status E0 aufgerufen *wird und auf SQL_HANDLE_ENV festgelegt* ist, gibt der Treiber-Manager SQL_INVALID_HANDLE zurück. Wenn Sie im Zustand E1 aufgerufen wird, wobei der *Typ* auf SQL_HANDLE_ENV festgelegt ist, wird die Umgebung in den Zustand E0 verschoben, wenn die Funktion erfolgreich ausgeführt wird, und bleibt im Zustand E1, wenn die Funktion fehlschlägt. Wenn Sie in State E2 aufgerufen wird, wobei der- *Typ* auf SQL_HANDLE_ENV festgelegt ist, gibt der Treiber-Manager immer SQL_ERROR und SQLSTATE HY010 (Funktions Sequenz Fehler) zurück, und die Umgebung verbleibt im Status E2.  
  
 Um die Status Übergangs Tabellen zu verstehen, müssen Sie wissen, auf welches Element (Umgebung, Verbindung, Anweisung oder Deskriptor) Sie verweisen. Angenommen, eine Funktion akzeptiert das Handle eines Elements vom Typ X. Die X-Status Übergangs Tabelle für diese Funktion beschreibt, wie sich das Aufrufen der-Funktion mit dem Handle eines Elements vom Typ X auf dieses Element auswirkt. **SQLDisconnect** nimmt z. b. ein Verbindungs Handle an. Die Verbindungsstatus-Übergangs Tabelle für **SQLDisconnect** beschreibt, wie **SQLDisconnect** den Status der Verbindung beeinflusst, für die er aufgerufen wird.  
  
 Angenommen, eine Funktion akzeptiert das Handle eines Elements vom Typ y, wobei Y nicht gleich X ist. Die X-Status Übergangs Tabelle für diese Funktion beschreibt, wie das Aufrufen der-Funktion mit einem Handle vom Typ X, das mit dem Element vom Typ y verknüpft ist, sich auf das Element vom Typ y auswirkt. Beispielsweise beschreibt die Anweisungs Status-Übergangs Tabelle für **SQLDisconnect** , wie sich **SQLDisconnect** auf den Zustand einer-Anweisung auswirkt, wenn Sie mit dem Handle der Verbindung aufgerufen wird, der die-Anweisung zugeordnet ist.  
  
 Dieser Anhang enthält die folgenden Themen:  
  
-   [Umgebungsübergänge](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [Verbindungsübergänge](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [Anweisungsübergänge](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [Deskriptorübergänge](../../../odbc/reference/appendixes/descriptor-transitions.md)
