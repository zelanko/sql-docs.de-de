---
description: Verwenden von Parameterarrays
title: Verwenden von Parameter Arrays | Microsoft-Dokumentation
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
ms.openlocfilehash: 1a592131165e7dc2370ab1d22a3d9eba5f9609dd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424412"
---
# <a name="using-arrays-of-parameters"></a>Verwenden von Parameterarrays
Um Parameter Arrays zu verwenden, ruft die Anwendung **SQLSetStmtAttr** mit einem *Attribut* Argument von SQL_ATTR_PARAMSET_SIZE auf, um die Anzahl von Parametern anzugeben. Er ruft **SQLSetStmtAttr** mit dem *Attribut* Argument SQL_ATTR_PARAMS_PROCESSED_PTR auf, um die Adresse einer Variablen anzugeben, in der der Treiber die Anzahl der verarbeiteten Parametersätze zurückgeben kann, einschließlich der Fehler Sätze. Er ruft **SQLSetStmtAttr** mit dem *Attribut* Argument SQL_ATTR_PARAM_STATUS_PTR auf, um auf ein Array zu verweisen, in dem Status Informationen für jede Zeile von Parameterwerten zurückgegeben werden sollen. Der Treiber speichert diese Adressen in der Struktur, die Sie für die-Anweisung verwaltet.  
  
> [!NOTE]  
>  In ODBC 2. *x*, **SQLParamOptions** wurde aufgerufen, um mehrere Werte für einen Parameter anzugeben. In ODBC 3. *x*, der Aufruf von **SQLParamOptions** wurde durch Aufrufe von **SQLSetStmtAttr** ersetzt, um die Attribute "SQL_ATTR_PARAMSET_SIZE" und "SQL_ATTR_PARAMS_PROCESSED_ARRAY" festzulegen.  
  
 Vor dem Ausführen der-Anweisung legt die Anwendung den Wert jedes Elements jedes gebundenen Arrays fest. Wenn die-Anweisung ausgeführt wird, verwendet der Treiber die gespeicherten Informationen, um die Parameterwerte abzurufen und an die Datenquelle zu senden. Wenn möglich, sollte der Treiber diese Werte als Arrays senden. Obwohl die Verwendung von Parameter Arrays am besten implementiert ist, indem Sie die SQL-Anweisung mit allen Parametern im Array mit einem einzigen Datenquellen aufzurufen, ist diese Funktion derzeit in DBMSs nicht allgemein verfügbar. Treiber können Sie jedoch simulieren, indem Sie eine SQL-Anweisung mehrmals ausführen, wobei jeder einzelne Satz von Parametern hat.  
  
 Bevor eine Anwendung Arrays von Parametern verwendet, muss Sie sicherstellen, dass Sie von den von der Anwendung verwendeten Treibern unterstützt werden. Hierfür gibt es zwei Möglichkeiten:  
  
-   Verwenden Sie nur Treiber, die bekanntermaßen Arrays von Parametern unterstützen. Die Anwendung kann die Namen dieser Treiber hart codieren, oder der Benutzer kann angewiesen werden, nur diese Treiber zu verwenden. Benutzerdefinierte Anwendungen und vertikale Anwendungen verwenden häufig einen begrenzten Satz von Treibern.  
  
