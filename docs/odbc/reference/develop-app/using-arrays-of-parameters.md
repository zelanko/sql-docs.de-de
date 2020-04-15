---
title: Verwenden von Parameterarrays | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 5a28be88-e171-4f5b-bf4d-543c4383c869
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b584dc3d635e9fa8ce3228e4e89b0f24451fe165
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306801"
---
# <a name="using-arrays-of-parameters"></a>Verwenden von Parameterarrays
Um Arrays von Parametern zu verwenden, ruft die Anwendung **SQLSetStmtAttr** mit dem *Attributargument* SQL_ATTR_PARAMSET_SIZE auf, um die Anzahl der Parametersätze anzugeben. Es ruft **SQLSetStmtAttr** mit einem *Attributargument* von SQL_ATTR_PARAMS_PROCESSED_PTR an, um die Adresse einer Variablen anzugeben, in der der Treiber die Anzahl der verarbeiteten Parametersätze zurückgeben kann, einschließlich Fehlersätzen. Es ruft **SQLSetStmtAttr** mit einem *Attributargument* von SQL_ATTR_PARAM_STATUS_PTR auf ein Array zu verweisen, in dem Statusinformationen für jede Zeile von Parameterwerten zurückgegeben werden. Der Treiber speichert diese Adressen in der Struktur, die er für die Anweisung verwaltet.  
  
> [!NOTE]  
>  In ODBC 2. *x*wurde **SQLParamOptions** aufgerufen, um mehrere Werte für einen Parameter anzugeben. In ODBC 3. *x*wurde der Aufruf von **SQLParamOptions** durch Aufrufe von **SQLSetStmtAttr** ersetzt, um die SQL_ATTR_PARAMSET_SIZE- und SQL_ATTR_PARAMS_PROCESSED_ARRAY-Attribute festzulegen.  
  
 Vor dem Ausführen der Anweisung legt die Anwendung den Wert jedes Elements jedes gebundenen Arrays fest. Wenn die Anweisung ausgeführt wird, verwendet der Treiber die gespeicherten Informationen, um die Parameterwerte abzurufen und an die Datenquelle zu senden. wenn möglich, sollte der Treiber diese Werte als Arrays senden. Obwohl die Verwendung von Arrays von Parametern am besten durch Ausführen der SQL-Anweisung mit allen Parametern im Array mit einem einzigen Aufruf der Datenquelle implementiert wird, ist diese Funktion in DBMS heute nicht weit verbreitet. Treiber können dies jedoch simulieren, indem sie eine SQL-Anweisung mehrmals mit jeweils einem einzigen Satz von Parametern ausführen.  
  
 Bevor eine Anwendung Arrays von Parametern verwendet, muss sichergestellt sein, dass sie von den von der Anwendung verwendeten Treibern unterstützt werden. Hierfür gibt es zwei Möglichkeiten:  
  
-   Verwenden Sie nur Treiber, die für die Unterstützung von Arrays von Parametern bekannt sind. Die Anwendung kann die Namen dieser Treiber hartcodieren, oder der Benutzer kann angewiesen werden, nur diese Treiber zu verwenden. Benutzerdefinierte Anwendungen und vertikale Anwendungen verwenden häufig eine begrenzte Anzahl von Treibern.  
  
