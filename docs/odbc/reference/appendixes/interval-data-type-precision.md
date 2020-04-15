---
title: Intervalldatentypgenauigkeit | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290740"
---
# <a name="interval-data-type-precision"></a>Genauigkeit des Datentyps „Intervall“
Die Genauigkeit für einen Intervalldatentyp umfasst Intervallführungsgenauigkeit, Intervallgenauigkeit und Sekundengenauigkeit.  
  
 Das führende Feld eines Intervalls ist eine signierte Zahl. Die maximale Anzahl von Ziffern für das führende Feld wird durch eine Menge bestimmt, die als *Intervallführungsgenauigkeit* bezeichnet wird, die Teil der Datentypdeklaration ist. Zum Beispiel hat die Deklaration: INTERVAL HOUR(5) TO MINUTE eine Intervall-Führende Genauigkeit von 5; Das Hour-Feld kann Werte von -99999 bis 99999 annehmen. Die Intervallführungsgenauigkeit ist im SQL_DESC_DATETIME_INTERVAL_PRECISION Feld des Deskriptordatensatzes enthalten.  
  
 Die Liste der Felder, aus denen ein Intervalldatentyp besteht, wird als *Intervallgenauigkeit*bezeichnet. Es handelt sich nicht um einen numerischen Wert, wie der Begriff "Präzision" andeutet. Die Intervallgenauigkeit des Typs INTERVAL DAY TO SECOND ist z. B. die Liste DAY, HOUR, MINUTE, SECOND. Es gibt kein Deskriptorfeld, das diesen Wert enthält. Die Intervallgenauigkeit kann immer durch den Intervalldatentyp bestimmt werden.  
  
 Jeder Intervalldatentyp mit einem SECOND-Feld hat eine *Sekundengenauigkeit*. Dies ist die Anzahl der Dezimalstellen, die im Bruchteil des Sekundenwertes zulässig sind. Dies unterscheidet sich von anderen Datentypen, bei denen die Genauigkeit die Anzahl der Ziffern vor dem Dezimaltrennzeichen angibt. Die Sekundengenauigkeit eines Intervalldatentyps ist die Anzahl der Ziffern nach dem Dezimaltrennzeichen. Wenn z. B. die Sekundengenauigkeit auf 6 festgelegt ist, wird die Zahl 123456 im Fraktionsfeld als .123456 interpretiert, und die Zahl 1230 wird als .001230 interpretiert. Bei anderen Datentypen wird dies als Skalierung bezeichnet. Die Genauigkeit der Intervallsekunden ist im SQL_DESC_PRECISION Feld des Deskriptors enthalten. Wenn die Genauigkeit der Komponente "Bruchsekunden" des SQL-Intervallwerts größer ist als die, die in der C-Intervallstruktur gehalten werden kann, wird der Treiber definiert, ob der Wert für Bruchsekunden im SQL-Intervall gerundet oder abgeschnitten wird, wenn er in die C-Intervallstruktur konvertiert wird.  
  
 Wenn das Feld SQL_DESC_CONCISE_TYPE auf einen Intervalldatentyp festgelegt ist, wird das Feld SQL_DESC_TYPE auf SQL_INTERVAL und der SQL_DESC_DATETIME_INTERVAL_CODE auf den Code für den Intervalldatentyp festgelegt. Das Feld SQL_DESC_DATETIME_INTERVAL_PRECISION wird automatisch auf die standardmäßige Intervallführungsgenauigkeit von 2 und das Feld SQL_DESC_PRECISION automatisch auf die Standardintervallsekundengenauigkeit von 6 festgelegt. Wenn einer dieser Werte nicht geeignet ist, sollte die Anwendung das Deskriptorfeld explizit über einen Aufruf von **SQLSetDescField**festlegen.
