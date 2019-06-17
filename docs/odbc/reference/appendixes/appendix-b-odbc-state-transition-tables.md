---
title: 'Anhang B: ODBC-Übergang Statustabellen | Microsoft-Dokumentation'
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
manager: craigg
ms.openlocfilehash: 82c19931073aa96eb045f574e8670068f3d3c659
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026896"
---
# <a name="appendix-b-odbc-state-transition-tables"></a>Anhang B: ODBC-Statusübergangstabellen
Die Tabellen in diesem Anhang zeigen, wie Funktionen mit ODBC-Übergang von der Umgebung, Verbindung, -Anweisung und Deskriptor Status führen. Der Status der Umgebung, die Verbindung, die Anweisung oder die Sicherheitsbeschreibung schreibt in der Regel vor, wenn Funktionen, mit denen den entsprechenden Typ des Handles (Umgebung, Verbindung, Anweisung oder Descriptor) aufgerufen werden kann. Die Status-Umgebung, Verbindung, anweisungs- und Deskriptorstatuswerte überlappen ungefähr wie in den folgenden Abbildungen dargestellt. Z. B. die genaue Überlappung der Verbindung gibt C5 und C6 und Anweisung gibt an, dass S1 bis S12 ist datenquellenabhängig, da Transaktionen, die zu unterschiedlichen Zeiten in verschiedenen Datenquellen beginnt und Deskriptor Zustand D1i (implizit Deskriptor zugeordnet) abhängig ist. auf den Zustand der Anweisung, die der Deskriptor zugeordnet ist, ist beim Status D1e (explizit Deskriptor zugeordnet) zum unabhängig vom Status-Anweisungen. Eine Beschreibung der einzelnen Status, finden Sie unter [Umgebungsübergänge](../../../odbc/reference/appendixes/environment-transitions.md), [Verbindungsübergänge](../../../odbc/reference/appendixes/connection-transitions.md), [Statusübergänge](../../../odbc/reference/appendixes/statement-transitions.md), und [Deskriptor Übergänge ](../../../odbc/reference/appendixes/descriptor-transitions.md)weiter unten in diesem Anhang.  
  
 Die umgebungs- und verbindungsstatuswerte überlappen wie folgt aus:  
  
 ![Umgebungs- und verbindungsstatuswerte überlappen](../../../odbc/reference/appendixes/media/app01.gif "app01")  
  
 Die Verbindungs- und -verbindungsstatuswerte überlappen wie folgt aus:  
  
 ![Verbindungs- und Anweisungsstatuswerte überlappen](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 Die Zustände anweisungs- und Deskriptorstatuswerte überlappen wie folgt aus:  
  
 ![Gibt an anweisungs- und Deskriptorstatuswerte überlappen](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 Die Zustände Verbindungs- und Deskriptorstatuswerte überlappen wie folgt aus:  
  
 ![Gibt an Verbindungs- und Deskriptorstatuswerte überlappen](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 Jeder Eintrag in einer Tabelle der Zustandsübergänge ist einer der folgenden Werte möglich:  
  
-   **--** -Der Status bleibt unverändert, nach der Ausführung der Funktion.  
  
-   **E**  

     **_n_**  , **C_n_** , **S_n_** , oder **D_n_** – die Umgebung, Verbindung, Anweisung oder Deskriptor Zustand verschoben wird, auf den angegebenen Zustand.  
 
-   **(BEI)**  -Ein ungültiges Handle an die Funktion übergeben wurde. Wenn das Handle ein null-Handle war oder ein gültiges Handle des falschen Typs – z. B. wurde ein Anweisungshandle war erforderlich – die Funktion gibt SQL_INVALID_HANDLE zurück ein Verbindungshandle bei übergeben; Andernfalls ist das Verhalten nicht definiert "und" wahrscheinlich schwerwiegend. Dieser Fehler wird angezeigt, nur, wenn es das einzig mögliche Ergebnis des Funktionsaufrufs im angegebenen Zustand ist. Dieser Fehler ändert sich nicht auf den Zustand und vom Treiber-Manager, wird immer erkannt werden, wie durch die Klammern angegeben.  
  
-   **NS** -nächsten Status. Der Anweisung Übergang ist identisch, als wäre die Anweisung die asynchronen Status nicht durchgearbeitet haben. Nehmen wir beispielsweise an eine Anweisung, die ein Resultset erstellt Status S11 vom Zustand S1 wechselt, da **SQLExecDirect** SQL_STILL_EXECUTING zurückgegeben. Die NS-Notation im Zustand S11 bedeutet, dass die Übergänge für die Anweisung sind identisch mit denen für eine Anweisung Zustand S1, die ein Resultset erstellt. Wenn **SQLExecDirect** einen Fehler zurückgibt, der Anweisung behält Ihre Zustand S1; Wenn dies gelingt, verschiebt der Anweisung in den Status des S5; Wenn sie Daten, verschiebt der Anweisung in den Status des S8; und wenn er noch ausgeführt wird, bleibt im Zustand S11.  

-   **_XXXXX_**  oder **(*XXXXX*)** – ein SQLSTATE, der auf die Tabelle der Zustandsübergänge; bezieht SQLSTATEs, die vom Treiber-Manager erkannt werden in Klammern eingeschlossen. Die Funktion zurückgegeben wird, SQL_ERROR zurück, und der angegebenen SQLSTATE, aber der Status ändert sich nicht. Z. B. wenn **SQLExecute** wird aufgerufen, bevor **SQLPrepare**, SQLSTATE HY010 zurückgegeben (Sequenzfehler funktionieren).  

> [!NOTE]  
>  Die Tabellen nicht mehr anzeigen Fehler, die nicht mit den Übergang-Tabellen, die den Status nicht geändert werden. Z. B. wenn **SQLAllocHandle** in Zustand der Umgebung E1 aufgerufen wird, und gibt SQLSTATE HY001 (Fehler bei der speicherbelegung), die Umgebung bleibt im Zustand E1; Dies wird nicht angezeigt, in der Umgebung übergangstabelle für  **SQLAllocHandle**.  
  
 Wenn die Umgebung, Verbindung, Anweisung oder -Deskriptor in mehr als ein Zustand verschoben werden kann, wird jedem möglicher Status wird angezeigt, und eine oder mehrere Fußnoten wird erläutert, die Bedingungen, unter denen jeder Übergang stattfindet. Die folgenden Fußnoten, möglicherweise in einer Tabelle angezeigt.  
  
|Fußnote|Bedeutung|  
|--------------|-------------|  
|b|Vor oder nach. Der Cursor wurde vor dem Start des Resultsets oder nach dem Ende des Resultsets positioniert.|  
|c|Aktuelle Funktion. Die aktuelle Funktion wurde asynchron ausgeführt.|  
|d|Benötigen Sie Daten an. Der Funktion zurückgegebene SQL_NEED_DATA zurück.|  
|e|Error (Fehler). Der Funktion zurückgegebene SQL_ERROR zurück.|  
|i|Ungültige Zeile. Der Cursor positioniert wurde in einer Zeile im Resultset Satz und die Zeile hatte wurde gelöscht oder in einem Vorgang in der Zeile ist ein Fehler aufgetreten. Wenn die zeilenstatusarray vorhanden war, wurde der Wert in der zeilenstatusarray für die Zeile SQL_ROW_DELETED oder SQL_ROW_ERROR. (Die zeilenstatusarray wird durch das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR verwiesen.)|  
|nf|Nicht gefunden. Der Funktion zurückgegebene SQL_NO_DATA zurückgibt. Dies gilt nicht beim **SQLExecDirect**, **SQLExecute**, oder **SQLParamData** gibt SQL_NO_DATA nach der Ausführung einer gesuchten update oder delete-Anweisung.|  
|np|Nicht vorbereitet. Die Anweisung wurde nicht vorbereitet.|  
|Nr.|Keine Ergebnisse. Die Anweisung nicht der Fall ist, oder ein Resultset nicht erstellt wurde.|  
|o|Andere Funktion. Eine andere Funktion wurde asynchron ausgeführt.|  
|p|Vorbereitet. Die Anweisung wurde vorbereitet.|  
|r|Ergebnisse. Die Anweisung oder hat ein Resultset für die (möglicherweise leere) erstellt wird.|  
|s|Erfolg. Die Funktion hat SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgegeben.|  
|v|Gültige Zeile. Der Cursor wurde in einer Zeile im Resultset positioniert und die Zeile mussten erfolgreich eingefügt wurde, wurde erfolgreich aktualisiert wurde, oder ein anderer Vorgang in der Zeile mussten erfolgreich ausgeführt wurden. Wenn die zeilenstatusarray vorhanden war, war der Wert in der zeilenstatusarray für die Zeile SQL_ROW_ADDED, SQL_ROW_SUCCESS oder SQL_ROW_UPDATED. (Die zeilenstatusarray wird durch das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR verwiesen.)|  
|x|Wird ausgeführt. Der Funktion zurückgegebene SQL_STILL_EXECUTING.|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 In diesem Beispiel wird die Zeile in der Umgebung Statusübergang für Tabelle **SQLFreeHandle** beim *HandleType* SQL_HANDLE_ENV ist wie folgt.  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> zugewiesen|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|E0|(HY010)|  
  
 Wenn **SQLFreeHandle** wird aufgerufen, in dem Zustand der Umgebung E0 mit *HandleType* auf SQL_HANDLE_ENV auf festgelegt ist, gibt der Treiber-Manager SQL_INVALID_HANDLE. Wenn sie aufgerufen wird, im Zustand E1 mit *HandleType* auf SQL_HANDLE_ENV auf festgelegt ist, verschiebt die Umgebung E0 angeben, wenn die Funktion erfolgreich ist, und im Status E1, verbleibt Wenn die Funktion fehlschlägt. Wenn sie aufgerufen wird, im Zustand E2 mit *HandleType* auf SQL_HANDLE_ENV auf festgelegt ist, der Treiber-Manager immer gibt SQL_ERROR zurück, und SQLSTATE HY010 (Funktion Sequenzfehler) und die Umgebung im Zustand E2 bleibt.  
  
 Um den Übergang Statustabellen zu verstehen, ist es erforderlich, um zu verstehen, welches Element (Umgebung, Verbindung, Anweisung oder Descriptor) auf die sie verweisen. Nehmen wir an, dass eine Funktion das Handle für ein Element vom Typ X akzeptiert. X Tabelle der Zustandsübergänge für diese Funktion wird beschrieben, wie der Aufruf die Funktion, mit dem Handle eines Elements vom Typ X, dieses Element wirkt sich auf. Z. B. **SQLDisconnect** akzeptiert ein Verbindungshandle. Verbindung der Tabelle der Zustandsübergänge für **SQLDisconnect** wird beschrieben, wie **SQLDisconnect** wirkt sich auf den Zustand der Verbindung für das es aufgerufen wird.  
  
 Nehmen wir an, dass eine Funktion das Handle für ein Element vom Typ "Y" akzeptiert, wobei Y nicht gleich X ist. X Tabelle der Zustandsübergänge für diese Funktion wird beschrieben, wie der Aufruf die Funktion mit einem Handle vom Typ X, die das Element vom Typ "Y" zugeordnet ist das Element vom Typ Y wirkt sich auf. Z. B. die Anweisungstabelle der Zustandsübergänge für **SQLDisconnect** wird beschrieben, wie **SQLDisconnect** wirkt sich auf den Zustand einer Anweisung, die bei einem Aufruf mit das Handle für die Verbindung mit dem die Anweisung ist zugeordnet.  
  
 Dieser Anhang enthält die folgenden Themen.  
  
-   [Umgebungsübergänge](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [Verbindungsübergänge](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [Statusübergänge](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [Descriptor Transitions (Deskriptorübergänge)](../../../odbc/reference/appendixes/descriptor-transitions.md)
