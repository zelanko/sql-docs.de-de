---
title: Verwenden von Parameterarrays | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cf6b5127bac7aedf9e67918d38020c73a4afe186
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079603"
---
# <a name="using-arrays-of-parameters"></a>Verwenden von Parameterarrays
Verwenden von Arrays von Parametern, die Anwendung ruft **SQLSetStmtAttr** mit einer *Attribut* Argument verweist SQL_ATTR_PARAMSET_SIZE auf die Anzahl der Sätze von Parametern anzugeben. Ruft **SQLSetStmtAttr** mit einer *Attribut* Argument SQL_ATTR_PARAMS_PROCESSED_PTR an die Adresse einer Variablen, in dem der Treiber kann die Anzahl von Parametersätzen verarbeitet, zurück, Legt fest, einschließlich Fehler. Ruft **SQLSetStmtAttr** mit einer *Attribut* Argument des SQL_ATTR_PARAM_STATUS_PTR, zeigen Sie auf ein Array, in dem Statusinformationen für jede Zeile von Parameterwerten zurückgegeben. Der Treiber speichert diese Adressen in der Struktur, die für die Anweisung verwaltet.  
  
> [!NOTE]  
>  In ODBC 2. *x*, **SQLParamOptions** war aufgerufen, um die für einen Parameter mehrere Werte angeben. In ODBC 3. *x*, den Aufruf von **SQLParamOptions** wurde ersetzt durch Aufrufe von **SQLSetStmtAttr** verweist SQL_ATTR_PARAMSET_SIZE und SQL_ATTR_PARAMS_PROCESSED_ARRAY Attribute festlegen .  
  
 Die Anwendung vor dem Ausführen der Anweisung, legt fest, dass den Wert jedes Elements des jedes gebundene Array. Wenn die Anweisung ausgeführt wird, verwendet der Treiber die Informationen, die sie zum Abrufen der Werte der Parameter, und senden sie an der Datenquelle gespeichert; Wenn möglich, sollte der Treiber diese Werte als Arrays senden. Obwohl die Verwendung von Arrays von Parametern am besten durch Ausführen der SQL-Anweisung mit der alle Parameter im Array mit einem einzigen Aufruf an die Datenquelle implementiert wird, ist diese Funktion Allgemein verfügbar in DBMS derzeit nicht. Jedoch können Treiber es simulieren, indem Sie eine SQL-Anweisung mehrere Male, jeweils mit einem einzigen Satz von Parametern ausführen.  
  
 Bevor eine Anwendung von Parameterarrays verwendet, müssen sie sicher sein, dass sie durch die von der Anwendung verwendeten Treiber unterstützt werden. Hierfür gibt es zwei Möglichkeiten:  
  
-   Verwenden Sie nur die Treiber, die Arrays von Parametern zu unterstützen. Die Anwendung kann hartcodiert die Namen dieser Treiber oder der Benutzer kann Sie nur diese Treiber angewiesen werden. Benutzerdefinierte Anwendungen und vertikale Anwendungen verwenden im Allgemeinen eine begrenzte Gruppe von Treibern.  
  