-   Überprüfen Sie, ob zur Laufzeit Parameter Arrays unterstützt werden. Ein Treiber unterstützt Parameter Arrays, wenn es möglich ist, das SQL_ATTR_PARAMSET_SIZE-Anweisungs Attribut auf einen Wert größer als 1 festzulegen. Generische Anwendungen und vertikale Anwendungen überprüfen häufig die Unterstützung von Parameter Arrays zur Laufzeit.  
  
 Die Verfügbarkeit von Zeilen Zählungen und Resultsets in parametrisierter Ausführung kann durch Aufrufen von **SQLGetInfo** mit den Optionen SQL_PARAM_ARRAY_ROW_COUNTS und SQL_PARAM_ARRAY_SELECTS ermittelt werden. Bei **Insert**-, **Update**-und **Delete** -Anweisungen gibt die Option SQL_PARAM_ARRAY_ROW_COUNTS an, ob einzelne Zeilen Anzahl (eine für jeden Parametersatz) verfügbar ist (SQL_PARC_BATCH) oder ob Zeilen Anzahlen in einen (SQL_PARC_NO_BATCH) Rollup eingefügt werden. Bei **Select** -Anweisungen gibt die Option SQL_PARAM_ARRAY_SELECTS an, ob ein Resultset für jeden Parametersatz (SQL_PAS_BATCH) verfügbar ist oder ob nur ein Resultset verfügbar ist (SQL_PAS_NO_BATCH). Wenn der Treiber nicht zulässt, dass resultsetgenerierende Anweisungen mit einem Array von Parametern ausgeführt werden, gibt SQL_PARAM_ARRAY_SELECTS SQL_PAS_NO_SELECT zurück. Dabei handelt es sich um Datenquellen spezifische Arrays von Parametern, die für andere Typen von Anweisungen verwendet werden können, insbesondere, weil die Verwendung von Parametern in diesen Anweisungen Datenquellen spezifisch ist und nicht der ODBC-SQL-Grammatik folgt.  
  
 Das Array, auf das das SQL_ATTR_PARAM_OPERATION_PTR Statement-Attribut verweist, kann verwendet werden, um Zeilen von Parametern zu ignorieren. Wenn ein Element des Arrays auf SQL_PARAM_IGNORE festgelegt ist, wird der Parametersatz, der diesem Element entspricht, aus dem **SQLExecute** -oder **SQLExecDirect** -Befehl ausgeschlossen. Das Array, auf das das SQL_ATTR_PARAM_OPERATION_PTR-Attribut verweist, wird von der Anwendung zugeordnet und ausgefüllt und vom Treiber gelesen. Wenn abgerufene Zeilen als Eingabeparameter verwendet werden, können die Werte des Zeilen Status Arrays im Parameter Vorgangs Array verwendet werden.  
  
## <a name="error-processing"></a>Fehlerverarbeitung  
 Wenn beim Ausführen der Anweisung ein Fehler auftritt, gibt die Ausführungs Funktion einen Fehler zurück und legt die Variable für die Zeilennummer auf die Nummer der Zeile fest, die den Fehler enthält. Dabei handelt es sich um Datenquellen spezifische Daten, unabhängig davon, ob alle Zeilen außer dem Fehler Satz ausgeführt werden oder ob alle Zeilen vor (aber nicht nach) des Fehler Satzes ausgeführt werden. Da er Sätze von Parametern verarbeitet, legt der Treiber den Puffer, der durch das SQL_ATTR_PARAMS_PROCESSED_PTR Statement-Attribut angegeben wird, auf die Nummer der aktuell verarbeiteten Zeile fest. Wenn alle Sätze außer dem Fehler Satz ausgeführt werden, legt der Treiber diesen Puffer auf SQL_ATTR_PARAMSET_SIZE fest, nachdem alle Zeilen verarbeitet wurden.  
  
 Wenn das SQL_ATTR_PARAM_STATUS_PTR-Anweisungs Attribut festgelegt wurde, gibt **SQLExecute** oder **SQLExecDirect** das *Parameter Status Array zurück,* das den Status der einzelnen Parameter enthält. Das Array für den Parameter Status wird von der Anwendung zugeordnet und vom Treiber ausgefüllt. Seine Elemente geben an, ob die SQL-Anweisung für die Zeile mit Parametern erfolgreich ausgeführt wurde oder ob beim Verarbeiten der Parametergruppe ein Fehler aufgetreten ist. Wenn ein Fehler aufgetreten ist, legt der Treiber den entsprechenden Wert im Array Parameter Status auf SQL_PARAM_ERROR fest und gibt SQL_SUCCESS_WITH_INFO zurück. Die Anwendung kann das Status Array überprüfen, um zu bestimmen, welche Zeilen verarbeitet wurden. Mithilfe der Zeilennummer kann die Anwendung den Fehler häufig beheben und die Verarbeitung fortsetzen.  
  
 Wie das Array für den Parameter Status verwendet wird, hängt von den SQL_PARAM_ARRAY_ROW_COUNTS-und SQL_PARAM_ARRAY_SELECTS Optionen ab, die durch einen **SQLGetInfo-Befehl**zurückgegeben werden. Für **Insert**-, **Update**-und **Delete** -Anweisungen wird das Array für den Parameter Status mit Statusinformationen aufgefüllt, wenn SQL_PARC_BATCH für SQL_PARAM_ARRAY_ROW_COUNTS zurückgegeben wird, jedoch nicht, wenn SQL_PARC_NO_BATCH zurückgegeben wird. Bei **Select** -Anweisungen wird das Array für den Parameter Status ausgefüllt, wenn SQL_PAS_BATCH für SQL_PARAM_ARRAY_SELECT zurückgegeben wird, jedoch nicht, wenn SQL_PAS_NO_BATCH oder SQL_PAS_NO_SELECT zurückgegeben wird.  
  
