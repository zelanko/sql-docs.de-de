---
title: Genauigkeit des Intervall Datentyps | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 746293c545c47917abd084ec3eb105051fc2fbcf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81290740"
---
# <a name="interval-data-type-precision"></a>Genauigkeit des Datentyps „Intervall“
Die Genauigkeit eines Interval-Datentyps umfasst Intervall führende Genauigkeit, Intervall Genauigkeit und Sekunden Genauigkeit.  
  
 Das führende Feld eines Intervalls ist eine numerische Zahl mit Vorzeichen. Die maximale Anzahl von Ziffern für das führende Feld wird durch eine Menge mit der Bezeichnung " *Intervall-Spitzen Genauigkeit* " bestimmt, die Teil der Datentyp Deklaration ist. Die Deklaration: Interval Hour (5) bis Minute hat z. b. eine Intervall führende Genauigkeit von 5. das Stunden Feld kann Werte von-99999 bis 99999 annehmen. Die angegebene Intervall Genauigkeit ist im SQL_DESC_DATETIME_INTERVAL_PRECISION-Feld des deskriptordaten Satzes enthalten.  
  
 Die Liste der Felder, aus denen ein Intervall Datentyp besteht, wird als *Intervall Genauigkeit*bezeichnet. Es handelt sich hierbei nicht um einen numerischen Wert, da der Begriff "Precision" möglicherweise impliziert. Beispielsweise ist die Intervall Genauigkeit des typintervalls Day to Second der listentag, Hour, Minute, Second. Es ist kein Deskriptorfeld vorhanden, das diesen Wert enthält. die Genauigkeit des Intervalls kann immer durch den Datentyp interval bestimmt werden.  
  
 Jeder Intervall Datentyp mit einem zweiten Feld hat eine *Genauigkeit von Sekunden*. Dies ist die Anzahl der Dezimalstellen, die im Bruchteil des Sekunden Werts zulässig sind. Dies unterscheidet sich von anderen Datentypen, wobei Genauigkeit die Anzahl der Ziffern vor dem Dezimaltrennzeichen angibt. Die Sekunden Genauigkeit eines Interval-Datentyps ist die Anzahl der Ziffern nach dem Dezimaltrennzeichen. Wenn beispielsweise die Sekunden Genauigkeit auf 6 festgelegt ist, wird die Zahl 123456 im Bruchfeld als. 123456 interpretiert, und die Zahl 1230 wird als. 001230 interpretiert. Bei anderen Datentypen wird dies als Skalierung bezeichnet. Die Genauigkeit der Intervall Sekunden ist im SQL_DESC_PRECISION-Feld des Deskriptors enthalten. Wenn die Genauigkeit der Komponente für Sekundenbruchteile des SQL-Intervall Werts größer ist als die in der c-Intervall Struktur enthaltene Genauigkeit, wird der Treiber definiert, ob der Wert für die Sekundenbruchteile im SQL-Intervall beim Konvertieren in die c-Intervall Struktur gerundet oder abgeschnitten wird.  
  
 Wenn das SQL_DESC_CONCISE_TYPE-Feld auf einen Interval-Datentyp festgelegt ist, wird das SQL_DESC_TYPE Feld auf SQL_INTERVAL festgelegt, und der SQL_DESC_DATETIME_INTERVAL_CODE wird auf den Code für den Interval-Datentyp festgelegt. Das SQL_DESC_DATETIME_INTERVAL_PRECISION Feld wird automatisch auf die standardmäßige Intervall führende Genauigkeit von 2 festgelegt, und das Feld "SQL_DESC_PRECISION" wird automatisch auf die Standardgenauigkeit von 6 Sekunden des Intervalls festgelegt. Wenn einer dieser Werte nicht angemessen ist, muss die Anwendung das Deskriptorfeld explizit durch einen **SQLSetDescField**-Befehl festlegen.