-   Überprüfen Sie für die Unterstützung von Arrays von Parametern zur Laufzeit. Ein-Treiber unterstützt Arrays von Parametern, wenn es möglich ist, das Anweisungsattribut verweist SQL_ATTR_PARAMSET_SIZE auf einen Wert größer als 1 festgelegt. Generische Anwendungen und vertikale Anwendungen überprüfen Sie im Allgemeinen für die Unterstützung von Arrays von Parametern zur Laufzeit.  
  
 Die Verfügbarkeit der Zeilenanzahl und Resultsets, parametrisierten Ausführung kann bestimmt werden, indem **SQLGetInfo** mit den Optionen SQL_PARAM_ARRAY_ROW_COUNTS und SQL_PARAM_ARRAY_SELECTS. Für **einfügen**, **UPDATE**, und **löschen** -Anweisungen, die SQL_PARAM_ARRAY_ROW_COUNTS-Option gibt an, ob einzelne Zeilenanzahl (eine für jeden Parametersatz) verfügbar (SQL_PARC_BATCH) oder ob Zeilenanzahl in einem (SQL_PARC_NO_BATCH) Rollup enthalten sind. Für **wählen** -Anweisungen, die die SQL_PARAM_ARRAY_SELECTS-Option gibt an, gibt an, ob ein Resultset für einen Satz von Parametern (SQL_PAS_BATCH) verfügbar ist oder ob nur ein Resultset zur Verfügung (SQL_PAS_NO_BATCH) ist. Wenn der Treiber keine Ergebnis generieren mit dem Satz von auszuführenden Anweisungen mit einem Array von Parametern zulässt, gibt SQL_PARAM_ARRAY_SELECTS SQL_PAS_NO_SELECT zurück. Es ist Data Source-spezifische, ob Arrays von Parametern mit anderen Typen von Anweisungen verwendet werden können, insbesondere deshalb, weil die Verwendung von Parametern in diesen Anweisungen datenquellenspezifische Daten und würde nicht die ODBC-SQL-Grammatik.  
  
 Das Array verweist das SQL_ATTR_PARAM_OPERATION_PTR-Anweisungsattribut kann verwendet werden, um Zeilen der Parameter zu ignorieren. Wenn ein Element des Arrays auf SQL_PARAM_IGNORE festgelegt ist, wird der Satz von Parametern, die zum betreffenden Element gehörende ausgeschlossen der **SQLExecute** oder **SQLExecDirect** aufrufen. Das Array verweist das Attribut SQL_ATTR_PARAM_OPERATION_PTR zugeordnet und ausgefüllt von der Anwendung und vom Treiber gelesen. Wenn der abgerufene Zeilen als Eingabeparameter verwendet werden, können die Werte der zeilenstatusarray im Parameterarray Vorgang verwendet werden.  
  
## <a name="error-processing"></a>Fehlerverarbeitung  
 Wenn beim Ausführen der Anweisung ein Fehler auftritt, wird die Ausführungsfunktion einen Fehler zurück und wird die Anzahl Zeilen-Variable auf die Anzahl der Zeile, die den Fehler enthält. Es ist Data Source-spezifische, ob alle Zeilen außer dem festgelegten Fehler ausgeführt werden, oder, ob alle Zeilen (aber nicht nach) vor dem festgelegten Fehler ausgeführt werden. Da diese Sätze von Parametern verarbeitet, legt der Treiber den Puffer, der durch das SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisungsattribut auf die Anzahl der aktuell verarbeiteten Zeile angegeben. Wenn alle festlegt, außer dem festgelegten Fehler ausgeführt werden, legt der Treiber diesen Puffer, verweist SQL_ATTR_PARAMSET_SIZE, nachdem alle Zeilen verarbeitet wurden.  
  
 Wenn das SQL_ATTR_PARAM_STATUS_PTR-Anweisungsattribut festgelegt wurde, **SQLExecute** oder **SQLExecDirect** gibt die *Status Parameterarray,* dem bietet es sich um des Status der einen Satz von Parametern. Das Parameterarray-Status wird von der Anwendung belegt und vom Treiber ausgefüllt. Die Elemente anzugeben, ob die SQL-Anweisung für die Zeile der Parameter erfolgreich ausgeführt wurde, oder gibt an, ob ein Fehler aufgetreten ist, während der Verarbeitung des Satz von Parametern. Wenn ein Fehler aufgetreten ist, wird der Treiber legt den entsprechenden Wert im Parameterarray Status zu SQL_PARAM_ERROR und gibt SQL_SUCCESS_WITH_INFO zurück. Die Anwendung kann überprüfen, die Statusarray, um zu bestimmen, welche Zeilen verarbeitet wurden. Verwenden die Nummer der Zeile, die Anwendung kann häufig den Fehler zu beheben und die Verarbeitung fort.  
  
 Wie das Parameterarray-Status verwendet wird richtet sich nach den SQL_PARAM_ARRAY_ROW_COUNTS und SQL_PARAM_ARRAY_SELECTS-Optionen, die durch einen Aufruf zurückgegeben **SQLGetInfo**. Für **einfügen**, **UPDATE**, und **löschen** -Anweisungen, die Status-Parameterarray wird mit Informationen aufgefüllt, wenn SQL_PARC_BATCH für SQL_PARAM_ARRAY_ zurückgegeben wird ROW_COUNTS, aber nicht, wenn SQL_PARC_NO_BATCH zurückgegeben wird. Für **wählen** -Anweisungen, die Status-Parameterarray wird ausgefüllt, wenn SQL_PAS_BATCH für SQL_PARAM_ARRAY_SELECT zurückgegeben wird, aber keine SQL_PAS_NO_BATCH oder SQL_PAS_NO_SELECT zurückgegeben wird.  
  
