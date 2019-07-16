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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086366"
---
# <a name="multiple-results"></a>Mehrere Ergebnisse
Ein *Ergebnis* etwas von der Datenquelle nach dem Aufruf zurückgegeben eine Anweisung ausgeführt wird. ODBC verfügt über zwei Arten von Ergebnissen: Resultsets und Zeilen-. *Zeilen-* sind die Anzahl der von einem Update betroffenen Zeilen gelöscht, oder insert-Anweisung. Batches, die in beschriebenen [Batches von SQL-Anweisungen](../../../odbc/reference/develop-app/batches-of-sql-statements.md), mehrere Ergebnisse generieren können.  
  
 Die folgende Tabelle enthält die **SQLGetInfo** Optionen, die eine Anwendung verwendet, um festzustellen, ob eine Datenquelle mehrere Ergebnisse für jeden Batch zurückgibt. Insbesondere eine Datenquelle kann eine einzelne Zeilenanzahl für den gesamten Batch von Anweisungen zurückgeben, oder einzelne Zeilenanzahl für jede Anweisung im Batch. Die Datenquelle kann ein einzelnes Resultset für alle Parametersätze zurückgeben oder Resultsets für jeden Satz von Parametern, im Fall einer Ergebnis generiert Set-Anweisung mit einem Array von Parametern ausgeführt.  
  
|Batchtyp|Zeilenanzahl|Resultsets|  
|----------------|----------------|-----------------|  
|Explizite batch|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|Prozedur|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|Arrays von Parametern|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] Zeile, die Anweisungen in einem Batch Count generiert möglicherweise unterstützt werden, aber die Rückgabe von der Zeilenanzahl wird nicht unterstützt. Die Option SQL_BATCH_SUPPORT in **SQLGetInfo** gibt an, ob Zeile Count – Generieren von Anweisungen in Batches zugelassen sind; die SQL_BATCH_ROW_COUNTS-Option gibt an, ob diese Zeilenanzahl für die Anwendung zurückgegeben werden.  
  
 [b] explizite Batches und Prozeduren immer mehrere Resultsets zurückgeben, wenn sie mehrere Ergebnis generiert Set-Anweisungen enthalten.  
  
> [!NOTE]  
>  Die SQL_MULT_RESULT_SETS-Option in ODBC-1.0 eingeführten bietet nur allgemeine Informationen, ob mehrere Resultsets zurückgegeben werden können. Insbesondere ist es auf "Y" festgelegt, wenn die Bits SQL_BS_SELECT_EXPLICIT oder SQL_BS_SELECT_PROC für SQL_BATCH_SUPPORT zurückgegeben werden oder SQL_PAS_BATCH für SQL_PARAM_ARRAYS_SELECT zurückgegeben wird.  
  
 Um mehrere Ergebnisse zu verarbeiten, eine Anwendung ruft **SQLMoreResults**. Diese Funktion verwirft das aktuelle Ergebnis und das nächste Ergebnis zur Verfügung. Es gibt SQL_NO_DATA zurück, wenn keine weiteren Ergebnisse verfügbar sind. Nehmen wir beispielsweise an, dass die folgenden Anweisungen als Batch ausgeführt werden:  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 Nachdem Sie diese Anweisungen ausgeführt werden, die Anwendung ruft Zeilen aus dem Resultset, erstellt die **wählen** Anweisung. Wenn dies das Abrufen von Zeilen abgeschlossen ist, ruft er **SQLMoreResults** um die Anzahl der Teile verfügbar zu machen, die repriced wurden. Bei Bedarf **SQLMoreResults** verwirft Resultsetzeile Zeilen und schließt den Cursor. Die Anwendung ruft dann **SQLRowCount** um zu bestimmen, wie viele Teile von repriced wurden die **UPDATE** Anweisung.  
  
 Es ist treiberspezifisch gibt an, ob die gesamte Batch-Anweisung ausgeführt wird, bevor alle Ergebnisse verfügbar sind. In einigen Implementierungen ist dies der Fall. in anderen Fällen Aufrufen **SQLMoreResults** die Ausführung der nächsten Anweisung im Batch.  
  
 Wenn eine der Anweisungen in einem Batch fehlschlägt, **SQLMoreResults** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück. Wenn der Batch abgebrochen wird, wenn Fehler bei der Anweisung oder die fehlerhafte Anweisung die letzte Anweisung im Batch wurde **SQLMoreResults** SQL_ERROR zurück. Wenn der Batch nicht abgebrochen wird, wenn Fehler bei der Anweisung und die fehlerhafte Anweisung nicht die letzte Anweisung im Batch war **SQLMoreResults** SQL_SUCCESS_WITH_INFO zurück. SQL_SUCCESS_WITH_INFO gibt an, dass mindestens ein Resultset oder die Anzahl der generiert wurde und der Batch nicht abgebrochen wurde.