## <a name="data-at-execution-parameters"></a>Data-at-Execution-Parameter  
 Wenn einer der Werte im Längen-/indikatorenarray SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC (*length*)-Makros ist, werden die Daten für diese Werte auf die übliche Weise mit **SQLPutData** gesendet. Die folgenden Aspekte dieses Prozesses haben einen besonderen Kommentar, da Sie nicht sofort ersichtlich sind:  
  
-   Wenn der Treiber SQL_NEED_DATA zurückgibt, muss die Adresse der Variablen für die Zeilennummer auf die Zeile festgelegt werden, für die Daten benötigt werden. Wie im einwertigen Fall kann die Anwendung keine Annahmen über die Reihenfolge treffen, in der der Treiber Parameterwerte innerhalb eines einzelnen Parameter Satzes anfordert. Wenn bei der Ausführung eines Data-at-Execution-Parameters ein Fehler auftritt, der Puffer, der durch das SQL_ATTR_PARAMS_PROCESSED_PTR Statement-Attribut angegeben wird, wird auf die Nummer der Zeile festgelegt, in der der Fehler aufgetreten ist, der Status der Zeile im Zeilen Status Array, das durch das SQL_ATTR_PARAM_STATUS_PTR Statement-Attribut angegeben ist, wird auf SQL_PARAM_ERROR festgelegt, und der-Befehl **SQLExecute**, **SQLExecDirect**, **SQLParamData**oder **SQLPutData** gibt SQL_ERROR Der Inhalt dieses Puffers ist nicht definiert, wenn **SQLExecute**, **SQLExecDirect**oder **SQLParamData** SQL_STILL_EXECUTING zurückgeben.  
  
-   Da der Treiber den Wert im *ParameterValuePtr* -Argument von **SQLBindParameter** bei Data-at-Execution-Parametern nicht interpretiert, extrahiert und gibt **SQLParamData** ein Element dieses Arrays nicht an die Anwendung zurück, wenn die Anwendung einen Zeiger auf ein Array bereitstellt. Stattdessen wird der skalare Wert zurückgegeben, der von der Anwendung bereitgestellt wurde. Dies bedeutet, dass der von **SQLParamData** zurückgegebene Wert nicht ausreicht, um den Parameter anzugeben, den die Anwendung zum Senden von Daten benötigt. die Anwendung muss auch die aktuelle Zeilennummer in Erwägung gezogen werden.  
  
     Wenn nur einige Elemente eines Arrays von Parametern Data-at-Execution-Parameter sind, muss die Anwendung die Adresse eines Arrays in *ParameterValuePtr* übergeben, das Elemente für alle Parameter enthält. Dieses Array wird normalerweise für die Parameter interpretiert, bei denen es sich nicht um Data-at-Execution-Parameter handelt. Für die Data-at-Execution-Parameter ist der Wert, den **SQLParamData** für die Anwendung bereitstellt, der normalerweise zur Identifizierung der Daten verwendet werden kann, die der Treiber zu diesem Zeitpunkt anfordert, immer die Adresse des Arrays.
