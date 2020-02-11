---
title: Mehrere Ergebnisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLMoreResults function [ODBC], multiple results
- row counts [ODBC]
- multiple results [ODBC]
- result sets [ODBC], multiple results
- SQLGetInfo function [ODBC], multiple results
ms.assetid: a3c32e4b-8fe7-4a33-ae39-ae664001f315
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f8679bea49b63ffd5dc7164942b42ac9eed7e9ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086366"
---
# <a name="multiple-results"></a>Mehrere Ergebnisse
Ein *Ergebnis* ist ein Wert, der von der Datenquelle zurückgegeben wird, nachdem eine-Anweisung ausgeführt wurde. ODBC hat zwei Arten von Ergebnissen: Resultsets und Zeilen Anzahl. *Zeilen* Anzahl ist die Anzahl der Zeilen, auf die sich eine Update-, DELETE-oder INSERT-Anweisung auswirkt. Batches, die in [Batches von SQL-Anweisungen](../../../odbc/reference/develop-app/batches-of-sql-statements.md)beschrieben werden, können mehrere Ergebnisse generieren.  
  
 In der folgenden Tabelle sind die **SQLGetInfo** -Optionen aufgeführt, die eine Anwendung verwendet, um zu bestimmen, ob eine Datenquelle für jeden Typ von Batch mehrere Ergebnisse zurückgibt. Insbesondere kann eine Datenquelle eine einzelne Zeilen Anzahl für den gesamten Batch von Anweisungen oder einzelne Zeilenzähler für jede Anweisung im Batch zurückgeben. Wenn eine resultsetgenerierende Anweisung mit einem Array von Parametern ausgeführt wird, kann die Datenquelle ein einzelnes Resultset für alle Sätze von Parametern oder einzelne Resultsets für jeden Parametersatz zurückgeben.  
  
|Batchtyp|Zeilen Anzahl|Resultsets|  
|----------------|----------------|-----------------|  
|Expliziter Batch|SQL_BATCH_ROW_COUNT [a]|--[b]|  
|Verfahren|SQL_BATCH_ROW_COUNT [a]|--[b]|  
|Arrays von Parametern|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] Zeilen Anzahl: generierende Anweisungen in einem Batch werden möglicherweise unterstützt, aber die Rückgabe der Zeilen Anzahl wird nicht unterstützt. Die Option SQL_BATCH_SUPPORT in **SQLGetInfo** gibt an, ob Zeilen Anzahl generierende Anweisungen in Batches zulässig sind. die Option SQL_BATCH_ROW_COUNTS gibt an, ob diese Zeilen Anzahlen an die Anwendung zurückgegeben werden.  
  
 [b] explizite Batches und Prozeduren geben immer mehrere Resultsets zurück, wenn Sie mehrere Resultset-Generierungs Anweisungen enthalten.  
  
> [!NOTE]  
>  Die in ODBC 1,0 eingeführte SQL_MULT_RESULT_SETS-Option bietet nur allgemeine Informationen darüber, ob mehrere Resultsets zurückgegeben werden können. Insbesondere wird er auf "Y" festgelegt, wenn die SQL_BS_SELECT_EXPLICIT oder SQL_BS_SELECT_PROC Bits für SQL_BATCH_SUPPORT zurückgegeben werden oder wenn SQL_PAS_BATCH für SQL_PARAM_ARRAYS_SELECT zurückgegeben wird.  
  
 Zum Verarbeiten mehrerer Ergebnisse Ruft eine Anwendung **SQLMoreResults**auf. Diese Funktion verwirft das aktuelle Ergebnis und macht das nächste Ergebnis verfügbar. Wenn keine weiteren Ergebnisse verfügbar sind, wird SQL_NO_DATA zurückgegeben. Nehmen Sie beispielsweise an, dass die folgenden Anweisungen als Batch ausgeführt werden:  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 Nachdem diese Anweisungen ausgeführt wurden, ruft die Anwendung Zeilen aus dem Resultset ab, das von der **Select** -Anweisung erstellt wurde. Wenn das Abrufen von Zeilen abgeschlossen ist, ruft es **SQLMoreResults** auf, um die Anzahl der zu verteilenden Teile verfügbar zu machen. Bei Bedarf verwirft **SQLMoreResults** nicht abgerufene Zeilen und schließt den Cursor. Die Anwendung ruft dann **SQLRowCount** auf, um zu bestimmen, wie viele Teile von der **Update** -Anweisung neu berechnet wurden.  
  
 Es ist Treiber spezifisch, unabhängig davon, ob die gesamte Batch-Anweisung ausgeführt wird, bevor Ergebnisse verfügbar sind. In einigen Implementierungen ist dies der Fall. in anderen Fällen löst der Aufruf von **SQLMoreResults** die Ausführung der nächsten Anweisung im Batch aus.  
  
 Wenn eine der Anweisungen in einem Batch fehlschlägt, gibt **SQLMoreResults** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück. Wenn der Batch abgebrochen wurde, als die Anweisung fehlgeschlagen ist oder wenn es sich bei der fehlerhaften Anweisung um die letzte Anweisung im Batch handelt, gibt **SQLMoreResults** SQL_ERROR zurück. Wenn der Batch nicht abgebrochen wurde, als bei der Anweisung ein Fehler aufgetreten ist und die fehlgeschlagene Anweisung nicht die letzte Anweisung im Batch war, gibt **SQLMoreResults** SQL_SUCCESS_WITH_INFO zurück. SQL_SUCCESS_WITH_INFO gibt an, dass mindestens ein Resultset oder eine Anzahl generiert wurde und dass der Batch nicht abgebrochen wurde.
