---
title: Überschreiben von führenden und Genauigkeit für die Interval-Datentypen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: fdab9e6e60311aca4ce0ae35f92e38c45fdf3702
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63018475"
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Überschreiben der Standardwerte für die Genauigkeit des führenden Intervallfelds und die Sekundengenauigkeit für Intervalldatentypen
Wenn das SQL_DESC_TYPE-Feld, der eine ARD durch Aufrufen von entweder in einen datetime-Wert oder das Intervall C-Typ festgelegt ist **SQLBindCol** oder **SQLSetDescField**, Feld SQL_DESC_PRECISION (enthält das Intervall (Sekunden) Genauigkeit) wird auf die folgenden Standardwerte festgelegt:  
  
-   6 für Zeitstempel und alle Interval-Datentypen mit einer zweiten Komponente.  
  
-   0 für alle anderen Datentypen.  
  
 Für alle Arten von Intervall wird das Deskriptorfeld SQL_DESC_DATETIME_INTERVAL_PRECISION, das die Intervall-Genauigkeit der führenden Feld enthält, auf einen Standardwert von 2 festgelegt.  
  
 Wenn das SQL_DESC_TYPE-Feld in einer APD durch Aufrufen von entweder in einen datetime-Wert oder das Intervall C-Typ festgelegt ist **SQLBindParameter** oder **SQLSetDescField**, die SQL_DESC_PRECISION und SQL_DESC_DATETIME_INTERVAL_ Genauigkeit Felder im APD werden auf den Standardwert, der bereits erwähnten festgelegt. Dies gilt für Eingabeparameter, aber nicht für e/a oder Ausgabeparameter.  
  
 Ein Aufruf von **SQLSetDescRec** legt die Genauigkeit auf den Standardwert für anführenden Intervallwert, setzt jedoch Genauigkeit das Intervall (in das Feld SQL_DESC_PRECISION) auf den Wert des der *Genauigkeit* Argument.  
  
 Wenn entweder die Standardwerte angegeben zuvor ist nicht zulässig, eine Anwendung, sollte die Anwendung durch Aufrufen von Feld SQL_DESC_PRECISION oder SQL_DESC_DATETIME_INTERVAL_PRECISION festgelegt **SQLSetDescField**.  
  
 Wenn die Anwendung ruft **SQLGetData** um Daten in eine datetime-Wert oder die Intervall-C-Typ zurückgegeben werden, die führende standardgenauigkeit für Intervall und Intervall Genauigkeit verwendet. Wenn entweder standardmäßig nicht zulässig ist, muss die Anwendung aufrufen **SQLSetDescField** entweder Deskriptorfeld festlegen oder **SQLSetDescRec** SQL_DESC_PRECISION festlegen. Der Aufruf von **SQLGetData** sollte eine *TargetType* von SQL_ARD_TYPE, um die Werte in die deskriptorfelder verwenden.  
  
 Wenn **SQLPutData** aufgerufen wird, wird die Genauigkeit "und" Interval Sekunden Genauigkeit werden aus den Feldern der Deskriptordatensatz entsprechen, die gelesen, in die Data-at-Execution-Parameter oder eine Spalte, die APD Felder für Aufrufe sind für anführenden Intervallwert um **SQLExecute** oder **SQLExecDirect**, oder ARD Felder für Aufrufe von **SQLBulkOperations** oder **SQLSetPos**.
