---
title: Überschreiben der führenden und Sekunden Genauigkeit für Intervall Datentypen | Microsoft-Dokumentation
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
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: 3d65493f-dce7-4d29-9f59-c63a4e47918c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 13adfb16b772acc5fac30cf3d10c6199f16f479d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100624"
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Überschreiben der Standardwerte für die Genauigkeit des führenden Intervallfelds und die Sekundengenauigkeit für Intervalldatentypen
Wenn das SQL_DESC_TYPE-Feld eines ARDS auf einen DateTime-oder Interval-C-Typ festgelegt wird, indem entweder **SQLBindCol** oder **SQLSetDescField**aufgerufen wird, wird das SQL_DESC_PRECISION Feld (das die Genauigkeit der Intervall Sekunden enthält) auf die folgenden Standardwerte festgelegt:  
  
-   6 für Zeitstempel-und alle interval-Datentypen mit einer zweiten Komponente.  
  
-   0 für alle anderen Datentypen.  
  
 Für alle interval-Datentypen wird das SQL_DESC_DATETIME_INTERVAL_PRECISION Deskriptorfeld, das die Genauigkeit des führenden Felds für das Intervall enthält, auf den Standardwert 2 festgelegt.  
  
 Wenn das SQL_DESC_TYPE-Feld in einer APD auf einen DateTime-oder Interval-C-Typ festgelegt wird, indem entweder **SQLBindParameter** oder **SQLSetDescField**aufgerufen wird, werden die Felder SQL_DESC_PRECISION und SQL_DESC_DATETIME_INTERVAL_PRECISION in der APD auf den zuvor angegebenen Standardwert festgelegt. Dies gilt für Eingabeparameter, aber nicht für Eingabe-/Ausgabe-oder Ausgabeparameter.  
  
 Ein **SQLSetDescRec** -aufrufswert legt die angegebene Intervall Genauigkeit auf den Standardwert fest, legt jedoch die Genauigkeit der Sekunden Genauigkeit (im Feld "SQL_DESC_PRECISION") auf den Wert des *Genauigkeits* Arguments fest.  
  
 Wenn eine der zuvor angegebenen Standardwerte für eine Anwendung nicht akzeptabel ist, sollte die Anwendung die SQL_DESC_PRECISION oder SQL_DESC_DATETIME_INTERVAL_PRECISION Feld durch Aufrufen von **SQLSetDescField**festlegen.  
  
 Wenn die Anwendung **SQLGetData** aufruft, um Daten in einen DateTime-oder Interval-C-Typ zurückzugeben, werden die Genauigkeit des Standard Intervalls mit führender Genauigkeit und Intervall Sekunden verwendet. Wenn ein Standardwert nicht zulässig ist, muss die Anwendung **SQLSetDescField** aufrufen, um entweder das Deskriptorfeld festzulegen, oder **SQLSetDescRec** , um SQL_DESC_PRECISION festzulegen. Der **SQLGetData** -Befehl sollte über einen *TargetType* SQL_ARD_TYPE verfügen, um die Werte in den Deskriptorfeldern zu verwenden.  
  
 Wenn **SQLPutData** aufgerufen wird, werden die Genauigkeit der Genauigkeit und der Intervall Genauigkeit von Intervallen aus den Feldern des deskriptordaten Satzes gelesen, die den Data-at-Execution-Parametern oder-Spalten entsprechen, bei denen es sich um APD-Felder für **Aufrufe von** **SQLExecute** oder **SQLExecDirect** **handelt.**
