---
title: Ausrichtung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- alignment issues [ODBC]
ms.assetid: 06a01e51-e7a5-495f-aa27-e304b0d005ff
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b8b5a107f5ed8cd1c6c45317e60cc515a2601316
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077270"
---
# <a name="alignment"></a>Ausrichtung
Die Ausrichtungsprobleme in einer ODBC-Anwendung unterscheiden sich in der Regel nicht als sie in jeder anderen Anwendung sind. Die meisten ODBC-Anwendungen verfügen, also nur wenige oder gar keine Probleme mit der Ausrichtung. Die Strafen für nicht Ausrichten von Adressen mit der Hardware und Betriebssystem variieren und als eine leichte Leistungseinbuße wie Haupt- oder als als ein schwerwiegender Laufzeitfehler sein. Aus diesem Grund sollten ODBC-Anwendungen und portable ODBC-Anwendungen insbesondere sein darauf achten, dass Daten richtig ausgerichtet.  
  
 Ein Beispiel für ODBC-Anwendungen Ausrichtungsprobleme, wenn auftreten ist, wenn sie einen großen Speicherblock zuordnen und verschiedene Teile der, dass der Speicher auf die Spalten in einem Resultset zu binden. Dies ist höchstwahrscheinlich auftreten, wenn eine generische Anwendung muss bestimmen die Form eines Resultsets, zur Laufzeit und zuordnen und Speicher entsprechend zu binden.  
  
 Nehmen wir beispielsweise an, die eine Anwendung ausgeführt wird ein **wählen** -Anweisung vom Benutzer eingegeben wurde, und ruft die Ergebnisse von dieser Anweisung. Da die Form dieses Resultsets nicht bekannt ist wenn das Programm geschrieben ist, muss die Anwendung bestimmen Sie den Typ der einzelnen Spalten aus, nachdem das Resultset erstellt wurde, und binden Speicher entsprechend. Die einfachste Möglichkeit hierzu ist, um einen großen Speicherblock zuordnen und verschiedene Adressen in diesen Block zu binden, für die einzelnen Spalten. Für den Zugriff auf die Daten in einer Spalte, wandelt die Anwendung den Arbeitsspeicher für diese Spalte gebunden.  
  
 Das folgende Diagramm zeigt ein Beispielergebnis aufgeführt, festlegen und wie ein Speicherblock, der mit der Standard-C-Datentyp für jeden SQL-Datentyp gebunden werden kann. Jedes "X" stellt ein einzelnes Byte Arbeitsspeicher dar. (Dieses Beispiel zeigt nur die Datenpuffern, die den Spalten gebunden sind. Dies geschieht aus Gründen der Einfachheit. Im tatsächlichen Code müssen die Längenindikator/Puffern auch ausgerichtet, werden führen.)  
  
 ![Bindung von Standard-C-Datentyp in SQL-Datentyp](../../../odbc/reference/develop-app/media/pr24.gif "pr24")  
  
 Vorausgesetzt, die gebundenen Adressen befinden sich in der *Adresse* Array, das die Anwendung verwendet die folgenden Ausdrücke auf den Arbeitsspeicher für die einzelnen Spalten gebunden:  
  
```  
(SQLCHAR *)       Address[0]  
(SQLSMALLINT *)   Address[1]  
(SQLINTEGER *)    Address[2]  
```  
  
 Beachten Sie, dass die Adressen, mit dem zweiten gebunden und dritten Spalten ungerade Byte starten und, dass die Adresse der dritten Spalte gebunden ist nicht von vier, wird die Größe einer SDWORD geteilt werden kann. Auf einigen Computern ist wird dies kein Problem sein. in anderen bewirkt es, eine leichte Leistungseinbuße; in anderen verursacht dies ein schwerwiegender Laufzeitfehler. Eine bessere Lösung wäre jede gebundene Adresse auf die natürlichen Ausrichtungsgrenzen ausrichten. Vorausgesetzt, dass dies 1 für einen UCHAR, 2 für eine "sword" und 4 für eine SDWORD, ist würde dies erhalten das Ergebnis sehen Sie in der folgenden Abbildung, in dem ein "X" stellt ein Byte Arbeitsspeicher, der verwendet wird und "O" ein Byte Arbeitsspeicher, der verwendet wird.  
  
 ![Bindung nach natürlichen Ausrichtungsgrenzen](../../../odbc/reference/develop-app/media/pr25.gif "pr25")  
  
 Obwohl diese Lösung nicht den gesamten Arbeitsspeicher von der Anwendung verwendet, ist es nicht Ausrichtungsprobleme auftreten. Leider dauert es eine beträchtliche Menge Code zur Implementierung dieser Lösung, wie jede Spalte einzeln nach Typ ausgerichtet sein muss. Eine einfachere Lösung ist es, alle Spalten in der Größe der größten Ausrichtungsgrenzen abzustimmen 4 wird im Beispiel in der folgenden Abbildung dargestellt.  
  
 ![Bindung nach größten Ausrichtungsgrenzen](../../../odbc/reference/develop-app/media/pr26.gif "pr26")  
  
 Obwohl diese Lösung größere Löcher verlässt, ist der Code für die Implementierung relativ einfach und schnell. In den meisten Fällen offsets dies den Nachteil, kostenpflichtige in nicht verwendeten Arbeitsspeicher. Ein Beispiel, diese Methode verwendet, finden Sie unter [mithilfe von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).
