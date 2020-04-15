---
title: 'Anhang B: OdBC-Zustandsübergangstabellen | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db20c492ababbe6bf8f065fce88067c643f2694d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302884"
---
# <a name="appendix-b-odbc-state-transition-tables"></a>Anhang B: ODBC-Statusübergangstabellen
Die Tabellen in diesem Anhang zeigen, wie ODBC-Funktionen Übergänge der Umgebungs-, Verbindungs-, Anweisungs- und Deskriptorzustände verursachen. Der Zustand der Umgebung, Verbindung, Anweisung oder Deskriptor bestimmt in der Regel, wann Funktionen aufgerufen werden können, die den entsprechenden Handletyp (Umgebung, Verbindung, Anweisung oder Deskriptor) verwenden. Die Umgebungs-, Verbindungs-, Anweisungs- und Deskriptorzustände überschneiden sich grob wie in den folgenden Abbildungen dargestellt. Beispielsweise ist die genaue Überlappung der Verbindungszustände C5 und C6 und der Anweisungszustände S1 bis S12 datenquellenabhängig, da Transaktionen zu unterschiedlichen Zeitpunkten auf verschiedenen Datenquellen beginnen und der Deskriptorstatus D1i (implizit zugewiesener Deskriptor) vom Status der Anweisung abhängt, der der Deskriptor zugeordnet ist, während der Status D1e (explizit zugewiesener Deskriptor) unabhängig vom Status einer Anweisung ist. Eine Beschreibung der einzelnen Status finden Sie weiter unten in diesem Anhang unter [Umgebungsübergänge](../../../odbc/reference/appendixes/environment-transitions.md), [Verbindungsübergänge](../../../odbc/reference/appendixes/connection-transitions.md), [Anweisungsübergänge](../../../odbc/reference/appendixes/statement-transitions.md)und [Deskriptorübergänge](../../../odbc/reference/appendixes/descriptor-transitions.md).  
  
 Die Umgebungs- und Verbindungszustände überschneiden sich wie folgt:  
  
 ![Umgebungs- und Verbindungsstatuswerte überlappen](../../../odbc/reference/appendixes/media/app01.gif "app01")  
  
 Die Verbindungs- und Anweisungszustände überschneiden sich wie folgt:  
  
 ![Verbindungs- und Anweisungsstatuswerte überlappen](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 Die Anweisungs- und Deskriptorzustände überschneiden sich wie folgt:  
  
 ![Anweisungs- und Deskriptorstatuswerte überlappen](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 Die Verbindungs- und Deskriptorzustände überschneiden sich wie folgt:  
  
 ![Verbindungs- und Deskriptorstatuswerte überlappen](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 Jeder Eintrag in einer Übergangstabelle kann einer der folgenden Werte sein:  
  
-   **--**-Der Zustand ist nach der Ausführung der Funktion unverändert.  
  
-   **E**  

     **_n_** , **C_n_**, **S_n_** oder **D_n_** - Der Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptorstatus wird in den angegebenen Zustand verschoben.  
 
-   **(IH)** - Ein ungültiges Handle wurde an die Funktion übergeben. Wenn das Handle ein NULL-Handle war oder ein gültiges Handle des falschen Typs war - z. B. ein Verbindungshandle übergeben wurde, wenn ein Anweisungshandle erforderlich war -, gibt die Funktion SQL_INVALID_HANDLE zurück. andernfalls ist das Verhalten nicht definiert und wahrscheinlich tödlich. Dieser Fehler wird nur angezeigt, wenn es das einzig mögliche Ergebnis des Aufrufs der Funktion im angegebenen Zustand ist. Dieser Fehler ändert den Status nicht und wird immer vom Treiber-Manager erkannt, wie von den Klammern angegeben.  
  
-   **NS** - Nächster Zustand. Der Anweisungsübergang ist derselbe, als ob die Anweisung nicht die asynchronen Zustände durchlaufen hätte. Angenommen, eine Anweisung, die ein Resultset erstellt, wechselt vom Status S1 in den Zustand S1, da **SQLExecDirect** SQL_STILL_EXECUTING zurückgegeben hat. Die NS-Notation im Zustand S11 bedeutet, dass die Übergänge für die Anweisung mit denen für eine Anweisung im Zustand S1 identisch sind, die eine Ergebnismenge erstellt. Wenn **SQLExecDirect** einen Fehler zurückgibt, verbleibt die Anweisung im Status S1. Wenn dies erfolgreich ist, wird die Anweisung in den Zustand S5 verschoben. Wenn datenbenötigt wird, wird die Anweisung in den Zustand S8 verschoben. und wenn es noch ausgeführt wird, bleibt es im Zustand S11.  

-   **_XXXXX_** oder **(*XXXXX*)** - Ein SQLSTATE, der mit der Übergangstabelle verknüpft ist; SQLSTATEs, die vom Treiber-Manager erkannt werden, sind in Klammern eingeschlossen. Die Funktion gab SQL_ERROR und die angegebene SQLSTATE zurück, aber der Status ändert sich nicht. Wenn **SQLExecute** beispielsweise vor **SQLPrepare**aufgerufen wird, gibt es SQLSTATE HY010 (Funktionssequenzfehler) zurück.  

> [!NOTE]  
>  In den Tabellen werden keine Fehler angezeigt, die nichts mit den Übergangstabellen zu tun haben, die den Status nicht ändern. Wenn **SQLAllocHandle** beispielsweise im Umgebungszustand E1 aufgerufen wird und SQLSTATE HY001 (Speicherzuordnungsfehler) zurückgibt, verbleibt die Umgebung im Status E1; Dies wird in der Umgebungsübergangstabelle für **SQLAllocHandle**nicht angezeigt.  
  
 Wenn die Umgebung, die Verbindung, die Anweisung oder der Deskriptor in mehr als einen Zustand verschoben werden kann, wird jeder mögliche Zustand angezeigt, und eine oder mehrere Fußnoten erläutern die Bedingungen, unter denen jeder Übergang stattfindet. Die folgenden Fußnoten können in jeder Tabelle angezeigt werden.  
  
|Fußnote|Bedeutung|  
|--------------|-------------|  
|b|Vorher oder nachher. Der Cursor wurde vor dem Beginn des Resultsets oder nach dem Ende des Resultsets positioniert.|  
|c|Aktuelle Funktion. Die aktuelle Funktion wurde asynchron ausgeführt.|  
|d|Benötigen Sie Daten. Die Funktion hat SQL_NEED_DATA zurückgegeben.|  
|e|Fehler. Die Funktion hat SQL_ERROR zurückgegeben.|  
|i|Ungültige Zeile. Der Cursor wurde in einer Zeile im Resultset positioniert, und entweder wurde die Zeile gelöscht, oder es ist ein Fehler in einem Vorgang in der Zeile aufgetreten. Wenn das Zeilenstatusarray vorhanden war, wurde der Wert im Zeilenstatusarray für die Zeile SQL_ROW_DELETED oder SQL_ROW_ERROR. (Auf das Zeilenstatusarray wird durch das Attribut SQL_ATTR_ROW_STATUS_PTR Anweisung verwiesen.)|  
|nf|Nicht gefunden: Die Funktion hat SQL_NO_DATA zurückgegeben. Dies gilt nicht, wenn **SQLExecDirect**, **SQLExecute**oder **SQLParamData** SQL_NO_DATA zurückgibt, nachdem eine suchte Aktualisierungs- oder Löschanweisung ausgeführt wurde.|  
|np|Nicht vorbereitet. Die Erklärung wurde nicht vorbereitet.|  
|nr|Keine Ergebnisse. Die Anweisung erstellt keine Ergebnismenge oder hat sie nicht erstellt.|  
|o|Andere Funktion. Eine andere Funktion wurde asynchron ausgeführt.|  
|p|Vorbereitet. Die Erklärung wurde vorbereitet.|  
|r|Ergebnisse. Die Anweisung erstellt ein (möglicherweise leeres) Resultset.|  
|s|Erfolg. Die Funktion wurde SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgegeben.|  
|v|Gültige Zeile. Der Cursor wurde in einer Zeile im Resultset positioniert, und die Zeile wurde erfolgreich eingefügt, erfolgreich aktualisiert oder ein anderer Vorgang in der Zeile wurde erfolgreich abgeschlossen. Wenn das Zeilenstatusarray vorhanden war, war der Wert im Zeilenstatusarray für die Zeile SQL_ROW_ADDED, SQL_ROW_SUCCESS oder SQL_ROW_UPDATED. (Auf das Zeilenstatusarray wird durch das Attribut SQL_ATTR_ROW_STATUS_PTR Anweisung verwiesen.)|  
|x|Ausführen. Die Funktion hat SQL_STILL_EXECUTING zurückgegeben.|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 In diesem Beispiel ist die Zeile in der Umgebungsstatusübergangstabelle für **SQLFreeHandle,** wenn *HandleType* SQL_HANDLE_ENV ist, wie folgt.  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|E0|(HY010)|  
  
 Wenn **SQLFreeHandle** im Umgebungszustand E0 aufgerufen wird, wobei *HandleType* auf SQL_HANDLE_ENV festgelegt ist, gibt der Treiber-Manager SQL_INVALID_HANDLE zurück. Wenn sie im Zustand E1 aufgerufen wird und *HandleType* auf SQL_HANDLE_ENV festgelegt ist, wird die Umgebung in den Status E0 verschoben, wenn die Funktion erfolgreich ist und im Status E1 verbleibt, wenn die Funktion fehlschlägt. Wenn es im Zustand E2 aufgerufen wird, wobei *HandleType* auf SQL_HANDLE_ENV festgelegt ist, gibt der Treiber-Manager immer SQL_ERROR und SQLSTATE HY010 (Funktionssequenzfehler) zurück, und die Umgebung verbleibt im Status E2.  
  
 Um die Zustandsübergangstabellen zu verstehen, ist es notwendig zu verstehen, auf welches Element (Umgebung, Verbindung, Anweisung oder Deskriptor) sie sich beziehen. Angenommen, eine Funktion akzeptiert das Handle eines Elements vom Typ X. Die X-Statusübergangstabelle für diese Funktion beschreibt, wie sich das Aufrufen der Funktion mit dem Handle eines Elements vom Typ X auf dieses Element auswirkt. **SQLDisconnect** akzeptiert z. B. ein Verbindungshandle. Die Verbindungsstatusübergangstabelle für **SQLDisconnect** beschreibt, wie **sich SQLDisconnect** auf den Status der Verbindung auswirkt, für die sie aufgerufen wird.  
  
 Angenommen, eine Funktion akzeptiert das Handle eines Elements vom Typ Y, wobei Y nicht gleich X ist. Die X-Statusübergangstabelle für diese Funktion beschreibt, wie sich das Aufrufen der Funktion mit einem Handle vom Typ X, das dem Element vom Typ Y zugeordnet ist, auf das Element vom Typ Y auswirkt. Die Anweisungsstatusübergangstabelle für **SQLDisconnect** beschreibt beispielsweise, wie **SQLDisconnect** den Status einer Anweisung beeinflusst, wenn sie mit dem Handle der Verbindung aufgerufen wird, der die Anweisung zugeordnet ist.  
  
 Dieser Anhang enthält die folgenden Themen.  
  
-   [Umgebungsübergänge](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [Verbindungsübergänge](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [Statusübergänge](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [Descriptor Transitions (Deskriptorübergänge)](../../../odbc/reference/appendixes/descriptor-transitions.md)