-   Überprüfen Sie, ob Arrays von Parametern zur Laufzeit unterstützt werden. Ein Treiber unterstützt Arrays von Parametern, wenn es möglich ist, das SQL_ATTR_PARAMSET_SIZE-Anweisungsattribut auf einen Wert größer als 1 festzulegen. Generische Anwendungen und vertikale Anwendungen überprüfen häufig auf die Unterstützung von Arrays von Parametern zur Laufzeit.  
  
 Die Verfügbarkeit von Zeilenanzahlen und Resultsets in der parametrisierten Ausführung kann durch Aufrufen von **SQLGetInfo** mit den SQL_PARAM_ARRAY_ROW_COUNTS- und SQL_PARAM_ARRAY_SELECTS-Optionen bestimmt werden. Für **INSERT**-, **UPDATE**- und **DELETE-Anweisungen** gibt die Option SQL_PARAM_ARRAY_ROW_COUNTS an, ob einzelne Zeilenanzahlen (eine für jeden Parametersatz) verfügbar sind (SQL_PARC_BATCH) oder ob Zeilenanzahlen in einer (SQL_PARC_NO_BATCH) zusammengefasst werden. Für **SELECT-Anweisungen** gibt die Option SQL_PARAM_ARRAY_SELECTS an, ob für jeden Parametersatz (SQL_PAS_BATCH) ein Resultset verfügbar ist oder ob nur ein Resultset verfügbar ist (SQL_PAS_NO_BATCH). Wenn der Treiber nicht zulässt, dass result set-generating-Anweisungen mit einem Array von Parametern ausgeführt werden, gibt SQL_PARAM_ARRAY_SELECTS SQL_PAS_NO_SELECT zurück. Es ist datenquellenspezifisch, ob Arrays von Parametern mit anderen Typen von Anweisungen verwendet werden können, insbesondere weil die Verwendung von Parametern in diesen Anweisungen datenquellenspezifisch wäre und nicht der ODBC SQL-Grammatik folgen würde.  
  
 Das Array, auf das das Attribut SQL_ATTR_PARAM_OPERATION_PTR-Anweisung zeigt, kann verwendet werden, um Parameterzeilen zu ignorieren. Wenn ein Element des Arrays auf SQL_PARAM_IGNORE festgelegt ist, wird der Diesem Element entsprechende Parametersatz vom **SQLExecute-** oder **SQLExecDirect-Aufruf** ausgeschlossen. Das Array, auf das das SQL_ATTR_PARAM_OPERATION_PTR Attribut s. zeigt, wird von der Anwendung zugewiesen und ausgefüllt und vom Treiber gelesen. Wenn abgerufene Zeilen als Eingabeparameter verwendet werden, können die Werte des Zeilenstatusarrays im Parameteroperationsarray verwendet werden.  
  
## <a name="error-processing"></a>Fehlerverarbeitung  
 Wenn beim Ausführen der Anweisung ein Fehler auftritt, gibt die Ausführungsfunktion einen Fehler zurück und legt die Zeilennummernvariable auf die Nummer der Zeile fest, die den Fehler enthält. Es ist datenquellenspezifisch, ob alle Zeilen außer dem Fehlersatz ausgeführt werden oder ob alle Zeilen vor (aber nicht nach) dem Fehlersatz ausgeführt werden. Da es Parametersätze verarbeitet, legt der Treiber den vom Attribut SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisung angegebenen Puffer auf die Nummer der aktuell verarbeiteten Zeile fest. Wenn alle Sätze außer dem Fehlersatz ausgeführt werden, legt der Treiber diesen Puffer auf SQL_ATTR_PARAMSET_SIZE, nachdem alle Zeilen verarbeitet wurden.  
  
 Wenn das SQL_ATTR_PARAM_STATUS_PTR Anweisungsattribut festgelegt wurde, gibt **SQLExecute** oder **SQLExecDirect** das *Parameterstatusarray zurück,* das den Status jedes Satzes von Parametern bereitstellt. Das Parameterstatusarray wird von der Anwendung zugewiesen und vom Treiber ausgefüllt. Seine Elemente geben an, ob die SQL-Anweisung für die Parameterzeile erfolgreich ausgeführt wurde oder ob bei der Verarbeitung des Parameterssatzes ein Fehler aufgetreten ist. Wenn ein Fehler aufgetreten ist, legt der Treiber den entsprechenden Wert im Parameterstatusarray auf SQL_PARAM_ERROR und gibt SQL_SUCCESS_WITH_INFO zurück. Die Anwendung kann das Statusarray überprüfen, um zu bestimmen, welche Zeilen verarbeitet wurden. Mithilfe der Zeilennummer kann die Anwendung den Fehler häufig korrigieren und die Verarbeitung fortsetzen.  
  
 Wie das Parameterstatusarray verwendet wird, hängt von den SQL_PARAM_ARRAY_ROW_COUNTS- und SQL_PARAM_ARRAY_SELECTS-Optionen ab, die von einem Aufruf von **SQLGetInfo**zurückgegeben werden. Bei den Anweisungen **INSERT**, **UPDATE**und **DELETE** wird das Parameterstatusarray mit Statusinformationen ausgefüllt, wenn SQL_PARC_BATCH für SQL_PARAM_ARRAY_ROW_COUNTS zurückgegeben wird, jedoch nicht, wenn SQL_PARC_NO_BATCH zurückgegeben wird. Für **SELECT-Anweisungen** wird das Parameterstatusarray ausgefüllt, wenn SQL_PAS_BATCH für SQL_PARAM_ARRAY_SELECT zurückgegeben wird, jedoch nicht, wenn SQL_PAS_NO_BATCH oder SQL_PAS_NO_SELECT zurückgegeben wird.  
  
