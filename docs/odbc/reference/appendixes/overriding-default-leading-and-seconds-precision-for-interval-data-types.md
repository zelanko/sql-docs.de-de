---
title: Überschreitung der Leading- und Sekundengenauigkeit für Intervalldatentypen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1e60d5d8fc696ad8e2bd4cfb0c082ff214e066d0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303601"
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Überschreiben der Standardwerte für die Genauigkeit des führenden Intervallfelds und die Sekundengenauigkeit für Intervalldatentypen
Wenn das SQL_DESC_TYPE Feld einer ARD auf einen Datums- oder Intervall-C-Typ festgelegt ist, wird durch Aufrufen von **SQLBindCol** oder **SQLSetDescField**das SQL_DESC_PRECISION Feld (das die Intervallsekundengenauigkeit enthält) auf die folgenden Standardwerte festgelegt:  
  
-   6 für Zeitstempel und alle Intervalldatentypen mit einer zweiten Komponente.  
  
-   0 für alle anderen Datentypen.  
  
 Für alle Intervalldatentypen wird das Feld SQL_DESC_DATETIME_INTERVAL_PRECISION Deskriptor, das die Intervall-führende Feldgenauigkeit enthält, auf den Standardwert 2 festgelegt.  
  
 Wenn das SQL_DESC_TYPE Feld in einer APD auf einen Datumszeit- oder **SQLSetDescField**Intervall-C-Typ festgelegt ist, werden die felder SQL_DESC_PRECISION und SQL_DESC_DATETIME_INTERVAL_PRECISION in der APD auf den zuvor angegebenen Standardwert festgelegt. **SQLBindParameter** Dies gilt für Eingabeparameter, nicht jedoch für Eingabe-/Ausgabe- oder Ausgabeparameter.  
  
 Ein Aufruf von **SQLSetDescRec** legt die Intervallgenauigkeit auf den Standardwert fest, legt jedoch die Intervallsekundengenauigkeit (im Feld SQL_DESC_PRECISION) auf den Wert des *Precision-Arguments* fest.  
  
 Wenn eine der zuvor angegebenen Standardeinstellungen für eine Anwendung nicht akzeptabel ist, sollte die Anwendung das Feld SQL_DESC_PRECISION oder SQL_DESC_DATETIME_INTERVAL_PRECISION festlegen, indem sie **SQLSetDescField**aufruft.  
  
 Wenn die Anwendung **SQLGetData** aufruft, um Daten in einen Datumszeit- oder Intervall-C-Typ zurückzugeben, werden die Standardmäßigsintervallführungsgenauigkeit und die Intervallsekundengenauigkeit verwendet. Wenn eine der Standardeinstellungen nicht akzeptabel ist, muss die Anwendung **SQLSetDescField** aufrufen, um entweder das Deskriptorfeld oder **SQLSetDescRec** auf SQL_DESC_PRECISION festzulegen. Der Aufruf von **SQLGetData** sollte über einen *TargetType* von SQL_ARD_TYPE verfügen, um die Werte in den Deskriptorfeldern zu verwenden.  
  
 Wenn **SQLPutData** aufgerufen wird, werden die Intervallführende Genauigkeit und die Intervallsekundengenauigkeit aus den Feldern des Deskriptordatensatzes gelesen, die dem Parameter oder der Spalte data-at-execution entsprechen, d. h. APD-Felder für Aufrufe von **SQLExecute** oder **SQLExecDirect**oder ARD-Feldern für Aufrufe von **SQLBulkOperations** oder **SQLSetPos**.
