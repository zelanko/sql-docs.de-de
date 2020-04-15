---
title: Mehrere Ergebnisse | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d90414b631a7e81a7868ab7974b64ea84a0ea452
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302411"
---
# <a name="multiple-results"></a>Mehrere Ergebnisse
Ein *Ergebnis* ist etwas, das von der Datenquelle zurückgegeben wird, nachdem eine Anweisung ausgeführt wurde. ODBC hat zwei Arten von Ergebnissen: Resultsets und Zeilenanzahlen. *Zeilenanzahlen* sind die Anzahl der Zeilen, die von einer Aktualisierungs-, Lösch- oder Insert-Anweisung betroffen sind. Batches, die in [Batches of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md)beschrieben werden, können mehrere Ergebnisse generieren.  
  
 In der folgenden Tabelle sind die **SQLGetInfo-Optionen** aufgeführt, mit denen eine Anwendung bestimmt, ob eine Datenquelle mehrere Ergebnisse für jeden einzelnen Batchtyp zurückgibt. Insbesondere kann eine Datenquelle eine einzelne Zeilenanzahl für den gesamten Batch von Anweisungen oder einzelne Zeilenanzahlen für jede Anweisung im Batch zurückgeben. Im Fall einer result set-generating-Anweisung, die mit einem Array von Parametern ausgeführt wird, kann die Datenquelle ein einzelnes Resultset für alle Parametersätze oder einzelnen Resultsets für jeden Parametersatz zurückgeben.  
  
|Batch-Typ|Reihenzählungen|Resultsets|  
|----------------|----------------|-----------------|  
|Expliziter Stapel|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|Verfahren|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|Arrays von Parametern|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] Zeilenzählgenerierende Anweisungen in einem Batch können unterstützt werden, die Rückgabe der Zeilenanzahl wird jedoch nicht unterstützt. Die option SQL_BATCH_SUPPORT in **SQLGetInfo** gibt an, ob Zeilenzähl-Generierungsanweisungen in Batches zulässig sind. Die Option SQL_BATCH_ROW_COUNTS gibt an, ob diese Zeilenanzahlen an die Anwendung zurückgegeben werden.  
  
 [b] Explizite Batches und Prozeduren geben immer mehrere Resultsets zurück, wenn sie mehrere Resultset-Generierende Anweisungen enthalten.  
  
> [!NOTE]  
>  Die in ODBC 1.0 eingeführte SQL_MULT_RESULT_SETS-Option enthält nur allgemeine Informationen darüber, ob mehrere Resultsets zurückgegeben werden können. Insbesondere wird auf "Y" gesetzt, wenn die SQL_BS_SELECT_EXPLICIT oder SQL_BS_SELECT_PROC Bits für SQL_BATCH_SUPPORT zurückgegeben werden oder wenn SQL_PAS_BATCH für SQL_PARAM_ARRAYS_SELECT zurückgegeben wird.  
  
 Um mehrere Ergebnisse zu verarbeiten, ruft eine Anwendung **SQLMoreResults**auf. Diese Funktion verwirft das aktuelle Ergebnis und stellt das nächste Ergebnis zur Verfügung. Es gibt SQL_NO_DATA zurück, wenn keine weiteren Ergebnisse verfügbar sind. Angenommen, die folgenden Anweisungen werden als Batch ausgeführt:  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 Nachdem diese Anweisungen ausgeführt wurden, ruft die Anwendung Zeilen aus dem Resultset ab, das von der **SELECT-Anweisung** erstellt wurde. Wenn das Abrufen von Zeilen abgeschlossen ist, ruft es **SQLMoreResults** auf, um die Anzahl der Teile zur Verfügung zu stellen, die neu bewertet wurden. Bei Bedarf verwirft **SQLMoreResults** nicht abgerufene Zeilen und schließt den Cursor. Die Anwendung ruft dann **SQLRowCount** auf, um zu bestimmen, wie viele Teile durch die **UPDATE-Anweisung** neu bewertet wurden.  
  
 Es ist treiberspezifisch, ob die gesamte Batchanweisung ausgeführt wird, bevor Ergebnisse verfügbar sind. In einigen Implementierungen ist dies der Fall; In anderen Ländern löst der Aufruf von **SQLMoreResults** die Ausführung der nächsten Anweisung im Batch aus.  
  
 Wenn eine der Anweisungen in einem Batch fehlschlägt, gibt **SQLMoreResults** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück. Wenn der Batch abgebrochen wurde, wenn die Anweisung fehlgeschlagen ist oder die fehlgeschlagene Anweisung die letzte Anweisung im Batch war, gibt **SQLMoreResults** SQL_ERROR zurück. Wenn der Batch nicht abgebrochen wurde, wenn die Anweisung fehlgeschlagen ist und die fehlgeschlagene Anweisung nicht die letzte Anweisung im Batch war, gibt **SQLMoreResults** SQL_SUCCESS_WITH_INFO zurück. SQL_SUCCESS_WITH_INFO gibt an, dass mindestens ein Resultset oder eine Anzahl generiert wurde und dass der Stapel nicht abgebrochen wurde.