## <a name="data-at-execution-parameters"></a>Data-at-Execution-Parameter  
 Wenn einer der Werte im Längen-Indikator-Array SQL_DATA_AT_EXEC oder das Ergebnis des Makros*SQL_LEN_DATA_AT_EXEC(Länge*) ist, werden die Daten für diese Werte auf die übliche Weise mit **SQLPutData** gesendet. Die folgenden Aspekte dieses Prozesses tragen besondere Anmerkungen, da sie nicht ohne weiteres ersichtlich sind:  
  
-   Wenn der Treiber SQL_NEED_DATA zurückgibt, muss er die Adresse der Zeilennummernvariablen auf die Zeile festlegen, für die er Daten benötigt. Wie im einzelwertigen Fall kann die Anwendung keine Annahmen über die Reihenfolge treffen, in der der Treiber Parameterwerte innerhalb eines einzigen Satzes von Parametern anfordert. Wenn bei der Ausführung eines Data-at-Execution-Parameters ein Fehler auftritt, wird der durch das Attribut SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisung angegebene Puffer auf die Nummer der Zeile festgelegt, in der der Fehler aufgetreten ist, der Status für die Zeile im Zeilenstatusarray, die durch das Attribut SQL_ATTR_PARAM_STATUS_PTR Anweisung angegeben wird, auf SQL_PARAM_ERROR festgelegt ist und der Aufruf von **SQLExecute**, **SQLExecDirect**, **SQLParamData**oder **SQLPutData** SQL_ERROR zurückgibt. Der Inhalt dieses Puffers ist nicht definiert, wenn **SQLExecute**, **SQLExecDirect**oder **SQLParamData** SQL_STILL_EXECUTING zurückgeben.  
  
-   Da der Treiber den Wert im *ParameterValuePtr-Argument* von **SQLBindParameter** für Data-at-Execution-Parameter nicht interpretiert, extrahiert **SQLParamData** kein Element dieses Arrays und gibt es an die Anwendung zurück, wenn die Anwendung einen Zeiger auf ein Array bereitstellt. Stattdessen wird der Skalarwert zurückgegeben, den die Anwendung angegeben hat. Dies bedeutet, dass der von **SQLParamData** zurückgegebene Wert nicht ausreicht, um den Parameter anzugeben, für den die Anwendung Daten senden muss. Die Anwendung muss auch die aktuelle Zeilennummer berücksichtigen.  
  
     Wenn nur einige Elemente eines Arrays von Parametern Daten-at-Execution-Parameter sind, muss die Anwendung die Adresse eines Arrays in *ParameterValuePtr* übergeben, das Elemente für alle Parameter enthält. Dieses Array wird normalerweise für die Parameter interpretiert, die keine Data-at-Execution-Parameter sind. Für die Parameter data-at-execution ist der Wert, den **SQLParamData** für die Anwendung bereitstellt, der normalerweise verwendet werden könnte, um die Daten zu identifizieren, die der Treiber bei dieser Gelegenheit anfordert, immer die Adresse des Arrays.
