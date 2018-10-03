---
title: Genauigkeit für Datentyp Interval | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- precision [ODBC], interval data types
- seconds precision [ODBC]
- interval data type [ODBC], precision
- precision [ODBC]
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: eb73bd77-2e7e-4498-a266-4d7c990a0d56
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98be3b4a7e4db30f394a2834364ecab9a20ef182
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706428"
---
# <a name="interval-data-type-precision"></a>Genauigkeit des Datentyps „Intervall“
Genauigkeit für eine Interval-Datentypen enthält, mit einfacher Genauigkeit, Intervall Präzision und Genauigkeit für anführenden Intervallwert.  
  
 Ein Intervall der führende Feld handelt es sich um ein Vorzeichen versehene Zahl. Die maximale Anzahl von Ziffern für das Feld "führende" richtet sich nach einer Menge namens *Genauigkeit für anführenden Intervallwert* die ist Teil der Deklaration. Z. B. die Deklaration: Intervall HOUR(5) auf MINUTE hat eine Genauigkeit von 5; für anführenden Intervallwert dem Stundenfeld dauert Werte aus –99999 und 99999 angegeben. Die Genauigkeit für anführenden Intervallwert, die im Feld SQL_DESC_DATETIME_INTERVAL_PRECISION anwendungsparameterdeskriptor-Datensatz enthalten ist.  
  
 Die Liste der Felder, die Daten Intervalltyp aus besteht heißt *Intervall-Genauigkeit*. Es ist kein numerischer Wert, wie der Begriff "Precision" impliziert. Beispielsweise ist die Intervall-Genauigkeit des Datentyps INTERVAL DAY TO ZWEITENS die Liste Tag, Stunde, MINUTE, Sekunde. Es gibt keine Deskriptorfeld, die diesen Wert enthält; die Genauigkeit Intervall kann immer durch den Datentyp Interval ermittelt werden.  
  
 Alle Interval-Datentypen, die ein zweites Feld verfügt über eine *Genauigkeit in Sekunden*. Dies ist die Anzahl der Dezimalstellen, die in den Bruchteil der Sekundenwert zulässig. Dies unterscheidet sich für andere Datentypen, wobei der Genauigkeit die Anzahl der Ziffern vor dem Dezimaltrennzeichen angibt. Die Genauigkeit des ein Intervall-Datentyp ist die Anzahl der Ziffern nach dem Dezimaltrennzeichen an. Z. B. wenn die Genauigkeit auf 6 festgelegt ist, würde die Zahl 123456 in das bruchteilfeld interpretiert werden als.123456 und die Anzahl 1230 als.001230 interpretiert werden würde. Für andere Datentypen wird dies als Skalierung bezeichnet. Intervall-Sekunden-Genauigkeit ist in der SQL_DESC_PRECISION-Feld des Deskriptors enthalten. Wenn die Genauigkeit der Sekundenbruchteil-Komponente von der SQL-Zeitintervall-Wert größer ist, was die C-Intervall-Struktur gespeichert werden können, ist es treiberdefinierten, ob der Wert für die Sekundenbruchteile in das SQL-Zeitintervall gerundet oder abgeschnitten werden, wenn für den C-konvertiert Intervall-Struktur.  
  
 Das Feld "SQL_DESC_CONCISE_TYPE" auf ein Intervall-Datentyp festgelegt ist, wird das SQL_DESC_TYPE-Feld als SQL_INTERVAL festgelegt und die SQL_DESC_DATETIME_INTERVAL_CODE festgelegt ist, auf den Code für die Interval-Datentypen. Das SQL_DESC_DATETIME_INTERVAL_PRECISION-Feld wird automatisch auf die führenden Intervalls standardgenauigkeit von 2 festgelegt, und das SQL_DESC_PRECISION-Feld wird automatisch auf die standardmäßige Intervall Sekunden Genauigkeit von 6 festgelegt. Wenn beide Werte ist nicht geeignet, die Anwendung sollte explizit festlegen das Deskriptorfeld durch einen Aufruf von **SQLSetDescField**.