## <a name="data-at-execution-parameters"></a>Data-at-Execution-Parameter  
 Wenn einer der Werte im Array Längenindikator/SQL_DATA_AT_EXEC oder das Ergebnis der SQL_LEN_DATA_AT_EXEC (*Länge*)-Makro, erhält die Daten für diese Werte mit **SQLPutData** auf die übliche Weise. Die folgenden Aspekte dieses Prozesses sollten besonderen Kommentar, da sie nicht sofort offensichtlich sind:  
  
-   Der Treiber gibt SQL_NEED_DATA muss er die Adresse der Variablen Anzahl Zeile auf die Zeile festgelegt, für die sie Daten benötigt. Wie im Fall einwertig kann nicht die Anwendung keine Annahmen über die Reihenfolge vornehmen, in dem der Treiber die Parameterwerte in einer einzigen Gruppe von Parametern anfordert. Tritt ein Fehler bei der Ausführung von Data-at-Execution-Parameter, ist der Puffer angegeben werden, indem Sie das SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisungsattribut festgelegt, die Anzahl der Zeilen, die auf dem der Fehler aufgetreten ist, den Status für die Zeile in der zeilenstatusarray gemäß Das SQL_ATTR_PARAM_STATUS_PTR-Anweisungsattribut festgelegt ist, um SQL_PARAM_ERROR und der Aufruf von **SQLExecute**, **SQLExecDirect**, **SQLParamData**, oder  **SQLPutData** gibt SQL_ERROR zurück. Der Inhalt dieses Puffers sind nicht definiert, wenn **SQLExecute**, **SQLExecDirect**, oder **SQLParamData** SQL_STILL_EXECUTING zurück.  
  
-   Da der Treiber nicht den Wert in interpretiert die *ParameterValuePtr* Argument **SQLBindParameter** für Data-at-Execution-Parameter, wenn die Anwendung einen Zeiger auf ein Array ist, bietet  **SQLParamData** nicht extrahieren und an die Anwendung ein Element dieses Arrays zurück. Stattdessen wird zurückgegeben, dass die Anwendung über der skalare Wert angegeben haben. Dies bedeutet, dass der Rückgabewert von **SQLParamData** ist nicht ausreichend zum Angeben des Parameters für die die Anwendung muss zum Senden von Daten, die Anwendung muss auch die aktuelle Zeilennummer zu berücksichtigen.  
  
     Wenn nur einige der Elemente eines Arrays von Parametern Data-at-Execution-Parameter, leitet die Anwendung muss die Adresse eines Arrays in *ParameterValuePtr* , die Elemente für alle Parameter enthält. Dieses Array wird normalerweise für die Parameter interpretiert, die keine Data-at-Execution-Parameter sind. Für die Data-at-Execution-Parameter, der Wert, der **SQLParamData** bietet für die Anwendung, die normalerweise verwendet werden kann, die Daten zu identifizieren, die der Treiber bei dieser Gelegenheit anfordert, wird immer die Adresse des Arrays.
